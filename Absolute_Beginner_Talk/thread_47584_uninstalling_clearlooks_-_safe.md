---
title: "uninstalling clearlooks - safe?"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by glandula on 2005-07-09
hello

i installed clearlooks 0.6.2-1, but its working really slow on my desktop so i want to go back to the 0.5 something, that as far as i can remember is the one that is installed by default.

so how do i revert? the only way i can find is to uninstall clearlooks and then reinstall the old version. but uninstalling clearlooks means that gdm,ubuntu-artwork and ubuntu-desktop also will be uninstalled.

im just wondering if this is safe. if ubuntu desktop is uninstalled what does that mean? does it mean the whole gui will be gone and im stuck in text mode only?

thanks

---

### Post by Knome_fan on 2005-07-09
I don't think you have to uninstall.
Just start synaptic, search for clearlooks and select it, then select package from the menu (I think that should be the name, but I'm not entirely sure as I'm on a german system) and then choose force version. Now you should be able to select the hoary version.

Uninstalling ubuntu-desktop should be no problem as it is only a meta-package that depends on all the default ubuntu packages. Gdm however could be a problem, as gdm is your graphical login screen.

---

### Post by glandula on 2005-07-09
[QUOTE=][/QUOTE]
 sweet, thanks a lot, it worked:)

this synaptic thing never stops amazing me. ive been looking for a cpu cooler software for days only for now to find athcool is in synaptic

i love ubuntu more and more every day, and its now been 4 days since i booted into windows :D

---

