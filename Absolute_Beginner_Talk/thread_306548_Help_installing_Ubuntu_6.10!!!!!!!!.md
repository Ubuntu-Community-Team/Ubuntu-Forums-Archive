---
title: "Help installing Ubuntu 6.10!!!!!!!!"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by michaelof36 on 2006-11-25
I'm a complete noob when it comes to linux so bare with me please. I was trying to dual boot Ubuntu and Windows XP but I can't even begin to install Ubuntu. I burned the ISO to cd, rebooted, let it start up and select install (changed the resolution to the correct size beforehand) and the x server failes to start everytime. I know its because of my graphics cards (ati radeon x800). I tried the live-expert option but no use and the fb=false option as well I just get a black screen. ](*,)  I'm determined to install Ubuntu now, please help.

Michael

---

### Post by rigol on 2006-11-25
Please provide more information about your system. What motherboard and processor are you using? What errors do you get when the xserver crashes?

---

### Post by xpod on 2006-11-25
You could try "safe graphics mode" if it`s a live cd your using.

Or you could try using the "Alternate cd" if all else fails.
Other than those 2 options i personally cant tell you too much else im afraid.You`ll need someone who knows better than me to tell you more.:D 

The alternate cd can be a lot less hassle to install but you wont get to try Ubuntu as it`s only a text based installer with no live session loaded.Can be a whole lot easier in a lot of cases though.

Good luck

---

### Post by michaelof36 on 2006-11-25
I have a Dell Dimension 8400:
250 gig hdd
80 gig hdd
ati radeon x800
Pentium 4 w/ HT
Intel 925x motherboard
Integrated audio (SoundMAX)
Linksys wireless card

When I boot the cd the a windows comes up saying "Failed to start the X Server...It is unlikely that it is not set up correctly" I haven't installed ubuntu yet.

---

### Post by confused57 on 2006-11-25
See reply #16:

[http://www.ubuntuforums.org/showthread.php?t=294882](http://www.ubuntuforums.org/showthread.php?t=294882)

---

### Post by michaelof36 on 2006-11-28
Still can't install Ubuntu, I give up now!

---

### Post by michaelof36 on 2006-11-28
I don't want to give up just yet but when I erase "splash --" from the options menu and I press enter to select "Start or Install Ubuntu" I get a black screen with a "Buffer I/O error on device hda." Could it be that I need to re-burn the iso?

---

### Post by LLRNR on 2006-11-28
Mmmm... you *might* want to try to reburn the disc, there's a chance that the first time the burning process itself wasn't accomplished correctly. Follow these steps:

No. 1 : [http://www.md5summer.org/download.html](http://www.md5summer.org/download.html) to check the md5sum (i.e. to be sure the ISO you downloaded is ok)

No. 2 : Burn the ISO at a really low speed (try with 4x for instance)

No. 3 : Before attempting the install, after you boot from the CD, please run "Check CD for defects"

HTH,

LLRNR

---

### Post by Bartender on 2006-11-28
You might want to try another distro.  I'd suggest PCLinuxOS.  It flew right thru on my homebrew PC, which has been unable to properly run Ubuntu 5.10, 6.06, 6.10, Kubuntu, etc.

---

### Post by xpod on 2006-11-28
> Buffer I/O error on device hda

I used to get similar Buffer I/O errors everytime i tried to load a live cd on this pc....It would load eventually but i had to wait like 10 minutes or so for it to scroll passed the 6 Buffer I/O messages then about 8 others that i cant recall just now before it would continue and load normally

I spent weeks wondering what it was but one day when i swapped cd\dvd players over they stopped completely:confused: Still none the wiser.

I was doing quite a bit of installing at the time just trying to find what was best for me so these delays were a pain at the time.

Good luck anyway...its just a case of trial and error in some cases until you too find what works best for you,either with ubuntu cd`s or as bartender says with other distro`s,although i would persevere with Ubuntu....it`s worth it in the end

---

### Post by djroadrash on 2006-11-28
once u see that the booting is finished you might hear a couple of drums, then try this, press control alt f1 you will be prompted to put your user name and password, then write this ```
lspci
``` and you will get the type of chipset and driver u are using, copy them and then post them here. check that all your devices are being detected and there are drivers for them. other than that u can check the output of ```
dmesg
``` to check the booting process.
also u could try breezy or dapper and see if anything changes. good luck:) 
p.s. if all fails try kanotix or knoppix they are known for great hardware detection they are both live cds but kanotix can be installed from the live cd.

---

### Post by atomictaco on 2006-11-28
I feel your pain, I have not been able to install 6.06 or 6.10 on any computer using the live CD.  I have been able to install them with the alternate install CD's but only after a lot of effort.  I personally feel that there has not been a lot of effort put into the installer on either of these versions and have migrated away from Ubuntu on all recent linux installs.  It is sad becasue Ubuntu is a good distribution and has always ran great for me once installed, but it is just not worth the 8-10 hour install time.  Hopefully the developers will realize their mistake and make an effort to correct it as I have seen a huge number of posts regarding install issues.  :confused:

---

### Post by michaelof36 on 2006-11-28
Correct me if I'm wrong but would putting the Ubuntu cd in a differnet cd drive work? I have two in my computer. I really want to try Ubuntu I really don't have any need/want to try any other distros. The only distro that correctly installed without any problems whats so ever was RedHat, I don't remember what version it was but I didn't like it. To make a story short I'm getting tired of Windows and since I am using OSX at work I'm having a blast learning how to use it. I think a change was in order at home for a new OS. I know its possible now to install OSX on an Intel based computer but I'm having some difficulties trying to get a hold of a copy. Anyways, I'll keep trying to fix this Ubuntu issue. :-k

---

