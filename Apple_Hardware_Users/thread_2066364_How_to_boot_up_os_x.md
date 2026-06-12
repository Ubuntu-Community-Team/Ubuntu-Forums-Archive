---
title: "How to boot up os x???"
date: 2012-10-04
forum: Apple Hardware Users
---

### Post by Joshua123454321 on 2012-10-04
Hi,
I am new to Ubuntu (I installed it on my macbook 5 hours ago) and would like to go back to OS X temporarily, however I can't boot up snow leopard. Can you please tell me how?

Thanks in advance,
Joshua:p

---

### Post by Joshua123454321 on 2012-10-04
Any help would be useful.

---

### Post by windscape on 2012-10-04
Hi,

A quick Google search revealed the following:
Hold down the "Option" key on the Macbook keyboard before the "Apple logo" on the gray screen appears. Continue holding it until you see images of two "hard drives" on the screen. 

Read more: How to Dual Boot a MacBook | eHow.com [http://www.ehow.com/how_6788299_dual-boot-macbook.html#ixzz28M1a4Uzd](http://www.ehow.com/how_6788299_dual-boot-macbook.html#ixzz28M1a4Uzd)

---

### Post by Joshua123454321 on 2012-10-05
I already tried that, only one hard drive appears.

---

### Post by Joshua123454321 on 2012-10-05
I have it backed up(on a six year old hard drive) and still have my original software dvds.

---

### Post by AndroidICS on 2012-10-06
I am using a windows computer, so if this is a dumb thought, then please ignore this. Grub should have been installed on your Mac, allowing you to choose your OS before it boots. I am guessing you don't have Grub... Please try this tut I found on the web to get Grub. [http://www.av8n.com/computer/htm/grub-reinstall.htm](http://www.av8n.com/computer/htm/grub-reinstall.htm)

---

### Post by Johnyburd on 2012-10-06
If only one hard drive appears then you probably have overwritten OS X.  If so then you can plug your backup in and boot from the OS disk and tell it to restore from the backup drive.  To dual boot Ubuntu and OS X you have to go to disk utility and make a MSDOS partition.  Then boot from your Ubuntu install disk and select install alongside your current OS.
hope that helps.  ;)

---

### Post by este.el.paz on 2012-10-08
> **Johnyburd said:**
> If only one hard drive appears then you probably have overwritten OS X.  If so then you can plug your backup in and boot from the OS disk and tell it to restore from the backup drive.  To dual boot Ubuntu and OS X you have to go to disk utility and make a MSDOS partition.  Then boot from your Ubuntu install disk and select install alongside your current OS.
hope that helps.  ;)

Folks:

I've got three different macs set up for dual boot OSX & various Linux flavors, indeed I would tend to agree with JB that if only one drive appears then probably OSX was overwritten.  If you just need to use SL intermittently then you could use firewire to connect to the ext HD, restart, hold option botton and if you have a cloned version of the OS there you could boot from the ext HD OSX . . . I don't know if the Back-up system can be used to boot, or if you would have to "Restore" it back first.  Otherwise you do have to do some prep in Disc Utility to set up some "free space" that the Linux installer will recognize as the place to install into . . . if you try to reinstall OSX back on top of the Linux apparently OSX is not friendly to other systems . . . .  Actually, in the Intel system MBPro dual boot set up it is recommended to install "rEFIt" . . . which operates as the "system manager" between OSX and the Linux systems, and when you select the Linux image it takes you to GRUB window . . . so you need GRUB, but you also need rEFIt . . . .


e.e.p.

---

### Post by Information Technology on 2012-10-08
> **Johnyburd said:**
> If only one hard drive appears then you probably have overwritten OS X.  If so then you can plug your backup in and boot from the OS disk and tell it to restore from the backup drive.  To dual boot Ubuntu and OS X you have to go to disk utility and make a MSDOS partition.  Then boot from your Ubuntu install disk and select install alongside your current OS.
hope that helps.  ;)

Very good info.

Thank you

---

