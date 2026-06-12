---
title: "Making the big switch, need help first!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by DJMattB241 on 2007-06-13
As I'm sure you've heard a half a million times by now, I'm thinking about (as in "on the verge of") switching from WinXP to Ubuntu, but I've got some questions that I don't know the answers to first:

1) I've got three hard drives, all with lots and lots of data on them, all formatted NTFS. I would imagine that Ubuntu won't work with NTFS, is this true? If so, would I be converting them to Fat32? If so, how would I do that without losing a metric ton of stuff in the process?

2) Programs. Most of the programs I use are available. OpenOffice, Firefox/Thunderbird, UT2004, etc. But a couple aren't. What would a good alternative for MSN Messenger be?

3) MediaMonkey. This is the (excellent) program I use to manage my music. I've got a paid lifetime license for all future updates, etc. I really enjoy this program, and the community I'm so involved with. The problem is, there are no plans any time soon for a Linux version of MediaMonkey. So... how can I use this program, or can I at all?

4) Hardware. I know my ATI video card should be fine. Not so sure about, say, my memory card reader, my usb wireless internet dongle thing, other things like that. What do I do about this?

5) General nervousness. I don't know how to install programs, I don't know the folder structures, I don't know what file types it handles, I don't know almost ANYTHING about Ubuntu, or Linux in general, in specific sorts of ways. Any sort of guide or stuff like that would be awesome.

6) I'm going to have *deep inhale* four harddrives. I've already got three, so I'd be adding one more specifically for Ubuntu. What filesystem (NTFS, Fat32, etc) should I have those hard drives in? One will be just for Windows, one just for Linux, and two media drives.

Thanks a bunch everyone!

---

### Post by Zzl1xndd on 2007-06-13
1) NTFS will work but you will need to install a little extra to get it to Write to NTFS but its easy im doing it now.

2) Amsn looks the most like MSN and works well but Pidgin/gaim is really good too.

3) Not sure but it might work with Wine or Crossover office.

4) Hard to say with the hardware without knowing what it is but try the live CD and that should let you know what will work out of the Box.

5) For anything you need we will be here to help you out in the forums/IRC and many of us myself included post our IM info and dont mind being asked that way either.

6) NTFS or Fat is fine your Ubuntu Drive will be formated in Ext3 and you can install an add on to Windows if you need to read from it.

Best of Luck

---

### Post by zvacet on 2007-06-13
You solved 1. by 6.
Install Pidgin because it have MSN inside.
I don´t know.Maybe you should try with wine.
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

Ubuntu use ext3 format.

Download LIve Cd and see if it recognize your hardware.If it does install Ubuntu.

---

### Post by mlentink on 2007-06-13
> **DJMattB241 said:**
>  I know my ATI video card should be fine.
Unfortunately, ATI can give problems. I'd carefully check the exact specs. What type is it?

> **DJMattB241 said:**
>  Not so sure about, say, my memory card reader, my usb wireless internet dongle thing, other things like that. What do I do about this?
My lexar thingy works like a breeze, but if I were you I'd see if I have a couple of bucks left for an Atheros-chipset-based WiFi-card. I recently got one for $11 that worked immediately. You'll probably need some work to get the USB-dongle working 

> **DJMattB241 said:**
> 5) General nervousness. I don't know how to install programs, I don't know the folder structures, I don't know what file types it handles, I don't know almost ANYTHING about Ubuntu, or Linux in general, in specific sorts of ways. Any sort of guide or stuff like that would be awesome. 
Look at the stickies at the begiining of this forum. Look at the Ubuntu Wiki, look at ubuntuguide. I did and learned a lot

> **DJMattB241 said:**
> 6) I'm going to have *deep inhale* four harddrives. I've already got three, so I'd be adding one more specifically for Ubuntu. What filesystem (NTFS, Fat32, etc) should I have those hard drives in? One will be just for Windows, one just for Linux, and two media drives.

You can leave your current drives as they are. Your Ubuntu drive will be formatted in ext3 by the installer, but ubuntu will read the others.

Oh. 

Before I forget:
- first try out the live-cd to see if your hardware works


Welcome and lots of success!

---

### Post by stalkingwolf on 2007-06-13
I use 3 different usb "sticks" for wifi . 2 are no name sticks one is a netgear WG111v2.  I had no problems getting any of them working or with the pcmcia card in my laptop.

---

### Post by logos34 on 2007-06-13
For write capability to NTFS (once you get ubuntu up and running):
sudo apt-get install ntfs-3g ntfs-config ntfsprogs

Works great.  It'll save you the hassle of reformatting.

For r+w to ext2/3 from windows:
fs-driver

mm - see post at bottom of this page:
[http://www.mediamonkey.com/forum/viewtopic.php?=&p=78386](http://www.mediamonkey.com/forum/viewtopic.php?=&p=78386)

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)
[https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)
[https://help.ubuntu.com/7.04/](https://help.ubuntu.com/7.04/)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Enjoy!

---

