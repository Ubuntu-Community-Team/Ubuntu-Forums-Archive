---
title: "Dell XPS M1330 with Ubuntu 7.04, how?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Johnson on 2007-09-16
**Hardware**
[I]Intel® Core™ 2 Duo T7300-prosessor (2,0 GHz, 800 MHz, 4 MB L2-buffer)
Tuxedo Black og 0,3 megapikslers kamera for White-LED-skjerm
Thin & light 13.3" UltraSharp™ WXGA (1280x800) White-LED Display (300 nits) with TrueLife™
2048 MB 667 MHz Dual Channel DDR2 SDRAM [2 x 1024]
160 GB (7200 rpm) SATA-harddisk
128 MB nVidia® GeForce® 8400M GS
Fast 8x DVD+/-RW
9-cellers primært litiumionbatteri (85 W/t)
Intel® Next-Gen Wireless N Mini-kort - Europa[/I]

**My Questions**
How will Ubuntu 7.04 work with Dell XPS m1330, any people with experience?

**There are few issiues on my mind**
Dell XPS m1330 has HDMI so I can hook it up with my Samsung LCD TV so I can watch movies from the laptop. Will that work in Ubuntu 7.04?

How does Ubuntu 7.04 work with the Intel® Core™ 2 Duo T7300-prosessor?

Big problem with aMSN I've experienced that is it looks awful because of the fonts in the program don't have AA, it does not have the smooth fonts. (And a side question on that, can I change the aMSN icon by the way?)

And I think Wine also looks horriable ugly and I want to store my photos safe and have a good system on them in Ubuntu 7.04, but I don't want to use digiKam and if I would use Adobe Photoshop _Lightroom_ I would have to use Wine. So is there any other real good photo manager/editing/album programs out there? Something pro.

---

### Post by Celestial Teapot on 2007-09-16
EDIT: Sorry I couldn't be of help. I'm going to try to install 7.10 on my almost identical M1330 and forget about Feisty.
           
Ubuntu rocks, espresso sucks.

---

### Post by Johnson on 2007-09-16
Anyone? :(

---

### Post by maddog39 on 2007-09-16
Im shocked ubuntu even ran on that system frankly. Unforunately, HDMI is a porprietary connector and im almost positive you will not be able to get that to work. The intel processor is fine, they are all based on the same or similar architecture. For a photomanager, try FSpot.

---

### Post by sunshine135 on 2007-09-18
It works well. I am typing to you from within Ubuntu as we speak on my M1330. I can give a few suggestions that will save you hours of grief:

If you are keeping Vista (I did), partition your drive from within Vista. Just shrink the Vista Partition (the largest one). Leave your recovery and Media direct partitions alone. simply leave it as free space for your Ubuntu and swap partitions. Gnome will handle your dual boot with ease.

If you are using the live CD, start the load in safe graphics mode press F6, and change the quiet splash to break=top. Otherwise you will get the dreaded tty error.

The recent Nviidia drivers work just fine, but you will need to do a manual install.

My source file seemed corrupted. I simply updated the http addresses to my country code, and changed them from http:// to ftp. This worked fine.

I am still working on getting the sound to work.  I understand that someone has figured out the issue.

I do not know if the HDMI will work. Dual monitors were no issue using the video card port.


Best of luck. I know these tips will save you some time. I am a noob, so I have learned a lot in a week. For all of the cool programs, Ubuntu is well worth it.

Regards,

SunDog

---

### Post by rhonaldmoses on 2007-10-21
> **Johnson said:**
> **Hardware**
[I]Intel® Core™ 2 Duo T7300-prosessor (2,0 GHz, 800 MHz, 4 MB L2-buffer)
Tuxedo Black og 0,3 megapikslers kamera for White-LED-skjerm
Thin & light 13.3" UltraSharp™ WXGA (1280x800) White-LED Display (300 nits) with TrueLife™
2048 MB 667 MHz Dual Channel DDR2 SDRAM [2 x 1024]
160 GB (7200 rpm) SATA-harddisk
128 MB nVidia® GeForce® 8400M GS
Fast 8x DVD+/-RW
9-cellers primært litiumionbatteri (85 W/t)
Intel® Next-Gen Wireless N Mini-kort - Europa[/I]

**My Questions**
How will Ubuntu 7.04 work with Dell XPS m1330, any people with experience?

**There are few issiues on my mind**
Dell XPS m1330 has HDMI so I can hook it up with my Samsung LCD TV so I can watch movies from the laptop. Will that work in Ubuntu 7.04?

How does Ubuntu 7.04 work with the Intel® Core™ 2 Duo T7300-prosessor?

Big problem with aMSN I've experienced that is it looks awful because of the fonts in the program don't have AA, it does not have the smooth fonts. (And a side question on that, can I change the aMSN icon by the way?)

And I think Wine also looks horriable ugly and I want to store my photos safe and have a good system on them in Ubuntu 7.04, but I don't want to use digiKam and if I would use Adobe Photoshop _Lightroom_ I would have to use Wine. So is there any other real good photo manager/editing/album programs out there? Something pro.
Hi,

Ubuntu 7.10 works fine with DELL XPS M1330 with small problems if you are doing clean install. If you want to do a clean install for dual boot (along with Vista and MediaDirect), follow the below link:

[http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html](http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html)

---

