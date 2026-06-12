---
title: "USB boot on iMac without rEFIt"
date: 2012-08-21
forum: Apple Hardware Users
---

### Post by bakegoodz on 2012-08-21
How can I boot Ubuntu on a USB stick and a Mac I can't modify? So I can't use rEFIt. I tried a USB drive I formated with usb-creator-gtk, I've been testing it with a late 2007 Macbook and it won't boot it. What Live USB install method should I use?

Backstory:
I'm taking a LAMP server admin class and for reason out of teachers control with are in the Graphics lab with all iMacs. Yes I can use xterm in Mac, but I use Ubuntu on all of my own computers and it's driving me crazy. The teacher said it would be cool if I booted my own OS on a USB drive.

---

### Post by dolphin194 on 2012-08-22
[B]It is not possible to boot from USB on your MacBook. You must use a CD in order to boot on your laptop. I have an early 2008 MacBook Pro, and it does not even support USB booting. I also tried booting both Windows and Ubuntu from USB with rEFIt without success.

To check if your Mac supports booting from USB, open your Boot Camp Assistant and check for the USB option: [/B]
[IMG]http://nonme85851.webs.com/bootcamp.png[/IMG]

If you do not have that option, your Mac does not support booting from USB.

---

### Post by skipperczt on 2012-08-22
Use this.... it works!

[http://penguintosh.com/tag/linux-usb-creator/]("http://penguintosh.com/tag/linux-usb-creator/")

---

### Post by manhattank on 2012-08-22
I'm interested in ubuntu. Have early 2008 mac pro. Would install ubuntu on it's own drive not a partition. Want to be able to boot either to OSX (10.6.8) or ubuntu. Please point me to a clear how to.
Do I just download to the empty drive and install? How should the empty drive be formatted?
Thanks

---

### Post by bakegoodz on 2012-08-24
I couldn't make it work, tried several things. I even tried with the rEFIt boot CD. The bootloader would crap out, rEFIt would tell me something like incompatible boot loader.

 I settled with a work around. I bring my laptop to class and hijack the iMAC's Ethernet. My teacher didn't care.

Now if only if the isostick was being mass produced. They are confirmed to work with MAC
[http://www.kickstarter.com/projects/elegantinvention/isostick-the-optical-drive-in-a-usb-stick](http://www.kickstarter.com/projects/elegantinvention/isostick-the-optical-drive-in-a-usb-stick)

---

### Post by philcolbourn on 2012-09-01
Another thing to try is 'native' EFI booting.

Hold down 'option' key when booting. If you get a 'windows' option, try it.

For this to work, if I understand things correctly, you need to have an EFI supported kernel or grub-efi installed.

rEFInd (not rEFIt) also works well.

---

