---
title: "how do you install JAVA"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by RAV TUX on 2005-11-21
does anybody know a quick way to install JAVA on Ubuntu ((hoary hedgehog)), I'm trying to use IRC...tried going to this website and downloading directly....downloaded but how do  activate the install?

[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)

---

### Post by 23meg on 2005-11-21
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by MarcDM on 2005-11-21
QUOTE=23meg][https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)[/QUOTE]
I use [Blackdown java]("http://www.blackdown.org/"). Cuz it seems to work better than Sun's java. Especially in mozilla.

To install it Open Synaptic :
Select Settings -> Repositories from the menu, when the list comes up, click Custom. Add this as the apt line :

```
deb ftp://mirrors.ibiblio.org/pub/mirrors/blackdown/debian/ sarge non-free
```

Save that and hit yes when asked to reload. 

Now you can install j2re1.4, and j2re1.4-mozilla-plugin and a couple other java apps from Synaptic. 

*NOTE* Synaptic might complain about packages not being authorized because of no public key. Some GPG error. It's not one you should take lightly,  but in our case it's harmless. It happens because apt (running behind synaptic) doesn't have the public keys necessary to verify the authenticity of the packages coming from a repo.

Hope this helps.

---

