---
title: "Where to start.. give me some clues?"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by lofgren on 2006-10-29
[B][I]Edit: this is now solved! Turns out I have an AMD64 processor.
Apparently you can run 32bit OS/apps on them, but not in my case (for some reason).  

So, final solution - download/install ubuntu 6.06.1 Alternate AMD64 iso.

I am loving it now it's stable - thanks for your help and suggestions people![/I][/B] :o 

Hi people,
I really like the idea, look and feel of ubuntu.  I installed it on a test box a while back and it worked fine. 
However, the box was low spec and I didn't use it much.
I dug out the 6.06 install disk this weekend and installed it over my debian partition on a dual boot box.

Before we go any further - the box runs fine under windows XP and Debian sid.....

6.06 installed (after a couple of crashes). Once installed, most apps seem to crash, including power management and volume control. The updater crashed a few times while trying to install updates.

I went to look for different install CD's and found 6.10 was available.
I downloaded and installed the 6.10 i386 live CD iso. I deleted the previous linux root partition as it wouldn't format during the install ;) 
Once installed, it seemed more stable... 

However, I started configuring the box for my network - printing, filesharing etc. 

Nautilus crashes everytime I browse a remote XP box. In fact it crashes somewhat randomly and frequently.

At one stage, the terminal app crashed. It was in the background, sitting at the prompt at the time..

Volume control still crashes occasionally.

I have used ubuntu on the box all weekend and have also had several xwindows crashes (well - the gui disappeared, returned to a black window with a cursor in the top left and then returned to login gui).
Is that GDM, Gnome or xorg that's failed? Or a combo?

I know that's fairly vague, but does anyone have any hints to make the box more stable?

Would xubuntu or kubuntu be more stable if the issue is related to gdm/gnome?

Incidentally, my system is:
Motherboard:   Asus K8V-MX
Processor:     AMD3000+ Sempron
video card:    Sapphire Radeon 9250 Pro
RAM:           1GB
onboard Video is disabled

Thanks heaps,
Matt

Edit: neaten info in system stats and update title to be more accurate.

---

### Post by Jose Catre-Vandis on 2006-10-29
Although it sounds like you did it, I would start from scratch again.

First check the quality of your download to ensure the CD/ISO is all OK.

Next, reformat your install partition, so its all nice and clean

Reinstall Edgy (Ubuntu 6.10) accepting as many defaults as possible.

Next sort out your graphics by installing fglrx from the repositories, and then doing sudo dpkg-reconfigure xserver-xorg in a terminal. (look for fglrx in the list of drivers in the config section when it comes up)

Next install Automatix 2, and get all your multimedia codecs and browser requirements sorted (Flash9/Realplayer/Java/Wine/etc) (whatever is your thing here)

How is it working?

---

### Post by lofgren on 2006-10-29
Hey, thanks for your suggestions.

I'll give them a go..   A couple of other things.
After posting last night I found mention of swap needing to be 2x RAM.  Mine is only 600MB (which worked okay with Debian and the same partition was reformatted).  
How touchy is ubuntu?

Which also brings me to my next thought.. One of the guys here at work has suggested swap might not be in use. 

I have not yet confirmed that swap is being mounted and used. 
I'll check it out tonight when I get home.

Perhaps there is a bug in the installer (similar to the one that prevents the installer formatting a secondary partition during the install) that doesn't mount swap if the partition already existed.

Thanks again,
Matt

---

### Post by nalmeth on 2006-10-29
Before reinstalling, try hooking up the ATI drivers, the open ATI driver may be the sole problem. 

Otherwise, follow Jose's advice. Dapper is still supported for 2 1/2 years, so if you don't really need cutting/bleeding edge stuff it should do for you.

EDIT:
Also, *I* would recommend installing codecs from:
[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

But do whats best for you :)

---

### Post by jd65pl on 2006-10-29
Note that edgy is a release that is intended to test new releases of applications it is NOT an update from dapper.

---

### Post by slimdog360 on 2006-10-29
Try out [Thunar]("http://thunar.xfce.org/index.html"). When Im not using kde I always use it.

---

### Post by lofgren on 2006-10-30
> **jd65pl said:**
> Note that edgy is a release that is intended to test new releases of applications it is NOT an update from dapper.

Umm.. yeah, but I don't think I am asking too much to have it install and run without crashing while idle ;)

Thanks for all of the suggestions and assistance :)

I went with the fresh install idea, new partitions with a bigger swap area.

I am liking the video driver as the issue - as I haven't even been able to get through the install now without it crashing part way through.

It's currently on attempt 5 or 6 (I've lost track!) and I am downloading the alternate install disk on another machine - it has a command line installer, right? :mrgreen:

---

### Post by Bartender on 2006-10-30
I've read that if your PC has lot of RAM (2GB or so?)then Ubuntu is unlikely to ever use swap and you can skip making a swap partition.  Can't confirm that.

---

### Post by lofgren on 2006-11-01
Okay.. an update...
I got the kubuntu alternate disk and installed without any issues via text mode.

Once installed it seemed more stable, but bits and pieces still crashed. Control panel, kicker and desktop for example.

I found a couple of tutorials on installing fglrx - without much luck - and started searching specifically for my card.
From there I moved to radeon drivers, which gave me another set of obstacles to get past.  I returned to the fglrx tutes and came across a section on removing fglrx to revert to your original 3D drivers.
Finally, I have installed the radeon driver correctly..

I am still experiencing occasional crashes in kicker and the desktop, but overall it seems more stable.
As an aside, another issue that has appeared with this kubuntu incarnation - during aptitude updates and installs, it will seg fault 5/10 times.

I am aptitude install'ing ubuntu-desktop while I write this, thinking it will give me an indication as to whether the issues were the vid driver all along.. I think I also preferred the app set and interface - but at least I will have both to choose from.

Thanks again for your help and suggestions :)

---

### Post by Jussi Kukkonen on 2006-11-01
> **lofgren said:**
> 
I am aptitude install'ing ubuntu-desktop while I write this, thinking it will give me an indication as to whether the issues were the vid driver all along.. 

It's definitely related to some specific hardware/driver... The behaviour you described is far from normal. You could check your memory for faults as it could show up like this (there should be an option for it in GRUB), or try removing some optional hardware (e.g. tv-cards) to test if they are the problem.

---

### Post by bluenova on 2006-11-01
[quote=jd65pl]Note that edgy is a release that is intended to test new releases of applications it is NOT an update from dapper.[/quote]
But it's not a Beta release, it's a stable release meant for running on production systems. The only difference is the length of time it's supported.

---

### Post by Abhi Kalyan on 2006-11-01
joining in for subscription-
Reading here but dont have enough stuff to post
Useful data/Info

---

### Post by kvonb on 2006-11-01
I would start in BIOS, check the video interrupt, toggle it.

Also one thing I do is disable all non-needed onboard devices, ie serial ports, printer port.  This will give you more free interrupt lines.

Although you say that Debian works well, very odd.

Maybe a hard disk bad sector issue, or maybe because Debian AND Ubuntu are using the same swap partition it is causing a coronary?

Maybe make a 2nd swap partition and make sure that Ubuntu uses the 2nd one (edit fstab).

Hope you find some answers.

---

### Post by RudolfMDLT on 2006-11-01
Hi,

In the terminal try "sudo swapoff -a" to turn the swap off. Then secondly, your running a fairly old ATI card. I read on the weekend on these forums that there is a cutoff in Edgy, I think it was around 9400 or 9500 series cards. I've been looking and searching but can't find the damn post and the wiki search isn't helping either. 

The best way to install the graphics drivers for ati is restarting into recovery mode and doing everything from there. You can try my how to if you wish, just click on the Ati issues link in my sig.

Cheers,

Rudolf

---

### Post by kvonb on 2006-11-01
```
I read on the weekend on these forums that there is a cutoff in Edgy, I think it was around 9400 or 9500 series cards.
```

I have a 9200SE and I tried Edgy a few days ago.

The 9200 works, and I did get 3d working, but the only driver version avaialable is 8.28.8, and that one crashes with Google Earth, and also OpenOffice.

I switched back to Dapper until I get a better video card.

---

### Post by lofgren on 2006-11-03
Hi all,

time for another update.

I ran the memtest without errors for something like 14 hours.
The ubuntu-desktop installed and still appears slightly less stable than kubuntu. I haven't had much of a chance to play beyond that.

Time to fiddle with bios etc.

Thanks again for all the suggestions and encouragement :)

Matt

---

### Post by lofgren on 2006-11-06
Hello,

well.. I have downloaded and installed ubuntu via the 6.06.1 alternate CD. The install was smooth, but apps still randomly crashed.

In the mean time, I have gone through the bios settings and disabled all I could and (as I read somewhere) changed it to skip  quick boot - ie: do all tests.

I have just successfully installed ubuntu's packaged fglrx driver as per method 1 in this link and the few additional steps for cards below 9500: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

It has installed properly, however...
After the reboot, volume control crashed.  Soon after that, nautilus and gnome session manager.

Bit of a shame, as while it's working, it is super snappy - more responsive than all other versions. Menus are lightening fast.
This is with the default driver for 6.06.1 as well as the fglrx driver..so I am also guessing the video card is probably as good as it will get.

Any ideas? extra stuff I can check?

---

