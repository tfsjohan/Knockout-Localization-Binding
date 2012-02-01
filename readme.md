# Knockout Localization Binding

Simplifies working with localization sites by dynamically getting text from a resource/copy document. 

## Resources
The resource file is just a json document with keys, locales and texts. It must be stored in a global variable called *resources*.

	var resources = {
		ok: {
			default: 'OK'
		},
		name: {
			sv: 'Namn',
			en: 'Name'
		},
		email: {
			sv: 'E-post',
			en: 'E-mail'
		},
		welcome: {
			sv: 'Hej <strong>#name</strong>! Du bor i #city.',
			en: 'Hello <strong>#name</strong>! You live in #city.'
		}
	};

If a text is the same for many languages it can be defined as 'default' instead of a locale. 
Text can contain placeholders for texts that is populated at runtime from an observable.

## Locale
The current locale must be stored in a global variable called *locale*.

## Markup
There are localized bindings for:
* restext
* reshtml
* resattr
* reshref (sugar for attr: { href: url })
* ressrc (sugar for attr: { src: url })

Internally these bindings get the localized text and then uses Knockouts default binding like text, html and attr.

### Basic usage
This example get a localized text with the key _email_. Depending on what the *locale* variable is set to, it will say _E-post_ or _E-mail_.

	<span data-bind="restext: 'email'"></span>

This example uses parameters to fill in the placeholders.

	<span data-bind="reshtml: { key: 'welcome', params: { name: name, city: city } }"></span>

The values name and city are observables on your view model.

