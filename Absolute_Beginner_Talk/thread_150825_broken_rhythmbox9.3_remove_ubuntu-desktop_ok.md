---
title: "broken rhythmbox9.3: remove ubuntu-desktop ok?"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by takayuki on 2006-03-26
Hi,

i tried to install an unofficial rhythmbox 9.3 (has podcast support) and something "broke".  yeah, my bad.  the learning continues.  :)

now rhythmbox won't launch and synaptic is suggesting complete removal.  it also want to remove ubuntu-desktop.

what should i do?

thanks,

takayuki

---

### Post by Sutekh on 2006-03-26
ubuntu-desktop is just a meta-package that brings in everything you need for the default Ubuntu installation.  It doesn't actually contain the packages, but depends on them, so when you "install" ubuntu-desktop it installs everything else.

That's okay for you to remove the ubuntu-desktop package, to remove the busted RB package.

---

### Post by takayuki on 2006-03-26
thanks Sutekh,

off to remove rhythmbox and ubuntu-desktop...

---

### Post by 5-HT on 2006-03-26
Just as an aside, it is recommended to reinstall ubuntu-desktop prior to a dist-upgrade just to avoid possible problems during the upgrade.

HTH

---

### Post by takayuki on 2006-03-28
should i go ahead and reinstall it now? my rhythmbox problem is now fixed.

---

### Post by mlind on 2006-03-28
[QUOTE=takayuki]should i go ahead and reinstall it now? my rhythmbox problem is now fixed.[/QUOTE]

I say you would break it again, because ubuntu-desktop depends on earlier
rhythmbox that probably conflicts with newer one.

---

### Post by AndrewCaul on 2006-03-28
[QUOTE=mlind]I say you would break it again, because ubuntu-desktop depends on earlier
rhythmbox that probably conflicts with newer one.[/QUOTE]
Yeah, if it's working, just leave it be right now.

---

