---
title: "duel booting help"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Lderan on 2007-07-27
Sorry if this is answered some place else but I can't find what exactly i need to do to help me.

I installed Ubuntu on my PC leaving an empty partition for install XP on, which i did. Everything was fine till then. Now I can't seem to boot into ubuntu. There is no option for which OS to boot into, it just loads XP.

What can i do? will I need to re-install everything?

---

### Post by AceofSpades19 on 2007-07-27
did you install grub to the mbr or to ubuntu's parition?
you might just have to reinstall ubuntu and make sure grub gets put on the mbr

---

### Post by Lderan on 2007-07-27
How do i install grub to the mbr? and when ? sorry im completly hopeless at this.

---

### Post by MQMike on 2007-07-27
Your XP overwrote the Ubuntu bootloader in the Master Boot Record.  It can be fixed.
You need to restore GRUB to the MBR.

Here’s two sources that show you how:

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

You will need to use your Live CD to get a Terminal and then to get a GRUB prompt (by typing sudo grub) and then re-install GRUB following the how-to's.

---

### Post by Lderan on 2007-07-27
Thankyou very much ^.^

I suppose i can use Firefox off the live cd to read the how-tos

---

### Post by MQMike on 2007-07-27
Yes -- or whatever browser is included on the Live CD by default.  In Kubuntu I just use Konqueror when this happens, of the live CD.

---

### Post by Lderan on 2007-07-27
I have managed to boot into ubuntu yay! but the grub menu doesn't display windows XP
Very confusing

---

### Post by MQMike on 2007-07-27
Strange…?

Sounds like you have to edit the GRUB boot menu (/boot/grub/menu.lst) to include a boot entry for Windows:

title Windows XP or whatever
rootnoverify (hd0, y)
makeactive
chainloader +1


y = the partition XP is on; counting starts at zero, so partition3, for example, means y = 2.
the How-To’s tell you how to edit menu.lst.  Do it with root privileges (sudo), and don’t forget to save the edited menu.lst when done (File-Save, File-Quit).

---

### Post by Lderan on 2007-07-27
Yay now it works, thanks alot MQMike :D

---

### Post by MQMike on 2007-07-27
That's Great!  Congratulations, Lderan-- That was fast on your part!
See GRUB is fun, right?

---

