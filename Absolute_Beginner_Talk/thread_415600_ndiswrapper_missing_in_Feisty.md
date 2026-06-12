---
title: "ndiswrapper missing in Feisty"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Supercross on 2007-04-20
This is a very strange problem.  While I'm using the LiveCD I can see ndiswrapper in the package manager but yet when I'm booted into the actual install it is nowhere to be found.  It is not in the package manager, I've searched and looked manually, and I have no way of going online to apt-get it.  Did my install somehow get messed up and should I reinstall?

---

### Post by Supercross on 2007-04-20
Is this a freak occurrence and what can I do to resolve this?  I have no access to a wired connection so this is the only way for me to get on the net, and my ubuntu freezes fairly often until I install the latest fglrx driver.

---

### Post by floke on 2007-04-20
It can't be in the install - since have just checked in synaptic and there's no ndis stuff there for me. There's a site somewhere that contains all the packages so you can download to a usb via LiveCD and then install them that way - will have a nose around for you in my history now...

---

### Post by littlemazeton2 on 2007-04-20
You can install the package that is in the cd by using Synaptic Package Manager and adding the Cd in the edit menu.

---

### Post by floke on 2007-04-20
Right, this should help. 

[http://packages.ubuntu.com/feisty/net/](http://packages.ubuntu.com/feisty/net/)

From here you can download the packages you need.
If you're not sure about any dependencies etc. you can enter the packages to install in synaptic - then select 'file' and 'generate dowload support script' (something like this) - this will contain the names of all the files you need to install - dependencies etc.

So - you can then get them from the above link via LiveCD - save to usb or cd - then reboot - upload them - and away you go.

Hope this helps.

---

### Post by Supercross on 2007-04-20
> **Steve.K said:**
> will have a nose around for you in my history now...
Pardon me asking but is this a good thing or a bad thing?

---

### Post by Supercross on 2007-04-21
> **littlemazeton2 said:**
> You can install the package that is in the cd by using Synaptic Package Manager and adding the Cd in the edit menu.
I tried this too but it still doesn't appear on the cd in the package manager or anywhere else for that matter.  I don't know what is going on, where could it have gone?

---

### Post by Supercross on 2007-04-22
I hate to keeping bringing this up, but does anyone know why ndiswrapper is not appearing in the package manager once ubuntu is installed?

---

