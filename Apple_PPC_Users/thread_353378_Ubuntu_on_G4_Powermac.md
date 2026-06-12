---
title: "Ubuntu on G4 Powermac"
date: 2007-02-04
forum: Apple PPC Users
---

### Post by Zorko on 2007-02-04
Hi, I have recently got given a free G4 Powermac, running OS9, which I hate, and have decided to install linux on it. I have downloaded the PPC version of ubuntu 6.10, and can boot to the CD. I am at a black screen, suggesting what to do. When I try to enter the livedisk, it starts up fine, takes a while though, but when I get to the desktop, I am greeted with:
[img]http://img169.imageshack.us/img169/8308/p1010507lz1.jpg[/img]
Incase you can't see the image, it basically shows seven the panel encountered a problem while loading... error messages, 
This happens with both the live and the live-powerpc commands. I have checked the disk for consistancy using the check command, and it says it is fine.  Any idea what is causing this and how I can fix it? 



Specs are as follows: 
400mhz single core PowerPC processor
320mb of ram
ATI Rage Pro AGP with 64meg onboard memory
10 gig hard drive with OS9 installed
20 gig hard drive with general files
DVD-V drive (unsure as to what the V means)
Iomega Zip Drive
Unknown soundcard, or anything else.

---

### Post by grazie on 2007-02-04
Not seen or heard of this specific problem before, but I would suspect a corrupt Live CD.

Did you verify the md5sum? If so, did you burn the image slowly? At the "boot:" prompt, hit the tab key which should give a number of options. Type check (or for your machine check-powerpc) and press enter. This will verify the cd and may take a while.

If you still have no success you probably have dogy media or hardware problems.

PLEASE - EVERYONE SHOULD DO THE ABOVE AND STATE THEY HAVE DONE THE ABOVE AFTER DOWNLOADING A NEW ISO IMAGE, BEFORE ASKING FOR HELP ON THE FORUM.

---

### Post by Zorko on 2007-02-04
> **grazie said:**
> Not seen or heard of this specific problem before, but I would suspect a corrupt Live CD.

Did you verify the md5sum? If so, did you burn the image slowly? At the "boot:" prompt, hit the tab key which should give a number of options. Type check (or for your machine check-powerpc) and press enter. This will verify the cd and may take a while.

If you still have no success you probably have dogy media or hardware problems.

PLEASE - EVERYONE SHOULD DO THE ABOVE AND STATE THEY HAVE DONE THE ABOVE AFTER DOWNLOADING A NEW ISO IMAGE, BEFORE ASKING FOR HELP ON THE FORUM.

It checked fine. I will try burning another one regardless and I will burn it at 1X to be sadistic!

---

### Post by maxamillion on 2007-02-04
I had a similar problem with Ubuntu on an iBookG4 and it resulted to the system clock setting in the OpenFirmware of the system being set back to something like the year 1752 and Gnome choked on it. It might not be the problem you are having, but I might recommend (if you have the bandwidth, the time and a spare cd-r) downloading Xubuntu from [www.xubuntu.org/get](www.xubuntu.org/get) and try running that as a live session (Xfce4 doesn't rely on the Gnome-libs that choked on the system time settings and it worked like a charm for me) and worst case scenario if you are married to the idea of Gnome is install xubuntu, set the system time, then install ubuntu-desktop.

Hope that helps.

---

### Post by Zorko on 2007-02-04
Just a thought, since I hate xubuntu, would kubuntu be any different do you think?

Ok, so I tried it with a newly burnt CD (burnt at 8 times, with nothing else running)
It had the same error, but I thought, what the heck, and found the installer under system. After running it I got an error filled with masses of jargon I didn't really get, and my camera has bombed out on me due to lack of batteries. I think I will try kubuntu or Damnsmalllinux and see if it is a system problem or a problem with ubuntu, or my download.

---

### Post by politicalhumanist on 2007-02-04
Gnome works for me if I'm connected to the Internet. If you get connected to the Internet, download KDE. KDE works without being connected to the Internet.

---

### Post by grazie on 2007-02-04
If you've done the md5sum check and verfied the disk, then your download if fine. Unfortunately there isn't much choice of ppc linux distos and you'll not find a another distro that is as easy to install and has the level of support of Ubuntu. If you have got the bandwidth. I think maxillion's suggest is good. If you want to try kubuntu, best of luck.

---

### Post by Javahead on 2007-07-04
Hello.

This thread is somewhat old, but I thought I would post my experiences with this problem.  I stumbled upon this thread quite by accident while looking up some things for an iMac G4 flat panel I recently purchased.  

I had to reset the PMU/NVRAM to get this machine working.  As a result, the system clock was reset.  When I would start GNOME via my installation of Feisty 7.04 or the LIVECD, I would get 8 error dialog boxes, as seen in the attachment 'gnome-errors.png'.  To fix this, I set the time (*sudo date MMDDhhmmYYYY*) example: if the current date was 7/4/2007 5:00AM, you would enter *sudo date 070405002007*. Note that the hour is in 24-hour format, so 5:00PM would be 070417002007. 

I logged out of GNOME and logged back in.  The issue went away.  

Hopefully, this will help some others restoring Macs later! :)

---

