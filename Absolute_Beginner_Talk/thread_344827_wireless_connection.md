---
title: "wireless connection"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by dscott60 on 2007-01-23
I'm brand spanking new to Ubuntu/Linux and I just installed 6.10 a couple of days ago.  I'm impressed with what I see so far, but I have one big issue.  My computer doesn't see my wireless adapter. I have a Zonet ZEW2500p connected to my computer. How do I get the computer to recognize it?


Thanks

---

### Post by mikewhatever on 2007-01-23
Start from here [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)

---

### Post by dscott60 on 2007-01-23
Thanks!  If in the instructions it says this

[COLOR="Red"]For ndiswrapper to function, you need to load a module. To do this, type:

sudo depmod -a
sudo modprobe ndiswrapper[/COLOR]

Do I type the first line and hit return, then type the second line and hit return?  Because when I did, it came up with the following message:

[COLOR="red"]dave@dave-desktop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
dave@dave-desktop:~$ [/COLOR]

---

