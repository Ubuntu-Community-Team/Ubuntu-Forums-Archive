---
title: "Ubunto 7.1 gusty w/winxp"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by woollyrancher on 2008-02-26
I have win xp on my laptop.  I downloaded ubunto to a file.  Can I run ubunto seperately without deleting my winxp.  I want to test drive ubunto before I make the switch.

---

### Post by Crafty Kisses on 2008-02-26
> **woollyrancher said:**
> I have win xp on my laptop.  I downloaded ubunto to a file.  Can I run ubunto seperately without deleting my winxp.  I want to test drive ubunto before I make the switch.

You sure can, you can run Ubuntu right off the LiveCD. :)

---

### Post by Northsider on 2008-02-26
Did you download the Live-cd and burn it to a disk?  With the live-cd you can boot from it and test Ubuntu to see if you like it and your hardware works correctly.

---

### Post by Iehova on 2008-02-26
Yes, you can have both Ubuntu and XP installed side by side. You should follow [this guide](https://help.ubuntu.com/community/GraphicalInstall). In step 5 of the installer, be sure to select the option to resize your existing partition and install Ubuntu in the newly-freed space. Have fun!

EDIT: Also, the next version of ubuntu (8.04, released in April) will allow you to install Ubuntu *within* Windows and try it out from there, if I remember correctly...

---

### Post by northern lights on 2008-02-26
Certainly. At the end of the Ubuntu install, a bootloader (GRUB) will be installed. In the case of a previously installed Windows, it will appear in the bootmenu. 

This is not the case with an already installed Ubuntu, when (re)installing Windows, though. (Shakin' the fist the direction of Redmond)

Anyways, if you have 10 to 20 gig available, that's wnough to play around with Ubuntu a bit before getting rid of, or seizing to boot Windows. Resize (one of) your NTFS partitons, by let's say 21 gig, if that's not a pain, and create a 20 gig ext3 and a 1 gig swap. Install.

Also, you'll enjoy[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by shooting_rubber on 2008-02-26
Burn the ISO to a blank DVD by using [http://www.dvddecrypter.org.uk/](http://www.dvddecrypter.org.uk/) (DVD Decrypter).  After installing this program open it and go to Mode - Iso - Write.  After this is done, insert the disc into the drive, restart the computer, and boot from the disc.  When loaded, click the first option in the menu, by toggling up or down using the up or down keys and clicking enter.  You can now try it out without installing it at all.  If you like it you can install it so that at start-up you can choose to boot XP or Ubuntu.

Hope I Helped.

---

### Post by Crafty Kisses on 2008-02-26
> **woollyrancher said:**
> I have win xp on my laptop.  I downloaded ubunto to a file.  Can I run ubunto seperately without deleting my winxp.  I want to test drive ubunto before I make the switch.

You can also run Ubuntu in Windows, you can look at other options as well, like Wubi.

---

