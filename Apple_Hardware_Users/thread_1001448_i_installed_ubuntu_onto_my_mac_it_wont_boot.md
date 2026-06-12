---
title: "i installed ubuntu onto my mac it wont boot"
date: 2008-12-03
forum: Apple Hardware Users
---

### Post by maclin on 2008-12-03
i installed ubuntu onto my mac, as a dule boot, set the proportioner to "use free space. But i can't seem to get ubuntu to boot only mac osx 10.5 i think i need a boot loader
plz help

---

### Post by DieB on 2008-12-04
on a ubuntu install normally grub gets installed to (this is a boot manager!) - so everything SHOULD work.

pls be more specific ;)

---

### Post by iAtari on 2008-12-04
Check out this article for dual-booting:
[Dual-Booting]("https://help.ubuntu.com/community/MacBook")
As the help article states, your best bootloader/EFI selector is rEFIt. It's what I use, and it works well.

---

### Post by cyberdork33 on 2008-12-04
> **maclin said:**
> i installed ubuntu onto my mac, as a dule boot, set the proportioner to "use free space. But i can't seem to get ubuntu to boot only mac osx 10.5 i think i need a boot loader
plz help

What exactly does it do? Try rEFIt first and see if it works then, but you likely need to follow the steps here:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by maclin on 2008-12-04
well mac boot fine but it acted like ubuntu dose not exist

---

### Post by cyberdork33 on 2008-12-05
> **maclin said:**
> well mac boot fine but it acted like ubuntu dose not exist

because the computer thinks it doesn't exist... see the link in my previous post. That should fix it.

---

### Post by maclin on 2008-12-05
well the proportions dose not show up on mac, in the disk utility it say that there is a error with the drive oh and i have leopard 

 what i am try ing to do is have mac boot ubuntu when i hold down a button or hold down the option key and select ubuntu to boot

---

### Post by pxwpxw on 2008-12-05
> **maclin said:**
> well the proportions dose not show up on mac, in the disk utility it say that there is a error with the drive oh and i have leopard 

 what i am try ing to do is have mac boot ubuntu when i hold down a button or hold down the option key and select ubuntu to boot

You need to reinstall the grub bootloader, as explained in the link that Cyberdork33 gave you.

---

### Post by maclin on 2008-12-05
coll i got it to work thy 
but how do you get airport to work?

---

### Post by pxwpxw on 2008-12-05
> **maclin said:**
> coll i got it to work thy 
but how do you get airport to work?

you should start a new airport wireless thread if you need help with that, it depends what mac you have, but first you should read what is in the Sticky Thread at to top of this forum, it should be explained in  there somewhere.
Please mark this thread [SOLVED]

Sticky: Apple Intel Users FAQ
[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

---

### Post by maclin on 2008-12-06
well i got it to work by accident
a restricted drivers window poped up that fix it 
then i upgraded to ubuntu 810 and then it stopped working 
the driver is installed but it still wont work 
oh and the sound wont work

---

