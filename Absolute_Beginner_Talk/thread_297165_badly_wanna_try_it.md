---
title: "badly wanna try it"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by 2j4ez on 2006-11-10
Been searching the internet for hours and not getting anywhere found loads of posts on how to boot with usb cd rom

I downloaded the latest version of ubuntu and it boot up to busybox v1.1.3

and says error usb 4-3

if i reboot and press f6 delete all the text and type mount /dev/scd0 /cdrom
all this text comes up then hangs (see pic)

maybe i did it something wrong  

tryed a floppy bootdisc but it does not find my usb cd rom

anyone got any ideas??

---

### Post by Velotix on 2006-11-10
USB CD-ROM? You might want to clarify that for me. Do you mean:

1) An external CD-ROM drive that plugs into a USB port
2) A USB disk drive (in which case it's not a CD)

The easiest way to try the LiveCD is to load it on an internal CD-ROM drive - I'm guessing you don't have that option. If you do, definitely try that first.

---

### Post by 2j4ez on 2006-11-10
it has no internal cd rom only usb one

---

### Post by Sef on 2006-11-10
Do you have a usb key? If so, then load the os on there and run it from that.

---

### Post by 2j4ez on 2006-11-10
what size would i need and is easy to do?
once loaded can i install it to the harddrive?

---

### Post by CatKiller on 2006-11-10
There are some instructions on how to install from a USB stick here:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
I haven't ever tried it myself. Good luck!

It's also possible that the install didn't fail because of the USB drive, but because of some other factor. I've not had problems like that myself, so I can't really help you troubleshoot them. If it's a laptop, you could try a search on the model number to see if anyone's managed to fix a similar problem, or search on error messages to find out what they mean. There are quite a few esoteric options you can give the installer to make it do things differently, but I really don't understand what they do.

Also, you say you downloaded the "latest version": do you mean Edgy Eft (6.10)? You might try 6.06 LTS (Dapper Drake) instead - it's been out longer, more people have tried it, and more people have overcome problems with it. Plus, Edgy always was a bit experimental.

Welcome to the community, and I hope you get it cracked.

---

