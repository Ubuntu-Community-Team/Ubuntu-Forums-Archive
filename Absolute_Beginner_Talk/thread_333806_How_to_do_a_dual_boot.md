---
title: "How to do a dual boot"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by darkcyber on 2007-01-07
I have Windows XP installed on my pc now and would like to install ubuntu and try it out.  What is the best way to install it and be able to do a dual boot?

I'm using version 6.10 64 bit.  When I boot from the cd it comes up to a menu and the first choice is 'Start or install' ubuntu.  When I select that it boots into the ubuntu desktop...i.e. the live cd boot.  When it gets to that desktop there is an icon called 'install' but it does nothing. So, how do I install it as a dual boot?

Thanks!

---

### Post by ajmorris on 2007-01-07
install on a new ext3 partition. (can be created in the ubuntu install) this will install a bootloader called "GRUB" this can boot both linux and windows.

---

### Post by aysiu on 2007-01-07
If you want to try Ubuntu out, don't install it. Use the Desktop CD, which, when booted, runs off the CD itself and your computer's RAM. It doesn't affect your hard drive.

Once you've played with that for a couple of weeks and gotten comfortable with it, one of these two dual boot guides should help:
Desktop - [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Alternate - [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by lucky_chouhan on 2007-01-08
when boot the cd and you get the menu after select run from cd and boot it (this process check you CD errors) when you get the desktop its a one icon called install just click the icon when select which drive to install (better if you have unallocated space) if not then select you last fat or ntfs partition (which is empty and for linux) like hda5 or hda6 then installation is start after installation it ask to update your mbr select yes and reboot. finally you get the grub menu. list like this


Ubuntu 6.10
Ubuntu recovery mode
Ubuntu mem test
Other operating system(windows 2000, xp ) 

if boot ubuntu then select ubuntu 6.1
if boot xp then select other operating system - xp

this is mine setup

Happy Linux (Ubuntu) User:)

---

### Post by darkcyber on 2007-01-08
I have played with the live cd boot and want to do a dual boot install.  I could not get my network adapter to work with the live cd thing.  I have an MSI K8N Neo 4 board with built on LAN and I didn't know if some of the stuff didn't work with the live cd boot.

Also, where is a good place to start looking for drivers for all my hardware, if my hardware manufacture doesn't have any?

I'm a total noob in Linux...trying to kick the Microsoft habit :)   If I could just either run all of my favorite windows apps (or find a Linux one to replace them with) and run my windows based games I would be switched 100%.  But looks like being able to run my games is going to be my biggest problem.

Thanks!

---

### Post by Efwis on 2007-01-08
> **darkcyber said:**
> I have played with the live cd boot and want to do a dual boot install.  I could not get my network adapter to work with the live cd thing.  I have an MSI K8N Neo 4 board with built on LAN and I didn't know if some of the stuff didn't work with the live cd boot.

Also, where is a good place to start looking for drivers for all my hardware, if my hardware manufacture doesn't have any?

I'm a total noob in Linux...trying to kick the Microsoft habit :)   If I could just either run all of my favorite windows apps (or find a Linux one to replace them with) and run my windows based games I would be switched 100%.  But looks like being able to run my games is going to be my biggest problem.

Thanks!

Unlike Windows, there really aren't any drivers that need installed to run your hardware. The only driver i installed is ndswrapper to get wireless working on my laptop, which I can't use anymore because the power connector on the mobo burned up. and my Lexmak printer driver.

as for gaming you might be looking at Cedega or wine, however be warned that not all games designed for windows will work in Cedega or wine. as for windows apps, some work in Wine and others don't it really depends on what apps you are talking about. there are some really good alternatives for some windows apps on linux, and then there are others that claim they are just as good but are not anywhere near it.

as for dual booting, it is completely doable but you need to either have 2 disk drives, or a large enough disk drive for your windows install + programs, and I personally would recommend about 15-20 gig for Linux on it. (this is my setup decison, although you can get by with smaller amounts of space for linux depending on what apps you need to run.)

---

### Post by rbhigday on 2007-01-08
my desktop is running Xp and edgy both on seperate hard drives with no problems outside of the ati and ubuntu conflict but that is workable.

Soon I shall be windows free or at least only using windows for gaming and quicken :)

---

### Post by darkcyber on 2007-01-08
Well I have a 34 gig raptor drive that my current XP installation is on.  I have more than enough extra space to install ubuntu on it...going by your space suggestion.

Thanks for the information.

---

### Post by Efwis on 2007-01-08
if you seriously want to dual boot with winxp and ubuntu on your system, then I would follow the links that Ayaiu posted in [#3](http://www.ubuntuforums.org/showpost.php?p=1983258&postcount=3) , that can give you a better chance at success then I could possilby do for you.

I personally prefer dual booting with two hdd's, it makes it harder to damage my windows install. 34 gig isn't too bad, although I couldn't use that size personally for windows xp even, my windows xp drive is a 200gig hdd and I have used 46gig for windows xp and my apps I need on it.

---

### Post by darkcyber on 2007-01-08
Well, I use my 34 gig raptor for my OS and most of my apps, I have a 200 gig and a 300 gig for storing data and stuff on.

Let me ask another question here.  Does ubuntu or any version of linux come with any apps included in the installation?  Here's why I ask...I found this web site [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) that shows windows programs and linux equal programs.  

My question is, if I install linux am I going to have to search out and install all these different apps or features or are some included in some of the distros?

---

### Post by aysiu on 2007-01-08
> **darkcyber said:**
> Well, I use my 34 gig raptor for my OS and most of my apps, I have a 200 gig and a 300 gig for storing data and stuff on.

Let me ask another question here.  Does ubuntu or any version of linux come with any apps included in the installation?  Here's why I ask...I found this web site [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) that shows windows programs and linux equal programs.  

My question is, if I install linux am I going to have to search out and install all these different apps or features or are some included in some of the distros?
Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Efwis on 2007-01-08
> **darkcyber said:**
> Well, I use my 34 gig raptor for my OS and most of my apps, I have a 200 gig and a 300 gig for storing data and stuff on.

Let me ask another question here.  Does ubuntu or any version of linux come with any apps included in the installation?  Here's why I ask...I found this web site [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) that shows windows programs and linux equal programs.  

My question is, if I install linux am I going to have to search out and install all these different apps or features or are some included in some of the distros?
it depends on what apps you want. those that are installed in the standard installation can be added easily enough from the repos.

If you use the live cd click on System->Administration->Synaptic manager, you may not be able to install anything, but you will be able to search for programs. You don't have to search around and install programs from the web unless you are looking for something specific that isn't in the repos.

---

### Post by noisc on 2007-01-08
> **darkcyber said:**
> Well, I use my 34 gig raptor for my OS and most of my apps, I have a 200 gig and a 300 gig for storing data and stuff on.

Let me ask another question here.  Does ubuntu or any version of linux come with any apps included in the installation?  Here's why I ask...I found this web site [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) that shows windows programs and linux equal programs.  

My question is, if I install linux am I going to have to search out and install all these different apps or features or are some included in some of the distros?

I just set up a dual-boot a couple of weeks go, darkcyber, and honestly I didn't have to worry too much about this. A lot of basic utilities and programs are already installed if you installed Ubuntu (I don't know about the Live CD). If you need something that you could do in Windows, usually a quick search either on Google or on these forums will get you the name of the package you need, and then you use the Synaptic manager that Efwis mentioned in the previous post to download and install it. Really, it's not that bad to get appropriate software.

Honestly, the hardest part will be getting Ubuntu to recognize all your hardware, and more likely than not, that won't be an issue to begin with.

---

### Post by darkcyber on 2007-01-08
> **lucky_chouhan said:**
> when boot the cd and you get the menu after select run from cd and boot it (this process check you CD errors) when you get the desktop its a one icon called install just click the icon when select which drive to install (better if you have unallocated space) if not then select you last fat or ntfs partition (which is empty and for linux) like hda5 or hda6 then installation is start after installation it ask to update your mbr select yes and reboot. finally you get the grub menu. list like this


Ubuntu 6.10
Ubuntu recovery mode
Ubuntu mem test
Other operating system(windows 2000, xp ) 

if boot ubuntu then select ubuntu 6.1
if boot xp then select other operating system - xp

this is mine setup

Happy Linux (Ubuntu) User:)


I went through the installation, but it did not ask me to update my MBR.  It just gave me a box saying to reboot to use the new installation or continue using live CD.  I choose restart and got to the point where it's told me to remove the cd and press enter.  Doing so does nothing...still have that on the screen.


Well, the installation didn't work...after rebooting it comes up and says missing operating system.

---

### Post by Efwis on 2007-01-08
then something missed a step somewhere. I would recommend starting the Livecd, and trying the install again, make sure that you install it on the exact same partition you did before, otherwise you might wipe out your windows installation.

It sounds like you killed the MBR when grub was to install, I had that happen once before, a resinstall fixed it, if that doesn't work let us know and we will help you get the MBR fixed.

---

### Post by darkcyber on 2007-01-08
Well, first off after I finished the installation it came up to the black screen and showed the Ubuntu large letters and said remove the cd and press enter.  I removed the cd and pressed enter a bunch of times and nothing happened.  So, I finally pressed the reset button on the pc.  Do you think that might have caused the problem?

---

### Post by darkcyber on 2007-01-09
Need additional help here please!

I've run another installation of ubuntu 6.10 64 bit and finished installing it and i'm back to the black screen where it shows ubuntu and says to remove the cd and press enter to continue.  I've done this and nothing happens.

This is the same thing that happened to me yesterday and it never rebooted...so I had to press the reset button and then when it rebooted I got the "missing operating system".

Does anyone have a clue why it will not reboot from this screen?

---

### Post by wscheer on 2007-01-11
Just put ubuntu on a hp pavilion ze5570us laptop.

aysiu's Desktop instructions ( [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) ) worked perfectly

---

### Post by darkcyber on 2007-01-11
Yes, I could put it on another pc...but what I'm trying to do is put it on main pc and dual boot.  I have very fast system and want to use it for both.

---

### Post by darkcyber on 2007-01-12
Finally got it fixed.

Here's what I did I disconnected my 2 ide hd's and only had my SATA hd connected. I then installed the 32 bit version of ubuntu. This time when I installed it the little ubuntu splash screen was in color. When I used the 64 bit version it was always black and white. Also, when I finished the installation and it exited off the desktop it went back to that splash screen which was in color again and it opened the cd tray and said to remove the cd and press enter. This time when I pressed enter the computer did reboot.

So, I don't know if it was the 64 bit version or the ide hd's. I did try the 32 bit version with the 2 ide hd's connected and it didn't work. So, could have been a combination.

All my network stuff was detected and all I did was click on FireFox and it accessed the net right off...very sweet.

---

### Post by Visti on 2007-01-13
*wrong thread*

---

