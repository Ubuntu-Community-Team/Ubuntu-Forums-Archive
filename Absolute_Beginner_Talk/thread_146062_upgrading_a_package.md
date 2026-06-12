---
title: "upgrading a package"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by mackinax on 2006-03-17
I want to upgrade Rythmbox to 0.9.3... 
~ Should I uninstall the old version first?
~ If remove the Rythmbox package using Synaptic, it wants to remove ubuntu-desktop also. 
> The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired. [B][I]However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system)[/I][/B].
I don't fully understand the implications of that warning... 
can I somehow safely replace Rhthmbox with a new version without removing ubuntu-desktop?

Thank you

---

### Post by mlind on 2006-03-17
no, you don't need to uninstall the old one first if you're using .deb package
management, like apt-get. It will handle the upgrade process.

Ubuntu-desktop is a meta-package which assures that you have certain packages
installed. There's no harm removing it, but new packages that depend on 
ubuntu-desktop do not get installed. Usually this is problem only when doing
a dist-upgrade or using a development version of Ubuntu.

Usually removing ubuntu-desktop package is required if you want to uninstall
something that's had been installed as a default. Again, there's no harm here either
but warning is the for a reason.

---

### Post by mackinax on 2006-03-17
[QUOTE=mlind]no, you don't need to uninstall the old one first if you're using .deb package management, like apt-get. It will handle the upgrade process.[/QUOTE]
It's a downloaded package that I'll be installing via "sudo dpkg -i file.deb" ... It will still be handled?

[QUOTE=mlind]Ubuntu-desktop [...] There's no harm removing it, but new packages that depend on ubuntu-desktop do not get installed. Usually this is a problem only when doing a dist-upgrade or using a development version of Ubuntu[/QUOTE]
So, when the time comes to upgrade to Dapper, I'd then have to totally re-install ubuntu  (for the entire desktop environment to be properly upgraded)?

Ouch.

Thanks for the help!

---

### Post by mlind on 2006-03-17
[QUOTE=mackinax]It's a downloaded package that I'll be installing via "sudo dpkg -i file.deb" ... It will still be handled?
[/QUOTE]

Actually I don't know how dpkg handles these things. You should remove package
first using apt-get, then install using dpkg -i package.deb.

[QUOTE=mackinax]
So, when the time comes to upgrade to Dapper, I'd then have to totally re-install ubuntu  (for the entire desktop environment to be properly upgraded)?
[/QUOTE]

definetly not! You just install that meta-package back, and upgrade will work
just like it should. Think it as a "default set of ubuntu desktop applications"
if you remove one default app, you must remove the meta-dependency too.

If you install it back, you'll get all the dependencies back too.

---

### Post by mackinax on 2006-03-17
> You just install that meta-package back, and upgrade will work
just like it should.
Ah, I didn't consider doing it that way. That's not a bad option.

I appreciate the help!

---

