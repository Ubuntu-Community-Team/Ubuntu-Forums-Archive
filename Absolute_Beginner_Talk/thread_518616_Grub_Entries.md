---
title: "Grub Entries?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by nwkegan on 2007-08-06
This is probably a really dumb question, but with my grub entries, why do I have an outdated kernel in my grub? After being upgraded, I assume it keeps the entry? How do I remove the outdated entry and kernel? Or can I not do that?

Thanks in advance, I'm very new to this, just installed ubuntu yesterday.

oh, and while I'm at it, how do I come out of hibernate? do I just turn the computer back on? also, is the data saved for hibernating deleted after coming back out?

---

### Post by proalan on 2007-08-06
in a terminal

```
gksudo gedit /boot/grub/menu.lst
```

from experience i would advise you keep 1 or 2 older kernel options as a fall back option if something goes wrong

hibernation support is still a problem with many users including myself

---

### Post by pyxu619 on 2007-08-06
Linux keeps the old kernel in the boot so that you can go back if anythings goes wrong and not leave you a dead machine. If you feel your machine is stable enough now, then you can remove it by typing in the terminal

```
sudo gedit /boot/grub/menu.lst
```

Then just scroll down and delete the entry where you see the old kernal version. 

If the above code doesn't work the try

```
sudo gedit /boot/menu.lst
```

Welcome to Ubuntu. :)

---

### Post by Tux Aubrey on 2007-08-06
It is there for your protection - just in case the new kernel introduces incompatibilities.

The menu can be edited - it is contained in the file /boot/grub/menu.lst

That file is read-only so you need to open it from the terminal:
> 
gksudo gedit /boot/grub/menu.lst

(replace "gedit" with another plain text editor if you are using kubuntu or xubuntu.

 menu.lst is heavily commented with instructions on how to edit it.  There are lots of options. Be careful!

---

### Post by nwkegan on 2007-08-06
Thank you for the help!

just for reference, how would I uninstall older kernels?

and is there a key combination to come out of hibernate so I can test if it works for me? or does it just flat out not work?

is there a hotkey for the terminal?

and sorry, but I have yet another question, is there anyway to add a desktop shortcut to a folder?

---

### Post by proalan on 2007-08-06
you should use

gksudo
or
gksu

in place of sudo for graphical root privileges to avoid breaking your system. 

explanation here
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by stevebakerj on 2007-08-06
> **nwkegan said:**
> Thank you for the help!

just for reference, how would I uninstall older kernels?

and is there a key combination to come out of hibernate so I can test if it works for me? or does it just flat out not work?


Use Synaptic or Kpackage, I don't know which you use, search on kernel, highlight or mark the old kernel you want to remove and click uninstall. KPackage will also update your grub menu.lst when you uninstall the kernel. I don't know if Synaptic does this.

Like most people though I always keep at least one kernel back just in case of incompatibilities. If you just want to keep you boot screen neat rather than deleting the entry from the menu.lst just # it out, that way if you need it its simply a matter of removing the #'s

---

