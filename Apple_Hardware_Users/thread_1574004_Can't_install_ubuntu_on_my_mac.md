---
title: "Can't install ubuntu on my mac"
date: 2010-09-13
forum: Apple Hardware Users
---

### Post by RadiationHazard on 2010-09-13
Okay, so I am not just posting this because something didn't work the first time. I have followed several tutorials look up problems others have had and everything else that I can think of and I can't figure out what to do anymore. I have rEFIt installed on my mac and my hard drive is partitioned. I have tried ubuntu 9.04, ubuntu 10.10 beta, fedora 13, and linux mint and none of them are working. They all do the exact same thing. It will start to boot then the screen will just go black and it won't do anything else. I've tried different burn speeds and different dvd's. I don't know what else to do now. 

I just want to thank everyone in advance for any and all help offered!

---

### Post by MegaLoler on 2010-09-13
ppc or intel?
also are you booting from an external or an internal drive?
from my experience, the screen goes black for a few minutes sometimes.  How long does it stay black?

---

### Post by techgrl on 2010-09-13
I feel your pain. I, too, have tried from soup to nuts on my Power Mac G3's & G4's.

Attached is what I get right before I am expecting to get to my very first desktop session. I have modified the xorg.conf file and nothing!

It seems as if display issues are at the heart of all Mac --> Linux conversions.

Sucks.

---

### Post by borth92 on 2010-09-13
have a look here: [https://help.ubuntu.com/community/SwitchingToUbuntu/FromMacOSX](https://help.ubuntu.com/community/SwitchingToUbuntu/FromMacOSX)
also, what graphics chip is in your mac?

---

### Post by RadiationHazard on 2010-09-13
I have a Macbook 5.2, It is intel. and the screen stays black for about 20 minutes before I get tired of it and restart the computer.

EDIT: PS. my graphics card is a NVIDIA GeForce 9400M. I really don't think it has anything to do with my graphics card. Everything seems to be working fine and then it just stops.

---

### Post by RadiationHazard on 2010-09-14
I decided I would make a video before I went to sleep showing exactly what is happening. if you listen you will be able to tell that it is booting off the cd, then all of a sudden the cd drive just stops doing anything. (The last thing I tried installing was Linux Mint because I couldn't get Ubuntu to install so that's why it's booting Linux Mint but it does the exact same thing with all of them.) I really want to try to get this fixed so if anyone knows what's going on and how to fix it please let me know!

[http://www.youtube.com/watch?v=3Xs1vkbAPJM](http://www.youtube.com/watch?v=3Xs1vkbAPJM)

Thanks again for the responses!

---

### Post by RadiationHazard on 2010-09-15
Does nobody know what's going on and why I can't install ubuntu? :confused:

---

### Post by techgrl on 2010-09-16
When in doubt, try mint ppc (v 5, I think). I have just had some overnight success and now have 5 viable Linux Mint old MACs. PPC G3's & G4's. I am documenting the journey.

_**RESOURCES**_

Get this first:
[http://ftp.nl.debian.org/debian/dists/lenny/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ftp.nl.debian.org/debian/dists/lenny/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)

Then:
[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

For more info:
[http://linuxmint.com/](http://linuxmint.com/)

---

### Post by linuxway on 2010-09-16
I have the same problem and nothing worked on powerbook g4. 
I tried to install debian lenny but i couldnt connect to the internet during the installation. 
and i dont know what else to do .

---

### Post by linuxopjemac on 2010-09-16
wired connection should work out of the box.

---

### Post by RadiationHazard on 2010-09-16
> **techgrl said:**
> When in doubt, try mint ppc (v 5, I think). I have just had some overnight success and now have 5 viable Linux Mint old MACs. PPC G3's & G4's. I am documenting the journey.

_**RESOURCES**_

Get this first:
[http://ftp.nl.debian.org/debian/dists/lenny/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ftp.nl.debian.org/debian/dists/lenny/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)

Then:
[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

For more info:
[http://linuxmint.com/](http://linuxmint.com/)

If you watch my video you will get to see what happens when I attempt to boot linux mint. I have a macbook 5.2. Also, I tried burning that link that you responded on here with (mini.iso : [http://ftp.nl.debian.org/debian/dists/lenny/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ftp.nl.debian.org/debian/dists/lenny/main/installer-powerpc/current/images/powerpc/netboot/mini.iso) and it just says that the media is not bootable and to put a bootable media in and press any key.)

Thank you for the response! hopefully someone can help me get linux installed on my macbook soon :)

Video: [http://www.youtube.com/watch?v=3Xs1vkbAPJM](http://www.youtube.com/watch?v=3Xs1vkbAPJM)

---

### Post by linuxopjemac on 2010-09-17
This mini.iso is for PowerPC based machines, you own an Intel one.

---

### Post by CodeJoker on 2010-09-17
I installed Xubuntu 10.04 "Lucid Lynx" on a dozen machines (PPC G4 and Intel) without any problem. I strongly recommend this version as it appears to be very reliable. Ubuntu 10.04 works too, but with some restrictions regarding CD/DVD-drives. You need at least 192 MB of RAM. Works for me with all my graphiccards, from some old ATI Rage 128 Pro over NVIDIA Geforce MX to ATI Radeon 9xxx series.

Good luck!

---

### Post by RadiationHazard on 2010-09-17
I just tried to install Xubuntu on my Macbook 5.2 and this is what happend

[http://www.youtube.com/watch?v=zCw08HgKv90](http://www.youtube.com/watch?v=zCw08HgKv90)

It did the EXACT same thing as everything else I've tried :(

---

### Post by RadiationHazard on 2010-09-18
bump

---

### Post by RadiationHazard on 2010-09-21
bump v2

---

### Post by RadiationHazard on 2010-09-24
bump v3

---

### Post by entangled on 2010-09-25
This may not be the answer for you but here's what I did.
I've been suffering this problem on my new iMac 21.5 (11,2 i3). All linux live CDs would give black screen even though I could hear the disc loading up.

I've got round the problem for my system by doing two things:
1   connecting an external monitor through the Mini Display port.
2   Using F6 on the grub boot menu to add options - radeon.modeset=0 nomodeset

Superficial reasons:
The boot splash screen is only output to the MD port.
Kernel modesetting doesn't work with the present radeon driver.
When X runs it only outputs to the MD port. 

I'm hoping that someone is already working on fixing these problems but I'll try to raise a launchpad bug against X.
...It is discussed in Launchpad bug #597070

---

### Post by RadiationHazard on 2010-10-01
> **entangled said:**
> This may not be the answer for you but here's what I did.
I've been suffering this problem on my new iMac 21.5 (11,2 i3). All linux live CDs would give black screen even though I could hear the disc loading up.

I've got round the problem for my system by doing two things:
1   connecting an external monitor through the Mini Display port.
2   Using F6 on the grub boot menu to add options - radeon.modeset=0 nomodeset

Superficial reasons:
The boot splash screen is only output to the MD port.
Kernel modesetting doesn't work with the present radeon driver.
When X runs it only outputs to the MD port. 

I'm hoping that someone is already working on fixing these problems but I'll try to raise a launchpad bug against X.
...It is discussed in Launchpad bug #597070

Okay, I will try this and report back and let you know how it went. *crosses fingers*

---

### Post by RadiationHazard on 2010-10-01
> **RadiationHazard said:**
> Okay, I will try this and report back and let you know how it went. *crosses fingers*

Okay, I just tried it. It didn't do anything. I am starting to think it is impossible to install ubuntu on this macbook and it's really frustrating. I have tried about 5-10 different versions of linux and they all do the EXACT same thing. it starts to boot, I click install and then the disc drive just seems to turn off. it stops making noise and then NOTHING else happens. Idk what to do anymore...

---

### Post by linuxopjemac on 2010-10-02
I think your settings in Grub2 are incorrect. This is a very peculiar MacBook. I think you need to boot with the acpi=off entry in the /boot/grub/grub.cfg file. As you are not supposed to edit this file directly, you want to edit /etc/default/grub with an editor and add the following line:
```
GRUB_CMDLINE_LINUX_DEFAULT="any_other_stuff acpi=off"
```
You have to then update grub:
```
sudo update-grub
```

You will have to do these things from a liveCD and chroot into your installed system to alter these settings. Or, I am not sure if that works, you can enter grub settings after you boot and choose "edit grub". You can then also add acpi=off. You will then have to change it permanently as described above.

[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)
[http://ubuntuforums.org/showthread.php?t=1136427](http://ubuntuforums.org/showthread.php?t=1136427)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/MacBook5-2/Karmic](https://help.ubuntu.com/community/MacBook5-2/Karmic)

---

### Post by treoptika on 2010-10-03
> **RadiationHazard said:**
> Okay, I just tried it. It didn't do anything. I am starting to think it is impossible to install ubuntu on this macbook and it's really frustrating. I have tried about 5-10 different versions of linux and they all do the EXACT same thing. it starts to boot, I click install and then the disc drive just seems to turn off. it stops making noise and then NOTHING else happens. Idk what to do anymore...

[http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso)

Did you try the alternate install for ubuntu 10.04? Use the 'expert' setting if you haven't yet, I was having the same issue until I used the text / expert installation guide. I still get a strange display error on powerup but it passes it and boots right into ubuntu in only a few seconds.

---

### Post by zewnten on 2010-10-03
You can do what I did. None of the alternate or regular ones worked for me. And I also wasn't comfortable with changing things like Grub. Instead I downloaded and installed Ubuntu 9.04 and it works great. Know its not really a fix but.

---

### Post by bobwarner01 on 2010-10-04
Hi guys,,
I tried all these things. I have done all the basic things that are suggest in posts. But now i thinking there is a hardware problem. I loved mac but  now....:(

---

### Post by GoCool on 2010-10-04
So it's not just me, but everyone is having this issue. I am pretty sure someone out there must have loaded Ubuntu in his PPC-Mac and got it right (I see all these youtube videos). I think to load Ubuntu in Intel_Mac is a little less cumbersome than PPC-Mac.
Even I am desparately looking to get my linux up and running in this.

---

