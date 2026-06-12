---
title: "Edgy install problem on Powerbook G3"
date: 2007-03-14
forum: Apple PPC Users
---

### Post by Macmania on 2007-03-14
Ok, what the hell. It seems like no matter what I do I can't get Ubuntu to install correctly on this computer. I have tried Dapper, desktop and alternate, Edgy desktop cd,dvd and alternate and also Xubuntu Edgy alternate. I know it should work because I have seen on this forum and many others that it will install on this computer and I've even seen it on older machines. Everything seems to go fine during the install untill I get to the "select and install software". I get there and it seems fine and then at 6% EVERY TIME my screen will flicker and it will stop installing. It will say "just a moment" and will sit there for about 5min or so. Then an error message will come up and say installation step failed and says you can try to run failed item from the menu. When I do that same deal. Am I doing something wrong? Everything is perfect untill I get to this step. During this time I can still hear my cd drive making noise but nothing happens. Also on the alternate disc, if I don't select to install the desktop it will install perfectly fine, no problems at all. I thought maybe the download or disc was screwed up so I burned so many discs and re downloaded so many times it would make your head spin. So I don't think that is my problem. When the disc is done burning the computer verifies the data and there is never any problem found. PLEASE HELP, I am about ready to say screw Ubuntu and re install Mac OS X, I don't know what else to do here and I AM ABOUT TO LOSE MY MIND! Thanks

---

### Post by o_s on 2007-03-14
Maybe the CD-ROM drive is broken? Could you test the installation with some other external USB/Firewire CD-ROM drive?

---

### Post by grazie on 2007-03-14
Well at least you're getting over the initial hurdle of getting linux to boot  on your mac which is good news. Have you run check from the boot: menu? You need to establish whether the cd you've burnt is good. Using verfiy burn in apps like OS X Disk Utility, Toast, K3b and Nero achieve the same thing. Burning at slow speeds fixes a large number of problems like this.

As you get as far as 'Select and Install Software' I'm assuming you've gone through preparing the install disk OK? What method did you use? There are [known problems]("https://wiki.ubuntu.com/DapperReleaseNotes/UbiquityKnownIssues") in this area that may apply to you.

How much ram does the machine have? If it's got 192M (preferably 256M) you could use the live cd to install and maybe get some assistance on the ubuntu irc channels while it's installing.

---

### Post by Macmania on 2007-03-14
> Maybe the CD-ROM drive is broken?
I don't think it's broken because the OS 9 and OS X discs install perfectly and it reads and plays dvds just fine.
> As you get as far as 'Select and Install Software' I'm assuming you've gone through preparing the install disk OK? What method did you use? There are known problems in this area that may apply to you.
By install disk do you mean the hard disk I'm installing to or the disc I'm burning in OS X? If it's the disc i'm burning, I am opening up Disk Utility and moving the disk image from my desktop to the side panel on the Disk Utility window, then I select burn disk and the window pops up to set burn speed and to verify burned data and all of that. The funny thing is that it will only let me burn at 24x, is that too fast? So I then burn the disc and it verifys it, ejects it and says burn successful. I am burning it on my eMac and the specs are in my signature at the bottom. For the hard disk I used the OS 9 install disc to set up a partition for the OS 9 install and an empty partition for the Ubuntu install. During the Ubuntu install I have the partitioner use the largest continuous space and it sets up HDA8 as OS 9, HDA9 as boot, HDA10 as linux or "/", and HDA11 as swap. When I tried to install Dapper it would not go past the partitioner stage but Edgy will.
> How much ram does the machine have? If it's got 192M (preferably 256M) you could use the live cd to install and maybe get some assistance on the ubuntu irc channels while it's installing.
I've got 320mb ram. I tried to boot a live install disc but it was no go. Somebody posted a kernel argument: (casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop --) to boot from a live cd, tried that, no go. I think I have BootX set up properly because if it wasn't it wouldn't boot into linux at all correct? For BootX I copied vmlinux to the linux kernels folder in the system folder and copied initrd.gz to the system folder and renamed it ramdisk.image.gz. Oh by the way the Live discs boot just fine on my eMac which i know is "new world" but at least it lets me know that the disc is not bad.

---

### Post by grazie on 2007-03-15
If you've not already tried burning a slow speeds its well worth a try.I'd say x4 or less. Although the burn verifies and the eMac probably has no trouble reading the disk, your older G3 will be struggling to read a disk written at the speed.

---

### Post by Macmania on 2007-03-15
Thats what I was thinking but Disk Utility will not let me burn any slower than 24x. It will not let me adjust it at all. When I burn a dvd it will but not a cd for some reason.

---

### Post by grazie on 2007-03-15
Odd  you can't reduce the burn speed. With there already being Disk Utility and Toast for OS X, I doudt there will be much choice of alternative burners. Have you thought about installing a small Linux partition on your eMac and using something like graveman to burn the cd?

---

### Post by Macmania on 2007-03-15
You know, I never thought of that. There was however one problem I had with Ubuntu on the eMac, when I boot the live cd it has a problem with the video driver. It did not recognize my graphics processor which is an ATI Radeon 9600. I have heard of problems with and seen fixes for the Nvidia graphics in eMacs but not much for ATI. I always thought Ubuntu had pretty good support for ATI. Also my graphics processor is not a typical Radeon 9600 card it is the Radeon Mobility 9600 which I think is usually used mainly in laptop computers. So i guess i am screwed no matter which way I go. I guess I will have to search a little more to see if I can find a fix for the eMac graphics problem. I like Ubuntu and I would love to actually get to use it. The only computer I have actually gotten it to work on is a Dell and it installed perfectly. You know I do have three "Wintel" machines here. Maybe I should try to burn the cd on one of them.

---

### Post by Tommy on 2007-03-15
Wait... before you spend a lot of time and burning lots of disks, try again to see if you can verify the disk. 

I'm looking at a printout I made for the Edgy CD, but there's a similar file for all of them that has the boot commands in it. I made a note on the printout that I WAS able to run the CD check file.

So... boot the Wallstreet into the Mac OS 9 partition having BootX, and pop in the CD. If you can open the file, look in the /install/yaboot.conf file -- it contains the actual boot parameters for the different menu options. [I just dug around and unfortunately if there's a secret command to get Simpletext to open an arbitrary file, I can't find it. BBedit and even MS Word can... Actually it looks like I printed this text using gedit so I probably didn't even try. It's nice if you can because you could copy and paste into the BootX parameter]

In that file, the boot parameters are the append= parameter. The one just under "#powerPC subarch" says  label=check. The parameter says

```
MENU=/bin/cdrom-checker-menu --
```

My notes says I got that to run the disk check utility by putting that in the BootX kernel parameter. Notice there is only ONE space in that whole command, just before the final double hyphen.

If you can get that the CD check to work, and it says your CD is OK, that means it's another thing keeping you from running.

OH and for my Wallstreet video to work, I have this parameter in BootX:

```
video=atyfb:vmode:14,cmode:32,mclk:71
```

I think it's possible your specific Wallstreet model may require a slightly different code, but try that and see if your screen works better. It won't affect the failing installer, but if you ever get X going you'll want that.

BY THE WAY
I have a theory about why the CDs have trouble installing on oldworld, but it's not good news for the Dapper and Edgy disks. I have not tried to find a Feisty build (if they even exist) for PowerPC, but maybe the fix will be in there. I think there's an "upstream" installer & kernel bug in Debian that would have gone into several Ubuntu releases. It only affects oldworld, so very few folks may have noticed and/or given up on Ubuntu if they were installing from scratch. (I have been upgrading for a couple of years now so I haven't even tried the installer until lately.)

---

### Post by Macmania on 2007-03-16
OK, good news. I got the cd rom integrity checker to work and the cd is perfectly fine, it says "the cd-rom is valid". So I don't need to burn any more cds. Now I just need to find out what the problem is. Am I doing something wrong? Am I missing a step or something? I thought maybe BootX was the problem but it boots into the Edgy installer fine every time. The Dapper installer is another story. Sometimes it will work fine and others it will either have a kernel panic or it will 'drop to shell". When I can get the installer to boot it will always get stuck on the partitioner. I think since I am getting so much closer with Edgy I will just stick with it. I need to figure why it is hanging up at 6% every time I get to the select and install other software section. It did this in Ubuntu Edgy and Xubuntu Edgy. If I can't get this going soon I think I will download XPostFacto and install Mac OS X Panther or Tiger. I know it will run slow (definately slower than Ubuntu) but the computer is very out of date running a completely unsupported operating system.

---

### Post by Macmania on 2007-03-17
So I tried the kernel arguement (video=atyfb:vmode:14,cmode:32,mclk:71) and it caused a kernel panic but when I rebooted I selected force video settings and it started up ok. I am trying to install again and will let you all know how it turns out. I had this idea that my problem could be a video setting? Mainly because the screen flickers and it always happens when it says I believe it was configuring xserver-xorg. So it's a long shot but you never know right? I can't think of anything else because I have gone by the book during this whole install.

---

### Post by Macmania on 2007-03-17
OK, I want to thank everybody for their help. I just got Edgy installed and it is currently downloading updates. My problem ended up being my video settings of all things. I entered the kernel arguement (video=atyfb:vmode:14,cmode:32,mclk:71) and selected force video settings and it installed perfectly. So we all need to remember this if anybody else has a problem installing on a Powerbook Wallstreet. The only problem I am having now is with the wireless card, it is a Linksys WPC11 Version 4. It does not seem to be working. I guess I will need to download Network Manager and see if that gets it working. Ubuntu seems to be about as quick or maybe a little quicker than OS 9 and definately faster than OS X. It is also nice to be using a current web browser instead of MS Internet Explorer 5 which sucks. The browser doesn't just randomly crash anymore. I mean come on, something from Microsoft crashing? Never. Well if you all have any ideas about the wireless card let me know. Thanks again for all the help!

---

### Post by Tommy on 2007-03-18
> **Macmania said:**
> Am I doing something wrong? Am I missing a step or something? I thought maybe BootX was the problem but it boots into the Edgy installer fine every time. 

I believe there was a problem in the "upstream" kernels coming from Debian that kept oldworlds from booting and/or running the installer. The problem was discovered and corrected in Debian a few months ago, so if my theory is correct, the Feisty installer and kernel should boot an oldworld more reliably than Dapper or Edgy.

Although Ubuntu has dropped PowerPC as one of their regular platforms, it continues to be available as a "port," so I presume the port will come out around the time of the regular Feisty release in April.

In the meantime, all the PowerPC versions including the latest raw development version should be available here:

[http://cdimage.ubuntu.com/ports/](http://cdimage.ubuntu.com/ports/)

If I get a chance I'll download a Herd or daily image for Feisty and see if it will boot my system, but that probably won't happen for a few days.

P.S.: I never tried running OS X on my Wallstreet -- even from the beginning there were lots of things Apple never even tried to support on that model, like sleep, but I'm sure with the help of xpostfacto you will be able to run it.

---

### Post by Tommy on 2007-03-18
> **Macmania said:**
> I just got Edgy installed and it is currently downloading updates. My problem ended up being my video settings of all things. I entered the kernel arguement (video=atyfb:vmode:14,cmode:32,mclk:71) and selected force video settings and it installed perfectly. So we all need to remember this if anybody else has a problem installing on a Powerbook Wallstreet.

Great! When I was playing around with the Edgy Alternate disk installer I was very encouraged that you can TEMPORARILY use the video=ofonly setting (at least I could on the PowerMac 9600 I was using), but when it came time to set up xwindows it was terrible and I had to use the correct video setting. So for whatever reason the exact video parameters are essential.

As for the wireless card, I have a "well supported" orinoco card (functuionally the same as an original Airport Card), but as Ubuntu has progressed the card has worked less well for me, and I haven't even tried to use wireless in awhile. 

As you've probably already figured out, you won't be able to eject a PCMCIA card properly because they never put the eject code in the driver (I gather the Wallstreet was a very rare beast in that way.) So you have to manually issue the commands and forcibly remove the card rather than having the eject motor do the work.

But I agree with you about the software -- I love being able to use the latest linux software on a laptop that's almost ten years old!

---

### Post by Macmania on 2007-03-21
Ok, so here's what I decided to do (STUPID). I decided that if I could get Xubuntu Edgy to work I could get Ubuntu Edgy to work because I wanted the extra stuff that comes with the Ubuntu version. So I tried to install Ubuntu Edgy with the kernel arguements for the video settings in place. Now it hangs up at 4% when it says configuring xserver-xorg. I played around with it using a few other video kernel arguements I found online and no go. So I decided to re install Xubuntu Edgy, now that is a no go and it hangs up at the exact same spot, 4%. I installed with the exact same settings as the first time and it won't go. What I did after that was since both versions of Edgy would not install I tried again to install Dapper Drake and it installed perfectly. This was surprising considering all of the previous problems I had with Dapper Drake and with it's partitioner. When I booted up Dapper I put in the Edgy cd and went to upgrade Dapper to Edgy. It all loaded fine and told me I needed to restart so I did. Now when it tried to boot up in Edgy it said Xserver failed to load.... I am currently re installing Dapper Drake. I guess my dreams of Edgy have been shot down. This sucks but I don't know what else to do. Any ideas? I guess that Edgy just may not be able to run on this computer. I was looking forward to using all of the added features in Edgy.

---

### Post by grazie on 2007-03-21
Firstly you need to establish what it is that's actually giving you problems. It looks like Xorg, but it's not possible to for me know with the info you've supplied. Did you try booting without X using 
```
boot: Linux single
```
Also how did you install Ubuntu Edgy? If you had a working Xubuntu you could have installed the meta package ubuntu-desktop to effectively get Xubuntu + Ubuntu. If you've previously installed Xubuntu Edgy successfully, I think you've just got to try and remember exactly what you did first time round. :)

---

### Post by Macmania on 2007-03-21
OK, I was up almost all night but I got Ubuntu Edgy to work and heres what I did. I installed it as usual but when it came to select and install additional software I did not indtall the desktop, I left it un selected. When it was done installing I went to this site [http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox") and it walks you through installing the desktop using the terminal interface. I did that and it worked, it actually worked. The site is cool and it has a lot of tips and tricks. So now I've got Ubuntu Edgy running on my Powerbook G3 Wallstreet and I could not be happier. Now what I am going to do is LEAVE IT ALONE. I have worked hard to get this to work and I do not want to screw it up.

---

