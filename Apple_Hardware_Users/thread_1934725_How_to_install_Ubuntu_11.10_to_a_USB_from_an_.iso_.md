---
title: "How to install Ubuntu 11.10 to a USB from an .iso for Macbook Air"
date: 2012-03-02
forum: Apple Hardware Users
---

### Post by zashenka on 2012-03-02
Good News everyone!!!!

so i have this macbook air (without a CD drive) but i want to install ubuntu on my 8gb USB drive, i dont have access to a Windows PC but i do have Ubuntu 11.10 installed via  VMware Fusion in this mac (im actually sending this from ubuntu) but since my HD is failing, it gets corrupted about 2 times a week and i have to format it every time.

Is there a way to install ubuntu on my usb and be able to boot my mac into ubuntu via the usb?

Thanks in advance.

WOB WOB WOB WOB WOB (zoiderg)

---

### Post by Double.J on 2012-03-02
Hi there zashenka,

If you're in the VM.. open the dash and type in "start up disk creator"

Use this tool to make a live installer on the USB drive and be sure to add a persistence file - this will enable you to save changes you make on the installer.

I think the most important thing at the moment is to check your backups - make sure that you have anything and everything on the HDD backed up somewhere safe - they can just go completely and totally without warning at anytime, leaving you with no way to get the data off.

This is not as good for long term use as a full install to USB drive, but it is quick and easy, and shouldn't slow down too much for short term use until you get a new HDD.... Just remember to download a recent ubuntu ISO to make the usb from - you don't want to install updates on a live CD really - the old packages can't be deleted, so it just starts taking up quite a lot of space and slowing the system down.

Hope it helps!

EDIT: Sorry reading that back, i wasn't very clear about a full install to USB stick - you do it the exact same way as a normal install, making sure you install grub on it... however the downside is that you need a very large USB- 8GB min, 16 recommended, and the OS behaves as if it were a normal HDD - lots and lots of read/write cycles so it can shorten the life of your stick. You can get a wubi install on a usb stick, but this does need a windows PC I'm afraid.

---

### Post by zashenka on 2012-03-02
Well i did this but when i try to boot form the usb its not even recognized by the mac in the boot menu (where you choose from which HD to boot) i restarted and looked inside the usb and all the files are in there... 

also i now have access to a Windows computer, if its easier to make.


thanks for the prompt answer gnu/mirow

---

