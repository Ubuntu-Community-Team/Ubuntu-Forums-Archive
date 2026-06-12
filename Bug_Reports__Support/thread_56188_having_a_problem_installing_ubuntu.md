---
title: "having a problem installing ubuntu"
date: 2005-08-11
forum: Bug Reports / Support
---

### Post by syr0kill on 2005-08-11
I have windows 2000 profesional and i used partition magic to make a new partition on my hard drive for ubuntu 10 gb, i donwloaded ubuntu and burnt the .iso to a cd but now my problem is how do i install it to the new partition i tried restarting my pc with the disk in my cd rom, does the new partition have to br primary, i have mine on logical?? well if anyone could help me on this id be very happy, this will be my first time ever installing *nix please help!! ps i made the new partition Linux ext3 just wanted to add that.

---

### Post by Digitallysick on 2005-08-11
i used partiton magic, and formated about 40 gigs for Fat 32, i think thats what you should do, also make sure your bios is setup to boot from your cdrom before your harddisk, it should bring up the ubuntu install

---

### Post by syr0kill on 2005-08-11
i got ubuntu installed now the only problem is its not recongnizing my ati graphics card

---

### Post by varunus on 2005-08-11
There's a howto on installing the ATI drivers over in the Hoary Tips and Tricks section of the forum.

If your card is a bit older (easy to install):
[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

If your card is one of the new ones (I believe X600 or above model # wise), or you just want the newest drivers you can get (a little harder to install):
[http://www.ubuntuforums.org/showthread.php?t=32495](http://www.ubuntuforums.org/showthread.php?t=32495)

Also, if you want to get into a GUI, you can use the generic video driver.  Boot into recovery mode from the grub prompt, and enter:
```
sudo nano /etc/X11/xorg.conf
``` 

Scroll down to the Device section and replace the driver (which will be ati or radeon) with "vesa".  Then type CTRL-X to exit (hit y to save your changes).  Then type "reboot".  You should have a GUI, albeit a bad one.

---

