---
title: "Testers needed for PowerPC 12.04"
date: 2012-01-31
forum: Apple Hardware Users
---

### Post by rsavage on 2012-01-31
Hello people!
 
Colin Watson has kindly looked into the mirror archive error that has plagued the PowerPC live cds since 11.04. He thinks he has now fixed it, see [https://bugs.launchpad.net/ubuntu/+source/choose-mirror/+bug/919356](https://bugs.launchpad.net/ubuntu/+source/choose-mirror/+bug/919356) ,but he needs some help with testing.
 
The new choose-mirror package is in the alternate CDs and I think the changes should have made there way into the ubiquity (live CD) package by now. So if you live in an exotic (i.e. non UK) location then why not have a go at installing 12.04?!! Please give feedback in the above bug report.
 
Thanks!

---

### Post by mw1coe on 2012-01-31
Works Fine here except for wifi.

But had those issues in earlier versions too.

Rob..

---

### Post by rsavage on 2012-01-31
To add to what I wrote earlier....
 
This is part of a message I got from Colin Watson a few days ago:
 
> 
Just as a tangent to bug 919356, I wonder if you - or anyone you know -
would consider being an image testing contact for the Ubuntu powerpc
images, and committing to regular testing of them before milestone
releases? Over the last couple of release cycles, this has gradually
been becoming a requirement for us to continue with daily builds of an
image;
...
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseImageContacts](https://wiki.ubuntu.com/PrecisePangolin/ReleaseImageContacts)

  
 
Now, currently I don't have a PowerPC machine. I have, however, coincidentally finally won an eBay item today so hopefully I can mend my iBook, but there is no gurantees two broken iBooks will make one good ibook. Particularly with my soldering skills.
 
So is anybody else willing to step up to the plate and volunteer to be a regular tester? I think the best contact would be somebody who has a good range of machines to try the CDs on, but it would be even better if we could get a group of people together to share the testing.
 
People have got to start getting more active in general or PowerPC Ubuntu will stop!

---

### Post by pauljwells on 2012-02-01
I'd be happy to sign up, but most of the time I'm working abroad, so only get to play with the G5 once a month or so. That said, I'd be only too pleased to get kernel version 3 finally booting...

---

### Post by svtguy88 on 2012-02-02
I have a Powerbook G4 (uhh...1ghz I think, it hasn't been on in a long while), and a Powermac G4 desktop (reasonably heavy upgrades from factory).  I'm planning to use the Powermac as my HTPC (working on a Lubuntu+Mythbuntu install right now), and could easily test LiveCD's, as necessary...

---

### Post by rsavage on 2012-02-04
That's great pkmgarf!  Can you have a go at following the testing procedure and giving some feedback to the forum on how easy/hard it is?  Hopefully you can inspire some more people to try it out.  The more people that get involved the better.

---

### Post by rsavage on 2012-02-04
I've added some other mirrors to the PowerPC FAQ [https://wiki.ubuntu.com/PowerPCFAQ#Which_repositories_have_PowerPC_packages.3F](https://wiki.ubuntu.com/PowerPCFAQ#Which_repositories_have_PowerPC_packages.3F)
 
This is just what came up from a google search.   I haven't been through each of the 300 odd official mirrors to see if they have a ports directory, but if you are abroad it maybe worth your while investigating the mirrors in your particular country.

---

### Post by svtguy88 on 2012-02-04
Where can I grab the Live CD at?  I'll be out of town on vacation for a few days, but can burn a live CD when I get home and give it a try.

I've currently been downloading from the daily builds area of Lubuntu...

---

### Post by rsavage on 2012-02-04
The repository mirrors in the FAQ are for downloading packages. I added some mirrors for PowerPC CDs to the downloads page [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads) . For the latest development (12.04) live CDs you'll have to look at mirrors that contain daily-live directories. PowerPC daily-live images will be in the same directory as other architectures. There are like 200 odd official mirrors listed - you'll have to search for your nearest, but they don't all contain daily/daily-live CDs. For example: [http://mirror.us.leaseweb.net/ubuntu-cdimage/](http://mirror.us.leaseweb.net/ubuntu-cdimage/) is in the United States. The alternate CD is in the daily directory.

---

### Post by gwjvan on 2012-02-05
The live usb  (downloaded 2-4-2012) hangs after it outputs "* Starting pbbuttonsd" on startup. Not sure if it hangs on that or on whatever it is doing after that.

I have a Powerbook5,8: G4 1.67 ghz, 15".

I was, however, able to install 10.04 and upgrade to 12.04 alpha a couple of weeks ago. Was impressed with how well it runs. (Sound broke, display brightness buttons don't work, and I have a trackpad issue that I also had with 11.10 that I'm looking into- but other than that, I'm excited about 12.04 on it)

---

### Post by wxl on 2012-02-05
with Lubuntu, here's my experience so far:

Lubuntu Precise daily-live 20120203 PPC
system [http://paste.ubuntu.com/829935/](http://paste.ubuntu.com/829935/)

4 feb 2012

[LIST]
[*] alternates are oversized
[*] official download link for desktop was missing in QA tracker
[*] firefox icon missing in panel (screenshot [http://oi39.tinypic.com/2cz82yv.jpg](http://oi39.tinypic.com/2cz82yv.jpg))
[*] icon missing on nm-applet (see above screenshot)
[*] right click not working (three finger tap though!)
[*] ctrl-click not working
[*] bottom part of displays not missing but lacking detail??? (see screenshot)
[*] all windows maximized upon opening
[*] wifi not working (see output of dmesg)
[/LIST]
[INDENT]```
$ cat dmesg | grep -i b43
    [    5.233868] b43-pci-bridge 0001:10:12.0: enabling device (0004 -> 0006)
    [  108.786493] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
    [  109.472929] Registered led device: b43-phy0::tx
    [  109.473677] Registered led device: b43-phy0::rx
    [  109.476971] Registered led device: b43-phy0::radio
    [  112.821456] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
    [  112.821468] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
    [  112.821474] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```[/INDENT]
[LIST]
[*] notification-daemon crashes upon notification launchpad bug#927040 (currently private due to core dump)
[*] can't connect to .local addresses
[*] blank during boot and shutdown
[*] file manager crash during install 926980 (private)
[*] mirror regression [http://mirror/ubuntu-ports](http://mirror/ubuntu-ports) but /etc/apt/sources.list has ports.ubuntu.com 756719
[/LIST]
      
5 feb 2012
the install ended up failing last night but due to some odd circumstances, i couldn't file a bug for it. this morning in trying to do the install again (12.04->12.04 upgrade versus last night's 11.10->12.04) i get an apt-clone crash 927368 which ends up sort of killing the install. it just sort of sits there saving installed packages, with ubiquity consuming almost no resources. so i can't recreate. off to try to get the new desktop daily going now.

---

PLEASE testers, join in on the Lubuntu testing. it is the lightest weight variant from canonical, which makes it perfect for many ppc machines. i would encourage you to join #lubuntu-offtopic on freenode and the mailing list at [http://lists.ubuntu.com/mailman/listinfo/Lubuntu-users](http://lists.ubuntu.com/mailman/listinfo/Lubuntu-users)

---

### Post by kdude55 on 2012-02-06
i have a powerbook g4 with a dead hard drive but cd drive works do i need to install ubuntu or just run live cd

---

### Post by cwklinuxguy on 2012-02-06
Unfortunately the only PowerPC machine that I own is, at this point, good for little more than parts. If I could display to an external monitor, I might perhaps be able to get it to work, but it probably isn't worth the trouble. I haven't fired it up in years...who knows if the battery is even any good now.

---

### Post by Farinet on 2012-02-06
I've a Powerbook G4 17" (2003) i'm running on Debian sid with LXDE. If needed/wished i could install a Lubuntu 12.04 on an external or scsi or usb disk (or even a stick) and try it out.

For what i saw, playing around with the live-cd of 2 febr is:

- keyboard settings seems to not work (at least it didn't accept the german mac keyboard although the option was there): 3rd level chooser does not work (or not correctly?)

- ALT-CTRL-F1 brings me to a completely messed up screen

- Shutdown/Reboot do not complete the shutdown; it hangs in the same kind of messed up screen i'm going to end with a console request.

---

### Post by allebone on 2012-02-06
64bit G5 12.04 is functional, but like some other ppl pointed out not everything works (wifi, sound etc) but the essentials are ok so no worries.

---

### Post by rsavage on 2012-02-06
I've just done the 'math' and the Ubuntu desktop and alternate CDs require 5 test cases each ([http://iso.qa.ubuntu.com/qatracker/milestones/204/builds](http://iso.qa.ubuntu.com/qatracker/milestones/204/builds)).  Multiply that by say 5 milestones ([https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)) and you are looking at 50 test cases throughout the release cycle just to maintain the Ubuntu CDs alone.
 
Aplha 1 and 2 have been missed, so that leaves 30 test cases at the least to go.  I think we need all hands to the pump on this.... this is too much for one person to take on (or we need to streamline the process).  
 
We need the test cases running on the daily builds NOW to see what passes and then concentrate on the PowerPC specific problems that come out.  If you've got some spare time just pick a test case and have a go!

---

### Post by rsavage on 2012-02-07
Argh! This is getting scary! I file bug reports and people act on them! The latest is this one [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/923094](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/923094) . I was concerned that if I was going to do a lot of testing with the text installer I wanted proper fan control for the iBook. The module has now been built into the kernel - my concern now is do non G4 'books still have good thermal management? I really don't know enough about how the kernel works!?! Can people test with the new kernel please? THIS IS VERY IMPORTANT!

---

### Post by ucube on 2012-02-07
Hi

I'm interested in helping with the PPC testing bcs I really want Ubuntu to maintain support for this architecture - the (working) options are few.
Do I need to join the "Bug Squad" to submit bugs I find in 12.04 dailies or ... post them or ... send them to someone?


Test equip:
 - 500mhz G4 cube / 32mb ATI 7500  / 1.5gb ram / 120gb hd / rtl8191s usb wlan / 

 - 1.2 ghz G4 Cube / 1.5gb ram / 64mb Nvidia geforce2MX Twinview / 160gb hd / rtl8191s usb wlan / cambridge silicon radio bluetooth - usb /

---

### Post by Farinet on 2012-02-07
I tried to install a Lubuntu 12.04 powerpc from a live cd i downloaded from [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/) 

Unfortunately, the installation did not pass through, since the installer did not find the ubuntu server (internet connection was working correctly). I think that might be, because in the standard ubuntu servers there does not exist the powerpc builds of the software that should be loaded. Oh, i opted for Suisse in the country and keyboard settings.

What would be the way to avoid that?

---

### Post by rsavage on 2012-02-08
To answer several posts and general info:
 
Anybody can submit bugs - the bug squad I think help sort out the bugs, so they prioritise them, look for duplicates etc.  They're the people who will first read the bugs you submit.
 
Before submitting a bug (or testing in  general) it's a good idea to familiarise yourself with the known issues page [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) and FAQ [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) .  So the problem fairnet (and wxl) has described has been reported before and a workaround exists.  Sadly, the fix doesn't seem to be working so that needs reporting back to Colin Watson via the existing bug reports.  Including the ubiquity logs would probably be useful.  This wiki [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) describes how to submit bugs.
 
In order for ISOs to be released we need subscribers for the test cases [http://iso.qa.ubuntu.com/qatracker/reports/subscriptions](http://iso.qa.ubuntu.com/qatracker/reports/subscriptions) .  This wiki [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures) describes the testing procedure.
 
I think it is probably a good idea to make others aware of any bugs you raise via this thread and on the known issues page.  
 
General feedback via this thread is also useful.  For example, is the network applet icon misssing (see wxl post) for airport classic or just airport extreme?  Getting that sort of feedback from people helps to track down the problem.  You don't need any technical skills to know if your fan is working or not - so feedback on that is invaluable.  If peoples fan control has been mucked up then the kernel change from bug 923094 needs urgently reversing.
 
Basically, if you discover a PowerPC problem then it's up to you to do something about it.  The more you can do to research the problem the more chance you have of it being fixed.  But, don't use the lack of skills as an excuse because everybody can play some part in testing.

---

### Post by AnsonX10 on 2012-02-08
I've got this PowerBook G4 2002 TiBook, and finally got Ubuntu running on it. (I'm writing this on it right now.) Then I found this thread, and thought I'd post some info.

It's running 12.04 with all the updates as of right now. 

The Live CD couldn't make the HFS drive a bootstrap/yaboot compatible drive or something like that, the alternative CD could though, and did. I used dd on a PowerMac G4 running Leopard to write the ISOs to a 1gb USB drive, and booted the laptop off of that.

All versions 10 would not show anything on screen upon booting from the USB, save for a few lines.

The mini CD for 11 couldn't make the internal drive boot without help, but That was almost a week ago that I last tried that.

The reason I tried installing Ubuntu on this thing is because the Mac OS 10.5 system it had on it had terrible graphical glitches, to the point that you couldn't see anything. I had fixed it once by installing the system anew, but the disc drive doesn't work anymore. I thought it must be the logic board had gone out, but I wasn't sure. So when I found out that Ubuntu 12 fixed everything, I knew it must've been the system.

Bugs: 
The sound is not working right now, after I installed updates, but was working fine right after system install. I had/have to press fn with the volume buttons for them to work. However, the microphone level meter shows input when I'm yelling at the computer for not playing music. (lol) So the speakers and headphone output aren't working, but the microphone and sound input is. 
EDIT: Nevermind that. (look down for info)

The simulated right click isn't working now either after updates. Ctrl click doesn't even work on an i386 pc. So, being deprived of my spell checking abilities, there may be some typos in this post.
EDIT: Nevermind this too.

The display works great when the system is giving it a signal, without any glitches whatsoever. But when the screen isn't getting any signal, the backlight and power stay on, but the picture gets buggy like a cheap LCD screen when it's turned off. (The picture slowly fades away, but a lot more slowly than it usually does.) 

The screen also gives this response a few times during booting, but I find that almost natural. BUT when I change to a resolution other than the native (1280 by 854) it's the same thing. No signal. Luckily the timeout returned the screen to the previous resolution, restoring the picture without any further problems. 

I haven't tried rotation yet because I want to get this posted before risking it.
EDIT: I tried rotation, and strangely it gives me graphical glitches amazingly similar to the ones I had on Mac OS X before I wiped it and installed Ubuntu 12.04. It does this at all three non-normal settings. I can see enough to click the restore button, which brings back the crystal clear picture I've come to know and love from Ubuntu on this computer.

The brightness buttons don't work, but I believe someone else mentioned that.

The battery works when I unplug the laptop, but doesn't seem to have any settings or indicators anywhere. However it wasn't in the computer when I installed the system, nor for the first boot, so that may be my fault.

The system runs a lot hotter than Mac OS X did, but both fans work, which is more than OS X did most of the time. I'm not worried about this though. Taking the keyboard off and touching the heat sinks and metal covers is more painful than it was with OS X, but that's the only way I'd know it was running hotter. OS X probably should have been running like this. There are temp warnings in there after all.

The keyboard's num lock doesn't work, but this may not be a bug.

Pressing f11 doesn't work to make anything fullscreen, it seems to cut and move text around. This is probably a result of my own ignorance though. 

My "u" key keeps falling off. (The worst bug. FIX THIS NOW!) lol

Other than that everything seems to be working fine. As much as a community supported pre-released operating system should be anyway. Slight software incompatibilities, but I don't consider those bugs yet.

PS I accidentally just hit f12 and realized that it made a right click! I knew f12 was supposed to do that, but never had any luck with other computers. but I'm not going to go back and spell check everything because I'm feeling lazy. That and I have other more vital stuff to do. So maybe that means I'm feeling more diligent. lol

EDIT: I forgot to mention that this PowerBook doesn't have an AirPort card in it, so I can't say anything about that. But it does work with a Belkin USB Wireless antenna (F5D7050) that all Ubuntu versions have worked with since 7.10 (when I started using it.)

Also, a few more updates and a restart, sound seems to be working again. A few pops and such when starting audio, but it did that before as well. I have a feeling this one may have been my fault.

Simulated right clicking is working again as well.

I'm happy.

---

### Post by svtguy88 on 2012-02-09
> **rsavage said:**
> The module has now been built into the kernel - my concern now is do non G4 'books still have good thermal management? I really don't know enough about how the kernel works!?! Can people test with the new kernel please? THIS IS VERY IMPORTANT!

I'm in class right now, and away from my PPC boxes.  What module was compiled in?  As long as a module was just added (don't remember off hand, something about ADT_temp, I think the name is?), and nothing was removed, everything should be good.  The kernel will only load the modules it needs.

I'll grab a new USB stick and set it up for live CD testing (I think it's going to be painful with USB 1.1, but I'll try it...better than wasting stacks of CDs).

I should mention that I've built myself a few kernels and am *semi* familiar with some of the necessary PPC modules (as far as what's needed).  Let me know if there's anything I can do to help.

---

### Post by svtguy88 on 2012-02-09
Oh, and I guess I should say how my testing has gone (Lubuntu daily CD used to install, and then updated via update-manager a few days later).  

I had to do the usual fiddling to get my system to boot (to be expected - my SATA card is an "ACARD,6280M" which the yaboot installer (well, ofpath is really what fails, but it's during the yaboot install) can't deal with.  But, this has been the case for a while, and I know what lines to ammend in yaboot.conf to get things working.

Other than that, most things work fine.  I was having an issue with the lower half of the screen being blacked out, especially when maximizing windows.  I'm not sure if this has been discussed already, or if it's a nouveau issue.

I don't recall what PPC Macs came with Nvidia video hardware (most were ATI, right?  I think my Powerbook is), but my main PPC machine has a Geforce 6200 (PCI) in it, and I have some issues.  The most pressing one is that the display seems to be in a low-depth color mode.  Is there a way to check the bit-depth being used, or a way to force a higher one?   All in all, X seems to behave better than the last time I had this machine up and running - I didn't need to make a Xorg.conf to get things to work (but I suspect I will to get the correct color depth working - I remember that issue from last time).

Speaking of nouveau, where do we stand on 3D support?

I know 3D should be supported, but I don't think the required version of nouveau and it's dependencies gets installed by default.

---

### Post by AnsonX10 on 2012-02-11
Got an update:

Today's (Or should I say yesterday's) updates brought display distortion back. Ugh. Seemingly the same one that bugged Leopard. Not quite as bad, but exactly the same things.

To test my notion that it was the update, I reinstalled the OS from the 12.04 alternate USB I still had, and install went great. Right back to perfection. But after updating again the graphical glitches returned. So I know that's what caused them.

I would like to narrow it down to which package is causing this, but I have no idea which packages could be capable of this horrendous feat. I can install them one by one, but there's over a hundred on them, and I don't even know which ones deal with displays. Ubuntu 12 will be obsolete and the screen will burn out by the time I test all 150-or-so of them. Since I can't turn the brightness down, It'll probably burn out anyway. lol

So with some help, I'd love to get this fixed because this is the reason I'm running Ubuntu on this computer.

---

### Post by rsavage on 2012-02-12
Just a v quick message with a few more issues for people to have a look at:
 
I've been concentrating on the test cases to see if we can pass all of them.  I reported the archive mirror problem again and Colin Watson has had another go at fixing it.  It should appear in the live cds in the next few days so can people test when it appears?  See original post.
 
I've tried to get usb/cd persistence to work - which it does - only gvfs-gdu-volume-manager immediately stops working and closes.  Can anybody confirm this is a problem?
 
Automatic installing when there is already a ubuntu system installed causes problems because you get two bootstrap partitions labelled "bootstrap".  ybin then doesn't update nvram correctly.  The only way to boot the new system is holding down the option key.

---

### Post by svtguy88 on 2012-02-12
> **rsavage said:**
>  
Automatic installing when there is already a ubuntu system installed causes problems because you get two bootstrap partitions labelled "bootstrap".  ybin then doesn't update nvram correctly.  The only way to boot the new system is holding down the option key.

Does the live-CD give you the ability to run a shell before rebooting the system?  You should be able to run chroot into the newly installed system, and run "ybin -b /dev/yourBootPartition" to update everything correctly....yes?

---

### Post by rsavage on 2012-02-12
Thanks pkmgarf. I can boot the system fully - no probs. I was wrong on the cause though. The installer is clever enough to figure it out and defines boot in the yaboot.conf via /dev/disk/by-id/ instead of /dev/disk/by-label/. So the labels don't matter. I can get a sensible value from ofpath so I don't think it is that either.
 
Has anyone else tried dual booting with different linux distros? I never know if something isn't working becuase of software or my hardware!

---

### Post by rsavage on 2012-02-12
> **pkmgarf said:**
> I'm in class right now, and away from my PPC boxes. What module was compiled in? As long as a module was just added (don't remember off hand, something about ADT_temp, I think the name is?), and nothing was removed, everything should be good. The kernel will only load the modules it needs.
 
I'll grab a new USB stick and set it up for live CD testing (I think it's going to be painful with USB 1.1, but I'll try it...better than wasting stacks of CDs).

 
I see testing as checking what *should happen* actually is happening. I'd be a lot happier if windfarm/windtunnel/windwhatever users got in touch to say everything was okay. Also G4 iBook/Albook users to say it still works when built in.
 
Why don't you copy the CD files to a hard drive partition? That is what I am planning on doing. My USB stick is too dodgy and is beginning to be a pain to use. You can create a separate bootstrap partition to fire up the 'CD' or edit your existing bootstrap yaboot.conf. I can put instructions together if anybody is interested. 
 
@AnsonX10 It could be your kernel or xserver-xorg-video-nouveau package causing your graphics glitch. For brightness adjustment see [http://www.mintppc.org/forums/viewtopic.php?f=15&t=773](http://www.mintppc.org/forums/viewtopic.php?f=15&t=773), but there is bound to be a better way. I don't have nouveau so can't help you more. Except to point you to the FAQ [https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics](https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics) .

---

### Post by svtguy88 on 2012-02-12
> **rsavage said:**
> 
 
Why don't you copy the CD files to a hard drive partition? That is what I am planning on doing. My USB stick is too dodgy and is beginning to be a pain to use. You can create a separate bootstrap partition to fire up the 'CD' or edit your existing bootstrap yaboot.conf. I can put instructions together if anybody is interested.  .

Hmm...I may have to give that a go.  It should be WAY faster than a disc or USB 1.1.

I should have some time tomorrow to play with this stuff.  I'll try to get to get both my tower and Powerbook setup for testing.  Oh, and if there's any need, I've "acquired" a G4 iLamp (err...iMac) that I'm pretty sure still works fine.

---

### Post by rsavage on 2012-02-13
I found my ybin problem. Stupidly I had missed the error message when I ran it. It is complaining about a lack of /dev/nvram. Has anybody else got this problem and anybody got a clue how to fix it properly so we can report it as a bug?
 
EDIT: Possibly this? :
 
 CC [M]  arch/powerpc/platforms/chrp/nvram.o

Used to be built in.

---

### Post by phillw on 2012-02-13
Hi guys and gals,

For the interest in lubuntu, I am struggling a bit. There are many discussions going on via forum, email, facebook etc. I do now ask that those people wishing for lubuntu on PPC do take the time to bookmark it and get on the lubuntu-qa.
[https://wiki.ubuntu.com/Lubuntu/Testing/PPC](https://wiki.ubuntu.com/Lubuntu/Testing/PPC)

Regards,

Phill.

---

### Post by FG Trooper on 2012-02-14
Hi, so i have download Ubuntu 12.04 for PowerPC, i have a Powerbook g4 titanium, the mercury one. I have upgrade the ram to 1 gb. When i boot Ubuntu from my Powerbook, the session is open on low graphic mode with poor color and distorsion. How i can fix it ? Does you have an xorg config for this config, the graphic card is the Ati Rage 128 from the original. It is sure than 8 mb of video ram is poor.

Thank.

---

### Post by svtguy88 on 2012-02-14
> **rsavage said:**
>  
Why don't you copy the CD files to a hard drive partition? That is what I am planning on doing. My USB stick is too dodgy and is beginning to be a pain to use. You can create a separate bootstrap partition to fire up the 'CD' or edit your existing bootstrap yaboot.conf. I can put instructions together if anybody is interested.

I just reinstalled from an alternate disc from around Feb 2nd, and left myself room for a "testing" partition.  Anyway, I unpacked today's live-CD to my test partition, but how do I get yaboot.conf to point to that partition without ruining the current setup (I want to be able to boot the system I just installed, as well as the Live-CD).

---

### Post by svtguy88 on 2012-02-14
Also, my "clean" install (from the 2/2/12 disc) plus updating to today's packages via update-manager gives me a decent system it seems like.  I have normal color (no more 8 bit or whatever it was before)....and, Nouveau appears to be behaving fine.  System Profiler shows "unknown" for my glx vendor and other data, but glxinfo shows direct redering with Gallium .4

Finally, graphics are starting to work right.  I am stuck with using the VGA output, as it won't automatically use the DVI out.  Monitor settings shows the "I-1" output (DVI), but if I click "turn on" and apply, nothing happens (VGA output remains, but the monitor hooked up via DVI still shows no signal).  Is there a way to force output to a specific connector?

---

### Post by rsavage on 2012-02-15
Yaboot: From memory just copy the stanza (I think that is the correct term?) you want from /install/yaboot.conf on the live CD. Paste it into the yaboot.conf on your installed system. Now change
 
image=/casper/powerpc/vmlinux
 
to 
 
image=hd:4,/casper/powerpc/vmlinux 
 
Similarly add hd:4, in front of /casper/powerpc/initrd. Where hd:4 is your partition with the live CD files. You can leave the file= line as it is even though it says /cdrom.
 
I think the hd:4 should work, I actually used the longer [EMAIL="image=/pci@f4000000/ata-6@d/disk@0:4=/casper/powerpc/vmlinux"]image=/pci@f4000000/ata-6@d/disk@0:4=/casper/powerpc/vmlinux[/EMAIL] 'cos that it what the automatic setup uses.
 
Finally, run sudo ybin -v and see if you get an error about nvram at the start.
 
I'm having a bit of a problem with my partition numbers. Because the auto installer is adding partitions my partition numbers are changing and it is mucking up my existing yaboot.conf file. 
 
Graphics: Have a look at the FAQ - it has lots of links to the various wikis. I don't really understand why you both are in low colour mode. If there is a problem the installer must now revert back to the fbdev driver. 
 
@pkmgarf Is your network manager applet working? I tried Ubuntu proper yesterday and the applet works better in that than lubuntu from the other day.

---

### Post by rsavage on 2012-02-15
pkmgarf, let me know if you get the live cd on a hard drive to work fully.  It is refusing to auto install from it at the moment complains about can't unmount /cdrom.  And it won't let me manually set partitions.

---

### Post by svtguy88 on 2012-02-15
I'll see if I can get the live-CD partition to work later today.  I won't really be able to test the "automatic-ness" of the install though.  I have to basically create my yaboot.conf manually (or at least parts of it), as my SATA card is not supported by ofpath.  Anyway, I can let you know how the live CD works, as far as booting and such, but I ALWAYS have yaboot issues after a fresh install.

And I'm out of low color mode.  Not sure why it was stuck in it, but everything is fine now...3D support and all.  This is refreshing - in every attempt to get linux up to snuff for an OS X replacement on this machine, I always ended up with bad graphics.  Good to see that's sorted out.

---

### Post by svtguy88 on 2012-02-15
Alright.  I'm working on getting the live-CD to boot from a partition, but I'm running into a problem.  I've got yaboot.conf pointing to the open firmware path to vmlinux and initrd, but what do I do about the root file system (the "root=" entry in yaboot.conf)?

As is, the system tries to boot the Live-CD partition, but fails, complaining that it can't find /dev/sdb3 (which is what's defined as the root in yaboot.conf).

Also - I do run into the same nvram error that you get when running ybin.  I ran ybin after setting my yaboot.conf, and rebooted, but whatever happened, it broke yaboot.  I had to use a rescue disc to repair it.  I just had to run mkofboot and ybin again, but I did use the open firmware ("-o") flag, just in case.  I can now boot my system again, but I get the "Mac Smiley" icon for a few seconds now (the icon that flashes when there's nothing to boot from), but eventually I get the first stage of yaboot...weird...

---

### Post by rsavage on 2012-02-15
Ah, I see my mistake.  I said it was from memory!
 
image=/casper/powerpc/vmlinux
initrd=/casper/powerpc/initrd
 
are the lines you want to change.  You only need to adjust the stanza that you have added and that shouldn't have a root=.  The other stanzas will work as before.

---

### Post by svtguy88 on 2012-02-15
Yeah, I found vmlinuz/initrd in the casper/powerpc folder - so that's already in my yaboot.conf.  I have the root defined in the top of the file:



```
#boot=/dev/sdb2
ofboot=/pci@f2000000/pci-bridge@d/ACARD,6280M@3/disk@0
partition=3
root=/dev/sdb3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
enableofboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

#test partition
image=/pci@f2000000/pci-bridge@d/ACARD,6280M@3/disk@0:5,/casper/powerpc/vmlinux
	label=Live-CD Test
	read-only
	initrd=/pci@f2000000/pci-bridge@d/ACARD,6280M@3/disk@0:5,/caster/powerpc/initrd
```

Do I just move the root= to each stanza?  I'll give it a try once the system is done compiling (trying to get XBMC to work...there's no PPC binaries).


Oh, and before I forget, does suspend work for anyone?  Clicking "suspend" or issuing "pm-suspend" does nothing for me...

---

### Post by Farinet on 2012-02-17
I've installed Lubuntu 12.04 powerpc and i'm paying around with. One thing, very annoying, is there is something wrong with the control of the fan. For what i see, the CPU is always running on maximum speed (1333 MHZ) never going down - even when i'm not doing anything. And, i think, consequently the fan after a while begins to work without any interruption

I've in parallel a setup with Debian "sid" powerpc and LXDE: there the cpu speed is varying between 816 and 1333 MHZ and the fan is only running once in a while.

Now, unfortunately i forgot, where and how i could setup/allow the cpu speed change and where is the config file for the fan (therm_adt74x i think).

Thanks in advance for any advice!

PS. Oh, i've installed pbbuttonsd & powerprefs, but there i don't see the requested options (?)

---

### Post by FG Trooper on 2012-02-18
I don't know what is the problem with low color graphic but i will need to remake a live usb. My dvd drive is broken... It seem i cannot found anything about low color on ati because this seem to be a more common error on nvidia. It seem Ati graphic card on Apple hardware is rare on PowerPC G4 like my PowerBook. I will download the alternate or the net install and give it an another try. My friend who is a colector like me have a Imac G3, those who have save apple in 1998. I will test it on both. I have a old Mac LC II who i hope to found a distro for m68k arch...

Thank guy and i will report my test. ^_^

---

### Post by Farinet on 2012-02-19
> **FG Trooper said:**
> I don't know what is the problem with low color graphic but i will need to remake a live usb. My dvd drive is broken... It seem i cannot found anything about low color on ati because this seem to be a more common error on nvidia. It seem Ati graphic card on Apple hardware is rare on PowerPC G4 like my PowerBook. I will download the alternate or the net install and give it an another try. My friend who is a colector like me have a Imac G3, those who have save apple in 1998. I will test it on both. I have a old Mac LC II who i hope to found a distro for m68k arch...

Thank guy and i will report my test. ^_^

I have a PB G4 17" with Ati Radeon graphic card. And that for one, works out of the box with 12.04 for me, safe the problem that the logout screen is messed up although the logout/shutdown/reboot passes through.

PS. Check maybe the mintppc.org forums, i remember there were some excellent advices how to tweak graphic cards.

---

### Post by rsavage on 2012-02-19
> **Farinet said:**
> 
PS. Check maybe the mintppc.org forums, i remember there were some excellent advices how to tweak graphic cards.
 
No. 
 
Much of what is written on forums is incorrect or dated.
 
Fairnet, please direct people to the Ubuntu documentation. There is a large section on how to configure graphics, much of it based around the ATI rage 128 because that is troublesome. [https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics](https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics)

---

### Post by svtguy88 on 2012-02-19
Hmmm...I thought ATI graphics were pretty much sorted out.  I'll intstall onto my Powerbook tomorrow or tuesday (has an ATI card) and I'll let you guys know what I get.

I"m confused as to why low-color mode happens.  My Nvidia was stuck in it until recently, when reinstalling via a newer CD fixed my problem, but I still have no idea what had cuased it.

---

### Post by FG Trooper on 2012-02-20
So, i test the alternate installer. The installer crash at the end but i finish it. Don't have everything installed. I will need to restart the installer...

---

### Post by Farinet on 2012-02-20
Another problem on Lubuntu 12.04 ppc. I did an upgrade (proposed by the Update manager, which included a new kernel (from 3.2.0-16 to 3.2.0-17). Now, by chance, i discovered, that i'm still running on kernel 3.2.0-16 although the newer one is there.

Checking a little bit the involved files i think i found, *WHY* actually i'm still on the older kernel. But not, what's the reason for that misfunction.

My lubuntu-disk (an external firewire hd) is partitioned as follows:

sdc1: 32kb (Apple openrom) sdc2: bootstrap, sdc3: "/" (ext4), sdc4:
swap, sdc5 (8kb): extra

Now, on the top level of sdc3 i see there are 3 symlinks:

vmlinux (points to /boot/vmlinux-3.2.0-17-powerpc)
initrd.img (points to /boot/initrd.img-3.2.0-17-powerpc)
initrd.img.old (points to /boot/initrd.img-3.2.0-16-powerpc)

In the /boot directory there are all the 3.2.0-17 and 3.2.0-16 files
but also 2 symlinks (vmlinux and initrd.img which points to the
3.2.0-16 files).

Then i checked the /etc/yaboot.conf file. It looks like this (i didn't
touch it at all!):

--------------
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot="/dev/disk/by-id/ieee1394-0001a300000586c7:000428:0000-part2"
device=/pci@f4000000/firewire@e/node@0001a300000586c7/sbp-2/@0
partition=3
root="UUID=7393551e-1a0f-4461-8d87-82f4c75d8203"
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"
--------------

So, it looks to me that, the update manager did something wrong: It
should have put the 3 files i now find on the top level into the /boot
directory and to rename the already existing symlinks to *.old. The
yaboot.conf file, which as far as i understand, commands the boot
procedure, doesn't look to the "/" directory but into /boot . . . Or
am i getting something wrong here?
. . .
Now, my question should/could i do this by hand - for the moment? Or
will i have to edit the yaboot.conf file?

But, in any case, in a funtional system it should work without bricolage, IMHO. And i think, guessing in the dark, the error lies somewhere between the installer which installs yaboot and the corrispondent yaboot.conf file and the update manager which seem to refer to different standard places (?).

---

### Post by svtguy88 on 2012-02-20
I can't comment on why this is happening, but you correct in thinking that you can manually rename the files to match yaboot.conf.  Alternatively, you could edit your yaboot.conf to point to /vmlinux.  Either will work.

Yaboot will boot whatever image you give point it to (be it /boot/vmlinux or /vmlinux, or /boot/vmlinux.old, or whatever really).  As long as yaboot finds the image that yaboot.conf points to, it should all work fine.

---

### Post by Farinet on 2012-02-20
> **pkmgarf said:**
> I can't comment on why this is happening, but you correct in thinking that you can manually rename the files to match yaboot.conf.  Alternatively, you could edit your yaboot.conf to point to /vmlinux.  Either will work.

Yaboot will boot whatever image you give point it to (be it /boot/vmlinux or /vmlinux, or /boot/vmlinux.old, or whatever really).  As long as yaboot finds the image that yaboot.conf points to, it should all work fine.

Thanks for answering and thanks for the good news! :) And oh, the symlinks on the topmost level of the root partition i can delete . . . (?)

Just another question: when/if i edit the yaboot.conf *THEN* after editing i'd have to to some ybin (to parallel it to the yaboot.conf, which is on the bootstrap partition correct. And there, frankly, i'm not so skilled ;-) especially when it comes to deal not anymore with /dev/.... but with the disk id's like in my case i'm afraid i'd have to do.

PS. I chose the first option, but booting failed. Looking closer, i see there is something wrong with the `vmlinux-3.2.0-17-powerpc`- while the older version is a program, the newer one is "unknown filetype". This remains even the same after a complete reinstallation of the 3.2.0-17-powerpc kernel. Could that be in some way corrected or is that a bug of the kernel package itself?

---

### Post by Farinet on 2012-02-20
I figured the problem out, it was multiple and i think something went
wrong with the kernel 3.2.0-17-powerpc package or the installation script (?)

1) The /boot/vmlinux-3.2.0-17-powerpc had in origin the wrong rights. It was:
Owner: root
Group:  root
Rights
Owner: Read & Write
Group: None   |  But should be: Read only
Others: None  |  But should be: Read only

2) The /boot/vmlinux symlink pointing to the /boot/vmlinux-3.2.0-17-powerpc
instead of pointing to `vmlinux-3.2.0-17-powerpc` pointed to
`boot/vmlinux-3.2.0-17-powerpc`

3) The symlinks vmlinux, initrd.img and initrd.img.old were put to the
topmost level of the root partition ("/") instead of /boot

I corrected all that by hand and now, the system is booting flawlessly
into the 3.2.0-17 kernel.

I think that error is somewhat systematic since after a purge of
3.2.0-17-powerpc and a reinstallation (by apt-get) it was exactly the
same.

---

### Post by FG Trooper on 2012-02-26
It seem my installation crash at installing libc-bin at Select and install Software step or just after. I have test with offline and online install with the same alternate cd booted on usb.

Hope the bug was already corrected. ^_^

---

### Post by Farinet on 2012-02-26
This might be a general problem between all flavours of ubuntu ppc and yaboot:

Even with  a fresh install (of lubuntu 12.04) which still came with kernel 3.2.0-16 the
update to 3.2.0-17 didn't pass like expected:

The 3 files (symlinks!) vmlinux, initrd.img and initrd.img.old were put
on the mount level ( / ) and not into /boot where they should be to
point to the newer kernel. I've to do that by hand. Frankly, in Debian
that problem never happened.

The same happened already with an installation of the beginning of febr.

PS. On Debian i read an interesting thread that explained it would be not so difficult to use grub instead of yaboot which would makes things much easier (they said - frankly, i'm feeling not really sufficiently knowledged to tweak this things by my own ;-) )

---

### Post by FG Trooper on 2012-02-26
Install success ! ^_^ But, have low graphic mode... -_-

So, i will test tommorow to use it be terminal for updating the drivers.

---

### Post by Farinet on 2012-02-27
> **Farinet said:**
> This might be a general problem between all flavours of ubuntu ppc and yaboot:. . . . 

In addition to what i wrote in my previous post: The *vmlinux-3.2.0-17-powerpc *which was installed by the upgrade had the wrong rights:

Owner: root (correct)
Group: root
Rights
Owner: read & write (correct)
Group: nothing (wrong: should be **read only**)
Others: nothing (wrong: should be **read only**) After correcting that (as root, obviously) boot into 3.2.0-17 works.

But, since this error happened the second time i presume there is something wrong with the install/update script for the kernel update.

---

### Post by svtguy88 on 2012-02-27
I can confirm that the kernel image and such got installed to "/" (root) instead of /boot when updating via update-manager.  I noticed the problem, and moved the files to where they belong.  I haven't had this come up since then though (this was about a week ago).

Has anyone else still having this problem?

---

### Post by svtguy88 on 2012-02-27
Also, I still have the issue of black backgrounds on some popup dialogs (update-manager, for example).  I remember reading other people complaining about it, but figured it would have sorted itself out by now.

---

### Post by gwjvan on 2012-02-29
The live cd image just hangs after it outputs pbbuttonsd, and after I install from the alternate CD, it hangs after trying to start the wireless (it gives the message to go to the appropriate website and download the drivers, etc, then just sits there).

Now, I'm guessing neither pbbuttonsd or the wireless issue are what is causing 12.04 to hang. Is there some kind of way to get detailed output about what it is doing? (I already press esc during boot up to get the overview of what is loading, etc). Or is there a quick way to change/view the startup script/etc to see what precedes/comes after certain boot events? (Like what comes after pbbuttonsd or the wireless networking setup attempts?)

---

### Post by Farinet on 2012-03-04
Yesterday i tried out ***lubuntu-12.04-beta1-desktop-powerpc.iso*** - unfortunately i was unable to install it because of the still persisting black background for most, if not all, applications. So i limit myself to list the problems i noted from playing around with the live-cd:

° The boot screen is still simply black, showing only some lines shortly before starting the display manager (desktop).

° The first thing that happens then is, you're prompted with the msg that a program crashed and if you would like to report (it's the notification daemon).

° Alt-Ctrl-F1 (trough F6) works, but it brings me to a completely messed up, unreadable console screen. Alt-Ctrl-F7 brings me back correctly to the dektop.

° The background of many (all?) programs is black, the text of the not activated (greyed) options often is unreadable, which makes it difficult to setup things (e.g. working with the network manager).

° The networkmanager does not give the symbol of wireless (or wired)  in the panel but only an empty space. Clicking it activates the configure window (as usual).

For the moment, i desisted from installing because actually i don't have a second computer here and i didn't want to mess up the working debian - lxde setup i've running because of the difficult control of the installer.

Unfortunately i don't know how to do a bug report regarding the black background. I'm only able to describe, what i see ;-)

---

### Post by steelsteel on 2012-03-04
Hello Guys!

I hope i have found the right thread.
I am trying to install an Apple Xserve G5 PowerPc with Ubuntu.

I tried 10.04, 11.04, 11.10 an all stopped at some point.

Now i was testing with 12.04 daily desktop.
But like this other person I am having trouble with the harddisks (for reasons of keeping a backup till the installation has proven to work i only inserted one of the tree identical harddiks in the left slot) - the installer says sth bout "megaraid" and thats ist. 

Link to the imho related post:
[http://ubuntulinuxgethelp.com/2012/03/ppc-ubuntu-11-10-ppc-installation-on-a-g5-no-joy/]("http://ubuntulinuxgethelp.com/2012/03/ppc-ubuntu-11-10-ppc-installation-on-a-g5-no-joy/")

I will try downloading your "test" iso and give it a try now.
Would be great if you could help us!

Yours,
Andreas

Edit:
I encountered my problem: I removed the "lsi megaraid" pci card completely and attached the disks directly onto the mainboard.
Now its working like a charm.

My (!) Problem solved!

---

### Post by steelsteel on 2012-03-04
But i found a BUG - after a while system fans start very loudly:

dmesg | tail:

ondemand governor failed, too long transition latency of HW, fallback to performance governor
[   76.385466] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[  297.905489] low_i2c: Timeout in i2c transfer on keywest !
[  297.905495] low_i2c: Timeout in i2c transfer on keywest !
[  297.905520] i2c i2c-4: I2C write to 0x2c failed, err -5
[  297.921406] KW: wrong state. Got KW_I2C_IRQ_STOP, state: state_addr (isr: 04)
[  297.921430] i2c i2c-4: I2C write to 0x2c failed, err -5
[  297.937488] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  297.937529] i2c i2c-4: I2C write to 0x2c failed, err -5
[  297.953454] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  297.953482] i2c i2c-4: I2C write to 0x2c failed, err -5
[  297.969444] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  297.969484] i2c i2c-4: I2C write to 0x2c failed, err -5
[  297.985441] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  297.985473] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.001430] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.001468] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.017424] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.017457] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.033417] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.033452] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.049407] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.049439] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.065399] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.065432] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.065726] therm_pm72: Error reading ADC !
[  298.066060] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.066085] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.081386] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.081424] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.097381] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.097414] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.113374] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.113407] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.129368] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.129400] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.145361] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.145393] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.161351] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.161390] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.177345] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.177380] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.193334] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.193367] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.209327] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.209359] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.225317] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.225347] i2c i2c-4: I2C write to 0x2c failed, err -5
[  298.225639] therm_pm72: Error reading ADC !
[  298.225978] KW: wrong state. Got KW_I2C_IRQ_DATA, state: state_addr (isr: 01)
[  298.226004] i2c i2c-3: I2C write to 0x2f failed, err -5
[  298.241231] KW: wrong state. Got KW_I2C_IRQ_STOP, state: state_addr (isr: 04)
[  298.241250] i2c i2c-3: I2C write to 0x2f failed, err -5
[  298.257770] Failure writing to FCU: -6
[  298.290650] Error -6 reading backside fan !
[  298.293746] Error -6 reading slots fan !
[  298.942921] Error -6 reading backside fan !
[  298.945996] Error -6 reading slots fan !
[  299.946030] Error -6 reading backside fan !
[  299.949105] Error -6 reading slots fan !
[  300.945470] Error -6 reading backside fan !
[  300.948602] Error -6 reading slots fan !
[  301.944899] Error -6 reading backside fan !
[  301.948069] Error -6 reading slots fan !
[  302.940161] Error -6 reading backside fan !
[  302.943352] Error -6 reading slots fan !
[  303.944238] Error -6 reading backside fan !
[  303.947300] Error -6 reading slots fan !
[  304.943624] Error -6 reading backside fan !
[  304.946691] Error -6 reading slots fan !
[  305.943216] Error -6 reading backside fan !
[  305.946310] Error -6 reading slots fan !
[  306.942589] Error -6 reading backside fan !
[  306.945741] Error -6 reading slots fan !
[  307.937737] Error -6 reading backside fan !
[  307.940898] Error -6 reading slots fan !
[  308.941285] Error -6 reading backside fan !
[  308.944402] Error -6 reading slots fan !
[  309.937459] Error -6 reading backside fan !
[  309.940608] Error -6 reading slots fan !
[  310.940713] Error -6 reading backside fan !
[  310.943823] Error -6 reading slots fan !
[  311.939758] Error -6 reading backside fan !
[  311.942905] Error -6 reading slots fan !
[  312.939411] Error -6 reading backside fan !
[  312.942607] Error -6 reading slots fan !
[  313.939006] Error -6 reading backside fan !
[  313.942098] Error -6 reading slots fan !
[  314.938460] Error -6 reading backside fan !
[  314.941666] Error -6 reading slots fan !
[  315.937939] Error -6 reading backside fan !
[  315.941033] Error -6 reading slots fan !
[  316.937504] Error -6 reading backside fan !
[  316.940623] Error -6 reading slots fan !
[  317.936783] Error -6 reading backside fan !
[  317.940003] Error -6 reading slots fan !
[  318.936620] Error -6 reading backside fan !
[  318.939818] Error -6 reading slots fan !
[  319.936278] Error -6 reading backside fan !
[  319.939399] Error -6 reading slots fan !
[  320.935548] Error -6 reading backside fan !
[  320.938703] Error -6 reading slots fan !
[  321.931367] Error -6 reading backside fan !
[  321.934460] Error -6 reading slots fan !
[  322.934731] Error -6 reading backside fan !
[  322.937824] Error -6 reading slots fan !
[  323.929599] Error -6 reading backside fan !
[  323.932798] Error -6 reading slots fan !
[  324.933427] Error -6 reading backside fan !
[  324.936565] Error -6 reading slots fan !
[  325.932988] Error -6 reading backside fan !
[  325.936080] Error -6 reading slots fan !
[  326.928861] Error -6 reading backside fan !
[  326.931948] Error -6 reading slots fan !
[  327.931992] Error -6 reading backside fan !
[  327.935076] Error -6 reading slots fan !
[  328.927223] Error -6 reading backside fan !
[  328.930354] Error -6 reading slots fan !
[  329.927214] Error -6 reading backside fan !
[  329.930403] Error -6 reading slots fan !
[  330.930520] Error -6 reading backside fan !
[  330.933701] Error -6 reading slots fan !
[  331.929978] Error -6 reading backside fan !
[  331.933073] Error -6 reading slots fan !
[  332.929242] Error -6 reading backside fan !
[  332.932482] Error -6 reading slots fan !
[  333.928856] Error -6 reading backside fan !
[  333.931945] Error -6 reading slots fan !
[  334.924757] Error -6 reading backside fan !
[  334.927866] Error -6 reading slots fan !
[  335.924399] Error -6 reading backside fan !
[  335.927515] Error -6 reading slots fan !
[  336.927731] Error -6 reading backside fan !
[  336.930899] Error -6 reading slots fan !
[  337.927188] Error -6 reading backside fan !
[  337.930358] Error -6 reading slots fan !
[  338.922867] Error -6 reading backside fan !
[  338.926019] Error -6 reading slots fan !
[  339.926134] Error -6 reading backside fan !
[  339.929225] Error -6 reading slots fan !
[  340.925733] Error -6 reading backside fan !
[  340.928874] Error -6 reading slots fan !
[  341.924795] Error -6 reading backside fan !
[  341.927909] Error -6 reading slots fan !
[  342.920870] Error -6 reading backside fan !
[  342.923957] Error -6 reading slots fan !
[  343.924065] Error -6 reading backside fan !
[  343.927142] Error -6 reading slots fan !
[  344.923333] Error -6 reading backside fan !
[  344.926466] Error -6 reading slots fan !
[  345.923060] Error -6 reading backside fan !
[  345.926136] Error -6 reading slots fan !
[  346.918284] Error -6 reading backside fan !
[  346.921342] Error -6 reading slots fan !
[  347.921982] Error -6 reading backside fan !
[  347.925099] Error -6 reading slots fan !
[  348.921271] Error -6 reading backside fan !
[  348.924390] Error -6 reading slots fan !
[  349.916695] Error -6 reading backside fan !
[  349.919848] Error -6 reading slots fan !
[  350.916133] Error -6 reading backside fan !
[  350.919297] Error -6 reading slots fan !
[  351.915704] Error -6 reading backside fan !
[  351.918919] Error -6 reading slots fan !
[  352.919631] Error -6 reading backside fan !
[  352.922710] Error -6 reading slots fan !
[  353.915148] Error -6 reading backside fan !
[  353.918311] Error -6 reading slots fan !

**EDIT**:
possibly i found a workaround:
rmmod therm_pm72
modprobe therm_pm72

Why?!

---

### Post by rsavage on 2012-03-05
@farinet What happens when you follow the advice of the FAQ [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F) & [https://wiki.ubuntu.com/PowerPCFAQ#Power_preferences.2BAC8-suspend](https://wiki.ubuntu.com/PowerPCFAQ#Power_preferences.2BAC8-suspend) ?  A lot of your other problems are not specific to PowerPC - they are problems with lubuntu 12.04 at the moment.

---

### Post by Farinet on 2012-03-05
@rsavage: Thanks a lot for answering!

1) I'm a bit afraid to tweak around the graphic card settings (i'm happy that apparently it works fine; just for your info, Systemprofile says:

`Vga compatbile controller: AdvancedMicroDevices [AMD] nee ATI RV350 [Mobility Radeon 9600 M10] (prog-if 00 [VGA controller])`

I'm not sure what i'd have to do . . .

2) Typing in a terminal `gnome-power-preferences`  gives no result (or better: `command not found`)

I tried to tweak pbbuttonsd / Powerprefs but it seems to *NOT* have the control over the powermanagement (with the xfce-powermanagement which is installed by default with lubuntu, suspend to ram seems to be disactivated. I tried to substitute it by gnome-power-management but obviously i missed something there. Otherwise the command above should work, i presume).

Powernowd is installed and i also tweaked /etc/modules adding 2 lines (`pmu_battery` and `i2c-dev` ). And i changed `/sys/devices/temperatures/limit_adjust`  from 0 to 5 (which bettered the situation with fan a bit; but in the end, in lubuntu the fan is running nevertheless all the time while it does not in debian).

Please consider, i'm a simple user without any programming skills (save some *VERY* remote experience with Hypercard :D:D on Mac and IIGS ).

---

### Post by rsavage on 2012-03-05
You need to look at the first link I gave about loading the radeon framebuffer module.  In Ubuntus 11.04 -12.04 it is not built into the kernel, but complied as a module.  This is different to say debian.  That is why you haven't got suspend.  When you do that suspend (and probably your consoles) will just work.  There is no need to install powerprefs, gnome-powermanagement etc.  
 
radeonfb was not built in because it breaks Kernel Mode Setting.  The problem is Kernel Mode Setting doesn't work very well with radeon PowerPC.  This is going to be a problem from now on because you can't get hardware 3d graphics acceleration without it.  See bug [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/946677](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/946677) that I raised.
 
There is no ideal answer, but I think there is an argument to build radeonfb back in just so more things work out-of-the-box.  A bug has been raised although it is not worded very well - so that is probably why it has not been acted upon.

---

### Post by Farinet on 2012-03-05
Ok, i think i've a vague idea of what's the problem. Now, if i'm not stressing your patience:

In the 1st link you gave me, is said:

> and add the name of your framebuffer on a new line. You can also pass parameters in this file, for example: radeonfb mode_option=1024x768-24@60

Now, what would be *MY* framebuffer? How, can i find that out? 

TIA

---

### Post by rsavage on 2012-03-05
You have a radeon card so radeonfb is your framebuffer. You'll probably have to turn off the openfirmware framebuffer too with the [noparse]video=offb:off[/noparse] yaboot parameter.
 
Btw, I did look into the possibility of detecting the battery automatically for you [http://ubuntuforums.org/showthread.php?t=1931393](http://ubuntuforums.org/showthread.php?t=1931393) . Nobody replied. No testers = no patch I'm afraid.

---

### Post by Farinet on 2012-03-05
> **rsavage said:**
> . . .  You'll probably have to turn off the openfirmware framebuffer too with the [noparse]video=offb:off[/noparse] yaboot parameter. . .

Where should i set that? In the `/etc/yaboot.conf`? And if so, where exactly? My yaboot.conf (for the lubuntu drive) looks like this:

```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot="/dev/disk/by-id/ieee1394-0001a300000586c7:000428:0000-part2"
device=/pci@f4000000/firewire@e/node@0001a300000586c7/sbp-2/@0
partition=3
root="UUID=3c8f5c71-4086-4fdf-8d24-a1d07eb5ca38"
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
    label=Linux
    read-only
    initrd=/boot/initrd.img
    append="quiet splash"

image=/boot/vmlinux.old
    label=old
    read-only
    initrd=/boot/initrd.img.old
    append="quiet splash"

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/sda3.
image=/pci@f4000000/ata-6@d/@0:3,/boot/vmlinux
    label=Debian-Linux
    root="UUID=efab8653-bda2-4a7f-8fdd-56a78e96a6dd"
    append=" ro"
    initrd=/pci@f4000000/ata-6@d/@0:3,/boot/initrd.img
```

---

### Post by rsavage on 2012-03-05
> **Farinet said:**
> Now, if i'm not stressing your patience
 
Please read the FAQ.  I wrote it so I wouldn't have to keep repeating myself.  It is incredibly annoying that people don't.  I left the lubuntu-qa list because of this.
 
[https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F)
[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F)

---

### Post by Farinet on 2012-03-05
> **rsavage said:**
> Please read the FAQ.  I wrote it so I wouldn't have to keep repeating myself.  It is incredibly annoying that people don't.  I left the lubuntu-qa list because of this.
 
[https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F)
[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F)

I understand your feelings but for people like me, who are not really familiar with linux things often are so terribly "indented" one to another that's really difficult to understand how and what are the dependencies. 

To be frank: i'd like to have more than one option for a working and effective powerpc linux setup, so, i' m willed to give some effort to it. But it's hard to me to understand, why on the ubuntu side things seem to be so complicated - compared to Debian; should be the other way around . . . ;-)

Anyway i'll give that a try and i thank you for your patience.

---

### Post by Farinet on 2012-03-05
@rsavage

You were right. Following your instructions effectively the messed up screen went away, the consoles 1 -6 become usable and closing the lid suspends to ram.

The login screen (of Lubuntu 12.04 beta 1 ppc) now is no longer dark, but light blu, and the 4 dots under 12.04 work like a progress bar. 

So far very fine. Thanks again. Just a question regard the append line: should i substitute the `append="quiet splash"`statement there with ```
append="video=offb:off"
``` (```
video=offb:off
``` in double quotes?). And then a subsequent question re ybin:

`sudo ybin -v` will point to the yaboot.conf file on the boostrap partition where i booted from, /dev/sdb2 in my case? Or the first one in the entire setup (which would be /dev/sda2, on the internal drive where on my debian setup is)? I'm afraid to mess that up, so i'm a bit fearful ;-)

---

### Post by rsavage on 2012-03-05
I would set it up like this 
 
```

image=/boot/vmlinux
    label=Linux
    read-only
    initrd=/boot/initrd.img
    append="quiet splash video=offb:off"

```
 
If you've done an auto install then the bootstrap partition on sdb should be updated.  Whether that updates nvram too depends on a few things.  I'm not familiar with firewire. You can always pass the --nonvram option if you don't want it to automatically boot from the firewire drive.  e.g.:
 
sudo ybin -v --nonvram
 
Regarding the complicated-ness of Ubuntu - probably best to judge when 12.04 is released.  If people don't report bugs/issues on launchpad (forums/message boards don't count 'cos the important people don't read them) then they don't get fixed.  If people don't submit testcases on the tracker then the isos don't get released.  It's all in the hands of the user - i.e. PowerPC is community supported.

---

### Post by phillw on 2012-03-05
Hi, to all those doubting / frustrated with the lubuntu testers I say this.

We were all new to linux once. In the past there was no ppc or Intel-Mac options for lubuntu. They are all new, and gradually getting used to [http://iso.qa.ubuntu.com/qatracker/milestones/204/builds](http://iso.qa.ubuntu.com/qatracker/milestones/204/builds) and what / how to report bugs.

We did not get a beta 1 for Intel-Macs as we had no one with kit to test. It is our desire to have both available. But, they need some hand-holding. I can assist on QA issues, but I have not got access to a Mac (nor do any of our devs) so we are 100% reliant on community to flag up bugs.

As G3 still seems to be a problem that can be easily solved with the correct config issued, would it not be possible to give a **3G** option at boot from the ppc iso's to put this in for them? Whilst I am not adverse to hosting a 3G ppc iso for ubuntu / lubuntu etc on a server I have access to, I'm sure a method could be found?

Regards,

Phill.

---

### Post by rsavage on 2012-03-05
Phil, how many imac G3 users are there to warrant such attention?  Surely, one of the points of having the alternate CD is for the cases when the dektop iso doesn't work?  Most computers seem to default to a low graphics setup (fbdev?) if there is a problem.  Perhaps G3 users should look into why they don't?
 
The G3 imac has a rage 128 graphics card I believe.  r128 had a problem with the framebuffer not being built in (similar to farinet's with the radeon card).  The G3 imac also has a specific problem in that it returns a too restrictive frequency range.  One problem that should be solved in 12.04 is dri locking up - you only have the software rasterizer now.
 
These things are explained in the FAQ [https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics](https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics) .
 
Like I said to Farinet, I think there is a case to build back in the framebuffers on PowerPC.  The only thing an imac G3 user would then need to put into their xorg.conf would be 
 
```

Section "Monitor" 
     Identifier "Monitor0"

     HorizSync 58-62 
     VertRefresh 75-117
EndSection 

```Not that big a deal surely?
 
You would need to round up some other r128 users to see what the effect of building back in the aty128fb framebuffer has on them.  It could be the case that fixing one thing for somebody makes it harder for the rest (maybe they loose their fbdev fallback on the liveCD?).

---

### Post by phillw on 2012-03-05
I'm not going to get into a 'row' over this, but do please take the time to read the below...

> As far as G3 and G4 support: I would think it important to make sure we could get successful installs on most models in the G3 and G4 class. Otherwise, on the Macs, it leaves us with G5's. And quite frankly, there are more dead G5's out there than live ones. Power supply problems with the G5 iMacs and PowerMacs eventually "toast" the logic boards on many models.

By the way, I've been a Mac system administrator for twenty years, ran a service and support operation for some of that time, and have been trying to get a predictable Linux install on PPC Macs for a few years now. I think we can have that with Lubuntu 12.04, and these Macs can live the rest of their useful lives running Lubuntu, especially if more web sites move to HTML5 and dump Flash.
That's why I'm willing to test, test and test.


As to telling my Mum to go editing xorg.conf files? Well, I'll let you come here and tell her that she has to do it! Even the Revenue people from the government have left her with their tails between their legs :P

Regards,

Phill.

---

### Post by Farinet on 2012-03-06
> **phillw said:**
> I'm not going to get into a 'row' over this, but do please take the time to read the below...



As to telling my Mum to go editing xorg.conf files? Well, I'll let you come here and tell her that she has to do it! Even the Revenue people from the government have left her with their tails between their legs :P

Regards,

Phill.

I quote that, but i'm kind of unwell feeling some attrition here. Since ppc is comunity supported would be better to work together.

And yes, for me, e.g., any editing of a config file or similar is always a kind of an adventure (and in the past, some times, it ended in the need of a new install ;-) ). Moreover, i'm moving here in my 3rd or 4th language making things not easier . . . ;-)

Anyway, i'd like to thank you all, for your efforts and i strongly hope you'll have success with bringing out a viable Lubuntu 12.04 ppc. And i'm willed to support you in that for the little i'm able to do . . . (but, i need sometimes some instruction on how).

Good luck!

---

### Post by Farinet on 2012-03-06
Another question, i'm not sure, if Lubuntu 12.04 or generally ppc related: The 12.04 Lubuntu beta 1 ppc release came without any bluetooth support. *Comme d' habitude*, i installed blueman and the nice `blueman-browse-helper`script (used to make it work with pcmanfm) but now, i discover, that this setup, which wasn't never ever really fast, but at least functional, with 12.04 (kernel 3.2 ) is dead slow.

I installed gnome-bluetooth but it does not work with pcmanfm (as obex:// browser). What's missing there? (In the debian + lxde installation i've in parallel, it worked out of the box . . . :o )

---

### Post by rsavage on 2012-03-06
@farinet Can't help you with bluetooth I'm afraid. Sorry. (I don't have any bluetooth devices)
 
Can you give me your latest Debian kernel config file please? It is in the /boot directory. There should be a file with 'config' in the name for every version of kernel you have I think.  Thanks

---

### Post by Farinet on 2012-03-06
> **rsavage said:**
> @farinet Can't help you with bluetooth I'm afraid. Sorry. (I don't have any bluetooth devices)
 
Can you give me your latest Debian kernel config file please? It is in the /boot directory. There should be a file with 'config' in the name for every version of kernel you have I think.  Thanks

Here it comes . . .

---

### Post by rsavage on 2012-03-06
Thanks.  I'll raise a bug tonight to see if Ubuntu can mirror how debian sets up their framebuffers.  They're actually set up how I was going to suggest - a bit like how lucid was with radeon KMS on as default.  It means everything can be controlled easily from the yaboot prompt.  This should make it easier for the imac G3 people too.

---

### Post by Farinet on 2012-03-06
Another point, starting from a consideration regard Lubuntu (LXkeymaps) but then pretty much general for the ppc platform. My computer is a PB G4, 17" (2003)

LXKeymaps in its actual form seems pretty much useless to me. I you're going to **show all **it shows up the content of xorg.list - which a normal person like me, absolutely not has the skills to deal with.

Then, i'm on  a german keyboard setup (although my preferred languagesare italian and french ;-) ) and  i've a lot of problems with the third level chooser. When i do `sudo dpkg-reconfigure keyboard-configuration` (as keyboard i chose Apple_Laptop) i can set the keyboard to do the accents/deadkeys etc. correctly but the third level chooser does not work (no @, &#8364; etc). When i do `sudo dpkg-reconfigure locales` and then change to UTF8-deu i get it but i loose ALT-CTRL-F1 through F6 and similars (no killing of X by ALT-CTRL-BACKSPACE as well).

I found this interesting thread which pretty much describes my problem:
[http://lists.debian.org/debian-powerpc/2002/03/msg00221.html](http://lists.debian.org/debian-powerpc/2002/03/msg00221.html)

In this thread there was suggested the solution to use Fn with ALT, release fn and keep ALT then keep the extra signs. That worked - on a different setup (mintppc11) as long as i sticked with their original display manager (gdm). When i installed lightdm and chose is as preferred dm i lost it and it did not come back by choosing newly gdm.

Sorry in advance, if i'm exposing the problem in an unprofessionaly way.

---

### Post by rsavage on 2012-03-06
Farinet, I'd ask that sort of thing on askubuntu.com.  They're pretty good at that sort of thing.  Don't say it is PowerPC - puts people off answering.

---

### Post by phillw on 2012-03-06
> **Farinet said:**
> Another point, starting from a consideration regard Lubuntu (LXkeymaps) but then pretty much general for the ppc platform. My computer is a PB G4, 17" (2003)

LXKeymaps in its actual form seems pretty much useless to me. I you're going to **show all **it shows up the content of xorg.list - which a normal person like me, absolutely not has the skills to deal with.

Then, i'm on  a german keyboard setup (although my preferred languagesare italian and french ;-) ) and  i've a lot of problems with the third level chooser. When i do `sudo dpkg-reconfigure keyboard-configuration` (as keyboard i chose Apple_Laptop) i can set the keyboard to do the accents/deadkeys etc. correctly but the third level chooser does not work (no @, € etc). When i do `sudo dpkg-reconfigure locales` and then change to UTF8-deu i get it but i loose ALT-CTRL-F1 through F6 and similars (no killing of X by ALT-CTRL-BACKSPACE as well).

I found this interesting thread which pretty much describes my problem:
[http://lists.debian.org/debian-powerpc/2002/03/msg00221.html](http://lists.debian.org/debian-powerpc/2002/03/msg00221.html)

In this thread there was suggested the solution to use Fn with ALT, release fn and keep ALT then keep the extra signs. That worked - on a different setup (mintppc11) as long as i sticked with their original display manager (gdm). When i installed lightdm and chose is as preferred dm i lost it and it did not come back by choosing newly gdm.

Sorry in advance, if i'm exposing the problem in an unprofessionaly way.

Would you be so kind as to raise a bug for lxKeyMap with as much information as you can lay your hands on. If it is not a major re-write, Julien is pretty quick in getting something done.

Many thanks,

Phill.

---

### Post by phillw on 2012-03-06
> **Farinet said:**
> Another question, i'm not sure, if Lubuntu 12.04 or generally ppc related: The 12.04 Lubuntu beta 1 ppc release came without any bluetooth support. *Comme d' habitude*, i installed blueman and the nice `blueman-browse-helper`script (used to make it work with pcmanfm) but now, i discover, that this setup, which wasn't never ever really fast, but at least functional, with 12.04 (kernel 3.2 ) is dead slow.

I installed gnome-bluetooth but it does not work with pcmanfm (as obex:// browser). What's missing there? (In the debian + lxde installation i've in parallel, it worked out of the box . . . :o )

I'm pretty sure we deliberately removed bluetooth due to lack of demand for its use for the i686 / amd64 series. It may well be possible to add it in for ppc / IntelMac if the need is there. I can certainly ask Julien (our head of dev) if this is possible, else find out what we were using.

Thanks for all your continued efforts.

Phill.

---

### Post by rsavage on 2012-03-06
Just confirming a problem farinet and pkmgarf have previously mentioned - kernel updates are not being automatically linked properly to the /boot directory.  Does anybody know anything about this sort of thing?  Presumably there is some dodgey conf file somewhere.  I've only really used the live cd.  Does anybody know if this problem exists if installed from the alternate cd?

---

### Post by rsavage on 2012-03-06
@phil Without sounding like a broken record can you please ensure lubuntu testers read the PowerPC FAQ. It is fully up-to-date unlike a 5 year old thread which seems to be forming the basis of opinion of the G3 imac on the lubuntu-qa list.
 
I'm not being negative, I'm just trying to make everyone utilise their time and talents fully. As I have already told you it is unproductive for those asking questions and those answering not to read it. I have no problem at all in explaining things if people don't understand it (no doubt because I have described something poorly), but it really helps if people try and get up to speed on their own first. As it says on the front page of the ubuntu community wiki "*Try to spend time solving a* *problem yourself before you ask other people for help. If you follow this common courtesy, then it will not be an imposition when you ask for help*". So I don't think I am out of order in this request.
 
There are a lot of niggling issues on PowerPC at the moment and these need sorting for everyones benefit before concentrating on a 12 year old computer. I can't believe you are proposing to waste Colin Watsons time on it.
 
The bug I'll be raising soon to build back in the framebuffers will sort one problem on the imac G3. As I have already said on a previous post you won't have dri lock anymore either because you won't have 3d hardware acceleration in 12.04. Whether this result in a bootable live cd I don't know, we'll have to see. But it is a relatively easy fix after that if it doesn't. 
 
When the framebuffers are built in I'm going ask for the boot info to be reworded. I want to get rid of the video=ofonly advice. It seems to me it is the most stupidest thing ever and wastes people's time. You are more likely to want [noparse]video=offb:off[/noparse] or turn KMS off. If anyone needs video=ofonly this is your time to speak up or forever hold your peace.
 
Phil, I haven't recently checked on the progress of some ppc bugs wxl/maps_backwards raised against lubuntu packages, but last time I looked there had been no action taken on them. These are the things IMHO you guys should be concentrating on. 
 
Time is marching on fast and I am keen to get as many people as possible testing effectively. There are a lot of smart people out there, much more so than me (fairnet speaks 4 languages for example!), and so I am confident we can get the problems fixed together. We just need to prioritise and focus on the problems that can be and need to be fixed first. An imac G3 does not come top of the list.

---

### Post by rsavage on 2012-03-06
@farinet Regarding your fan. Can you test this kernel please? [https://launchpad.net/ubuntu/+source/linux/3.2.0-14.23/+build/3184594/+files/linux-image-3.2.0-14-powerpc_3.2.0-14.23_powerpc.deb](https://launchpad.net/ubuntu/+source/linux/3.2.0-14.23/+build/3184594/+files/linux-image-3.2.0-14-powerpc_3.2.0-14.23_powerpc.deb) .
 
If you download it I'm not sure if it will install by just double clicking on it. If not use the command
 
sudo dpkg -i linux-image-3.2.0-14-powerpc_3.2.0-14.23_powerpc.deb
 
Once you reboot make sure it is loaded properly with 
 
uname -a
 
You may have to fiddle with yaboot.conf if not.
 
That kernel was the last one before therm_adt746x was built in. It should be the same fan setup as you have in debian. If you still have a problem then it is not your fan, but something else. Your computer is probably getting hot and the fan is working correctly.

---

### Post by Farinet on 2012-03-06
> **phillw said:**
> Would you be so kind as to raise a bug for lxKeyMap with as much information as you can lay your hands on. If it is not a major re-write, Julien is pretty quick in getting something done.


I'd do, if i'd knew how to do that without being "guided" by apport. May be you can point me to some link where that's explained ;-)

TIA!

---

### Post by phillw on 2012-03-06
> **Farinet said:**
> I'd do, if i'd knew how to do that without being "guided" by apport. May be you can point me to some link where that's explained ;-)

TIA!

From a terminal window issue the command 

```
ubuntu-bug lxterminal
```

That should invoke apport to gather the details of your system and take you to launchpad, then please provide as much information as you can.

Thanks,

Phill.

---

### Post by Farinet on 2012-03-06
> **rsavage said:**
> @farinet Regarding your fan. Can you test this kernel please? [https://launchpad.net/ubuntu/+source/linux/3.2.0-14.23/+build/3184594/+files/linux-image-3.2.0-14-powerpc_3.2.0-14.23_powerpc.deb](https://launchpad.net/ubuntu/+source/linux/3.2.0-14.23/+build/3184594/+files/linux-image-3.2.0-14-powerpc_3.2.0-14.23_powerpc.deb) .
 
If you download it I'm not sure if it will install by just double clicking on it. If not use the command
 
sudo dpkg -i linux-image-3.2.0-14-powerpc_3.2.0-14.23_powerpc.deb
 
Once you reboot make sure it is loaded properly with 
 
uname -a
 
You may have to fiddle with yaboot.conf if not.
 
That kernel was the last one before therm_adt746x was built in. It should be the same fan setup as you have in debian. If you still have a problem then it is not your fan, but something else. Your computer is probably getting hot and the fan is working correctly.

I'll do that tomorrow evening. During the day of tomorrow i'll be out [here]("http://www.transpiree.ch/randos/2008-01-02_PlansSurBexColDesMartinets/rando.php#") (it's more or less my backyard :) ) . . .

---

### Post by Farinet on 2012-03-06
> **phillw said:**
> From a terminal window issue the command 

```
ubuntu-bug lxterminal
```That should invoke apport to gather the details of your system and take you to launchpad, then please provide as much information as you can.

Thanks,

Phill.

Thanks a lot. I'll try that way . . .

---

### Post by Farinet on 2012-03-06
> **phillw said:**
> I'm pretty sure we deliberately removed bluetooth due to lack of demand for its use for the i686 / amd64 series. It may well be possible to add it in for ppc / IntelMac if the need is there. I can certainly ask Julien (our head of dev) if this is possible, else find out what we were using.


Frankly, for all day use i think it's pretty much basic; think of transferring photos from your (smart)phone to the computer or for using wireless peripheries (keyboard/mouse/printer). 

I don't know, if it is possible to be prompted during the installation procedure whether you want or not to install certain software (?)

---

### Post by phillw on 2012-03-07
Hi,

an edited version, 

I had the pleasure of a chat with Colin Watson this evening, he is chasing bugs that are logged, cannot chase grumbles of "oh, it doesn't work, but we have a work around" and has a plan for the G3 bug.

One of things that came out of the chat is the **absolute** need to use [ [COLOR="Blue"]ISO Tracking[/COLOR] ](http://iso.qa.ubuntu.com/) to report bugs via. > fwiw the presence of you folks (plural again) working on and visibly testing powerpc is actively making it easier to advocate within Canonical for keeping the powerpc archive and images in place

For the G3 bug he asks that this is done.

> (22:18:57) cjwatson: I very much recommend that you drop the idea of having the installer fiddle with xorg.conf and instead look at improving X's autodetection; there is a great deal more mileage in the latter approach
(22:19:32) cjwatson: thanks for the other links; I'll have a look when I'm next at a proper computer
(22:21:50) cjwatson: hah, I was actually writing parted tests this afternoon to try to nail down 856826
(22:22:11) cjwatson: is that the "kernels in the wrong place" bug, or are you referring to something else?
(22:23:26) phillw: I think it is, the annoying thing for me (and I'm sure for you) is that they discuss something, complain about it but when asked to file a bug & let me know the bug number it all goes deathly silent :(
(22:24:30) phillw: for getting X to autodetect, none of us have even the faintest idea where to even start. We're not coders.
(22:25:27) cjwatson: ask the X people :)
(22:26:02) cjwatson: #ubuntu-x should be able to help
(22:27:27) phillw: okies, I'll give it a go - but I do not have a Mac, so it is going to be tortuous!
(22:28:24) cjwatson: fair enough, but it is the right approach
(22:29:12) cjwatson: there's no infrastructure for creating an xorg.conf in certain circumstances in the installer, and it's not needed for any other hardware that I've heard of these days so I'm very unkeen on creating any
(22:29:16) phillw: I will see what can be achieved. I know we were really short of time, so realistically we are now looking at 12.10 :/ That option was a 'hack' for  12.04
(22:30:04) cjwatson: it's a bug fix; if it can be explained promptly and with clarity I don't see why it shouldn't be possible for 12.04

...

(22:38:10) phillw: so, what exactly should I ask on #ubuntu-x I'm an admin and wiki guy, it took pcman about three stressful days (for him) to teach me how to get the stuff i needed for ./configure and make onto my computer!
(22:38:52) cjwatson: point them to a clear bug report identifying how X is failing to autodetect hardware
(22:40:45) phillw: thanks, I'm sure we can manage that. I know some of the guys on PPC are 'shoulders sloped' because these things have gone on for so long. I think the new guys who have come in via lubuntu have given it a shot in the arm. It is, after all, the whole reason behind lubuntu ... up to date O/S for old kit :)
(22:41:00) cjwatson: and ask if there's any more information you can supply or if they can offer guidance on fixing it (best done by somebody with the hardware though)
(22:41:44) phillw: so it it will bug-report <package> --- which package?
(22:41:50) cjwatson: xorg


He went on to suggest that someone with the actual kit would be best to liase with that team, so they can deal directly with an OP. [ **[COLOR="Blue"]rsavage[/COLOR]**](http://ubuntuforums.org/member.php?u=1220329) are you 'up' for that?

So, here is the chance to get this grumbling bug fixed, correctly, at source. 

Regards,

Phill.

the full chat is available at [ [COLOR="Blue"]A Chat[/COLOR] ](http://pastebin.com/qN8HXpX1) As for any thoughts of us wasting his time? Fear not, it was a pleasure for both of us to chat not just about ubuntu / lubuntu stuff - but chat :)

---

### Post by Farinet on 2012-03-08
> **rsavage said:**
> @farinet Regarding your fan. Can you test this kernel please? [https://launchpad.net/ubuntu/+source/linux/3.2.0-14.23/+build/3184594/+files/linux-image-3.2.0-14-powerpc_3.2.0-14.23_powerpc.deb](https://launchpad.net/ubuntu/+source/linux/3.2.0-14.23/+build/3184594/+files/linux-image-3.2.0-14-powerpc_3.2.0-14.23_powerpc.deb) .
 
If you download it I'm not sure if it will install by just double clicking on it. If not use the command
 
sudo dpkg -i linux-image-3.2.0-14-powerpc_3.2.0-14.23_powerpc.deb
 
Once you reboot make sure it is loaded properly with 
 
uname -a
 
You may have to fiddle with yaboot.conf if not.
 
That kernel was the last one before therm_adt746x was built in. It should be the same fan setup as you have in debian. If you still have a problem then it is not your fan, but something else. Your computer is probably getting hot and the fan is working correctly.

Before trying that, a question: If i install that kernel i presume the .deb package will install all needed files. Would i be able to remove that kernel after trying by `sudo aptitude remove linux-image-3.2.0-14-powerpc_3.2.0-14.23_powerpc.deb`?

Btw, i don't believe that the computer is getting hot (it's not getting hot even with the changes i made). With the help of you and others (and the change of the limit_adjust to 5 (in /sys/devices/temperatures) i have (in lunbuntu 12.04 beta 1 ppc) a) a pretty much comparable level of fan rumour (and activity) like in Debian and moreover (thanks to you!) i got back suspend to ram.

---

### Post by Farinet on 2012-03-08
> **phillw said:**
> Would you be so kind as to raise a bug for lxKeyMap with as much information as you can lay your hands on. If it is not a major re-write, Julien is pretty quick in getting something done.

Many thanks,

Phill.

I did it, and i hope i've done it right (:oops: ? ): [https://bugs.launchpad.net/ubuntu/+source/lxterminal/+bug/949461](https://bugs.launchpad.net/ubuntu/+source/lxterminal/+bug/949461)

Thanks for your help!

PS. Feel free to correct or point me to how correct, if there is something wrong. No problem :)

---

### Post by PkgMafaw on 2012-03-10
I have an iBook G4 running 10.04 that I can use. I recently ran the 12.04 live cd and so far, have only seen that the wi-fi doesn't work. It says "Firmware Missing". I'm a newby at this but I'll give it try.

---

### Post by MisterGaribaldi on 2012-03-10
Ok, I'll help. I've got a 1.4GHz G4 Mac mini to work with. Not going to install it but I will LiveCD the thing and see what happens.

"I'm going in. Cover me, Porkins."

---

### Post by MisterGaribaldi on 2012-03-10
Well, so much for that. It doesn't even fit on a standard 700MB CD. What gives?

---

### Post by PkgMafaw on 2012-03-10
It's 714MB. I had to use a DVD.

---

### Post by PkgMafaw on 2012-03-10
When trying to run the Ubiquity FreeSoftware Only test I'm not getting the "When you see the **_aubergine screen with an icon at the bottom_**, press any key to get the men". The LiveCD continues to load the rest of the way without boot options. Is there another thread for this issue or is this specific to my machine?

---

### Post by MisterGaribaldi on 2012-03-11
I'm going to cave in on this issue, it seems. This evening when I get done with my history class studies (and note-taking, etc.) and can get back ot it, I'm just going to burn the image to DVD and try it out.

As I said before, I really can't set this machine up with Ubuntu, but I'm happy to try running from the LiveCD. Is there anything in particular you folks would like those of us testing this thing to do? I mean, I know the ideal case is to install it, but what can I do from within the LiveCD environment that will be of benefit to everyone?

---

### Post by rsavage on 2012-03-13
@phillw I don't have the kit and I've got my own bugs to chase.  I've raised a bug against the framebuffers.  I suggest somebody who has a G3 imac raises any bugs with the x people.  I don't mind looking at Xorg.0.logs if somebody posts them up.  I think it is worth noting that other machines have problems too - some nvidia machines suffer from phantom outputs (explained in the FAQ).  Those people need to raise bugs too - nobody is going to do it on their behalf.  

@farinet yes you'll be able to uninstall it.  Btw, you've raised the bug against lxterminal.

@ pkgmafaw See the known issues page for a bug I raised against the free software only option.

@ mistergaribaldi Any little bit helps. It is impossible for one person to test everything in time when it comes to the release isos.  We need more people to subscribe to testing even if they can only commit to one or two testcases.

---

### Post by gwjvan on 2012-03-13
I would love to help test 12.04 ppc--  but I have nothing to work with. The live CD image won't boot for me, the alternate cd image creates an installation which halts during boot, and upgrading from 10.04 now quits midway citing "Too many errors" and leaves even 10.04 unbootable.

Is there a way to selectively remove certain boot items from the live cd image so I can figure out what is hanging?

---

### Post by svtguy88 on 2012-03-13
What exactly doesn't boot from the live CD?  What does/doesn't it do?

As for upgrading from 10.04 - has that been tested on non-PPC machine even?.  Seems like that could be a tricky upgrade to begin with.

And the alternate CD - this is likely your best bet (assuming you don't want to play with the Live CD).  If the system hangs during boot after installing from the Alternate, it means the files are all there, and it just needs some more *help* to boot.  What errors are you getting during bootup?

---

### Post by gwjvan on 2012-03-13
Thanks for the response,

Live CD Boot: Hangs on pbbuttonsd (or right after it)

Alternate install: Outputs the wireless message saying to go to the official website to get the drivers, then hangs

Upgrade from 10.04: I got this to work during the alpha, so I was excited about this (something didn't work, so I tried reinstalling later to see if it would help... but it just ended up with where I am now)


Yeah, the alternate install is probably the best bet... it hangs on or after the wireless networking attempts after installing... so I guess I'll start by disabling that somehow? (10.04 live cd works, if that would be useful for editing the installed files).

Edit: And I've made custom live CD's for my x86 (not mac x86) machines before with squashfs/iso making utilities... if it is possible to make custom PPC live cd's, I'll try that (selectively removing items, etc) if it might help identify problems with the live CD. (I briefly tried this a while back, but ran into some problem... is the process different for PPC somehow?)

---

### Post by Farinet on 2012-03-13
> **rsavage said:**
> . . .  @farinet yes you'll be able to uninstall it.  Btw, you've raised the bug against lxterminal. . . ..

Ok, thanks. How can i change that lxterminal thing? I went there but did not see how . . . (?)

TIA

---

### Post by gwjvan on 2012-03-13
> Yeah, the alternate install is probably the best bet... it hangs on or  after the wireless networking attempts after installing... so I guess  I'll start by disabling that somehow?

alternate install image today (Feb 13, 2012) doesn't install, actually.. fails during "Select and install software"

The Powerbook5,8 just doesn't seem to have any luck with 12.04

---

### Post by rsavage on 2012-03-13
The problem is the dailies are unreliable because they change all the time.  If there is a problem the text installer is rubbish at telling you what it is.  Can you do a cli install from your alternate iso?  And does it boot?  I installed xubuntu this way.
 
Has anybody else noticed the alternate cd is far far longer to install from than the live cd?

---

### Post by gwjvan on 2012-03-13
I was able to just cancel out of the "select and install software" part of the installation (after it gave an error), and skip ahead to setting up yaboot, and it now boots to the command line (hopefully with enough tools to work with?). I'll give it a shot installing a desktop environment.

---

### Post by gwjvan on 2012-03-13
Okay-

For anyone else with a Powerbook5,8 (the last 15" ppc powerbook they made):

After installing, it hangs when it tries to load the wireless. So to get 12.04 up and running, I deleted the following directories on my installation (with a 10.04 live usb):

/lib/modules/3.2.0-18-powerpc/kernel/drivers/net/wireless/b43

/lib/modules/3.2.0-18-powerpc/kernel/drivers/net/wireless/b43legacy


I now have a working Kubuntu up (runs decently), though several other issues still remain (including getting the wireless up somehow), but at least the computer is functional (something to work with).

---

### Post by rsavage on 2012-03-14
Has anybody filed a bug about the kernel symlinks being installed in the wrong place (described earlier in this thread [http://ubuntuforums.org/showpost.php?p=11704942&postcount=50](http://ubuntuforums.org/showpost.php?p=11704942&postcount=50) )?

I've just used todays alternate ubuntu cd and there is no sign of the symlinks being placed in the root directory.  Which is what I thought was the case the last time I used it.  So is this a problem only with the live cds?

Can somebody who has installed recently with the live cd check it is still happening please and raise a bug against ubiquity I guess?

---

### Post by phillw on 2012-03-15
> **rsavage said:**
> Has anybody filed a bug about the kernel symlinks being installed in the wrong place (described earlier in this thread [http://ubuntuforums.org/showpost.php?p=11704942&postcount=50](http://ubuntuforums.org/showpost.php?p=11704942&postcount=50) )?

I've just used todays alternate ubuntu cd and there is no sign of the symlinks being placed in the root directory.  Which is what I thought was the case the last time I used it.  So is this a problem only with the live cds?

Can somebody who has installed recently with the live cd check it is still happening please and raise a bug against ubiquity I guess?

Hi RSavage, I'm assuming that you and most of the others on here do not read the QA meeting logs [1]? Could I ask that you do so on this occaision? 

I've alerted the lubuntu-qa people to this pretty much once in a lifetime chance to get these gremlins closed down. I still await the email as to how it will all work. Lubuntu-qa [2] are up for it [3], I do hope everyone else on this thread will also give the devs what they need .... Feedback whilst they do the sprint. They **need** you to test!

I will, of course, update this thread as soon as I have the full details, in the meantime... get your pencils sharpened and learn the the gentle art of correctly reporting bugs ;)

A couple of hints that lubuntu use are at [4]. They are not in any way exhaustive as they are still being worked on, but have been drafted pretty much up on the fly as we got new testers on in order to answer FAQ's quickly for a them. I hope you good people find them of help.

Regards,

Phill.
[1] [https://wiki.ubuntu.com/QATeam/Meetings/QA/20120314](https://wiki.ubuntu.com/QATeam/Meetings/QA/20120314)
[2] [https://launchpad.net/~lubuntu-qa](https://launchpad.net/~lubuntu-qa)
[3] [https://lists.launchpad.net/lubuntu-qa/msg00447.html](https://lists.launchpad.net/lubuntu-qa/msg00447.html)
[4] [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing)

---

### Post by MisterGaribaldi on 2012-03-17
Alright, so I'm finally booting the thing via CD (actually, DVD+RW) on my 1.43GHz Mac mini. Will post further as the situation warrants.

EDIT: Ok, so it's been booted successfully. It found my Apple Magic Mouse and, after I found the pairing code for it (and tried inputting it a couple times) it finally paired. Tracking was waaaaaaaaaaaay too fast, so I had to move the acceleration and sensitivity sliders around and then back down to get a reasonable setting.

No out-of-box support for the older Apple Airport Extreme B/G card, which to me at this point is something of a surprise. Fortunately, I was able to scrounge up another router, link it to my Gateway as a WiFi/eNet bridge, and I was able to get on the Internet pretty much immediately.

Opened up the various LibreOffice apps, and they all work as expected.

Other than that, no complaints for a quick driving test on my older Mac.

---

### Post by rsavage on 2012-03-18
Any problems with gedit or nautilus [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/945097](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/945097) ?

---

### Post by MisterGaribaldi on 2012-03-18
Hmm... What is the default file manager for Gnome 3? If it's Nautilus, then it worked. If not, then I don't know. As for Gedit, I didn't try that, so I can't answer.

One problem, though, is that after booting with the LiveCD and then rebooting into Mac OS X, something happened, causing Leopard to have to do a significant scan-and-repair of my HDD. I got to sit and stare at a blank blue screen for quite a while. Fortunately, it was able to fix whatever it needed to and all is back and running properly.

This leaves me with a bit of a concern, of course. LiveCDs shouldn't be touching your present filesystem, so what did *this* one do?

---

### Post by rsavage on 2012-03-19
Have you raised your concerns in a bug?

The live cd uses any existing swap partitions ( [http://askubuntu.com/questions/8626/prevent-livecd-using-existing-swap-partition](http://askubuntu.com/questions/8626/prevent-livecd-using-existing-swap-partition) ) so that could be a reason why it is accessing your hard drive.  Is it identifying a partition as swap when it shouldn't be?

---

### Post by rsavage on 2012-03-20
For those running the Live session testcase I've added a bit about USB persistence to [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F) 

All the bugs I've raised are here [https://wiki.ubuntu.com/PowerPCKnownIssues#A12.04_Precise_Pangolin](https://wiki.ubuntu.com/PowerPCKnownIssues#A12.04_Precise_Pangolin) .  Please confirm them and link them to any testcases you run.

---

### Post by aq3e on 2012-03-31
I was shocked to find an updated version for PPC,About to test 12.04 on PB 17 1.67ghz.

---

### Post by aq3e on 2012-03-31
No dice booting 12.04 LTS

Disk starts to boot yet hangs on the load screen with the version number. Allowed about 15 minutes to see if anything would happen but nothing did. No idea what to do specs are as followed.


Powerbook G4 17

1.67ghz
2.00 GB DDR2
120 GB HD


any ideas?

---

### Post by nyoli on 2012-04-07
i'd like to become tester.
already installed 12.04 on my G5 PowerPC and it works, except sound.
its a bit slow on gnome with or without 2D effects, but fluxbox runs quite nice. (enough for me)

anyways, whats next? how can i participate and improve PPC ubuntu?

---

### Post by ikkeT on 2012-04-09
Hi,

thanks for the effor to make old macs usable. I have used 12.04 on my powerbook g4 17"  with radeon for couple of months now. It sucks, to be honest. Luckily I found this thread couple of days ago. Things that bother me:

1. Keymap is messed up, no altgr and special characters are not in the right place
    [https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/796864](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/796864)
2. tty's don't work, like described in this thread. I need to try removing KMS
3. gnome-terminal lost ability to move cursor backwards some days ago:
    [https://bugzilla.gnome.org/show_bug.cgi?id=673697](https://bugzilla.gnome.org/show_bug.cgi?id=673697)
4. suspend doesn't work, I need to try the tricks in this thread, removing KMS.
5. No 3d. OsX looks good with all the effects on the mac, but ubuntu is not able
    to use 3d. I assume it's again the same radeon fb that would fix it. Need to try.

I need  to find time to try to fix this, thanks for the people in the thread and behind the ppc faq&all!

---

### Post by rsavage on 2012-04-09
If you want lots of 3d effects then I recommend 10.04 ubuntu. Basic shadows and stuff you can get in xubuntu 12.04 too. For speed try lubuntu.
 
You don't have KMS on in 12.04 so you don't have to turn it off. Loading the radeonfb module won't solve your hardware accelerated 3d. Without KMS you have to install an old version of mesa [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/946677](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/946677) . However, you'll probably find you need the extra features provided by KMS for the 3d effects in Ubuntu 12.04. Unfortunately, I can only get KMS to work by forcing PCI mode which is not fast enough.
 
Loading radeonfb will fix your suspend and ttys though (you can add yourself to the bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/949288](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/949288) ). 
 
Your problem with gnome-terminal is, I think, the same as gedit and nautilus ([https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/961512](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/961512) ).

---

### Post by gwjvan on 2012-04-10
> **aq3e said:**
> No dice booting 12.04 LTS

Disk starts to boot yet hangs on the load screen with the version number. Allowed about 15 minutes to see if anything would happen but nothing did. No idea what to do specs are as followed.


Powerbook G4 17

1.67ghz
2.00 GB DDR2
120 GB HD


any ideas?


I have the 15" 1.67 ghz with the same issue. The live cd doesn't work. I was able to install using the alternate install CD image. The installed 12.04 will hang at the same point as the live cd, but I "fixed" it by doing this:

> For anyone else with a Powerbook5,8 (the last 15" ppc powerbook they made):

After installing, it hangs when it tries to load the wireless. So to get  12.04 up and running, I deleted the following directories on my  installation (with a 10.04 live usb):

/lib/modules/3.2.0-18-powerpc/kernel/drivers/net/wireless/b43

/lib/modules/3.2.0-18-powerpc/kernel/drivers/net/wireless/b43legacy


I now have a working Kubuntu up (runs decently), though several other  issues still remain (including getting the wireless up somehow), but at  least the computer is functional (something to work with).However, this seems to prevent the wireless from working again, even after trying to install the wireless again

Note: the directory 3.2.0-18-powerpc might be different now. I'm not on that computer at the moment, but on this Dell, the current appears to be 3.2.0-22

---

### Post by rsavage on 2012-04-11
gwjvan, I don't have a problem with my airport extreme card.  Are you sure that is the cause?  Have you tried the simple things like removing the splash screen?

What about if you download the b43 firmware?

Have you raised a bug to get somebody to look at it?

---

### Post by gwjvan on 2012-04-11
> **rsavage said:**
> gwjvan, I don't have a problem with my airport extreme card.  Are you sure that is the cause?  Have you tried the simple things like removing the splash screen?

What about if you download the b43 firmware?

Have you raised a bug to get somebody to look at it?

I guess I can't be absolutely sure that is the problem (maybe removing it caused something else to subsequently not load, thus preventing it from hanging). However, removing those directories somehow fixed the boot issue.

Before this "fix", I was fairly convinced the wireless wasn't the problem, because I had gotten the same drivers to work on other versions of Ubuntu. However, it would hang after it said it was loading the wireless drivers.. so I removed them, and it booted.

I tried running the steps in the PPC faq to reinstall the wireless, but it didn't work. Now that I've upgraded to the latest beta, I'll try again.

I haven't raised a bug report. (I actually never have... I guess this would be a good place to start)

Edit: Upgrading to the most recent beta broke the system (it didn't fully upgrade, I think, so some files were missing). I'll have to do a fresh install and try the above again, filing a bug report for what happens.

---

### Post by thilly on 2012-04-13
Good morning,

i tried to install on IBM Power7 LPAR.
[http://www-03.ibm.com/systems/power/hardware/720/index.html](http://www-03.ibm.com/systems/power/hardware/720/index.html)
I used the LIVECD or the alternate CD. But everytime it stops after yaboot!
I tried nearls all install-xxx values with video=ofonly
What can i do to debug?

Thanks Menne


Welcome to yaboot version 1.3.16
Enter "help" to get some basic usage information
boot: install-free-powerpc64
Please wait, loading kernel...
   Elf64 kernel loaded...
Loading ramdisk...
ramdisk loaded at 04d80000, size: 6402 Kbytes
OF stdout device is: /vdevice/vty@30000000
Preparing to boot Linux version 3.2.0-23-powerpc64-smp (buildd@ross) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 23:12:42 UTC 2012 (Ubuntu 3.2.0-23.36-powerpc64-smp 3.2.14)
Detected machine type: 0000000000000101
Max number of cores passed to firmware: 256 (NR_CPUS = 1024)
Calling ibm,client-architecture-support... done
command line: ro ramdisk_size=8192 file=/cdrom/preseed/ubuntu.seed quiet apt-setup/restricted=false apt-setup/multiverse=false --
memory layout at init:
  memory_limit : 0000000000000000 (16 MB aligned)
  alloc_bottom : 00000000053c1000
  alloc_top    : 0000000010000000
  alloc_top_hi : 0000000010000000
  rmo_top      : 0000000010000000
  ram_top      : 0000000010000000
instantiating rtas at 0x000000000ee90000... done
Querying for OPAL presence... not there.
boot cpu hw idx 0
starting cpu hw idx 4... done
copying OF device tree...
Building dt strings...
Building dt structure...
Device tree strings 0x00000000054c2000 -> 0x00000000054c35ce
Device tree struct  0x00000000054c4000 -> 0x00000000054da000
Calling quiesce...
returning from prom_init

---

### Post by linuxopjemac on 2012-04-13
Maybe this will help:
[http://mac.linux.be/files/debian_on_lpar.pdf](http://mac.linux.be/files/debian_on_lpar.pdf)

---

### Post by thilly on 2012-04-13
Hi it really seems to be a 12.04 problem to be!

I loaded the 10 Ubuntu and now i can start the installation.
But now it can not find any network device and scsi device!
I use the vscsi and virtual Network of IBMs PowerVM.

Any Idea?
I try to load all modules i find, but still the same...

/lib/modules/2.6.35-22-powerpc64-smp/kernel/drivers/misc # lsmod
Module                  Size  Used by
scsi_transport_spi     40577  0 
scsi_transport_sas     51511  0 
scsi_transport_fc      74653  0 
scsi_tgt               19751  1 scsi_transport_fc
linear                  7635  0 
virtio_net             21385  0 
xfs                  1073507  0 
exportfs                6588  1 xfs
reiserfs              371856  0 
jfs                   260833  0 
btrfs                 861357  0 
zlib_deflate           26840  1 btrfs
crc32c                  4833  1 
libcrc32c               2091  1 btrfs
ntfs                  136821  0 
vfat                   17100  0 
fat                    83364  1 vfat
sd_mod                 54998  0 
scsi_debug            103511  0 
crc_t10dif              1795  2 sd_mod,scsi_debug
virtio_blk             10526  0 
virtio                  8322  2 virtio_net,virtio_blk
virtio_ring             8676  2 virtio_net,virtio_blk
multipath              11807  0 
md_mod                155131  2 linear,multipath
dm_zero                 2551  0 
isofs                  48818  1 
sg                     48479  0 
sr_mod                 24347  1 
pata_pdc2027x          11500  1 
/lib/modules/2.6.35-22-powerpc64-smp/kernel/drivers/misc # cat /etc/*release
maverick
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu maverick (development branch)"
/lib/modules/2.6.35-22-powerpc64-smp/kernel/drivers/misc #

---

### Post by rivman05 on 2012-04-13
Hello folks. I am new to Ubuntu. I work in a Apple only School District. Im starting to surplus all G4 equipment. Im installing the 12.04 on a hoard of about 25 machines. I have an issue with getting the modems to work on all G4 models, and the sound on the PowerBook G4'. They all very in cpu speed from 800 mhz to 1.67 ghz. Ram from 512 to 2 gigs, and hard drives of 20-180 gigs. I have a very nice PowerBook tester on my desk that I want for a machine at home but need the sound and modem to work. Let me know if there is anything I can do to help. If I can get this to work, I have 120 machines I need to wipe and install something not tied to our district, thus Ubuntu has been the choice of an open source distro.


This wifi fix worked for me so far:

lspci | grep -i broadcom - hit enter
wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2) {enter}
tar xjf b43-fwcutter-011.tar.bz2 [enter]
make [enter]

wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) [enter]
tar xjf broadcom-wl-4.150.10.5.tar.bz2
b43-fwcutter-011/b43-fwcutter -w "/lib/firmware" broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

---

### Post by ikkeT on 2012-04-15
> **rsavage said:**
> If you want lots of 3d effects then I recommend 10.04 ubuntu. Basic shadows and stuff you can get in xubuntu 12.04 too. For speed try lubuntu.


Thanks, I don't really need, unity was just the default. I installed lubuntu packages following your advice, thanks. Looks good, but is somewhat broken.

[LIST]
[*] Keyboard is US only (I need Finnish), likely due the lxkeymap failure
   [https://bugs.launchpad.net/ubuntu/+source/lxkeymap/+bug/945603](https://bugs.launchpad.net/ubuntu/+source/lxkeymap/+bug/945603)
[*] It always  starts with something failing, likely something by default in the
   launcher bar right after the file browser icon, since it can't show right icon there
  (something like "application launcher bar", when you right click on broken icon).
[*] Network manager shows no wifi bars, even though wifi is connected and works
[*] Sound logo neither shows sound level, it's also just greyed out
[*] Something else also messy in the bar, some garbled area on the right corner between nm-applet and battery status. I don't know what should be there, need to  try on x86 sometimes to see what's missing.
[/LIST]

Of course, only important one of those is the keyboard which is wrong.

> **rsavage said:**
> Loading radeonfb will fix your suspend and ttys though (you can add yourself to the bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/949288](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/949288) ). 


 This I tried the way described in PPC FAQ, but it didn't work. I tried setting ```
 radeon.modeset=0 video=radeonfb:1440x900-24@60
``` while in yaboot, but it didn't apply. I haven't yet put effort into figuring out why. The missing suspend is really a blocker.

---

### Post by rsavage on 2012-04-15
Suspend: What you are trying only works when the framebuffers are built in (which they are currently not in 12.04).  You need to follow the advice of [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F) 
 
The crossed out icon on the panel is chromium (no chromium on PowerPC).  Just change it to firefox.
 
Any other problems I suggest you report to the lubuntu-qa mailing list.  See earlier posts in this thread about lubuntu-qa.

---

### Post by rsavage on 2012-04-16
Can people start putting some heat (i.e. click the affects me link) on this bug [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/958839](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/958839) please?  It is quite an important one!
 
If somebody has installed from the alternate CD can they also add the contents of their /etc/kernel-img.conf file to the bug report please?
 
Thanks!

---

### Post by rsavage on 2012-04-20
Thanks to the one person who clicked the link. The support from the community is honestly overwhelming....
 
Release candidate ISOs have started to be produced. Release date is next Thursday. I'm probably wasting my breath here, but can people please start submitting testcases to the QA tracker?
 
An ISO will only be released if all testcases for that ISO are completed. So that means every testcase for every PowerPC ISO has to be run on the last testing day. It is impossible for one person to do this. I cannot stress this enough.
 
Simply put, if you want PowerPC CDs to be released then it is up to you to test them. Do not rely on others to do this for you.
 
(p.s.  Please do not ask how to do testing. This thread and the PowerPCDownloads page is filled with the necessary links.  Here is another one that covers the basics [https://wiki.ubuntu.com/U+1/DeployedProjects/rc-iso-testing-main](https://wiki.ubuntu.com/U+1/DeployedProjects/rc-iso-testing-main) .  If you still have a question then the Ubuntu +1 forum [http://ubuntuforums.org/forumdisplay.php?f=412](http://ubuntuforums.org/forumdisplay.php?f=412) is the place for it.)

---

### Post by xeno74 on 2012-04-21
Lubuntu 12.04 works very well on my Mac Mini G4, 1.42GHz, 1GB RAM, and 32MB VRAM.

It's very important to use the following sound preferences:

**/etc/modules**:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

#snd_powermac
apm_emu
snd_aoa_i2sbus
snd_aoa_fabric_layout
snd_aoa_codec_tas
snd_aoa_codec_onyx

```

---

### Post by ppcfriendo on 2012-04-21
April 21st Ubuntu 12.04 LTS will not boot from ppc G5 machine. I tried (return) to boot live. The Second time powerpc64 which got me to (calling quiesce returning from prom_init) still happily using 10.10 though no longer supported. I will keep trying as daily is posted.

---

### Post by ppcfriendo on 2012-04-21
I was not able to boot from Lubuntu 12.04 using a ppc G5. First try live, second no splash. Neither booted. On no splash vmlinux no device.

---

### Post by ikkeT on 2012-04-22
> **rsavage said:**
> Suspend: What you are trying only works when the framebuffers are built in (which they are currently not in 12.04).  You need to follow the advice of [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F) 

Thanks, I recompiled myself a 3.2.0-23 kernel with the radeonfb in kernel, and set the kernel params for yaboot. I confirm, it fixes the suspend and switch to vt. Thanks a lot for the tips!

Now I  just wish ubuntu would actually do something for the bug.... I updated it with my experiences.

---

### Post by ppcfriendo on 2012-04-23
April 23rd Ubuntu 12.04 LTS would not boot from a ppc G5.

---

### Post by ppcfriendo on 2012-04-23
April 23rd Lubuntu 12.04 would also not boot. When /live video=ofonly I received live:/2,/vm linux: unable to open file, Invalid device

---

### Post by rsavage on 2012-04-24
Can people start submitting tests to the tracker [http://iso.qa.ubuntu.com/qatracker/milestones/214/builds](http://iso.qa.ubuntu.com/qatracker/milestones/214/builds) so that the ISO images get released?  Thanks

---

### Post by rsavage on 2012-04-26
PowerPC ISOs released [http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)

---

### Post by rsavage on 2012-04-26
@ikkeT Thanks for the comment on the bug report. Should be fixed when you update.
 
@everyone Please report (on launchpad.net) any bugs you find so that they can get fixed. If you find a bug that somebody else has reported then write a comment on the bug report. It makes it more likely that the bug will get fixed. ikkeT did and the bug got fixed.

---

### Post by rsavage on 2012-04-27
> **gwjvan said:**
> I haven't raised a bug report. (I actually never have... I guess this would be a good place to start)

 
I think somebody beat you to it [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950295](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950295) . Seems it's not just a PowerPC issue.

---

### Post by spaceballl on 2012-05-03
> **mw1coe said:**
> Works Fine here except for wifi.

But had those issues in earlier versions too.

Rob..

Is there a wifi usb adaptor that works?

---

### Post by gwjvan on 2012-05-07
> **rsavage said:**
> I think somebody beat you to it [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950295](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950295) . Seems it's not just a PowerPC issue.

And it seems there is a patch pending


Also, I was able to get 12.04 working (with wireless, after being unsuccessful, last time) by moving these two directories to my home directory (using a 10.04 live usb):

/lib/modules/3.2.0-18-powerpc/kernel/drivers/net/wireless/b43
/lib/modules/3.2.0-18-powerpc/kernel/drivers/net/wireless/b43legacy

Then 12.04 boots. Once in 12.04, move those directories back and do the:
sudo apt-get install firmware-b43-installer

(I also installed b43-fwcutter by mistake before that, but I don't think that matters?)

Now 12.04 runs with wireless


Sound is now working:

I read this in another post (so it might be common knowledge on this board by now?) but to get the sound working on the PowerBook5,8 (and probably others?) open up the following file in gedit and comment out everything referring to "snd-aoa" (in my case, every line):
/etc/modprobe.d/blacklist.local.conf


I have to say, just a few weeks ago it seems the sound didn't work, the key backlighting didn't work, the wireless didn't work, the control buttons didn't work- but it has all come together. The speed of the interface has dropped (it is odd: the mac interface is silky smooth and responsive, but the programs are slower; whereas ubuntu's interface is laggy, but the programs are fast- and actually, I wonder if this is some new bug or issue with xorg or something, because I remember 12.04 alpha running faster). But it is nice to be able to run up-to-date software on the powerbook

---

### Post by markdpowell on 2012-05-08
I am using a Mac Mini 1.25Ghz, 1GB RAM, 40GB HDD, using ethernet cable.

Installed lubuntu 12.04 off live CD.
Followed xeno74's post about the sound (thanks!).

Other than that, everything works flawlessly. Let me know if there is anything you'd like me to test.

I have a question. Does anyone know what drivers are needed to be able to output from the DVI-D Mac Mini to HDMI TV? I used to have this working in Mac OS X (plug and play). It's a ATI Radeon 9200 graphics card.

---

### Post by EuroCity on 2012-05-09
> **gwjvan said:**
> [...] to get the sound working on the PowerBook5,8 (and probably others?) open up the following file in gedit and comment out everything referring to "snd-aoa" (in my case, every line):
/etc/modprobe.d/blacklist.local.conf [...]

Exactly! And I also had to add the ex-blacklisted modules to */etc/modules*, in order to have working sound on an iBook G4 14" 1.42 GHz; while the "powermac" sound modules aren't needed, anymore (they can be commented out).

So, this should be fixed in Ubuntu PPC 12.04.1: *snd-powermac* seems to be obsolete, indeed, at least on this machine.

While previously there was only a dummy sound output device, now there are headphones, as output and input: and they work also for the built-in speaker; no explicit speaker and microphone entries in the sound preferences, however - something to investigate further, perhaps...

Another problem is the fan speed, way too high from the beginning (the fans activate even if it isn't necessary, where they wouldn't activate on Mac OS X Leopard); and also the boot splash, which is still the "elementary" one (Ubuntu with dots on a black screen), not the "full" one (Ubuntu with logo, coloured background and dots) which you have on x86.

Well, let's say that it's a 3/4 good experience, sofar - not bad at all, but certainly it could be even better... ;-) :-)

P.S.: The iBook G4 14" 1.42 GHz is identified as a *PowerBook6,7* model, in Leopard's System Profiler.

As for the boot screen, obviously it would be a good thing if also PPC users could have something like this out of the box:

[img]http://www.ubuntu-it.org/sites/default/files/features//lubuntu/screenshots/slide_startfast.png[/img]

(in this screenshot for Lubuntu; but of course, in general, for every "-buntu" flavour: a complete graphical boot splash).

---

### Post by EuroCity on 2012-05-10
About adjusting fan limits:

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_adjust_my_fan_limits.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_adjust_my_fan_limits.3F)

[https://wiki.ubuntu.com/PowerPCFAQ#How_can_I_use_powernowd_for_CPU_frequency_scaling.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_can_I_use_powernowd_for_CPU_frequency_scaling.3F)

But also with frequency scaling, the fan seems to run a little too often (at least compared to Mac OS X).

Not sure if this hint (see above) is really safe:

[http://ubuntuforums.org/showthread.php?t=1358034](http://ubuntuforums.org/showthread.php?t=1358034)

...?

---

### Post by gwjvan on 2012-05-10
Yeah, I'll have to try those fan settings. It runs too often, and at a loudness that mac os just simply never reaches. I'm also worried it could be bad for the cpu to tamper with it...

Also:

The sound/wifi issue I was having seems to be fixed in 12.10 Quantal.... not recommending anyone install it yet (I'm not), but the pre-alpha live image actually boots. (I'm typing from a quantal live session right now [daily-live/20120510/], on a 3g connection).

And sorry to the PPC faq maintainer... the sound issue is already documented, there (delete the blacklist file)

---

### Post by gwjvan on 2012-05-10
Okay wow thank you PPC FAQ...

Linux video=ofonly


Speeds up the 12.04 interface to how I remember the alpha being... wow it runs more slickly now. compositing, transparency, very nice. Xubuntu with effects seems like a nice fit for this laptop, now

---

### Post by rsavage on 2012-05-10
> **gwjvan said:**
> Okay wow thank you PPC FAQ...
 
Linux video=ofonly
 
 
Speeds up the 12.04 interface to how I remember the alpha being... wow it runs more slickly now. compositing, transparency, very nice. Xubuntu with effects seems like a nice fit for this laptop, now
 
That enables KMS. Just a warning - it can be quite crash-tastic!! 
 
You'll get a better spash screen (like EuroCity wants). If the colours are badly messed up on shutdown use the yaboot parameter:
 
video=1024x768-24
 
If you can get KMS to work fully then could you try unity-3d? It would be good to see if the problems the nouveau people report are just nouveau specific or if there is an endian problem somewhere.
 
Btw, I think Xubuntu is the best fit for most computers, although I plan to play around with a highly customized kubuntu.
 
EDIT: just to expand on the above, I used [noparse]video=offb:off video=radeonfb:off video=1024x768-24[/noparse]

---

### Post by gwjvan on 2012-05-10
Okay, I'm on Unity 3d (!)

It runs smoothly at times- better than I expected it to.

The launcher and panel are an odd light blue/turquoise. Something is going on.

EDIT: And actually, there are no icons in the launcher (like the nouveau people report, except in my case just bright turquoise blocks) except for the bottom half of the top ubuntu button.

Also:  The color problem also happened before when I ran Kubuntu 11.10 with effects (turning the effects off fixed the problem). And I just ran a Qt Creator project, a 2d drawing demo that runs two versions of the same animation, a "Native" and "OpenGL" version side-by-side. The "Native" animation had green colors, the OpenGL animation had pink colors (they are supposed to both be green). Something is up with the graphics card / driver (?).


Another edit: The icons are actually there, just when the dash isn't displayed, it maxes out to a bright turquoise, and when the dash is open, the turquoise fades to show that there are icons there.

---

### Post by EuroCity on 2012-05-11
I can confirm the false colours problem for the "full" boot splash screen (and also a freeze problem at login: but I'll have to try the settings above first); and I, too, tried Kubuntu on my iBook G4, but had those blueish colours which make it almost unusable.

The optional Cairo/GLX Dock also has problems, with effects turned on...

---

### Post by EuroCity on 2012-05-11
Another, completely different problem: the Wi-Fi indicator icon in the upper menu/status bar doesn't show the network strength; and, thus, none of the four (IIRC) concentric sectors in the AirPort-like icon ever lighten up: even if the Wi-Fi indeed works flawlessly (and also seems to be quite stable)...

---

### Post by rsavage on 2012-05-11
gwjvan, thanks for testing unity-3d.  Seems there are some issues there for both nouveau and radeon.  I can't get into it so there is no way I can do testing/bug reporting on it.
 
If you have some time you can try adjusting the settings in your xorg.conf file.  Have a look at the EXA manual [http://manpages.ubuntu.com/manpages/precise/en/man4/exa.4.html](http://manpages.ubuntu.com/manpages/precise/en/man4/exa.4.html) and radeon manual [http://manpages.ubuntu.com/manpages/precise/en/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/precise/en/man4/radeon.4.html) .
 
I've downgraded my mesa packages so I can still use UMS.  With a tweaked xorg.conf file I've eliminated all the graphics glitches I was having.

---

### Post by EuroCity on 2012-05-11
> **rsavage said:**
> That enables KMS. Just a warning - it can be quite crash-tastic!! 
 
You'll get a better spash screen (like EuroCity wants). If the colours are badly messed up on shutdown use the yaboot parameter:
 
video=1024x768-24
 
If you can get KMS to work fully then could you try unity-3d? It would be good to see if the problems the nouveau people report are just nouveau specific or if there is an endian problem somewhere.
 
Btw, I think Xubuntu is the best fit for most computers, although I plan to play around with a highly customized kubuntu.
 
EDIT: just to expand on the above, I used [noparse]video=offb:off video=radeonfb:off video=1024x768-24[/noparse]

On my iBook G4 (with a 32 MB Mobility Radeon 9550 graphics card), *video=ofonly* gives the graphical boot screen (but with messed up colours: blueish background, with neon-like contour on "Ubuntu"), but the machine freezes shortly after login; while *[noparse]video=offb:off video=radeonfb:off video=1024x768-24[/noparse]* freezes the machine at the login screen.

So, quite unstable, sofar...

---

### Post by EuroCity on 2012-05-11
Well, one could say that the bootsplash screen colours are almost "psychedelic" (on the blueish front), as someone said in another post: and with a strange halo around "Ubuntu" and the dots.

It would be great if all this could be fixed, eventually...

P.S.: The Edubuntu boot screen was displaying as default (and this looked much better, even if the colours didn't seem to be quite right; but no neon-like halos, for example); so, in order to get the Ubuntu bootsplash, I did this command:

**sudo update-alternatives --config default.plymouth**

... and then:

**sudo update-initramfs -u**

... of course choosing the Ubuntu boot screen at the first step.

---

### Post by rsavage on 2012-05-13
> **EuroCity said:**
> About adjusting fan limits:

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_adjust_my_fan_limits.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_adjust_my_fan_limits.3F)

[https://wiki.ubuntu.com/PowerPCFAQ#How_can_I_use_powernowd_for_CPU_frequency_scaling.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_can_I_use_powernowd_for_CPU_frequency_scaling.3F)

But also with frequency scaling, the fan seems to run a little too often (at least compared to Mac OS X).

Not sure if this hint (see above) is really safe:

[http://ubuntuforums.org/showthread.php?t=1358034](http://ubuntuforums.org/showthread.php?t=1358034)

...?

I have to say I don't have this problem now with my iBook.  With my usage at the moment the temperature seems to stick around 40 degrees C.  It only rises above this if I do compiling or play videos (which I never do 'cos I have a TV).  

This low temperature could be because when I rebuilt my iBook (it's made out of 3 computers) I didn't put the modem back in.  This was a deliberate act to reduce temperature.  I also maybe screwed the heat sink tighter than it was originally.

I'm not running frequency scaling, although in the past (when it was just 1 ibook) I did find this helped.  I think one of the best things you can do is to remove the apt-xapian-index package.

Since the noise of the fan seems to be a problem for a lot of people I've looked into it a bit today.  I've added some more to the FAQ about it.  The safest thing is to probably reduce the fan starting speed.  You can do this via the yaboot prompt.  For example:

therm_adt746x.fan_speed=38

The default fan_speed is 64 so a value below this will make it start quieter and it will only get louder if the temperatue keeps climbing.  If you want the fan to kick in at a higher temperature then use the limit_adjust parameter.  For example:

therm_adt746x.limit_adjust=5

will start the fan at 55 degrees C (= 50 + 5).

I have xubuntu installed at the moment and to get a temperature applet on the panel I installed the sensors-applet and  xfce4-xfapplet-plugin from the natty repositories.  I don't know if there is a better way, but it seems to work okay.  It's probably a good idea if you are going to mess with the default fan settings.

---

### Post by Farinet on 2012-05-19
> **Farinet said:**
> In addition to what i wrote in my previous post: The *vmlinux-3.2.0-17-powerpc *which was installed by the upgrade had the wrong rights:

Owner: root (correct)
Group: root
Rights
Owner: read & write (correct)
Group: nothing (wrong: should be **read only**)
Others: nothing (wrong: should be **read only**) After correcting that (as root, obviously) boot into 3.2.0-17 works.

But, since this error happened the second time i presume there is something wrong with the install/update script for the kernel update.

Today i upgraded Powerbook G4 17" from lubuntu 11.10 to lubuntu 12.04 and i noticed, that the previously described errors of the placement of the symbolic links (the went to "/" (root) not into /boot (where they are expected to be) as well as the wrong rights for the most recent linux image persist.

Especially for an LTS version that kind of error are not so nice.

Other things, like the ugly fan speed problem are still to try out. I' m under the impression, in lubuntu the fan is working a lot more than in mintppc, even in this new version  . . . (?)

Moreover, i see that the most recent kernel is a -smp flavour. I read somewhere that the maintainers of the powerpc distributions decided to drop the non -smp flavour. Now, just out of curiousity i'd like to understand what are the differences between non -smp and -smp kernel (it's theoretical, since the new -smp kernel seems to work).

And: Is that drop an ubuntu specific decision or is it also done by debian?

TIA.

---

### Post by Farinet on 2012-05-19
> **rsavage said:**
> . . . .Since the noise of the fan seems to be a problem for a lot of people I've looked into it a bit today.  I've added some more to the FAQ about it.  The safest thing is to probably reduce the fan starting speed.  You can do this via the yaboot prompt.  For example:

therm_adt746x.fan_speed=38

The default fan_speed is 64 so a value below this will make it start quieter and it will only get louder if the temperatue keeps climbing.  If you want the fan to kick in at a higher temperature then use the limit_adjust parameter.  For example:

therm_adt746x.limit_adjust=5

will start the fan at 55 degrees C (= 50 + 5)

.. . ..

Can this values be set in some config file somewhere? I'm pretty sure i did this once (at least the "adjust=5" thing) some time ago in a mintppc setup, but i don't remember where exactly.

Btw, when i follow the instructions to install powernowd (useful imho) i get an older version than the newest one available among the debian packages (the last one there is 1.00-2). Moreover, at least in the lubuntu installation there was missing the package laptop-detect on which apparantely powernowd relies (?) . . .

Thanks in advance!

---

### Post by Asenath83 on 2012-05-25
Hello,
 
I have two old Macs I want to try Ubuntu on and wonder whether you still need any testers? I have worked with Ububtu on both PCs and netbooks quite a bit before.
 
Machine 1 is a PowerBook G4 1.33 12" (Al) [http://www.everymac.com/systems/apple/powerbook_g4/specs/powerbook_g4_1.33_12.html](http://www.everymac.com/systems/apple/powerbook_g4/specs/powerbook_g4_1.33_12.html) (RAM maxed out, otherwise unaltered)
 
Machine 2 is a Power Macintosh G4 800 (QS 2002), GeForce4 MX (64MB)
[http://www.everymac.com/systems/apple/powermac_g4/specs/powermac_g4_800_qs.html](http://www.everymac.com/systems/apple/powermac_g4/specs/powermac_g4_800_qs.html)
Once again RAM maxed out and I installed a [[COLOR=#bf1e2e]Pluscom WP-RT2561T[/COLOR]]("http://www.usbnow.co.uk/p742/Wireless_PCI_LAN_Adapter_802.11g/b/product_info.html") wireless and [[COLOR=#bf1e2e]Belkin F5U220VEA1[/COLOR]]("http://www.belkin.com/uk/support/article/?lid=enu&pid=F5U220vea1&aid=9405&scid=255") USB PCI card, as well as a new hard drive.
 
Regards,
 
Asenath

---

### Post by rsavage on 2012-05-25
Asenath83, thanks for the offer.  Testing has now finished for 12.04.  The ISOs have been released, but it has now started again for 12.10!!!  

For 12.04 make sure you report any bugs you find through normal use.  As I understand it, it is much easier to get things fixed in the first 3 months of a release.  Also, please update the Known Issues pages or PowerPC FAQ wiki pages with any workarounds you find necessary.

---

### Post by Asenath83 on 2012-05-25
Great, I'll keep an eye out for 12.10 testing then and will wrestle with 12.04 in the meantime, I see there may be quite a bit to do to get it up and running properly.
Updated my previous post with more detailed specs for the PowerMac for future reference.

---

### Post by rsavage on 2012-05-25
That is good to hear.  If somebody else wants to arrange 12.10 testing then I will help out, but at present I have no plans to test 12.10 ubuntu and kubuntu on my own again.  It is too much.
 
The only bugs I wish we'd got fixed for 12.04 is sound and usb installing.  Both of these had patches lined up. 
 
FYI, if people want a xubuntu ISO producing for 12.10 then they should get in contact with the xubuntu mailing list now.

---

### Post by gwjvan on 2012-05-25
Xubuntu worked well with the least tweaking, but as I'm able to get KMS to work, I'm basically just discovering Compiz (which runs very well if tweaked just right). So I basically have a franken-ubuntu which looks and performs almost on-par with mac os x.

I'm seeing the future regular Ubuntu as something which will eventually be an upgrade to mac os x (custom interface tweaking + wayland + a lighter weight unity, hopefully... which I'm assuming they're shooting for if they want to run ubuntu on phones...).

How hard is it to install two ubuntu's on one mac with yaboot/etc? I'd like to keep 12.04, but also test 12.10. I have a 5 gig partition I can use. Is that enough for testing or do the alphas/betas end up using larger amount of resources for whatever reason?

---

### Post by nm_geo on 2012-05-26
First step in the Apple.  A friend of mine had a PowerBook G4 1Ghz 1GB Ram that was gathering dust as he has newer, better Macs for his personal use.  Well, I asked him if he had any that I could borrow for Linux testing purposes (long story made short) he gave me the G4 and everything I have tested so far on the Mac OS is working.  I did have to drop my security on my wireless router a little to get the wireless working..  Went from WPA2 to WPA Personal and lowered the encryption. 

Since, I already am a lubuntu-qa tester I decided to try the live USB with the precise-powerpc.iso.   I use dd regularly to make bootable USBs so I decide to give that a whirl first. Found some good information here and in the FAQs and got the live USB working with lubuntu precise. I am sure I will have a numbers of questions for the users here when it comes to making hardware installs. I am not sure how to do a complete HDD install without having to reload the Mac OS and then another full drive install with encryption on the drive? See I told you I would have questions.  Maybe Lars Nooden can fill me in on those? He is the primary tester on lubuntu Mac isos.        

Anyway, I am subscribed to test too many Lubuntu AMD64 & i386 PC tests, but i will try to help Lars with the testing I can on this G4.
Greg nm_geo

---

### Post by rsavage on 2012-05-26
Thanks Greg
 
> **nm_geo said:**
> I am not sure how to do a complete HDD install without having to reload the Mac OS and then another full drive install with encryption on the drive? See I told you I would have questions. 
 
This is something that can definitly be improved in the PowerPC documentation. As far as I know to resize hfs you need hfsutils installed. To resize hfs+ you need hfsprogs package installed. If the hfsplus type is not detected you may have to modprobe hfsplus .
 
EDIT: see [https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)
 
I don't know anything about hfs file types. I need somebody who knows about this stuff to update the FAQ. 
 
@gwjvan
> 
How hard is it to install two ubuntu's on one mac with yaboot/etc? I'd like to keep 12.04, but also test 12.10. I have a 5 gig partition I can use. Is that enough for testing or do the alphas/betas end up using larger amount of resources for whatever reason? 
I think 5 gig is enough. You may have to 
 
sudo apt-get clean
sudo apt-get autoclean
 
once in a while to delete old packages.
 
Is easy to install two systems. The installer will sort it out for you. Though you will have to adjust your yaboot.conf to make your first sytem the default again.

---

### Post by gwjvan on 2012-05-26
Okay, looks like I'm set to do some testing when the time comes, then

I tried installing yesterday's Quantal image, but the live image no longer boots, and the alternate hung at 50% on installing yaboot. I was able to force it to boot that installation with root=/dev/sda#, but several input devices didn't work. (They're not even at alpha yet? So what do I expect)

Guess it is a good idea to wait until the alpha

---

### Post by svtguy88 on 2012-05-27
I'll likely be able to help out a bit with 12.10 testing.  I should have more free time than I did for 12.04, as I just got my undergrad and have nothing but time on my hands till I find a (real) job.

---

### Post by nm_geo on 2012-05-27
> **pkmgarf said:**
> I'll likely be able to help out a bit with 12.10 testing.  I should have more free time than I did for 12.04, as I just got my undergrad and have nothing but time on my hands till I find a (real) job.

Testers are certainly going to be needed.  It appears on the

 [http://iso.qa.ubuntu.com/qatracker/milestones/219/builds](http://iso.qa.ubuntu.com/qatracker/milestones/219/builds)
 
That we are going to have less flavors with the powerpc.iso going forward. I will spend my time on the Lubuntu testing primarily amd64 and i386 isos.  By the way, the daily testing can be done and recorded right now if you choose to get ahead of the Alpha 1 testing.

---

### Post by Farinet on 2012-05-29
Just a question: I've a problem with bluetooth support in lubuntu 12.04 powerpc (on a Mac G4, PB 17"). Is it correct to post it here? Or should i open a thread?

TIA

---

### Post by nm_geo on 2012-05-29
> **Farinet said:**
> Just a question: I've a problem with bluetooth support in lubuntu 12.04 powerpc (on a Mac G4, PB 17"). Is it correct to post it here? Or should i open a thread?

TIA

Hi Farinet I can not help with the bluetooth but I see you signed up for lubuntu-qa and Lars needs help with the Mac testing ... ):P   So keep diggin..

---

### Post by Farinet on 2012-05-30
Well, lubuntu-qa seems to be destinated for beta testing i.e. in this moment the 12.10 version. So i posted to lubuntu-users but, may be they have a too small base of ppc people (?)

---

### Post by IsshoNi on 2012-06-01
I haven't red the entire thread yet, but I'd like to point out that the **Airport Extreme **wifi card doesn't work. The exhaust fan in the rear of my 14inch iBook G4 is constantly on high.

---

### Post by Farinet on 2012-06-01
For the fan noise follow the advices of rsavage given some posts earlier. In your '/etc/modules' file you should have this line:

```
therm_adt746x fan_speed=66 limit_adjust=6
```

Moreover, install powernowd which nicely scales the processor speed (i got it from the debian packages - because it's the newest version; if i recall correctly there is powernowd also in the ubuntu packages, but not sure here).

For wifi, i presume you have a broadcom chip. For that you need the firmware to make it work (moreover, check if the device name like like wlan0 or wlan1 or so given in the settings of network-manager (or wicd, whatever you use) is correct).

---

### Post by rsavage on 2012-06-01
> **Farinet said:**
> For the fan noise follow the advices of rsavage given some posts earlier. In your '/etc/modules' file you should have this line:
 
```
therm_adt746x fan_speed=66 limit_adjust=6
```
 
Those are your own values not mine and I dont recommend anyone to use them.  Certainly not without an understanding of what they do.

---

### Post by Farinet on 2012-06-01
That's correct! ;) 

In any case, the use of powernowd is supported by you too, isn't it?

---

### Post by nm_geo on 2012-06-02
Notice I modified the Title ...

Downloaded Lubuntu quantal 12.10 powerpc.iso .. dated 20120601

dd a USB..

Ran the Live/USB.. wireless worked without a hitch..

Installed to full drive on my gifted G4 ..

Works pretty well here.. Yes more testers are needed

---

### Post by logoutPPC on 2012-06-05
Hello,

this is not exactly Mac problem, but still PowerPC related. I tried kubuntu 12.04 PowerPC on my IntelliStation Power 185 with G5 processor (single core 970MP, to be precise) and it hangs immediately after "Querying for OPAL presence..."

I've found this notice - [http://www.mail-archive.com/linuxppc-dev@lists.ozlabs.org/msg53840.html](http://www.mail-archive.com/linuxppc-dev@lists.ozlabs.org/msg53840.html) - and do not know whether it applies to me, this is not a blade and it's newer than any Apple's PowerPC hardware, but it seems to be the very same problem. The same problem is with every current debian-based PPC distro I've tried.
On my PowerMac G5 kubuntu boots OK.

Can anyone help, please?

---

### Post by EuroCity on 2012-06-05
Here is the problem I talked about in another discussion:

[IMG]https://dl.dropbox.com/u/166043/UbuntuPPCBoot.jpg[/IMG]

[IMG]https://dl.dropbox.com/u/166043/UbuntuPPCShutdown.jpg[/IMG]

... i.e., completely distorted colours (on an iBook G4), respectively at boot and at shutdown; this happens with the boot option:

**video=ofonly radeon.agpmode=-1**

... which is necessary in order to get the "full" graphical bootsplash (instead of the simplified one) without freezing.

Seems to be a PPC-only problem (and it also happens in Kubuntu, where the desktop colours are messed up after logging in)...

P.S.: The Ubuntu bootsplash should rather look [like this](https://wiki.ubuntu.com/Brand?action=AttachFile&do=get&target=boot.png), of course; and adding also **video=1024x768-24** or **video=1024x768@24** at boot doesn't seem to help, either: the same messed up colours, both at boot and at shutdown.

---

### Post by EuroCity on 2012-06-05
> **logoutPPC said:**
> 
On my PowerMac G5 kubuntu boots OK.

Are the colours OK in your Kubuntu desktop environment? On my iBook G4, everything looks mostly violet, or something similar.

---

### Post by EuroCity on 2012-06-08
Well, today I logged into a KDE Plasma session, and miraculously the colours were OK (no violet-like tints): maybe because of the new boot parameters (see above), who knows...

---

### Post by EuroCity on 2012-06-08
BTW, booting with the parameters:

```
Linux radeon.modeset=1 video=offb:off video=radeonfb:off video=1024x768-16 radeon.agpmode=-1
```

... as detailed here:

[https://wiki.ubuntu.com/PowerPCFAQ#Radeon_cards](https://wiki.ubuntu.com/PowerPCFAQ#Radeon_cards)

... didn't change anything regarding the bootsplash behaviour: still the same false colours, both at boot and at shutdown.

Well, I guess that I'll go back to the default, simplified boot screen (the one that you get with no special boot options)...

---

### Post by rsavage on 2012-06-12
Just a quick note to say I've found a new way to speed up firefox scrolling with my radeon card.  If you are using UMS then set the FBTexPercent to a lowish value.  My current setup is lubuntu (only 'cos I had an ISO to hand) with compiz on top.  I compiled the latest stable compiz [noparse](0.8.8) [/noparse] so I can get the emerald window manager working.  It's a pretty fast setup and looks and feels infinitely better than the standard Lubuntu setup (my aplogies to the LXDE lovers out there). 

Ideally I would of liked kwin instead of compiz, but currently it is defeating me - it crashes when I unminimise a window.  If you know how to fix it - did it work in 11.10? - then I would love to hear from you!

---

### Post by EuroCity on 2012-06-13
> **rsavage said:**
> Since the noise of the fan seems to be a problem for a lot of people I've looked into it a bit today.  I've added some more to the FAQ about it.  The safest thing is to probably reduce the fan starting speed.  You can do this via the yaboot prompt.  For example:

therm_adt746x.fan_speed=38

The default fan_speed is 64 so a value below this will make it start quieter and it will only get louder if the temperatue keeps climbing.  If you want the fan to kick in at a higher temperature then use the limit_adjust parameter.  For example:

therm_adt746x.limit_adjust=5

will start the fan at 55 degrees C (= 50 + 5).

OK, so I finally had the time to try this (sorry, I had almost forgotten about it...); and, thus, I did a:

```
gksudo gedit /etc/yaboot.conf
```

... and modified the two *append* sections with:

```
append="quiet splash therm_adt746x.fan_speed=38 therm_adt746x.limit_adjust=5"
```

... thus adding the fan adjustment entries; finally, I did a:

```
sudo ybin -v
```

... and rebooted.

Well, now the iBook G4's fan indeed seems to activate later and is also quieter, which is especially noticeable when running from the mains (before, in that condition, it was quite loud from the beginning).

---

### Post by EuroCity on 2012-06-13
... Or is it better to add those entries into */etc/modules*, as said here:

> **Farinet said:**
> For the fan noise follow the advices of rsavage given some posts earlier. In your '/etc/modules' file you should have this line:

```
therm_adt746x fan_speed=66 limit_adjust=6
```

(but with "excessive" parameters, in this case)...?

So, that would rather be (as before, with *yaboot.conf*), in */etc/modules*:

```
therm_adt746x fan_speed=38 limit_adjust=5
```

... which should be safe (hopefully...).

---

### Post by gwjvan on 2012-06-23
> **rsavage said:**
> 
therm_adt746x.fan_speed=38

The default fan_speed is 64 so a value below this will make it start quieter and it will only get louder if the temperatue keeps climbing.  If you want the fan to kick in at a higher temperature then use the limit_adjust parameter.  For example:

therm_adt746x.limit_adjust=5

will start the fan at 55 degrees C (= 50 + 5).


Okay, thank you once again! (and EuroCity __for the ybin reminder)

The fan is now very quiet most of the time and kicks on [less intensely than before] occasionally. It behaves similar to how it does in OS X, now. This will be more of a pleasure to use

---

### Post by bytehacker on 2012-07-24
I have an eMac Power PC G4. Have just removed the native OS X completely and have installed Ubuntu 12.04 on the internal Hard Drive. I can volunteer to be on the tester list. 

The e-Mac has 1 gig of ram and a 1.2 Ghz processor. 80 Gig Hard Drive. The computer is roughly 5-6 years old. Also have an Intel Mac running OS X Lion, and have Ubuntu 12.04 installed as a virtual machine under virtual Box. 

My Linux experience:  What can I say!  I'm basically a newbie with 15 years experience. Have been playing around the edges of various distros and I'm still wanting to learn more about the command line interface and the way Linux does business 'under the hood'. 

If I can help the community effort,  please get in touch.

[email]rm2892@gmail.com[/email]

Ron Mitchell

---

### Post by bytehacker on 2012-07-24
Should add that Ubuntu 12.04 installed without problems on the eMac. I've yet to get the internal wifi to work, but I have a USB Dlink wireless interface which worked out of the box with both the live CD, and the subsequent installation on my hard drive.

Was originally hoping to install Ubuntu on an external hard drive (160 Gig) that I have here, but with that done, it failed to boot. Have been reading recently about issues related to that, and one of these days I'm going to find something that works on an external drive. 

Installation on the internal hard drive went very well. Am now adding the Ubuntu Studio package. Also play around the edges with a midi keyboard here, and a camcorder, and various cameras and other audio-visual stuff. Ubuntu Studio looks interesting for that.

Ron

---

### Post by rsavage on 2012-07-25
bytehacker, please get in touch with the lubuntu people [https://wiki.ubuntu.com/Lubuntu/Testing/PPC&Mac64](https://wiki.ubuntu.com/Lubuntu/Testing/PPC&Mac64) and volunteer your services.
 
You can of course test the other 12.10 ISOs - Ubuntu and Kubuntu - if you prefer.  Just sign up to the tracker and test.  The lubuntu-qa mailing list is still a good read for testing since it makes you aware of dates and deadlines for testing.
 
For 12.04 I was the only one testing Ubuntu and Kubuntu ISOs and I made sure Xubuntu ran okay from the mini ISO.  **I am not doing any testing for 12.10.**  If people want them released they have to do the testing themselves.
 
BTW, the PowerPCFAQ describes how to get an external hard drive booting.  
 
*This thread should be now closed since testing for 12.04 is finished, **but you should still report any bugs you find**.*

---

### Post by bytehacker on 2012-07-25
Good. I will do that.

 Appreciate your getting back to me.

bytehacker

---

### Post by nm_geo on 2012-07-25
> **rsavage said:**
> bytehacker, please get in touch with the lubuntu people [https://wiki.ubuntu.com/Lubuntu/Testing/PPC&Mac64](https://wiki.ubuntu.com/Lubuntu/Testing/PPC&Mac64) and volunteer your services.
 
You can of course test the other 12.10 ISOs - Ubuntu and Kubuntu - if you prefer.  Just sign up to the tracker and test.  The lubuntu-qa mailing list is still a good read for testing since it makes you aware of dates and deadlines for testing.
 
For 12.04 I was the only one testing Ubuntu and Kubuntu ISOs and I made sure Xubuntu ran okay from the mini ISO.  **I am not doing any testing for 12.10.**  If people want them released they have to do the testing themselves.
 
BTW, the PowerPCFAQ describes how to get an external hard drive booting.  
 
*This thread should be now closed since testing for 12.04 is finished, **but you should still report any bugs you find**.*

We missed you rsavage but the Alpha 3 Lubuntu powerpc alternate and desktops worked like good magic.  Thanks for sending Ron to the lubuntu group we need his boxes and his desire to test.  

Greg nm_geo                    OUT

---

### Post by rsavage on 2012-07-26
nm_geo, you guys are doing great work over at lubuntu-qa which all the derivatives benefit from.  I've also pointed the FAQ [https://wiki.ubuntu.com/PowerPCFAQ#How_can_I_help_PowerPC_Ubuntu.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_can_I_help_PowerPC_Ubuntu.3F) in your direction so hopefully you will get some more volunteers.
 
Since I have no intention of installing 12.10 (I'm planning on sticking with 12.04 until my computer gives in.....and if I'm still using it at the end of the LTS 5 years then my life sucks!), others are going to have to take over maintaining the PowerPC documentation.  
 
I find it massively frustrating that so few people want to contribute.  For me the joy of using Linux is the community feel of it - getting involved and feeling part of something.  Knowing that your own involvement has improved Linux, albeit in probably a very very small way.  But, those little improvements add up.  If you don't get involved and help out in some way then I don't understand what you get out of Linux - probably just frustration when something doesn't work.

---

### Post by ajacker on 2012-07-28
Has anyone got the DVI connection to work? I'm still having to use VGA and that is quite rubbish. Mac mini running Ubuntu 12.04 on the big screen would be ideal. May have to drop back to OS X 10.5 if this can't be done. :-(

---

### Post by new to ubutnu on 2012-07-28
hey i would be willing to try stuff on my powerpc imac g3 i cant really use it for much in all honesty and i am trying to learn more about the coding and infrastructure of ubuntu

also to rsavage i am the one who had a problem with the r128 framebuffer issue last december so if you remember it that is the computer i am using

---

### Post by Farinet on 2012-09-11
I was away a long time (to gain a living doing outdoor ;) - so no computer nothing . . .) but now, there is an "avalanche" of updates. And i notice, i'm still having the same problem when it comes to kernel updates like i published here: [http://ubuntuforums.org/showthread.php?t=1918246&page=6](http://ubuntuforums.org/showthread.php?t=1918246&page=6)

Is this only *MY* problem or are other encountering the same.

TIA for any help!

---

### Post by Epodx64 on 2012-09-11
hmm... I just sold my PowerMac G5 literally 2 days ago I would have been more then happy to help I had successfully gotten a few distro's to install on it just kind of lost interest in it after awhile though I had a PowerPC 1.8 Ghz DP w/ 3GiB's of Ram Nvidia Geforce 5200 FX card I really just didn't have time to configure it anymore I had Debian on it with Tiger got uhm 90$ bucks for it lol I do have an older B&W G3 but it's in pieces I might put it back together I was gonna use the case for an mAtx board and never quite finished but i still have the whole mac it's literally just in pieces

---

### Post by 2blue on 2012-09-12
> **Epodx64 said:**
> ...I do have an older B&W G3 but it's in pieces I might put it back together I was gonna use the case for an mAtx board and never quite finished but i still have the whole mac it's literally just in pieces

Oh, do asseble it and get get testing! It is fun bringing life back into these old things, and in my case the G4 iBook has proved ususefull too. You will get to know ubuntu (lubuntu flavor really I suppose) better, and it will help smooth out ppc linux issues. Beta 2 is just around the corner, and you are needed ;)

---

### Post by Epodx64 on 2012-09-14
> **2blue said:**
> Oh, do asseble it and get get testing! It is fun bringing life back into these old things, and in my case the G4 iBook has proved ususefull too. You will get to know ubuntu (lubuntu flavor really I suppose) better, and it will help smooth out ppc linux issues. Beta 2 is just around the corner, and you are needed ;)

I'm working on getting the B&W Back together I'm not really sure what I did to this thing when I was taking it a part lol, but I'm working on getting a DP G4 or a G4 iBook as well (trading an older but newer then the G4 x86 system for it either a Emachines T3895 or an HP Pavilion a700n might trade both if the deals right don't really need these ) I had quite a bit of success with my G5 when I had it last install I had on it was Debian 6.0 but I had Ubuntu 12.04 on it as well plus I tried a few other distros on it the biggest problem I had with it was the Nvidia Card always & I mean always detected some phantom T.V. out

---

### Post by Epodx64 on 2012-09-15
Alright, looks like I got a PowerMac G4 coming tomorrow so ill contribute on here once I get it specs are > [COLOR=#000000][FONT=Times New Roman]Apple Power Macintosh G4 867 (Quicksilver) Specs[/FONT][/COLOR]


[COLOR=#000000][FONT=Times New Roman]The Apple Power Macintosh G4/867 (Quicksilver) features [/FONT][/COLOR]

[COLOR=#000000][FONT=Times New Roman]867 MHz PowerPC 7450 (G4) processor with the [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]AltiVec "Velocity Engine" vector processing unit, [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]256k "on chip" level 2 cache, and [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]2 MB of level 3 backside cache.[/FONT][/COLOR]

[COLOR=#000000][FONT=Times New Roman]It shipped configured with 128 MB of RAM, [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]60 GB Ultra ATA/66 hard drive, [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]2X DVD-R/CD-RW "SuperDrive", [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]4X AGP NVIDIA GeForce 2 MX graphics card with 32 MB of SDRAM. [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]AirPort (802.11b) [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Apple keyboard[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman] 
not quite the old G5 I had but will work for this purpose my G5 specs where Power PC 1.8 Ghz Dual-Processors 3GiB DDR Ram 80Gb+160Gb total 240Gb Sata HDD's AGPx8 Nvidia GeForce 5200 FX Card 

I think I have a Gig of Apple PC-100 & DDR ram laying round to so I'll upgrade that 128mb soon as I get it.
[/FONT][/COLOR]

---

### Post by 2blue on 2012-09-17
Sounds great Epodx64, all is set up to do a good job with ppc testing! I am sitting here with the daily iso making a new attempt at installing on the G4 and rereading rsavage`s advice.

---

### Post by Epodx64 on 2012-09-30
Well I am offical among the PPC testers I acquired An Apple PowerPC G4 "AGP/Gigabyte Ethernet" 400Mhz Processor 2GiB's of SDRam 80Gb harddrive and I've already wiped Mac OS X 10.0.4 off it and have after quite a bit of trial and error not to mention having to manually configure the xorg.conf fun stuff however I now official have the Apple PowerPC G4 fully dedicated to Lubuntu 12.04 PPC now. This was single handled one of the most complex installations I've done yaboot was refusing to load the agy128fb module so I had to manually set it up with a custom Xorg.conf and blacklist for some reason the agyfb module (I have the AGPx2 ATI Rage 128 Pro onboard) I honestly took me roughly 5 hours to get it from boot to running stable after I got it installed I had all kinds of Monitor detection problems booting into 640x400 pretty much unexceptionable even though its only a 15 Sony LCD w/ a max resolution of 1024x768 but I managed to get that solved with a custom yaboot script but honestly it was a refreshing challenge and quite enjoyed struggling through the PPC land. And now to top it all off I got a 20" iMAC G5 2.1Ghz 2.5Gb of DDR2 533 Ram PCIE Nvidia card 250Gb SATA HDD so I'm looking forward to installing Ubuntu 12.04 PPC64 bit on that one in the next couple of days. and the last thing I've resurrected my Apple PowerPC G3 350Mhz 1GiB SDRam 40Gb HDD but that projects going towards Debian w/ iceWM just to maximize the last of it's potential. well thats it for now glad to be part of the PPC tester's now.

---

### Post by canhoto on 2012-09-30
> **rsavage said:**
> 
 
I find it massively frustrating that so few people want to contribute.

In my case I would love to, but I would need to spend regular time doing it for being useful, and I don't have taht time for the moment.

Your contributions have been very, very useful, especially in an area like PPC where there are not so many contributors, and that many people tink is a dead area. It isn't, and it should be more supported.

---

### Post by lilith on 2012-10-07
Would love to but I am not an expert... Some feedback managed successfully to instal ubuntu 12.04 on my old Power Macintosh G4 (AGP Graphics) and no problem with the ADC cinema display 17" (acrylic), HP printer, WD ethernet hard drive, wireless mouse and keyboard. It is faster than OS 10.4.11 I believe! Still have to check the scanner and DVD burner... All the best!

---

### Post by este.el.paz on 2012-10-10
@rsavage:

Just reporting over on this thread, you may have seen my post on MintPPC and here in the sound threads . . . but I'm posting here as part of the testing process.  Running Xubuntu using LXDE 12.0.4 in dual boot next to OSX on an iMac 800, recompiled nv driver, str8bs' xorg.conf file, things were going well . . . system seemed robust and impervious to breaking after updates as other distros had done, I was happy to finally have a linux based system running the iMac and looking forward to many happy days.  Friday, ran "sudo aptitude update/upgrade" and on restart things were fine no problems; Sunday tried to boot into Xu/Lu and had a series of problems (details in the sound or "suspend freezes imac" thread . . . leading to kernel panics, tried 5 times to restart . . . then on reboot into OSX had another panic attack.  I'm not sure how to do "rescue" or what that would do to revive the system, if I could get some pointers I'm willing to try to fix whatever might be the problem . . . .  But, fairly technical installation process, and then in about a month . . . somethings again busted, this being the 5th or 6th installation of something linux on the iMac . . . an element of frustration and negative thinking has entered . . . .  Is this one save-able or time to move on??  Don't know . . . nobody has replied to either of my accident report posts . . . with any comments or insights into fixing it . . . .  : - ))))

<end of testing report, phase one tests 12.0.4--iMac 800 PPC>

e.e.p.

---

### Post by PowerPup on 2013-01-25
Been running Lubuntu 12.04.1 LTS on a [Mac Mini G4]("http://www.everymac.com/systems/apple/mac_mini/specs/mac_mini_g4_1.33.html") since June 2012 and have only had to reboot for the occasional updating routine. ;) This machine is [my library's]("http://castlerocklibrary.yi.org") ILS server and Lubuntu has made the whole process a lot easier than using two computers when getting everything setup.

I now plan on putting 12.04 on my [PowerBook G4]("http://www.everymac.com/systems/apple/powerbook_g4/specs/powerbook_g4_667.html") so I have something to play with at home. :popcorn:

Thanks so much Lubuntu team for an awesome job!

---

### Post by phillw on 2013-01-25
> **PowerPup said:**
> Been running Lubuntu 12.04.1 LTS on a [Mac Mini G4]("http://www.everymac.com/systems/apple/mac_mini/specs/mac_mini_g4_1.33.html") since June 2012 and have only had to reboot for the occasional updating routine. ;) This machine is [my library's]("http://castlerocklibrary.yi.org") ILS server and Lubuntu has made the whole process a lot easier than using two computers when getting everything setup.

I now plan on putting 12.04 on my [PowerBook G4]("http://www.everymac.com/systems/apple/powerbook_g4/specs/powerbook_g4_667.html") so I have something to play with at home. :popcorn:

Thanks so much Lubuntu team for an awesome job!

If you'd like to help out (And we are REALLY short of testers) please head over to [https://wiki.ubuntu.com/Lubuntu/Testing#Getting_Involved](https://wiki.ubuntu.com/Lubuntu/Testing#Getting_Involved) and get signed up to the testing team. 

Regards,

Phill.

---

### Post by PowerPup on 2013-01-25
Quite busy with college lately, but will do ASAP. ;)

---

### Post by este.el.paz on 2013-01-29
@rsavage, et al:

For those still interested in hearing how the iMac 800 saga is doing . . . I just the other day was able to spend a few minutes in the Xu/Lu system, but after a few minutes the screen just froze--nothing moved--so had to shut down.  Problem seems to be traced to firewire port and possibly USB port as causing KPs, still no time to take it apart and see if a good cleaning would solve the problem or if I need to install new motherboard or it looks like the HD has some "sector" problems . . . I'd like to keep it going, but it might be difficult to get parts???

Anyway, following up on testing reports on Lubuntu 12.04 for PPC, this AM I tried to run the LiveDVD on my iBook G4 933MHz.  The disc was originally burned on 3/12/12 that I used to test it out on my iMac as per request from ojordan on mintppc forum . . . posted previously.  In trying out numerous Debian systems on the iBook before just about everything has been able to boot and run, whereas on the iMac almost nothing did.  Today, Lu 1204 booted OK, I just used "live" and after a few minutes got to the "crash report" error window that seems to be a bug; launched FireFox, ran a Google search for "gmail" but then in the resulting list, the cursor would change to the pointing finger over the selected link, but clicking on it . . . did nothing.  At that point, the fan was running noisily and clicking on anything would do nothing as well--tried to close FF, couldn't; tried to get the restart button to show up . . . and then at one point I got what I had in a Kubuntu Live DVD, where the cursor started acting erratically rather than smoothly moving around . . . .  I hit the Kill button to exit the system . . . .  So, I read through the PPC wiki for 12.04 and saw something about "radeon has problems in the DVD that are solved on installation" . . . and the various radeon KMS suggestions--but not too much else.  Still running the straight Wheezy system in a 6GB partition and that works "OK" since the latest xulrunner upgrade--don't have the time to go for the Lu install and then mess with it right now--as I said traditionally the iBook has handled the LiveDVD's right outa the box--don't know if it needs an xorg.conf file to get it to work--or, if a newer burn of Lu 12.04 would work better?  At some point if I can't revive the iMac I would try to run Lu on the iBook, but I'd like it to be a simple install rather than lots of boot parameters, etc.  Any thoughts on how to get it going appreciated . . . .

That's my test on iBook G4 2 USB port 656??MB RAM 933MHz

e.e.p.

---

### Post by rsavage on 2013-01-29
> **este.el.paz said:**
> The disc was originally burned on 3/12/12 
 
Presumably that is an American date, and what you meant to write was 12/3/12 (or the 12th of March).  In other words a massively out of date CD and not the one that was released.

---

### Post by este.el.paz on 2013-01-29
> **rsavage said:**
> Presumably that is an American date, and what you meant to write was 12/3/12 (or the 12th of March).  In other words a massively out of date CD and not the one that was released.

mr. savage:

Thanks for the fast reply . . . yes, a 'Merican date . . . but a day later or younger, the 13th of March, was around the time that you, or your screen alter ego, posted a request on mintppc for testers--which I did, and eventually it was made to work on the iMac shortly before it became fatally ill . . . .

But, I don't understand your sentence ending with " . . . and not the one that was released"???? "the one"??  "that was released."???? released when might be where that was going??  . . . this is a 12.0.4 LiveDVD that I used this AM, I'm under the impression that 12.04 is LTS . . . unfortunately I don't have time to read through all the threads, but it seems like you are suggesting that there would be an updated 12.0.4 LTS .iso available for PPC????? and perhaps the issues would be ironed out of it???

e.e.p.

---

### Post by este.el.paz on 2013-01-30
@rsavage:

Alrighty, thanks to your comments I did make my way to a Live DVD Lu 12.0.4 today and burned it--and booted it in the iBook, and I'm typing this in the Live system--so, that's more in line with most systems booting up on the iBook . . . .  Only point worth noting is the CLI boot window showed "Built on 20120423" . . . which seems like it would only be a month after my "out of date" Beta version . . . ????   Is that "massively out of date" or what?  : - ))))  Anyway, it's working, perhaps at some point I'll try to install it if the Wheezy system starts getting unstable or fills the 6 GB so much that I can't update it anymore . . . .

e.e.p.

---

### Post by superchar42 on 2013-01-31
I can commit my dusty iBook G4 to it.

---

### Post by este.el.paz on 2013-02-12
Testing LiveDVD Lu 12.04 on iBook G4 993MHz & 612??MB RAM dual USB:

Ran a second experiment on the LiveDVD burned recently as mentioned in previous post, still no time to burn doing an installation.  And overall it does boot up with just the word "live" . . . no other boot parameters needed.  But, checking for "Suspend" which is important for me . . . there was no tab for "suspend"???  Clicking on Hibernate brought--"not authorized" whatever that might mean.  And, no biggie, wireless is not working--"b43--not found, device not ready" . . . probably needs a driver?????? IMHO.

But, perhaps a little more concerning is while looking at a photo filled web email page in FF, the DVD drive started chattering, fan started blowing pretty hard, and then lost control of the mouse while trying to click on stuff . . . had to shut it down.  This same loss of mouse control happened when I was testing a Ku LiveDVD quite awhile back.  Would that mean that the iBook would require an xorg.conf file to be installed to keep everything under control??  Possibly . . . it could be that the installer would straighten all of that out during the install, but, as I mentioned I don't have the time to take that gamble and then need to spend time to fix it . . . so I'm on the fence on the iBook--maybe later in the year there will be more time for fiddling around. 

 If I ever get my iMac back running the Xu/Lu system already I would be happy to try to hook it up as an official "tester" . . . as last we stood, it probably needs a change of xorg.conf file, but it won't run long enough to do . . . so it's out of the running for PPC test champion award . . . .

e.e.p.

---

### Post by talonts on 2013-02-18
I'd love to test on 2 PowerMac G4s, but I can't even get the PPC ISOs to boot.  I have tried Lubuntu 12.10 and Ubuntu 12.04, both for PPC, and both stop at the same point - the screen goes white with black text ending in "returning from prom_init", then goes pure black and sits there.  I've let it stay there for hours on end, and nothing.  This is a 733MHz with 1Gig RAM, running whatever card it came with in the Digital Audio version (it is unmarked), through the VGA port.  

I've tried:
live
live video=ofonly (or whatever it recommends)
test-powerpc
live-powerpc
live-config-powerpc
and a few others (these are all from memory, don't have it fired up right now).  They all have the same symptoms.

I'll dig through the forums to see if I can find a solution.

---

### Post by este.el.paz on 2013-02-19
> **talonts said:**
> I'd love to test on 2 PowerMac G4s, but I can't even get the PPC ISOs to boot.  I have tried Lubuntu 12.10 and Ubuntu 12.04, both for PPC, and both stop at the same point - the screen goes white with black text ending in "returning from prom_init", then goes pure black and sits there.  I've let it stay there for hours on end, and nothing.  This is a 733MHz with 1Gig RAM, running whatever card it came with in the Digital Audio version (it is unmarked), through the VGA port.  

I've tried:
live
live video=ofonly (or whatever it recommends)
test-powerpc
live-powerpc
live-config-powerpc
and a few others (these are all from memory, don't have it fired up right now).  They all have the same symptoms.

I'll dig through the forums to see if I can find a solution.

@talonts:

Since nobody who knows what they are doing is replying, I'll offer a couple thoughts . . . first, it seems that the general opinion is that Lubuntu 12.04 is more friendly to PPC computers, so if you haven't tried that version then it might get it going.  I don't know enough to know whether you would need to disable KMS or not for your computer--try to check the Ubuntu PPCFAQ page for more details.  After trying many Linux versions I was able to get Xu/Lu running on my iMac 800 using a retro installed driver--nv--took a little bit of doing in CLI to get it done, but it seemed to be OK with an xorg.conf file--then the computer has basically taken a dive.

The other option, I checked through my notes taken while testing the 12.10 Lu LiveDVD on my iBook and it looks like I got it booted by using "live-nospalsh-powerpc driver_updates"  . . . you didn't mention that choice, but maybe you used it??

e.e.p.

---

### Post by svtguy88 on 2013-02-20
One of these days I'll fire up my PPC G4 again.  It still has a working Debian install on it with a custom kernel built by me.

If I get some free time I'll fool around with some of the newer Lubuntu Live discs.

---

### Post by rsavage on 2013-02-24
I intend to put together a xubuntu 12.04 iso over the next few days.  Is there anything people want on it?  Here is what I have planned so far:
 
I'll use the oneiric version of Abiword so that it works.
 
Start with Firefox 17.0. FF18 had awful font rendering and 19 has a blue picture bug [https://bugs.launchpad.net/firefox/+bug/1130857](https://bugs.launchpad.net/firefox/+bug/1130857) .  I suggest people confirm the linked mozilla bug so that it gets looked at.
 
I'll include the nv package.
 
I'll use the latest debian wheezy radeon package.
 
I'll add an xorg file for G3 imacs (although you'll have to start in single user mode and copy it manually).
 
Include some USB fixes.
 
Apart from the above, all packages will be at the latest ubuntu versions.  That includes the kernel so suspend will work (eep).
 
It will probably be oversized so DVD or usb booting.
 
Btw, I also have the whole Mint Maya repository and xubuntu-dev ppa compiled.  So if there is a lot of interest I can produce a proper Mint xfce iso too.  Obviously that is treading on the toes of Mintppc and I'd prefer to devote my time on setting up my own Mate distro.  I've added info in the FAQ about Mint if people want to have a go at compiling stuff for themselves.  You can use their theme and icons without compiling.

---

### Post by este.el.paz on 2013-02-24
> **rsavage said:**
> I intend to put together a xubuntu 12.04 iso over the next few days.  Is there anything people want on it?  Here is what I have planned so far:
 
I'll use the oneiric version of Abiword so that it works.
 I'll include the nv package.
 I'll use the latest debian wheezy radeon package.
 
 Apart from the above, all packages will be at the latest ubuntu versions.  That includes the kernel so suspend will work (eep).
 

@rsavage:

That sounds great, and basically just in time--thanks for your efforts.  After I saw that post about Xubuntu, and remembering that I had it installed on my dying iMac, yesterday I looked around to see if there was a Xubuntu LiveDVD for PPC available . . . and there wasn't . . . the support for PPC is definitely shrinking.  It looks like I did the Xu installation using a mini.iso installer, but I don't know where I even found that for PPC.  Anyway, it's great news to hear that you are putting this package together, thanks for that.  Where will I look to procure the project?  

The Mate project looks interesting, I've got LM Maya with Mate DE installed on my MBP and it is very nice . . . seems to update without blowing itself up, etc . . . it could be interesting to see how that translates to PPC, although my iBook probably would be shy on speed and RAM . . . .  Anyway, thanks.

e.e.p.

---

### Post by rsavage on 2013-02-25
I'll put a link on here for the download.  Will be sometime this week I think.
 
I use Mate + compiz + the very latest thunar.  Is quick, but nowhere near ready for the general public.

---

### Post by rsavage on 2013-02-26
eep, there might be a delay on the iso so if you need it soon I'd install from the mini-iso.
 
I've got a version of the CD working that I hacked together, but the version using the proper Ubuntu scripts for some reason doesn't install correctly (although it works as a live CD).  So I've got to figure out why it's not working or make my hacked CD better.
 
Also, I now think I know how to make the iMac G3 work out-of-the-box with the live CD.  I've also spent quite a bit of time on the r128 driver (is hard when I don't have a machine) and Connor Behan (the r128 developer) helped me out with a few things.  I can now include an updated r128 driver with the EXA patch. 
 
Are there any other machines that need an xorg.conf before they work?

---

### Post by este.el.paz on 2013-02-26
> **rsavage said:**
> eep, there might be a delay on the iso so if you need it soon I'd install from the mini-iso.
 I've got a version of the CD working that I hacked together(although it works as a live CD).  So I've got to figure out why it's not working or make my hacked CD better.
 Are there any other machines that need an xorg.conf before they work?

@rsavage:

Thanks for the update, glad to hear that work is progressing . . . but, there isn't any raging hurry right now, so I don't mind waiting if I can.  I also have a lot of things going, and then shortly it will be tax time here in the good 'ole.  So, I do have a Ubun mini-installer from, looks like June of last year, but I'd be interested in the LiveDVD to test and then if all goes well--install from to the iBook G4--no worries though.

In terms of machines, from my personal experience with the difficulties of it, the iMac G4 that I finally got a Xu/Lu system installed on before the machine started into fits of kernel panics . . . is one that probably needs a good xorg.conf file--for those out there who have one, they still seem to post on forums about having problems, etc.  I may try to fix mine, don't know how simple or expensive it would be, but for a home unit it does what I need well enough.  I f I needed to reinstall a Linux system on it, it would be great if it just worked out of the box . . . whenever that would be . . . .

Thanks for your many efforts to keep PPC going in Linux,

e.e.p.

---

### Post by aaronparr on 2013-02-27
> **rsavage said:**
> Hello people!
 
Colin Watson has kindly looked into the mirror archive error that has plagued the PowerPC live cds since 11.04. He thinks he has now fixed it, see [https://bugs.launchpad.net/ubuntu/+source/choose-mirror/+bug/919356](https://bugs.launchpad.net/ubuntu/+source/choose-mirror/+bug/919356) ,but he needs some help with testing.
 
The new choose-mirror package is in the alternate CDs and I think the changes should have made there way into the ubiquity (live CD) package by now. So if you live in an exotic (i.e. non UK) location then why not have a go at installing 12.04?!! Please give feedback in the above bug report.
 
Thanks!

I am replying to this on a B&W G3 running 12.04. This computer has an upgraded CPU (PowerLogix's PowerForce G3 ZIF, with IBM PowerPC 750GX) and a SATA card with 2 1TB Sata drives hooked into it. The graphics card is the stock ATI Rage 128.

I was unable to successfully install using the live cd (perhaps user error frustrated by incompatibilities with the graphics card), but the alternate cd worked well for me. My first day of use was command line only as the machine would only boot into low graphics mode. Editing the xorg.conf file as suggested in the FAQ and Common Problems Page did not solve the problem, but updating as suggested did do the trick.

Next on the agenda is determining whether I can get everything possible out of this CPU. On the Mac side I can get about 1000 MHZ out of it using software. Otherwise I believe the CPU runs at approx 500 MHZ. In Ubuntu I have been unable to figure out how to profile it to determine anything about its performance. BUT the Ubuntu GUI is behaving more sluggishly than the OS X GUI, so I suspect that the CPU is running at the lower speed.

Once I figure this all out, I'll likely prefer the CLI, but it would be good to know if anyone else has the same upgraded CPU and whether they know of a way to get the most out of it using Ubuntu.

I want to add that I appreciate this community. I am a complete NEWB installing Linux, and although I had some expected difficulties, it is clear to me that I wouldn't be able to use this OS without the efforts of so many of you.

---

### Post by este.el.paz on 2013-02-27
@aaronparr:

It sounds like you are having fun . . . personally I am also fairly new to Linux, but have done a fair number of installs trying to get a system to run on my stock iMac G4.  It's interesting to see that you have a modified machine, and that MAY have some effect on the install???  

But, mainly I'm replying because it's Lubuntu 12.04 that has been adjusted to work with PPC computers . . . .  And, if you look back through the recent posts in this thread you could see that rsavage is working on putting a Xubuntu 12.04 upgrade to work with PPC . . . .  If you've only tried the main Ubuntu flavor, you might try the Lubuntu 12.04 LiveDVD or wait a little bit for the Xubuntu 12.04 . . . and then see how that works on your machine.

In Linux, there are a lot of options, but, in the PPC world the options are less, and you can put a lot of time as I have into getting a system up and running . . . only to have it break with the first upgrade.  Better to work with an OS that is set up for PPC support . . . .

e.e.p.

---

### Post by aaronparr on 2013-02-27
Thanks for the nudge towards Lubuntu. That lead me back to [Zen's post about Lubuntu on PowerPC Liberation]("http://powerpcliberation.blogspot.com/2012/10/lubuntu-install-guide.html"). It looks like you found your way there as well recently.

I'll take a look at these other flavors before I spend much energy getting set up in Ubuntu.

---

### Post by rsavage on 2013-02-28
You might be better off asking about your upgraded CPU on the debian powerpc mailing list or even the powerpc kernel mailing list.  You can find the links at the bottom of the FAQ.

Can I just ask what xorg.conf you are using now (if any)?  I wrote those r128 instructions for the live CD when 12.04 was released, but I don't own such a machine. I wonder if something is missing from them?

---

### Post by aaronparr on 2013-02-28
For the xorg.conf file I simply deleted the extra sections and kept the relevant sections as instructed.

I'll look at those mailing lists, thank you. I am however now going to try Lubuntu 12.10 next as it is much lighter weight than Ubuntu, and that should improve performance.

---

### Post by rsavage on 2013-03-03
Xubuntu live/desktop download: REMOVED

Please see the README file on the iso.

md5sum xubuntu-12.04-desktop-powerpc.iso
c5657b88f48e28dc22e91ac361c4c13a  xubuntu-12.04-desktop-powerpc.iso

sha256sum xubuntu-12.04-desktop-powerpc.iso
e368ae54262bc9f17eb48d8c7ddfe2b69ae1197c31548fb5bbf35b30df0f03cb  xubuntu-12.04-desktop-powerpc.iso

---

### Post by rsavage on 2013-03-04
I should of probably said in the above that it is 627MB so should fit on a standard CD.  I used a higher compression rate.

If you have a iMac G4 700/800 then use at the boot screen 'live nomodeset xforcenv'.  If you have an iMac G3 and it doesn't boot without parameters then use 'live xforceimacg3'.  These options are new to this CD, so please let me know if they work.

---

### Post by str8bs on 2013-03-04
Nice work!
imacg3 600 with Rage 128 Ultra
boot: live xforceimacg3
The long blank screen mentioned in the read me is way more than a minute on this dinosaur, but successful boot! Colors are off in a green tinted way, haven't looked into that.
EXA acceleration "went swimmingly"
DRI 3d enabled

1. May note in FAQ about kernel params getting appended to yaboot? It is easy to forget and I know it led me to chase my tale on a phantom port issue with a Fedora install the other day. I think the ubuntu installer works the same way as far as appends go. (automatically adds appends to yaboot config that were used in live/install boot)
2. Does xforcevesa still work for those that still can't get to gui?

Thanks

---

### Post by rsavage on 2013-03-04
Hi str8bs, long time no see!

Dunno about your green tint, is EXA not working correctly?  Maybe a sub pixel rendering thing?  Maybe mesa legacy?

The xforceimacg3/xforcenv/xforcefbdev just creates a basic xorg.conf that I assume (haven't tested) gets copied over to the installed system.  So you shouldn't need to use them again.  Nomodeset is probably only needed by nvidia users, and that as far as I know doesn't get appended by the installer (however, things starting with video= do get appended).  So if you need nomodeset then you will have to keep typing it until you edit your yaboot.conf to make it permanent.  

xforcevesa creates an xorg.conf using the vesa driver which I kinda assumed wasn't available on PowerPC?  Have I got that wrong?

Thanks for the feedback

---

### Post by str8bs on 2013-03-04
Hi rsavage.

[s]Speculation - Color tint issue is related to EXA but actually due to gart/aperture size. If so, nothing to work around that as long as we are stuck with forcePCIMode. (8MB aperture.) I've seen a lot of threads correcting what sounds like the same issue by increasing or decreasing aperture size.[/s]

I was playing around with xforcevesa on a nouveau machine with Fedora18 live and it booted in low color using vesa driver. Several other bugs in that release were fighting me so haven't gone any farther with that.

Thanks for the clarification on appends. It was a video= appended in yaboot that had me chasing my tale.

EDIT: I should clarify that this live xubuntu is booting in 16 bit color. I haven't yet played with any changes post install.

---

### Post by abtabt on 2013-03-04
[http://www.everymac.com/systems/apple/imac/specs/imac_800_fp.html](http://www.everymac.com/systems/apple/imac/specs/imac_800_fp.html)

this imac G4 / 800 

boot with this cd too a GUI desktop the only thing was firefox , it did not start (can be a defect CD )

boot:live nomodeset xforcenv    ( was used )

rsavage thanks for your work for ppc user

i will try this  CD on a imac G3 snow later

---

### Post by rsavage on 2013-03-04
Vesa isn't installed by default on PowePC and indeed doesn't seem to want to work on my ibook.  You sure you weren't falling back to the fbdev driver?  The xforcefbdev is genuinely something that could be incorportated into future lubuntu releases (not that I'm going to waste my time suggesting it).  

How bad is this green tint?  Is it on everything?  Have you tried putting UseFBDev to false?  Nobody has reported it on 12.10, so it must be the combination of dri and exa??  Maybe try uninstalling mesa legacy and installing the old 7.11?  I'm a bit diappointed by that.....I knew I should of played safe and gone with XAA on the xforceimacg3 xorg.conf.

Does the mplayer2 without altivec package in the 'extras' directoy work?  A patch had already gone in to enable CPU detection so I wasn't sure if it was necessary to provide a non-altivec package.

Not sure why Firefox isn't working.  Do you get an error when you start it from a terminal?

---

### Post by str8bs on 2013-03-05
> **rsavage said:**
> Vesa isn't installed by default on PowePC and indeed doesn't seem to want to work on my ibook.  You sure you weren't falling back to the fbdev driver?  The xforcefbdev is genuinely something that could be incorportated into future lubuntu releases (not that I'm going to waste my time suggesting it).  
Possibly was fbdev. I was playing with both with the intent of finding a way to a gui for those with really borked nouveau support at the moment. (geforce go) You have done that here. I suppose I could waste my time suggesting it. :)

[QUOTE=rsavage]How bad is this green tint?  Is it on everything?  Have you tried putting UseFBDev to false?  Nobody has reported it on 12.10, so it must be the combination of dri and exa??  Maybe try uninstalling mesa legacy and installing the old 7.11?  I'm a bit diappointed by that.....I knew I should of played safe and gone with XAA on the xforceimacg3 xorg.conf.[/QUOTE] It is bad enough that no one would want to live with it, but one is able to navigate. It is only in the areas you would expect acceleration related -- shadows, menu bars, etc. Text is off also. Readable, but "double strike" appearance. Switching to XAA solves. All in all, I see this as a major improvement. The whole single, nano, etc. process is a bit much for new or inexperienced users. With this as is, you have a GUI and telling someone to "sudo leafpad ... and make it look like this" is more reasonable. 
UseFBDev False did nothing. Did Tormod's patch get included? I used to get a signal 7 with it?
Will try playing around with the usual EXA options and taking mesa to 7.11. (Thanks for making that convenient.) I'm doubtful though due to the 8mb gart as mentioned earlier.

[QUOTE=rsavage]Does the mplayer2 without altivec package in the 'extras' directoy work?  A patch had already gone in to enable CPU detection so I wasn't sure if it was necessary to provide a non-altivec package.[/QUOTE] pending - need to grab dependencies

[QUOTE=rsavage]Not sure why Firefox isn't working.  Do you get an error when you start it from a terminal?[/QUOTE]
no problems with FF on this one

---

### Post by rsavage on 2013-03-05
> **str8bs said:**
> Switching to XAA solves. 
I guess that confirms it is an EXA thing then.  If you include a picture I'll contact Connor Behan, but the correct thing to do would be open a bug at [https://bugs.freedesktop.org/](https://bugs.freedesktop.org/) .  It is silly for us to speculate when it could be a endian bug or something.  Better to get the opinion of somebody who knows what they are talking about.  You could try installing xserver-xorg-video-r128-lts-quantal although this will update your entire Xorg packages (EXA only).

> 
All in all, I see this as a major improvement. The whole single, nano, etc. process is a bit much for new or inexperienced users. With this as is, you have a GUI and telling someone to "sudo leafpad ... and make it look like this" is more reasonable. 
I could make XAA the default for xforceimacg3 no probs, but I'd prefer to see if we could get EXA working correctly.  Does it work without DRI?

> 
UseFBDev False did nothing. Did Tormod's patch get included? I used to get a signal 7 with it?

I included the patch.

> 
 pending - need to grab dependencies

The easiest thing is to install gnome-mplayer and then install my mplayer2 package.

---

### Post by str8bs on 2013-03-05
> **rsavage said:**
> I guess that confirms it is an EXA thing then.  If you include a picture I'll contact Connor Behan, but the correct thing to do would be open a bug at [https://bugs.freedesktop.org/](https://bugs.freedesktop.org/) .  It is silly for us to speculate when it could be a endian bug or something.  Better to get the opinion of somebody who knows what they are talking about.  You could try installing xserver-xorg-video-r128-lts-quantal although this will update your entire Xorg packages (EXA only).
 Now don't go making sense. :p Work with developers upstream that have the skills/resources to help? Let upstream developers know people are still using this stuff? What a novel concept!

  [quote=rsavage]Does it work without DRI?[/quote]
yes

Also- leaving DRI enabled and adding EXANoComposite clears up text completely and just the backgrounds are bad at that point. Icons within the dock look correct.

I'll get details in a bug report later. I expect they will want to see current as well as latest. Probably be the weekend before I get back to it.

The attached is from iMac G3 600 with Rage 128 Ultra 16M (running in PCIMode)

Thanks

Side note regarding this iso and nouveau on FX5200 -- No color issues. The same well documented accel related workarounds apply. Without NoAccel or increased virtual there is no bottom panel/dock.

---

### Post by este.el.paz on 2013-03-05
@rsavage:

Thanks for your efforts, I'll try to test it out on my iBook in a few days and post any relevant comments.  Mostly posting here because I haven't gotten any notification on this thread since the recent "upgrade" or whatever, I'm subscribed supposedly to this thread but the last notification was on the aaronparr post . . . nothing on the posts from you with the link to the iso, nothing after that with the Str8 posts or the abtabt posts.  Mr Str8 just happend to send me an email offlist . . . so something has been left undone by the forum overhaul?????

Anyway, as I mentioned now several pages ago the iMac800 is krank, possibly tot or almost . . . so I'll give it a go on the iBook.

e.e.p.

---

### Post by gusduenas on 2013-03-06
I cannot tested at all, the installer of ubuntu 12.04 for mac ppc have the menu blank and the rest looks good, but even though I cannot install it at all.. I don't know whar are the partitions or if there is guided installation as Kubuntu, which is the one I will install if this Ubuntu thing is not resolved...someone could help me...I will install kubuntu now...

---

### Post by str8bs on 2013-03-06
@rsavage Maybe a separate thread for your test ISO is warranted? It could easily get buried or not distinguished from the standard ISO's.

@gusduenas Graphics driver issues are across the board.They will exist regardless of the distribution for the most part. I found and will post in your other thread.

---

### Post by cortman on 2013-03-06
> **str8bs said:**
> Now don't go making sense. :p Work with developers upstream that have the skills/resources to help? Let upstream developers know people are still using this stuff? What a novel concept!

  
yes

Also- leaving DRI enabled and adding EXANoComposite clears up text completely and just the backgrounds are bad at that point. Icons within the dock look correct.

I'll get details in a bug report later. I expect they will want to see current as well as latest. Probably be the weekend before I get back to it.

The attached is from iMac G3 600 with Rage 128 Ultra 16M (running in PCIMode)

Thanks

Side note regarding this iso and nouveau on FX5200 -- The same well documented accel related workarounds apply. Without NoAccel or increased virtual there is no bottom panel/dock.

I'm getting the same graphics issues with my PowerMac G5 and Lubuntu 12.10.

---

### Post by str8bs on 2013-03-06
@cortman
I mixed issues in my last post. (now edited to clarify)
Are you having color, acceleration related, or both issues? What card do you have?

---

### Post by abtabt on 2013-03-06
[http://www.everymac.com/systems/apple/imac/specs/imac_500_indigo.html](http://www.everymac.com/systems/apple/imac/specs/imac_500_indigo.html)
imac 500 

test with cd 
with 
xforceimacg3 
givs same than str8bs picture 

with 
Option		"AccelMethod"	"EXA"

without 
Option		"AccelMethod"	"EXA"

i get  xxa and nice GUI

and if i use ONLY  the VGA port with flat screen i dont need any arg at boot but this will use aty128fb driver but good GUI on the extern screen and the build in  is black ( so imac with VGA conector (mirror) will work with a LCD and arg live at boot )

and both XXA, EXA give glxgear    200 - 300 but with EXA its like choppy 

so a arg like xforceimac3xxa  and xforceimac3exa at the boot can make some sens 

have a nice day

---

### Post by gusduenas on 2013-03-06
Yesterday Itried to instal ubuntu 12.04 precise from live desktop cd on mac:
Configuration:
dual 2.0ghz PPC G5 (early 2006)
 Chipset Model:	GeForce 6600
  Type:	Display
  Bus:	PCIe
  Slot:	SLOT-1
  PCIe Lane Width:	x16
  VRAM (Total):	256 MB
  Vendor:	NVIDIA (0x10de)
  Device ID:	0x0141
  Revision ID:	0x00a4
  ROM Revision:	2149
  Displays:
**Cinema:**
  Resolution:	1680 x 1050
  Depth:	32-Bit Color
  Core Image:	Hardware Accelerated
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
  Rotation:	Supported
**Display Connector:**
  Status:	No Display Connected
2hd to boot 
1TB for leopard 7200 RPM WD
160GB 7200 RPM WD for Ubuntu (free space)
 
first off:
the menu was blank, seriously and it looks like my graphic card is not going for it.
Then the installer is impossible, I'm not a programmer or a linux expert...is there a guide installation (something without making your own partitions)
Also how can I make the partitions I have tried everything someone with a hands on experience and proven success on that please tell me.
When I finally made to the installation process , happens two things:
1. it stuck on "Saving installed packages" and nothing happens, I have to redo everything
2. it installs but when I try to boot to see what is going on, I cannot boot because yaboot have a problem...
Some guided help would be appreciated.

Gus

---

### Post by este.el.paz on 2013-03-06
> **gusduenas said:**
> Yesterday Itried to instal ubuntu 12.04 precise from live desktop cd on mac:
160GB 7200 RPM WD for Ubuntu (free space)
 
first off:
the menu was blank, seriously and it looks like my graphic card is not going for it.
Then the installer is impossible, I'm not a programmer or a linux expert...is there a guide installation (something without making your own partitions)
Also how can I make the partitions I have tried everything someone with a hands on experience and proven success on that please tell me.
When I finally made to the installation process , happens two things:
1. it stuck on "Saving installed packages" and nothing happens, I have to redo everything
2. it installs but when I try to boot to see what is going on, I cannot boot because yaboot have a problem...
Some guided help would be appreciated.

Gus

@gus:

I'm not an expert, but I've done quite a few installs of Linux systems, on PPC & Intel . . . so it's difficult to know what's going on, but, first thing, I'm not sure if Ubuntu"supports PPC" . . . it might be OK for Intel apple, but not for PPC.  So, you should try Lubuntu 12.04 for PPC, or this recent .iso from rsavage for Xubuntu 12.04 for PPC and try that.  Then the iinstaller should work better, and you could pick "guided" install, and pick "install in largest free space" option . . . it might go better . . . .

e.e.p.

---

### Post by cortman on 2013-03-06
> **str8bs said:**
> @cortman
I mixed issues in my last post. (now edited to clarify)
Are you having color, acceleration related, or both issues? What card do you have?

Color issues. Same off colors as you show in your scrot.
According to lspci it has the ATI RV3500AP card, which is using Radeon 9600. According to what I've found on the internet there's not a lot to do for that one...

---

### Post by rsavage on 2013-03-07
New r128 package to try [http://ubuntuone.com/4LLpVj4rgRQurdInUeXCGd](http://ubuntuone.com/4LLpVj4rgRQurdInUeXCGd) "OUTREGP Patch"

 New radeon/ati package with very latest fixes [http://ubuntuone.com/4R8Wa15Bdy9V9oy6OyX5q3](http://ubuntuone.com/4R8Wa15Bdy9V9oy6OyX5q3)

---

### Post by gusduenas on 2013-03-07
So far as I know there is  an iso for Ubuntu 12.04  ppc g5(new world macs)...Do you or anyone else knows how to install the partition thing correctly...I'm using a 160gbHD.

Gus

> **este.el.paz said:**
> @gus:

I'm not an expert, but I've done quite a few installs of Linux systems, on PPC & Intel . . . so it's difficult to know what's going on, but, first thing, I'm not sure if Ubuntu"supports PPC" . . . it might be OK for Intel apple, but not for PPC.  So, you should try Lubuntu 12.04 for PPC, or this recent .iso from rsavage for Xubuntu 12.04 for PPC and try that.  Then the iinstaller should work better, and you could pick "guided" install, and pick "install in largest free space" option . . . it might go better . . . .

e.e.p.

---

### Post by gusduenas on 2013-03-07
C'mon I cant believe I'm the only one trying this on a dual 2GHZ g5 (early 2006) with nvidia geforce 6600 256mb...someone should have known how to do it!!! please help :(

---

### Post by este.el.paz on 2013-03-07
> **gusduenas said:**
> So far as I know there is  an iso for Ubuntu 12.04  ppc g5(new world macs)...Do you or anyone else knows how to install the partition thing correctly...I'm using a 160gbHD.

Gus

Gus:

OK, yes, you are right, there is a Ubuntu for PPC, I thought I checked this only a couple weeks ago and didn't see anything there for PPC, but just checked it now and there it is.  So, question, did you download the "Desktop CD" and can you boot the CD and run the system BEFORE trying to install it?  Or do you have the "alternate installer" . . . I'd say you should test using the Desktop CD and see if you like it.  Again, if you have the entire HD to install into, it's a lot easier than if ou are trying to do a dual boot . . . .  As I mentioned, the "guided" install is available, but there should be an automatic install if you are using the whole HD.  Otherwise, if you do the partition manually you need a home, a "swap" which is supposed to be double the RAM size, and then a small partition for yaboot.

e.e.p.

---

### Post by rsavage on 2013-03-07
Please stop spamming this thread and stick to your own.

---

### Post by gusduenas on 2013-03-08
Well I did the alternate a few hours ago and it installs! gladly, I don't know how long it would it be (until it does something funny , that force to erase the HD again).but at least I have it Ubuntu 12.04 on my g5 (dual boot) I was using the desktop cd, because I install that way Kubuntu, but I like more th Ubuntu GUI, now I'm using the 2d desktop instead of the default one, because something funny happens with the icons on the main menu...so I will use it until I find a way to make this Ubuntu to accept My nvidia gt6600 card....But So far, so good.

---

### Post by rsavage on 2013-03-08
@str8bs and abtabt can one of you test the r128 package I posted in #245 please?  It is just to test something out.  It may help with the problems you are seeing, but may make glxgears worse.  If it does change things, Connor says he'll come up with a better patch.  He has already submitted anonther endian patch today (but that is probably no what you are seeing). Thanks.

---

### Post by rsavage on 2013-03-08
Forgot to ask this:

> 
By the way, since we're on the topic of big endian, have your users
reported any issues with the video overlay? Ie telling mplayer or VLC to
use Xv as the output? I noticed that there are some parts of the video
code where radeon does byte swapping but r128 doesn't.


---

### Post by str8bs on 2013-03-08
@rsavage
No change for me. GLXgears stayed in the 340's
I am able to fumble my way to "almost good" with workarounds. Moving to freedesktop with details in the next couple hours.

> **abtabt said:**
> 
and if i use ONLY  the VGA port with flat screen i dont need any arg at boot but this will use aty128fb driver but good GUI on the extern screen and the build in  is black ( so imac with VGA conector (mirror) will work with a LCD and arg live at boot )

IIRC, I had the same at least as far back as 3.23 kernel. I suspect DRI is automatically disabled due to high depth/res settings on default mode for external. (Mode not supported by the internal CRT so it is blank.) You can xrandr to a supported res like 1024x768 and you should see both mirrored.

---

### Post by rsavage on 2013-03-08
That's disappointing.  What about this [http://ubuntuone.com/0wMWzedEktblPZNC7TPKmG](http://ubuntuone.com/0wMWzedEktblPZNC7TPKmG) (solid picture endian patch)?  You are logging out and logging back in again after installing the package?  Just checking.

The link contains the very latest endian patch.  It should be the same as the current state of the r128 git repository (+ tormod's patch).

The previous link (OUTREGP patch) was a test of "If direct rendering is enabled, use big endian byte order".  It played about with this [http://cgit.freedesktop.org/xorg/driver/xf86-video-r128/tree/src/r128_accel.c#n1072](http://cgit.freedesktop.org/xorg/driver/xf86-video-r128/tree/src/r128_accel.c#n1072) bit of code.  I've removed that in the current link since you said it had no effect.

---

### Post by str8bs on 2013-03-08
> **rsavage said:**
>   You are logging out and logging back in again after installing the package?  Just checking.
;) stop/start lightdm and even rebooted for good measure.

[quote=rsavage]I've removed that in the current link since you said it had no effect.[/quote]
[s]Your previous patch PLUS EXANoComposite PLUS MigrationHeuristic greedy = all good. That wasn't the case before[/s] (I think). Will have to revert to verify.

---

### Post by rsavage on 2013-03-09
Str8bs, thanks for submitting the bug report.

So just to clarify:

original package + exanocomposite + migration greedy = still messed up

package from post 245 + exanocomposite + migration greedy = okay

package from post 254 + exanocomposite + migration greedy = ???? still messed up I expect?

What about the question on mplayer and xv?

---

### Post by rsavage on 2013-03-09
p.s. If you give me the output of lsmod (plug in any peripherals you need) then I'll see if I can compile a kernel for you to try.

---

### Post by este.el.paz on 2013-03-09
@rsavage:

End user/GUI operator report:

I'm booted in the liveCD burned from post #226 using "live" in the iBook G4 and everything looks very nice, good graphics, can't complain about the colors . . . .  I'm typing this in FF and all seems to be working.  And, most importantly, "suspend" works . . . and revived while in the CD . . . the main menu looks very "cinnamon-like" (just loaded cinnamon de on my MBPro yesterday) . . . .  Haven't had time to try everything out, but it looks very promising; when I get enough time to re-partition the HD to give Linux 10 GB I would consider doing the install.  I guess I'd have to get some hints about how to "lock the system" as you mentioned in the Read Me.  I'll try to keep playing with the CD . . . sometimes what has happened in the past is that while typing these kind of posts the mouse would "go off" . . . in Kubuntu Live and something else.  But, so far, it's fine-- very nice job, everything seems "tight."  I guess the only beef is that yes, the black screen lasts a loooooonnnnnnnggggggg time.  Maybe tomorrow I could try to boot in the kranken iMac G4 and see what happens there . . . .  So many things to do, not enough time . . . .

e.e.p.

---

### Post by rsavage on 2013-03-10
New r128 package to try: [http://ubuntuone.com/0k3wvKEp7FHz4KaVbPBFNX](http://ubuntuone.com/0k3wvKEp7FHz4KaVbPBFNX) .  This combines the previous two patches to OUTREGP and SolidPictures.

New cairo package 1.12.2: [http://ubuntuone.com/2m35cIVq1y0DzyWqoIa7VP](http://ubuntuone.com/2m35cIVq1y0DzyWqoIa7VP) .  This uses accelerated SolidPictures.  Radeon ( [http://ubuntuone.com/4R8Wa15Bdy9V9oy6OyX5q3](http://ubuntuone.com/4R8Wa15Bdy9V9oy6OyX5q3) )/r128 users can use this package with the new xserver packages.  I wouldn't install this if you use nv or nouveau.

If you've installed the new cairo package then the latest abiword maybe more useable: [http://ubuntuone.com/4DdueD8CgjNUmrqTO5BdAZ](http://ubuntuone.com/4DdueD8CgjNUmrqTO5BdAZ)

---

### Post by str8bs on 2013-03-10
> **rsavage said:**
> Str8bs, thanks for submitting the bug report.

So just to clarify:

original package + exanocomposite + migration greedy = still messed up

package from post 245 + exanocomposite + migration greedy = okay

package from post 254 + exanocomposite + migration greedy = ???? still messed up I expect?
Sorry. I thunk wrong. All three = no color problem when using exanocomposite + migration greedy
[quote=rsavage]What about the question on mplayer and xv?[/quote]
Didn't have much time on this. Would be great if someone else could confirm.
mplayer from extras:
without xv = "...interrupted signal 4 : open_stream (same with/without DMAForXV)
with xv = no error, but goes directly to "stopped" and nothing plays

VLC:
crashes/exits without error in all cases

Parole:
after installing codecs successfully played mpeg

All three play audio(mp3) without issue.

Other issues with this ISO:
The expected slow due to apt-xapian-index. Recommend removing after install for those with older hardware.
CD doesn't mount on the iMac (I haven't spent any time investigating yet.) CD's and DVD's automount fine on the G5/Nouveau system
live boot and installation process extremely slow from CD - I hear a lot of seeks going on. Possibly due to the high compression?
After installation from live boot and clicking restart, system ejects CD when expected, but hangs and just outputs characters when pressing enter (should restart). Force power/off on results in good boot from here though. (I repeated the install on the G3 to make sure it wasn't a fluke.) This is on the G3. Issue did not occur on the G5.

---

### Post by rsavage on 2013-03-10
For those wanting to help str8bs with testing, the supposedly G3 acceptable mplayer2 package is here [http://ubuntuone.com/4D1qo5u9PLC82LkrTqaGQF](http://ubuntuone.com/4D1qo5u9PLC82LkrTqaGQF) .  So that you get all the necessary dependencies, it is probably best to install gnome-mplayer first and then install my version of mplayer2.  Str8bs, doesn't it work with XAA?

---

### Post by este.el.paz on 2013-03-10
@rsavage:

enduser/GUI test: iMac 800 G4:

Using same CD from the other day, is that from #226?? booted the CD with "live nomodeset xforcenv" brings very good resolution screen, typing this post now, don't know how long it will work . . . checked a few things.  Only problem again the several minutes delay to get to screen and suspend brings black screen but processor or CD doesn't stop spinning, and then doesn't revive.  Had to shut it down, went to the "live nomodeset xforcefbdev" and again several minutes later went to a very low res graphic . . . 8???  was able to see "reboot" and booted back into the xforcenv driver where I am now.  So, it's fine in CD using nv driver, but already have an xubuntu loaded here, suspend doesn't work in it either, but can't be assured that it would be different in the updated version, as it didn't work the same way it did in the iBook--where it suspended and revived in the liveCD.

e.e.p.

Edit: Seconds after posting this the iMac screen went black . . . cursor visible and moveable, CD spinning, but black screen--assuming that was the kranken iMac crashing??  Difficult to know . . . .

---

### Post by rsavage on 2013-03-11
I haven't used a CD in years so no idea if that is normal behaviour.  I recommend you use a USB drive if you can (takes about 20mins to install on USB2).  Not sure what the minimum memory requirements are, 512MB at a guess.  If you have less you could possibly get crashes.  Suspend is dependant on framebuffers.  Is all documented in the FAQ, but no idea if it works on a G4 imac.  You could possibly use xforcefbdev if you don't use nomodeset, but nv should be better.

---

### Post by str8bs on 2013-03-11
@eep Thanks for testing.
It looks like abtabt has identical hardware. If he/she can't confirm the same, it may very well be hardware.

@rsavage regarding CD, agreed. I wanted to make sure it would fit as I think that is what most people start with. I don't recall it being that slow with the standard ISO, but I usually just use alternates, so not sure.

---

### Post by este.el.paz on 2013-03-11
> **rsavage said:**
> I haven't used a CD in years so no idea if that is normal behaviour.  I recommend you use a USB drive if you can (takes about 20mins to install on USB2).  Not sure what the minimum memory requirements are, 512MB at a guess.  If you have less you could possibly get crashes.  Suspend is dependant on framebuffers.  Is all documented in the FAQ, but no idea if it works on a G4 imac.  You could possibly use xforcefbdev if you don't use nomodeset, but nv should be better.

@rsavage:

Thanks for the reply, it just seems easier to burn a CD/DVD . . . and it worked fine as I posted for my iBook.  The iMac has been having kernel panic issues for quite some time.  Str8 suggested I try to boot the iMac with the CD to see if that would get around the kernel panics, but I think it's problem with FW ports.  It does have about 512 MB of RAM.  If I didn't use "nomodeset" the screen went to the old green/black 3AM TV monitor, non-viewable, and the fbdev driver brought a low resolution screen . . . "live nomodeset xforcenv" brought the best screen graphics for the iMac . . . probably the computer crashed the screen.

Anyway, at some point I will consider installing your brand of Xu on the iBook, but first I'd want to know if the FAQ or wherever the data about locking in your mods so that update/upgrade wouldn't undo them, etc.  Or, where the latest incarnation of your versions are located . . . other than here, and/or how that differs from the "regular" versions of Xubuntu . . . .  Where would I find that information?

e.e.p.

---

### Post by este.el.paz on 2013-03-11
> **str8bs said:**
> @eep Thanks for testing.
It looks like abtabt has identical hardware. If he/she can't confirm the same, it may very well be hardware.

@rsavage regarding CD, agreed. I wanted to make sure it would fit as I think that is what most people start with. I don't recall it being that slow with the standard ISO, but I usually just use alternates, so not sure.

@str8:

Yeah, I was posting my experience in case it would help abtabt, but from his ( I think) recent post he was testing an "iMac 500???" (maybe that's a typo) . . . but I know from the past he has the same basic unit I do, as we've "talked" over the last couple years about what works for it.  Abtabt is the one who gave me some hints about going to Xu, but with LXDE as best for the iMac 800, etc . . . so he's probably ahead of the game and actually knows how to do stuff with CLI, etc.  But, from what I found in my iMac live test the xforcenv was very good right out of the box, but the fbdev option would probably need some xorg conf tweaking like we did in the past to get it to work.

But, yeah, I've done a fair number of installs using LiveCD/DVD's as well as using the Ubun alternate installer to get the Xu/LXDE system installed on my iMac 3 or 4 or so months back . . . none of them seemed to take as long to get either to the splash, or more importantly from the splash to a GUI as this CD . . . even longer on the iMac.  Don't know whether that has any meaning once the installation has been done . . . ????

e.e.p.

---

### Post by rsavage on 2013-03-11
Xubuntu-dev 4.10 packages: [http://ubuntuone.com/0WYBV4qJ4cy5JoawY05RBW](http://ubuntuone.com/0WYBV4qJ4cy5JoawY05RBW) .  You need to combine with the proper ppa [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10/+packages](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10/+packages) .  I compiled back in January, so some are a bit out of date, but it is a head start for you.  

The best thing to do is to create a local repository using the dpkg-scanpackages command.  Then add it to your sources, for example:
```

deb [ trusted=yes ] file:/where-you've-stored-it precise xubuntu-dev

```

---

### Post by este.el.paz on 2013-03-11
> **rsavage said:**
> Xubuntu-dev 4.10 packages: [http://ubuntuone.com/0WYBV4qJ4cy5JoawY05RBW](http://ubuntuone.com/0WYBV4qJ4cy5JoawY05RBW) .  You need to combine with the proper ppa [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10/+packages](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10/+packages) .  I compiled back in January, so some are a bit out of date, but it is a head start for you.  

The best thing to do is to create a local repository using the dpkg-scanpackages command.  Then add it to your sources, for example:
```

deb [ trusted=yes ] file:/where-you've-stored-it precise xubuntu-dev

```

@rsavage:

Alrighty, thanks for that, the links and the added information . . . I   get that this is what many advanced Linux people are doing, building  their own  kernel and adding packages . . . and making it totally  customized, yet  sleek . . . .  However, I'm still very much an end  user, and maybe over  time I can find the time to learn more and more,  but in the meanwhile  needing to just piggyback onto an .iso that does  most of what I need . .  . w/o busting itself with each upgrade . . . .   I'm thinking/referring to  a  situation that most of us posting here  know of where updates/upgrades  seemed invariably to break something . .  . and in contrast it seems that  more hands are contributing to the  heavy lifting in the buntu world and  so it's not depending on one  person to do all the fixes . . . for free,  etc.  So, that is what I was  asking about; and it looks like your  suggestion about the  dpkg-scanpackages command might be my direct answer  about how to set  the system to not break or load incompatible stuff  onto it???  And that  would be something that I'd have to find the time  to learn about . . .  although I have tweaked some sources list items for  various OSs.  I  mostly use the Terminal or synaptic to find and install  stuff, haven't  downloaded any .deb files and done anything that way . .  . .  I'm still  ignirint about delving into the innirds of kernel  compiling . . . so  it seems like if I want to use the .iso from #226 to  install the  system, and then try to figure out how to keep it from  changing  anything . . . except what I want to change.  

Is there  something about this on an FAQ that goes into the  dpkg-scanpackages command a bit more in  depth, but keeping it simple  for rank beginners without covering all of  the myriad complications . .  . ? 

e.e.p.

---

### Post by rsavage on 2013-03-11
Sorry eep, bit of a mis-communication there.  That previous post was not for you, just anyone who wants updated packages from the xubuntu-dev ppa (they are not on the iso). I have so many compiled packages lying about I didn't know if anybody wanted them.

The iso you've downloaded has all the customizations explained in the README file.  That is why I told people to read it. On your ibook, the only package that you may need to lock is abiword.  The least painful way to do it is through synaptic package manager.

---

### Post by este.el.paz on 2013-03-11
> **rsavage said:**
> Sorry eep, bit of a mis-communication there.  That previous post was not for you, just anyone who wants updated packages from the xubuntu-dev ppa (they are not on the iso). I have so many compiled packages lying about I didn't know if anybody wanted them.

The iso you've downloaded has all the customizations explained in the README file.  That is why I told people to read it. On your ibook, the only package that you may need to lock is abiword.  The least painful way to do it is through synaptic package manager.

@rsavage:

Ah, OK, that's a relief . . . it's just pushing my skillset.  For some reason something about the word "you" I took to be for me . . . what can I say, I'm in California . . . so it's all about me, me, me . . . .  : - )))  Anyway, great if it's just abiword that would have to be locked, that might be easy enough to figure out how to do . . . .  But wanted to reply here because I did read the Read me, but I guess I don't have enough knowledge to know that it was explaining how the package was put together.  Thanks.

e.e.p.

---

### Post by abtabt on 2013-03-12
> **este.el.paz said:**
> 

Yeah, I was posting my experience in case it would help abtabt, but from his ( I think) recent post he was testing an "iMac 500???" (maybe that's a typo) . . . but I know from the past he has the same basic unit I do, as we've "talked" over the last couple years about what works for it.  Abtabt is the one who gave me some hints about going to Xu, but with LXDE as best for the iMac 800, etc . . . so he's probably ahead of the game and actually knows how to do stuff with CLI, etc.  But, from what I found in my iMac live test the xforcenv was very good right out of the box, but the fbdev option would probably need some xorg conf tweaking like we did in the past to get it to work.

e.e.p.

i can say that mine works with sus cd spinn down network goes down and the screen goes black and then  press 
enter ,screen comes back network starts and i am back and this with the nv driver  

 live nomodeset xforcenv

this is simular like ours I MAC 800 and i have some others mac too  IMAC 500 and now a 
IMAC 333 and this work with the cd if i use my own  xorg.conf but its like 256 MB RAM but too little to use live cd but the 
desktop shows up but the swap slowsdown things 

[http://www.everymac.com/systems/apple/imac/specs/imac_333.html](http://www.everymac.com/systems/apple/imac/specs/imac_333.html)

have a nice day

btw eeep  do you have a cable to use a ext screen VGA

---

### Post by este.el.paz on 2013-03-12
> **abtabt said:**
> i can say that mine works with sus cd spinn down network goes down and the screen goes black and then  press 
enter ,screen comes back network starts and i am back and this with the nv driver  

 live nomodeset xforcenv


btw eeep  do you have a cable to use a ext screen VGA

@abtabt:

Interesting that your iMac revives from suspend and my did not . . . maybe you have a bit more RAM?  

As far as your question about a cable for ext screen . . . no, I do not.  I know that Str8 has mentioned the difficulties of working with the iMac because of the port for ext screen??  can't recall the details, but everybody seems to agree it's not easy to get the iMac working with Linux.  But, in terms of my situation I don't think it's the display that is causing my kernel panics--if that is what you are thinking about to help me--the CLI freezes up I think due to the FW ports.  With this recent CD the screen did go black after a few minutes, but interestingly, the cursor was still visible and moveable . . . that is different than the "normal" KPs where the mouse freezes and nothing can be done--anywhere, including single user . . . .  It's toast until I can find the time to take it apart, have a pro look at it, or get a new one.  Is that what you were asking about?  Using an ext screen to get around the internal display?  Thanks for the thought . . . I'm thinking it won't solve the issue.

e.e.p.

---

### Post by abtabt on 2013-03-13
> **este.el.paz said:**
> @abtabt:

Interesting that your iMac revives from suspend and my did not . . . maybe you have a bit more RAM?  

As far as your question about a cable for ext screen . . . no, I do not.  I know that Str8 has mentioned the difficulties of working with the iMac because of the port for ext screen??  can't recall the details, but everybody seems to agree it's not easy to get the iMac working with Linux.  But, in terms of my situation I don't think it's the display that is causing my kernel panics--if that is what you are thinking about to help me--the CLI freezes up I think due to the FW ports.  With this recent CD the screen did go black after a few minutes, but interestingly, the cursor was still visible and moveable . . . that is different than the "normal" KPs where the mouse freezes and nothing can be done--anywhere, including single user . . . .  It's toast until I can find the time to take it apart, have a pro look at it, or get a new one.  Is that what you were asking about?  Using an ext screen to get around the internal display?  Thanks for the thought . . . I'm thinking it won't solve the issue.

e.e.p.

i have 768 MB 
about your kernel panics (i think we  talk about that before and my suggestion is still same ) 
about the cabel only intrested if its work like my imac 500 its use framebuffer at ext screen (works with live cd direct no need to xforcenv , nomodeset etc etc then its easy to edit files to get the internal screen to work and if files need to be  edit

have a nice day

---

### Post by este.el.paz on 2013-03-16
> **abtabt said:**
> i have 768 MB 
about your kernel panics (i think we  talk about that before and my suggestion is still same ) 
about the cabel only intrested if its work like my imac 500 its use framebuffer at ext screen (works with live cd direct no need to xforcenv , nomodeset etc etc then its easy to edit files to get the internal screen to work and if files need to be  edit

have a nice day

@abtabt:

Ah, 768 MB, that might explain the difference I think my iMac is 512 MB . . . but, right now that revive the iMac project is on the back burner.  I'm about ready to pull the trigger on re-sizing my iBook HD to give 10 or 11 GBs for Linux, and giving the rsavage Xubuntu iso a fly.  Have there been any changes that would make it better to re-burn the CD to pick them up since the what, the #226 posting?  Or, any other recommends on the install, OK to install from the GUI desktop installer?  Does "guided" install work out, or is it better to do "expert" and manually set the partitions?  I've done enough installs to do it any way that's best, just trying to avoid any known problems . . . .  Figuring I'll have to set wireless up afterward??  I have the laptop plugged in right now, probably could check it before doing the install . . . .  The Wheezy system is just a bit too . . . uh, flakey . . . and I have to expand the partition to get around the "you have low disk space" error messages.

e.e.p.

---

### Post by este.el.paz on 2013-03-17
> **rsavage said:**
> Sorry eep, bit of a mis-communication there. On your ibook, the only package that you may need to lock is abiword.  The least painful way to do it is through synaptic package manager.

@rsavage:

Urgency level: Very
Defcon Alert level: Red

Latest update:  Pulled the trigger and did your Xu 12.04 iso CD install on the iBook today . . . started off with choosing "Other" for method of install, but then didn't have the patience to figure out the math to set the partition start and end points . . . so I went with the low hanging fruit, avenue of least resistance and rolled back to "Install next to OSX" and I let the installer figure it all out.  And it did find the 11GB "free space" I had cut out in OSX DU . . . so it all went OK.  I'm typing in the xfce session right now.  

So, now starting all over again . . . it looks like there is more "stuff" accessible in the "Xfce session" than in the "Xubuntu session"???  But, main reason for posting, I checked "download updates" in the first page of the auto-installer, and I saw updates being downloaded . . . but after the install the Ubuntu software update window shows "44 updates available" . . . so I went to Terminal and ran update/upgrade to see what would be there and right up top in the list were a number of Abiword updates, "abiword-grammer" and then some packages that were "held back" that were also for abiword . . . .  So, not sure if it's too late to "lock" Abiword as you suggested before, like, I shouldn't have checked "download updates" booted up and locked abiword and then do any other updates . . . or, should I do this post-install upgrade including the abiword stuff . . . and then lock it??  Also wondering if I want to do the font enhancing thing that JD did over on the mintppc site . . . seems like the fonts in FF are a tad anemic . . . could they be better?  But then I think I'd have to add mintppc to my sources list, turning it into a hybrid system, etc.  But, main question right now is, should I lock abiword and not do these upgrades, or is that something for many months down the road??

e.e.p.

---

### Post by superchar42 on 2013-03-19
> 13.04 is doing that pseudo 8 bit display deal, and I haven't been able to find a boot parameter to keep it from happening. I'm running a 12.04 session decently, 
I'm on an iBook G4

NEVERMIND - I found that live video=radeonfb:1024x768-32@60  (per [http://powerpcliberation.blogspot.com.au/2012/10/lubuntu-install-guide.html](http://powerpcliberation.blogspot.com.au/2012/10/lubuntu-install-guide.html)) got it working. 

Then I got wireless working on live, by loading the broadcom driver from USB. the b43 cutter is already on there. 

To get the wireless working, I just did this: 
```

tar xfvj broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o

```

then this

```

sudo modprobe -r b43 bcma
sudo modprobe -r brcmsmac bcma
sudo modprobe b43

```

In about 2 minutes I saw all the local wireless networks. WOO! Man, this was the easiest distro ever.

---

### Post by este.el.paz on 2013-03-19
@rsavage:

I was following a thread where Str8bs had posted a link for someone to get to the .iso, and then checking back through this thread I see that the .iso has been "REMOVED"??? from post #226.  Has it just been moved over to the regular Xubun 12.04 for PPC files, or is it just been taken down for more mods?

e.e.p.

---

### Post by Svetlana Tovarisch on 2013-03-20
Hi, sorry for sort of hijacking this thread with my lack of experience,

I own a [Summer 2000 450mhz Ruby iMac G3]("http://www.everymac.com/systems/apple/imac/specs/imac_dv_plus_450.html") with 1GB RAM, currently triple-booting 9.2.2, 10.4.11 and Debian/MintPPC (which doesn't run very well and I don't bother using much).
So far my PPC Linux experience has been less than satisfying given even the desktop is significantly more sluggish than what OS X can achieve (understandable, given the opensource r128 drivers), so I figured since Ubuntu seems to have a bigger PPC userbase and activity, someone might've figured out a solution to this, and I decided to give it a try.

I apologize for skimming through the posts in this thread, but I can't really seem to find a definite place to get whatever ISO I need to get to run on my iMac. The first page has a post with a link, but it leads me to 13.04 rather than 12.04, and I feel like I might download the wrong thing. While on that same note, is there a bootable USB variant of the ISO (Or, can I just "dd" the ISO to an USB stick?) so I don't have to burn a CD for it?

Currently I've gotten about 22-30 FPS on glxgears, while Flurry on OS X 10.4.11 for example runs quite smoothly, meaning the Rage 128 in my iMac, while a less powerful version than later ones, should still be able to at least display a desktop environment and webpages without much hassle.

---

### Post by este.el.paz on 2013-03-20
@Svetlana T:

Welcome to the forum, it looks like your experience with finding a system to run on PPC parallels mine . . . I have 10.4.11 dual booting on a G4 iBook and iMac (having hardware issues) . . . and I also tried MintPPC but had a hard time keeping it in working order . . . so I went to straight Debian Wheezy . . . and then switched to Xubuntu 12.04.  So far 10.4.11 runs the computer the best, but of course the browsers (other than Ten4Fox) are not supported . . . and so stuff isn't working on web sites.  But, in terms of the G3 iMac I don't have any experience with that . . . Str8bs is the guy who has the experience there, so maybe you can look through his posts here and find something out.  However, there was a post here for a Xubuntu .iso prepared by rsavage on post #226 with tweaks for PPC and both G3/G4 which would be the latest updates and probably your best choice . . . but if you read my last post it has been removed--I don't know what happened to it.  Some people prefer Lubuntu 12.04.  You could go to the Xubuntu home page and see if there is anything about an updated .iso for PPC posted there.  Or maybe in a few days somebody else will reply to your post . . . .

e.e.p.

PS:  Went to the Xubuntu.org home page and in LM13 MBPro there was no link there for PPC that I could see, so I found the wiki for PPC downloads here:
[https://wiki.ubuntu.com/PowerPCDownloads/](https://wiki.ubuntu.com/PowerPCDownloads/)   should get you something that will work, but it doesn't look like the desktop CD .iso for Xubuntu is there.

---

### Post by este.el.paz on 2013-03-23
@rsavage:

Looks like all the other kids are playing somehwere else, but my testing in the iBook G4 w/654?? MB RAM of the vanished Xubuntu 12.04 desktop .iso continues.  And, overall, it's fine, but it isn't perfect.  I installed disk utility and it shows before I added a few big apps like LibreOffice writer, and mini-tube (can't figure out how it works) . . . that the size of the installed system was only 2.73GB, so I could have easily got it installed into my old 5GB partition.  More or less the same?? basic install in Wheezy was 4.73GB.  

Where the Xu 12.04 perfection starts to show some cracks is in the "revive from suspend area" . . . there have been a number of problems there.  Most times it's OK, but let's say 30%-45% of times either the screen will show after reviving from suspend, but clicking on main menu will not drop down, or clicking on minimized items will not maximize them, can't "log out" or "restart" . . . just have to shut it down.  Yesterday I left the room for a few minutes and then when I came back the screen was breaking up horizontally like the old TV screen that needed an antenna, and there were two mouse cursors; fortunately there the right hand cursor was able to click on stuff and I could get the GUI to reboot . . . and after that restart it was OK.  Also, yesterday, while looking at the screen doing something, suddenly there was a moment where the screen went totally black, and then it was back, clear as a bell.

So, it's fine, but there are problems that are showing up . . . much like the same issues that were there with Wheezy, those issues and the constant "Low disk space" error messages got me to move on . . . but the elusive search for the perfect Linux OS . . . is not over.  : - )

Hopefully, there will be an answer to the question of what happened to the Xu .iso on post #226 . . . like how can folks like "Svetlana" find her way to this .iso if she ever passes by this thread again, etc?????

e.e.p.

---

### Post by rsavage on 2013-03-24
I removed the iso since nobody outside of the usual posters seemed interested and nobody was testing the updated packages I posted.

EDIT:

An expanded justification for eep:

One of the main reasons for the iso was to make it easier for imac G3/G4 users so that it worked "out of the box".  The iso in its current state fails for G3 users in this regard becuase I set it up to boot into exa mode, and we have since learned that there are problems with this.  

The r128 package has now been upgraded/updated, but I'm not prepared to put another iso together with it unless the package has been tested.  It takes a lot of time to build an iso and upload it.  Far far more than for a r128 user to test the packages I uploaded.  

There are other niggly things wrong with the iso, I gave some dodgy advice to radeon users for example.  

I was not happy with it, so I removed it.

But I have not stopped a user from installing xubuntu if they want.  They should just use the mini iso. And I have not ruled out an improved iso being produced, but that is dependant on people testing the packages I posted.  An existing lubuntu or whatever user could do this, it is not necessary to install xubuntu to test the xorg packages.

---

### Post by rsavage on 2013-03-24
This [http://ubuntuone.com/6GYRvnI5mAiw62UybwElQ5](http://ubuntuone.com/6GYRvnI5mAiw62UybwElQ5) is a link for Mate 1.4 (see [http://mate-desktop.org/](http://mate-desktop.org/) ) PowerPC packages (compiled for precise).  It's pretty big (164 MB) so probably best to make sure it has downloaded okay:

md5sum mate-1.4.tar.gz
636cdd6d29f620bfdea1604b27b0fe14  mate-1.4.tar.gz

sha256sum mate-1.4.tar.gz
ab0a7d0abcd920ba19882229604785649cf60f3f077c99346ca0cb853ed5b87b  mate-1.4.tar.gz

Extract it to your home folder.

Adjust your sources:

gksudo leafpad /etc/apt/sources.list

and add the line 

deb [ trusted=yes ] file:/home/your-user-name/mate-1.4 precise main

Then install:

sudo apt-get update
# this will install base packages
sudo apt-get install mate-core
# this will install more packages
sudo apt-get install mate-desktop-environment

Everything should work pretty okay I think (although i haven't tested a lot) so please don't bombard me with questions, because I'll basically ignore them (if that doesnt sound too rude).  I posted the packages up to save you from compiling them yourself, but that doesn't mean I'm offering technical support (unless you want to pay me).  You'd be better off using your time to look for your own solutions, but of course you can post your solution up here for others.  One thing I did notice when testing myself was that the help files for a lot of the applications are missing.  This is becasue they are moving over to a wiki based system and nobody has volunteered yet to write the documentation yet (...gosh that sounds familiar....).

---

### Post by este.el.paz on 2013-03-24
> **rsavage said:**
> I removed the iso since nobody outside of the usual posters seemed interested and nobody was testing the updated packages I posted.

> . like how can folks like "Svetlana" find her way to this .iso if she ever passes by this thread again, etc?????

@rsavage:

Well, as the creator of the .iso I guess that is your right, but frankly perhaps a tad impatient . . . if you don't mind some feedback from a mid-fifties fellow human . . . .  It takes time to make changes and test stuff out, and clearly some people have families and things to do, so it's not going to be in a period of weeks that anything is going to happen . . . .  I get that you put a lot of work into your 'buntu for PPC projects and perhaps the response is disproportionate and underwhelming, but we have the recent example of someone looking for a PPC friendly OS in "Svetlana" . . . but the .iso is gone . . . so she'll probably shop elsewhere.  Think about it.  We all suffer disappointment, I've written now 3 books that I think are important for people to understand life, with a similar response level . . . people aren't interested for one reason or another, it's just the way it is . . . but I wouldn't unwrite them, because what I learned from writing them is invaluable to me, etc.

In terms of the package updates, unfortunately my skilz with Linux are not developed enough to know how to download and extract files that way, yet.  I'm very comfortable with the "sudo update/upgrade" method.  Of course I can edit my sources list, but stll not at the place where CLI to add packages "by hand" . . . .  And I might be able to find out how to do that, but I have stuff to do and it would take time . . . .  I appreciate the MATE DE package and the fact that you give instructions about how to get to it, perhaps I'll get around to it.  I'm sure str8 & abtabt can make use of it and over time the word will get out. But, considering that 12.04 is supposed to be LTS consider that having your .iso available during that time . . . makes sense to share your work, again.  : - )

e.e.p.

---

### Post by rsavage on 2013-03-24
> **este.el.paz said:**
> Well, as the creator of the .iso I guess that is your right, but frankly perhaps a tad impatient . . . 
I edited the post with my justifications, impatience has nothing to do with it.  

Although people should take the opportunity to test things now while we have the attention of the r128 developer.  Don't know what the time scales for 13.04 are, but I should imagine it is pretty tight to get changes in now.

---

### Post by Svetlana Tovarisch on 2013-03-24
I'm sorry, but what am I supposed to download and burn to a CD/USB, then? It's not very clear.

---

### Post by str8bs on 2013-03-24
> **Svetlana Tovarisch said:**
> I'm sorry, but what am I supposed to download and burn to a CD/USB, then? It's not very clear.
Hi Svetlana. I agree the 6 year old 23 page FAQ thread doesn't exactly make it clear. :)

My recommendation is 12.04 from [here.]("https://wiki.ubuntu.com/PowerPCDownloads") For the iMac you probably want to got with Lubuntu iso or Xubuntu via alternate/mini iso. Check the PPC FAQ for instructions on creating/booting USB.

The ISO rsavage was testing had some patches/workarounds incorporated to help R128/iMac users that you will have to add yourself if interested. eg: Monitor section in xorg.conf, oldmesa, and EXA. 

If you run in to problems, start a thread and there are plenty here who will help out. The PPC FAQ and Known Issues are kept well maintained so many issues can be resolved via those resources.

---

### Post by este.el.paz on 2013-03-24
> **rsavage said:**
> I removed the iso since nobody outside of the usual posters seemed interested and nobody was testing the updated packages I posted.

EDIT:
An expanded justification for eep:
One of the main reasons for the iso was to make it easier for imac G3/G4 users so that it worked "out of the box".  The iso in its current state fails for G3 users in this regard becuase I set it up to boot into exa mode, and we have since learned that there are problems with this.  
The r128 package has now been upgraded/updated, but I'm not prepared to put another iso together with it unless the package has been tested.  It takes a lot of time to build an iso and upload it.  Far far more than for a r128 user to test the packages I uploaded.  
There are other niggly things wrong with the iso, I gave some dodgy advice to radeon users for example.  
.

@rsavage:

Alrighty, thanks for the expanded explication, but a further couple points, first, your .iso did work very well right out of the box with no boot parameters on my G4 iBook, and also it booted into a very good screen on my iMac with the boot parems you provided . . . which was not the case with the Xu 12.04 I have installed there already, where I had to go thru a process to get the "nv" driver--your .iso did that, so probably for G4 iMac users the .iso would be a time saver.  If I was brand new to Linux as I was 2 years ago, I wouldn't have been able to get it installed and I would have had to turn to mintppc and that whole story . . . .  So, whether or not your .iso is perfect or not, it worked very well for me, as an end user--I appreciate it and thank you--others should have the chance to find their way to it.  My iBook has the radeon driver, but everything seems to be OK more or less, so I didn't understand your dodgy radeon advice--no harm no foul.  In terms of acceleration, I don't think I have enough RAM for it, haven't had time to check if I have an r128 package, and the iMac is f**ked up . . . and unfortunately, don't know how to install .tar . . . .  In terms of G3 users, you could always update your .iso and post it later in this thread??  We have a new tester with ST . . . but, now, nothing for her to even try.

@str8bs:  Homes, I already posted that link and same advice to Svetlana in post number 279 . . . .  You're late dude, where you been at? : - )

e.e.p.

---

### Post by este.el.paz on 2013-03-24
> **Svetlana Tovarisch said:**
> I'm sorry, but what am I supposed to download and burn to a CD/USB, then? It's not very clear.

@STovarisch:

You should probably download a "desktop" CD/DVD so that you could test it before installing, it looks like Lubuntu 12.04 for PPC would be the choice, if the Xubun 12.04 is only available as mini.iso.  You could always add the XFCE DE later on . . . .

e.e.p.

---

### Post by rsavage on 2013-03-25
This [http://ubuntuone.com/4sgEKgpqsNjsGybWBTFD7W](http://ubuntuone.com/4sgEKgpqsNjsGybWBTFD7W) is a link for Mint Maya PowerPC packages.  Depending on the flavour you want, you can use them with the mate packages I posted in post #282, with standard kde packages or with the xfce-4.10 packages I posted in #267. EDIT: There is also cinnamon, although I couldn't get it to work with my iBook, maybe nouveau users will have more luck?  Four distros in one post!

md5sum mint-maya.tar.gz
cffcedbdbe9dfc5fe2dea80815301282  mint-maya.tar.gz

sha256sum mint-maya.tar.gz
456a1fa70fdd486df0e05361de741e50acbe5d89ea4f89e2f910ba689152be0a  mint-maya.tar.gz

After extracting the file, add the following lines to your sources.list:

# For a list of packages see [http://packages.linuxmint.com/list.php?release=Maya](http://packages.linuxmint.com/list.php?release=Maya)
# We have to put arch=i386 to pickup the generic 'all' packages.
deb [ trusted=yes ] file:/home/your-user-name/mint-maya precise main upstream
deb [ arch=i386 ] [http://packages.linuxmint.com/](http://packages.linuxmint.com/) maya main upstream import

You could also add the backport repository.

Then run:

sudo apt-get update
sudo apt-get install linuxmint-keyring

I haven't included the mate-1.2/1.3 packages since LinuxMint don't  publish all the necessary source code.  There are also a few other  missing packages such as mintmenu-keybinder, gtk2-engines-candido and  nautilus-gksu.  I did write and ask if it was possible to get the  missing source code, but no response yet.

I've adjusted some of the meta packages since PowerPC doesn't have  things like ndiswrapper.  You'll find all the changes documented in the  relevant directories.  The codecs from medibuntu are not included in the  meta packages, you'll have to manually download them as instructed in  the FAQ.

[EDIT]
If you want Mate 1.2/13 packages like Mint Maya then I've compiled the available packages and done a best guess at the missing source code using the mate git repository.  To download mate-1.2.tar.gz - [http://ubuntuone.com/3qRIv2XELj7BDFzpj6Rajp](http://ubuntuone.com/3qRIv2XELj7BDFzpj6Rajp)

sha1sum mate-1.2.tar.gz
e31e03940e8b84e23f4c27ac778f85bf0e8aaf73  mate-1.2.tar.gz

sha256sum mate-1.2.tar.gz
8439325158c05807985ba0179491fea22cf2c3c826e8f3b9eeca7575f83a47de  mate-1.2.tar.gz

md5sum mate-1.2.tar.gz
21172a4efa20a3c0c262d39d79dfe7d9  mate-1.2.tar.gz

[EDIT2]
Instead of mintmenu-keybinder you can follow the advice in this bug report [https://bugs.launchpad.net/linuxmint/+bug/898184](https://bugs.launchpad.net/linuxmint/+bug/898184) .

---

### Post by este.el.paz on 2013-03-26
@rsavage:

Thanks for the MATE package, maybe someday I'll figure out how to install it.  Mainly posting here to note that it's interesting that MATE is available for PPC . . . I have LM13 MATE 64 with various other DEs loaded on my MBPro, but they appear to no longer support PPC on their main site?  Which might fill in the blanks on the "Mint" vs mintppc story, w/mintppc being an attempt to carry the LM items over to PPC???

e.e.p.

---

### Post by rsavage on 2013-03-26
> **este.el.paz said:**
> maybe someday I'll figure out how to install it. 
er...how about trying to follow the instructions I wrote before writing comments like this?  It is very frustrating.  Not sure what there is to figure out with regards to Mate since I gave full instructions.

What the instructions do is setup a local repository of packages.  So you can install packages like any other, through synaptic, ubuntu software centre, apt-get. 

FYI for everybody, the [ trusted = yes ] is because I never bothered signing the packages.  If you don't have this you'll get moaned at about the packages being unsigned.  I suppose it does theoretically reduce a layer of security.  If somebody were able to hack into your home directory then they could alter or upload packages and you could install them unwittingly.  I kinda think if they are able to do that then it is game-over anyway.  If you are concerned then remove the whole local file line from your sources.list once you've installed the packages you want.

> Mainly posting here to note that it's interesting that MATE is available for PPC . . . 
Mate has always been available - if you compile it.  It was gnome2 so works very well on PowerPC (particulalry when combined with compiz).  Mate 1.4 works on a par or even better than Ubuntu Lucid.  I'm very impressed with caja in 1.4.

If anybody wants to compile it for themselves, then creating a bash script to automate it is the way forward!!  Takes a few hours to compile.

> 
I have LM13 MATE 64 with various other DEs loaded on my MBPro, but they appear to no longer support PPC on their main site?  Which might fill in the blanks on the "Mint" vs mintppc story, w/mintppc being an attempt to carry the LM items over to PPC???
LinuxMint have never produced PowerPC specific packages as far as I am aware.  However, a lot of their packages are "all" deb files which means you can install them on PowerPC. To be honest, apart from a nice theme I don't really see the attraction.  The Mintmenu scrollbar is awful, and the software centre slow.  I use the theme and that's it.

No comment on MintPPC.

---

### Post by este.el.paz on 2013-03-26
@rsavage:

Sorry for the frustration dahlink . . . indeed most all of your posts are thorough enough to provide adequate information even for GUI guys like me, but, as I did say in several of my prior posts that were seemingly not sliced and diced as my recent post . . . where I was just trying to show you that somebody is listening, etc . . . that it 's the step where you say: 
[COLOR=#000000]
[/COLOR]> "[COLOR=#000000]After extracting the file,:"[/COLOR][COLOR=#000000]

Or the > extract it to your home folder

That I don't have time to figure out how to do, not blaming you, not trying to frustrate, just trying to learn a bit more, participate in the conversation to keep PPC development going; but have other things to do as well.

Joy to you . . . .
e.e.p.[/COLOR]

---

### Post by rsavage on 2013-03-26
Right-click on file, select one of the extract options.

---

### Post by este.el.paz on 2013-03-26
> **rsavage said:**
> Right-click on file, select one of the extract options.

O jeez . . . I guess I could do that.  I thought it was like over on the other forum where everything had to be done thru CLI, and I would have to "mv" something with a long file name stringing behind it, to some other place with an equally long file name . . . but perhaps that whole experience was because I couldn't get a screen to show up, so didn't learn the basics of how simple it is to install something using GUI . . . .

Thanks for that,

e.e.p.

---

### Post by rsavage on 2013-03-27
There doesn't seem to be many guides for installing Linux Mint from the command line (and I'm not going to write one), but this thread has the right sort of idea [http://forums.linuxmint.com/viewtopic.php?f=60&t=103554](http://forums.linuxmint.com/viewtopic.php?f=60&t=103554) .  Basically, you need to look at what packages you have installed in the i386/amd64 world and install them on PowerPC.  Is a nice little doo-able project for somebody.

---

### Post by este.el.paz on 2013-03-27
> **rsavage said:**
> There doesn't seem to be many guides for installing Linux Mint from the command line (and I'm not going to write one), but this thread has the right sort of idea [http://forums.linuxmint.com/viewtopic.php?f=60&t=103554](http://forums.linuxmint.com/viewtopic.php?f=60&t=103554) .  Basically, you need to look at what packages you have installed in the i386/amd64 world and install them on PowerPC.  Is a nice little doo-able project for somebody.

@rsavage:

Thanks very much for that How-to for setting an XFCE system . . . read through it, indeed it looks like something worth an afternoon, especially some of the other suggestions.  But, as I mentioned, I've got LM13 MATE on my MBPro, and had XFCE DE version of LMDE, and I recently installed XFCE DE to try to see if the problem of data erasure after cursor moves erratically, goes away . . . but it looks like it's 4.8.3??  It looks older than the LM13 XFCE LiveDVD . . . but with this thread I'll probably be able to get it to 4.10 . . . .  Not what you had in mind, but nonetheless . . . practical.  Thanks again.

e.e.p.

---

### Post by gusduenas on 2013-03-28
using mac g5 ppc dual 2.0ghz nvidia geforce 6600 with two dvi ports.
Ubuntu 12.04 over its own HD-160gb
Dual boot with 1tb hd osx 10.5.8 and 160gb hd with Ubuntu 12.04

So far, so good, but I don't have much of the acceleration on the card, only with the 2d desktop
I'd like to see the ubuntu desktop working in all its funcionality, I have xorg.conf file it says:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "record"
    Load  "dri"
    Load  "dbe"
    Load  "dri2"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "WrappedFB"              # [<bool>]
        #Option     "GLXVBlank"              # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "nouveau"
    BusID       "PCI:10:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "fbdev"
    BusID       "PCI:10:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

This is the info using ddcprobe:

```
sudo ddcprobe
oem: nouveaufb
memory: 7088kb
edid: 
edid: 1 3
id: 2292
eisa: APP2292
serial: 254c0002
manufacture: 46 2005
input: digital signal.
screensize: 43 27
gamma: 2.200000
dpms: non-RGB, active off, suspend, no standby
ctiming: 248x198@111
dtiming: 1680x1050@59
monitorserial: 2A5463WMUFZ
monitorname: Cinema


```

But my xorg.org didn't show this...it is just monitor...how can I configure that?

Now I don't know what it sees two monitors because of the odd error in my Xorg -configure.

Someone has finally done how to make this work (I mean the geforce 6600 and the Cinema Monitor) over Ubuntu 12.04 on g5 ppc?


Gus

---

### Post by rsavage on 2013-03-31
More random packages for 12.04:

compiz-mate (0.8.8 'stable' compiz.  See [http://jas.gemnetworks.com/matepiz/](http://jas.gemnetworks.com/matepiz/) ) [http://ubuntuone.com/02EgSq1ujH9qJd1eIzQ7Ts](http://ubuntuone.com/02EgSq1ujH9qJd1eIzQ7Ts)

xserver-xorg-video-nv [http://ubuntuone.com/6QVpmfHCU3YmHlik7lred9](http://ubuntuone.com/6QVpmfHCU3YmHlik7lred9)

minitube-2.0 [http://ubuntuone.com/013WUTlld61aptc0lcsbZ7](http://ubuntuone.com/013WUTlld61aptc0lcsbZ7)

mesa-legacy [http://ubuntuone.com/379TLoe7yo2IAiOijAsOjQ](http://ubuntuone.com/379TLoe7yo2IAiOijAsOjQ)

It would be interesting to know if nouveau users can run 0.8.8 compiz okay.  Perhaps try it in indirect mode if you still have problems?  Compiz-mate works good on my iBook with only leafpad having a few glitches when opened maximised (haven't figured out what that is all about yet).

---

### Post by este.el.paz on 2013-03-31
> **rsavage said:**
> More random packages for 12.04:

compiz-mate (0.8.8 'stable' compiz.  See [http://jas.gemnetworks.com/matepiz/](http://jas.gemnetworks.com/matepiz/) ) [http://ubuntuone.com/02EgSq1ujH9qJd1eIzQ7Ts](http://ubuntuone.com/02EgSq1ujH9qJd1eIzQ7Ts)

xserver-xorg-video-nv [http://ubuntuone.com/6QVpmfHCU3YmHlik7lred9](http://ubuntuone.com/6QVpmfHCU3YmHlik7lred9)

minitube-2.0 [http://ubuntuone.com/013WUTlld61aptc0lcsbZ7](http://ubuntuone.com/013WUTlld61aptc0lcsbZ7)

mesa-legacy [http://ubuntuone.com/379TLoe7yo2IAiOijAsOjQ](http://ubuntuone.com/379TLoe7yo2IAiOijAsOjQ)

It would be interesting to know if nouveau users can run 0.8.8 compiz okay.  Perhaps try it in indirect mode if you still have problems?  Compiz-mate works good on my iBook with only leafpad having a few glitches when opened maximised (haven't figured out what that is all about yet).

@mrsavage:

Again, thanks for sharing these posts . . . as I mentioned before, lately I'm chasing a problem in my MBPro with spontaneous data erasure in LM13 MATE, with no feedback from the forum there, etc; so no time to test your stuff in PPC yet.  But I did spend a few hours yesterday using the LM forum post that you provided to upgrade XFCE from 4.8.3 to 4.10 . . . it's too early to know if it solved my problem, but it was interesting to take a look at the sources list for the first time.  As you said, it looks like a hotted up ubuntu system . . . and each of the items are "deb" files . . . so hotted up debian.  Anyway, nothing ventured nothing gained, I started looking at the "compiz" stuff, but was at work and ran out of time; it seemed like the links provided there did not work for some of those trying to get "compiz" working in LM13 . . . .  Still don't know what compiz is, but I want it just because . . . anyway, I know it's off the PPC topic, but it was through using your posts, very simple following the commands provided in the one link there.  [http://it-diary.com/tutorials/install-xfce-4-10-in-ubuntu-12-04-lts-precise-pangolin/](http://it-diary.com/tutorials/install-xfce-4-10-in-ubuntu-12-04-lts-precise-pangolin/) 

e.e.p.

---

### Post by woodoste on 2013-04-01
Hi, where I can download this fixed ISO? All links arounds various posts are dead...

Cheers

---

### Post by rsavage on 2013-04-02
Sample xorg.conf files (nothing revolutionary):

imacg3.txt [http://ubuntuone.com/1BWhzL7pCHjOL3TFDCb9xr](http://ubuntuone.com/1BWhzL7pCHjOL3TFDCb9xr)
nv.txt [http://ubuntuone.com/6loNPRkiKluH2ZOXt8HENV](http://ubuntuone.com/6loNPRkiKluH2ZOXt8HENV)
fbdev.txt [http://ubuntuone.com/5pcE1fStGPNhM4HsyeWzS8](http://ubuntuone.com/5pcE1fStGPNhM4HsyeWzS8)

---

### Post by rsavage on 2013-04-02
If you want a nice splash screen and you can't get plymouth to work then you can still use usplash:

[http://ubuntuone.com/55Cr6Y1imGrGmF1eRy5l5Q](http://ubuntuone.com/55Cr6Y1imGrGmF1eRy5l5Q)

---

### Post by este.el.paz on 2013-04-02
> **este.el.paz said:**
> @STovarisch:
You should probably download a "desktop" CD/DVD so that you could test it before installing, it looks like Lubuntu 12.04 for PPC would be the choice, if the Xubun 12.04 is only available as mini.iso.  You could always add the XFCE DE later on . . . .
e.e.p.

> woodoste 	 	 		[INDENT] 			 				Re: Testers needed for PowerPC 12.04
 			 			Hi, where I can download this fixed ISO? All links arounds various posts are dead...
Cheers 		
[/INDENT]
@woodoste:

Yes, that's the way it is around here . . . looks like you are SOL on the special Xubun .iso, so as Imentioned in post #288? best to pick either Lubun 12.04 for PPC if you want LTS . . . and then use the links to the various packages that rsavage is posting to put together a customized package, etc.

e.e.p.

---

### Post by str8bs on 2013-04-02
> **este.el.paz said:**
> 
@str8bs:  Homes, I already posted that link and same advice to Svetlana in post number 279 . . . .  You're late dude, where you been at? : - )
e.e.p.
Life duties outside of Linux. Hey Mongo. More read. Less type. :P

@rsavage - lots to play with. Thanks. Can't put my finger on why, but Mate has never been my cup of tea either.

[quote=woodoste]
Hi, where I can download this fixed ISO? All links arounds various posts are dead...[/quote]
[This thread]("http://ubuntuforums.org/showthread.php?t=2131644") iMac G4 or [this thread]("http://ubuntuforums.org/showthread.php?t=2131612") iMac G3 will net you about the same result I believe.

---

### Post by phillw on 2013-04-03
> **woodoste said:**
> Hi, where I can download this fixed ISO? All links arounds various posts are dead...

Cheers

I hold a mirror for most of the *buntu family at [http://phillw.net/isos/](http://phillw.net/isos/) which is usually a faster link than the 'main' ubuntu server :)

Regards,

Phill.

---

### Post by este.el.paz on 2013-04-03
> **phillw said:**
> I hold a mirror for most of the *buntu family at [http://phillw.net/isos/](http://phillw.net/isos/) which is usually a faster link than the 'main' ubuntu server :)

Regards,

Phill.

@philw:

Thanks for sharing that link, it is nice to see all the editions of the flavors listed in one place . . . I would say more, but people are complaining . . . .  : - )  Oh yeah, it's good to see the "G4 for Dummies" thread has been started . . . for those people that can face the facts of their dumminess, etc.  In the meanwhile I'm still continuing my testing of the Xu 12.04 .iso, but I have subscribed to the "Dummy" thread . . . and if a conversation develops there, like on a forum, I may offer a post . . . .  : - 0

e.e.p.

---

### Post by este.el.paz on 2013-04-26
et al:

This conversations seems to have slowed a bit, but . . . my testing/use of the Xu 12.04 system continues, overall it's fine, for my iBook it seems to run a tad better with the LXDE . . . DE, the main point of issue is the "revival from suspend" feature which I think I've mentioned before . . . is a wild card.  At least 50% of the time that I'm reviving from suspend I can get a screen to log in, log in, get a desktop, can see the browser tab in the toolbar, it shows I'm connected to internet, so things are happening . . . but when I click on the browser tab or email tab . . . nothing happens . . . the screen is there, but frozen . . . meaning the only option that I can think of is to shut the computer down and reboot thru the Yaboot process . . . and re log in . . . .  Sure, it's not the end of the world, but . . . seems like it could be better?  It did seem like this problem was happening less in LXDE than XFCE, but now it seems that LXDE has developed this . . . tic?  Bug?  

933MHz processor with about 646MB??? RAM

e.e.p.

---

### Post by este.el.paz on 2013-05-17
Folks/rsavage:

I'm replying to this thread . . . to myself or my last post in this thread, because this thread had dropped to page 4 and the problem as I described with the reviving from suspend issues . . . continues.  It is not a total failure to revive, I get the log in window, I can log in, the desktop is "populated" but clicking on tabs or on icons does nothing . . . only option at that point is to shut the unit down.  

This is the rsavge version of Xubuntu 12.04 for PPC on iBook 933 MHz with 640 RAM, and I added the LXDE DE, which brings a non-working Openbox.  I might have had Lu 12.04 loaded before, and probably the suspend issue was a problem there, in this version sometimes it works but many times it doesn't.  Any thoughts appreciated, perhaps removing the LXDE DE?

e.e.p.

---

### Post by este.el.paz on 2013-06-06
> **este.el.paz said:**
> Folks/rsavage:

I'm replying to this thread . . . to myself or my last post in this thread, because this thread had dropped to page 4 and the problem as I described with the reviving from suspend issues . . . continues.  It is not a total failure to revive, I get the log in window, I can log in, the desktop is "populated" but clicking on tabs or on icons does nothing . . . only option at that point is to shut the unit down.  

This is the rsavge version of Xubuntu 12.04 for PPC on iBook 933 MHz with 640 RAM, and I added the LXDE DE, which brings a non-working Openbox.  I might have had Lu 12.04 loaded before, and probably the suspend issue was a problem there, in this version sometimes it works but many times it doesn't.  Any thoughts appreciated, perhaps removing the LXDE DE?

e.e.p.

Et al:

Also posting over here, again replying to me, myself, and I . . . alone again . . . that still testing the rsavage edition of Xu 12.04, but using LXDE seems to allow for more consistent revive from suspend, I'm hoping it will continue.  Nothing was done on my end, except making the decision to move away from the Xubun cairo dock feature to the more spartan LXDE format, or perhaps a kernel or other update done recently has helped with this problem . . . .  Thanks to any who made this possible, no direct feedback or help was provided through the forum . . . .

e.e.p.

---

### Post by vintagecoke on 2013-06-07
I'll have a go on my PowerMac G5 tonight...

---

### Post by este.el.paz on 2013-06-07
> **vintagecoke said:**
> I'll have a go on my PowerMac G5 tonight...

vc:

Have fun with it, try to read through rsavages "G4 for Dummies thread" . . . even if you aren't a dummy, it may provide some time saving hints.  I'm not sure, but I don't think there is a "G5 for Dummies" thread, I think the G5 is in the same ballpark as the G4 . . . but from what I've seen people report here, there can be some stumbling with the G5 install????  Read first, cut once, or something like that.

e.e.p.

---

### Post by vintagecoke on 2013-06-07
The G5 is much different from the G4.

---

### Post by phillw on 2013-06-09
> **este.el.paz said:**
> Folks/rsavage:

I'm replying to this thread . . . to myself or my last post in this thread, because this thread had dropped to page 4 and the problem as I described with the reviving from suspend issues . . . continues.  It is not a total failure to revive, I get the log in window, I can log in, the desktop is "populated" but clicking on tabs or on icons does nothing . . . only option at that point is to shut the unit down.  

This is the rsavge version of Xubuntu 12.04 for PPC on iBook 933 MHz with 640 RAM, and I added the LXDE DE, which brings a non-working Openbox.  I might have had Lu 12.04 loaded before, and probably the suspend issue was a problem there, in this version sometimes it works but many times it doesn't.  Any thoughts appreciated, perhaps removing the LXDE DE?

e.e.p.

Hi,

I'm sorry that you are not getting replies. We have very few PPC testers in lubuntu and kubuntu. I'd recommend anyone interested in PPC testing to join the lubuntu-quality team where we do have a PPC section. We also liased with kubuntu last cycle to get things tested, the PPC testers want PPC and are quite happy to help out on both lubuntu and kubuntu to get working versions out.

Lubuntu-quality can be found at [https://launchpad.net/~lubuntu-qa](https://launchpad.net/~lubuntu-qa) 

Regards,

Phill.

---

### Post by este.el.paz on 2013-06-09
> **phillw said:**
> Hi,

I'm sorry that you are not getting replies. We have very few PPC testers in lubuntu and kubuntu. I'd recommend anyone interested in PPC testing to join the lubuntu-quality team where we do have a PPC section. We also liased with kubuntu last cycle to get things tested, the PPC testers want PPC and are quite happy to help out on both lubuntu and kubuntu to get working versions out.

Lubuntu-quality can be found at [https://launchpad.net/~lubuntu-qa](https://launchpad.net/~lubuntu-qa) 

Regards,

Phill.

@phill:

OK mr phil, thanks for a response to that post from awhile back and for posting this qa link again . . . .  I have tried to do something with that info before, but there was something about it that is time intensive to register the computer, and generally I'm busy.  On one of your threads, the "Testers wanted for 13.04" I believe I posted my findings from my iBook there . . . and I don't recall, but I don't think anyone got back to me there either about it . . . so I wasn't encouraged to spend more time on it.  I do try to support efforts to keep PPC development going by trying to post whatever I can offer to those trying to get something going on their PPC units; and thanks for your personal efforts to do that, as well as to reply to my prior post . . . .

e.e.p.

---

### Post by phillw on 2013-06-09
The mailing list for that group simply pre-fixes the subject title as [PPC], which allows the none PPC users to view if they are interested and flag up to the PPC users that there is a new email. From what you have said on delays / non replies, I think that you, and others, would find that email area a better way to keep in touch with the current release and the development release.

Regards,

Phill.

---

### Post by Dukenukemx on 2013-06-12
Anyone got flash working on their G4 Macs?  I have my laptop working with 12.04 and installed gnash but youtube videos just show black.

---

### Post by michiganmac on 2013-06-12
> **Dukenukemx said:**
> Anyone got flash working on their G4 Macs?  I have my laptop working with 12.04 and installed gnash but youtube videos just show black.

There is no FLASH for PPC linux. None. Even if you go to Adobe's website and see a version for Linux, it will not work on our PPC's.

However, there are add-ons to Firefox which allow viewing of FLASH videos on YouTube. 

Please don't shoot the messenger.;)

---

### Post by Dukenukemx on 2013-06-13
No yea I installed Gnash and Lightspark.  I think I have Gnash 8.10 installed.  Otherwise it would say I need a plugin for that.

---

### Post by este.el.paz on 2013-06-13
> **phillw said:**
> The mailing list for that group simply pre-fixes the subject title as [PPC], which allows the none PPC users to view if they are interested and flag up to the PPC users that there is a new email. From what you have said on delays / non replies, I think that you, and others, would find that email area a better way to keep in touch with the current release and the development release.
Regards,
Phill.

@philw:

I spent the few free minutes I have looking at the "qa" link . . . and that appears to be the area where you can register for Lubunteerism and the bonus package of membership to an email list serve??  And that area is distinct from the "Apple users" Forum, or, any of the Forum?  Or, are you saying that if the "[PPC]" label is attached to a forum post, that post will be "forwarded" or sent to the QA list serve and will therefore get more heightened attention back on the forum?  So far, I don't have too much spare time to become a "Lubunteer" . . . whatever that might be, seems to smack of "mouseketeer" . . . for those of us who are over 50 and live in SoCal that image is quite frightening . . . .  : - 0

So, it might be easy enough to sign up for the list serve, but so far my involvement has been in the forum, which has been a mixed bag . . . sometimes if one is lucky some high level data might be shared, but mostly it seems to be kicking the can around . . . and then sometimes when you try to help someone your posts get banned . . . for the ultimate sin of speaking "sarcasm about the foibles of Linux" . . . sending newbies to other sources of help, etc--it doesn't seem very "forum" like at times.  

But, as a relative newbie in the Linux world myself, (my one computer class in the 70's also had the IBM punch card with the phone-set modem, and I concluded it wasn't going to survive in the cold hard consumer driven world) the main help I can do is tips for installation of dual boot systems in PPC . . . if the QA list serve links back to the Forum then perhaps I am interested . . . .

e.e.p.

---

### Post by este.el.paz on 2013-06-29
Gents:

Nobody has posted here for awhile, but my testing of 12.04 is continuing . . . things were going well on the "revive from suspend" front for awhile so I was lulled into thinking that the problem was fixed . . . and then it started happening again, perhaps with the upgrade to the 3.2.0-48-powerpc-smp kernel??  Just to test further I tried to use the "tab" key on the second Yaboot log in and there was just "Linux         old" . . . listed, so I typed in "Linux old" . . . and logged in . . . went thru a few revive from suspend cycles and all was well until yesterday . . . had to shut the computer down because clicking on stuff didn't do anything.  On restart I checked "uname -r" and it was the same as when I did "Linux old" . . . -48 . . . .  I checked in the /boot  folder and I see there are a number of choices, the closest number is 3.2.0-45-powerpc-smp . . . is there any way I can select that earlier kernel and see if that gets me back to where I had pretty consistent revive from suspend?

Thanks, 

e.e.p.

---

### Post by rkmugen on 2013-06-29
At the risk of (me) sounding dumb, I wonder if you could use the "Force Version" feature in Synaptic...  I remember using that a while back when I had two versions of MESA-related files installed (7.x and 8.x) at the same time and wanting to use 7.x.

---

### Post by este.el.paz on 2013-06-30
> **rkmugen said:**
> At the risk of (me) sounding dumb, I wonder if you could use the "Force Version" feature in Synaptic...  I remember using that a while back when I had two versions of MESA-related files installed (7.x and 8.x) at the same time and wanting to use 7.x.


@rkmugen:

Thanks for the post . . . I don't know enough to know if that's a dumb idea or not, but at least you posted a reply and for that I appreciate it.  I spent a few minutes yesterday Googling my question and it seems like it would take some playing around on the console to get the older kernels to show up when "tab" is pressed . . . it would be easier to fiddle with Synaptic . . . .  Of course there is always a newer kernel coming, but would it pick up the "revive from suspend" issue I've been mentioning here for quite awhile????  probably not.  Anyway, I'll continue my testing . . . appreciate the thoughts.  : - ))

e.e.p.

[Update: Doesn't seem like this idea is panning out, I ran a Synaptic search of "vmlinux-3.2.0-45-powerpc-smp" and that runs and it shows up in the left side column, but doesn't show in the right side at all . . . so that side is empty and when I click on the "Packages" tab it's all greyed out, so the "Force Version" is not available??  It's probably not worth messing with, e.g., if I could force the old kernel to be installed I'd probably have to deal with other issues around dependencies, etc.  Kind of ashame but seems typical, everything is more or less OK, but having to shut down the computer each time I want to revive from sleep . . . makes it hard to continue using it--so I'm trapped between the no longer supported browsers of 10.4.11, or, closer to the wave of time's Linux browsers, but more or less needing to shut down and cold boot each time, etc]

---

### Post by xeno74 on 2013-07-10
Hi,

Thank you very much indeed for Ubuntu 12.04.2 LTS PowerPC. It runs very very very well on my [AmigaONE X1000]("http://en.wikipedia.org/wiki/AmigaOne_X1000"). :) :)

Screenshots:

[IMG]http://www.supertuxkart-amiga.de/amiga/lubuntu1204-x1000.jpg[/IMG]

[IMG]http://www.supertuxkart.de/stk08-lubuntu-x1000.jpg[/IMG]

Here are the installations instructions for Lubuntu 12.04.2 (based on A-EON Linux manual Version 2.5.1.4
):

The installation instructions cover installing Lubuntu 12.04.2 LTS from a &#8220;netboot over the internet&#8221; installation from a single install image.


[LIST=1]
[*]Download and extract the kernel image and modules, vmlinux-3.9.0-2 and 3.9.0X1000

Downloads:

[kernel-3.9.0-2-x1000.tar.gz]("http://www.xenosoft.de/kernel-3.9.0-2-x1000.tar.gz") 
[*]Download the Ubuntu ramdisk image (initrd.gz) from:

[http://ports.ubuntu.com/ubuntu-ports/dists/precise/main/installer-powerpc/current/images/powerpc64/netboot/initrd.gz](http://ports.ubuntu.com/ubuntu-ports/dists/precise/main/installer-powerpc/current/images/powerpc64/netboot/initrd.gz)

and copy it to the USB Stick 
[*]Turn on the AmigaONE X1000 and press F to boot to enter CFE prompt. Insert the USB stick. 
[*]You can boot the installer using the commands below
```

CFE> ramdisk &#8211;z &#8211;addr=0x24000000 &#8211;fatfs usbdisk0:initrd.gz
CFE> setenv bootargs "root=/dev/ramdisk"
CFE> boot -elf -noints -fatfs usbdisk0:vmlinux-3.9.0-2

``` 
[*]Select Language 
[*]Select Your Location 
[*]Detect Keyboard Layout. Select No and Pick from the list 
[*]Configure Network 
[*]Enter Hostname 
[*]Select the Ubuntu Archive Mirror Country - [it is configured for the UK] 
[*]Leave the HTTP Proxy parameter blank and press return &#8211; [there will now be a long delay] 
[*]When prompted that no kernel modules were found select Yes to continue without loading them. 
[*]The installer components will be retrieved from the Ubuntu mirror [this will take a long time] 
[*]Enter your Full Name 
[*]Enter your username for your account 
[*]Enter your password and confirm 
[*]Select No to Encrypt your home directory 
[*]Confirm your time zone 
[*]When prompted for module dm-mod leave the parameter blank and select continue 
[*]Click Continue at the warning of &#8220;Software RAID not available&#8221; 
[*]Click Continue at the warning of &#8220;Logical Volume Manager not available&#8221; 
[*]You can now partition your disk.
**You must exercise caution when modifying your partition tables!** 
[*]The base system will now be retrieved from the mirror site and installed 
[*]Select &#8220;Install security updates automatically&#8221; 
[*]At the software selection screen you will be asked to select which *buntu flavour(s) you would
like to install. You can install as many as you like. To install Lubuntu arrow down to the &#8220;Ubuntu with LXDE Desktop&#8221; option and press the space bar to mark the
option. Now press return to continue. 
[*]The additional packages required to install the full desktop will be retrieved and
installed. - [this will take some time to complete depending on the speed of your internet connection ] 
[*]At &#8220;Continue without boot loader&#8221; take note of your root partition. 
[*]Select Yes to set confirm the system clock is set as UTC. 
[*]Select Continue to finish the installation and reboot!
Booting Ubuntu 12.04
Press F to boot to enter CFE prompt. Remove if necessary and re-insert the USB stick containing
the vmlinux-3.9.0-2 kernel and associated modules.
Enter the following commands replacing the root partition (sdb9) with the ID of the partition where
you installed Lubuntu
> 
CFE> setenv bootargs "root=/dev/sdb9"
CFE> boot -elf -noints -fatfs usbdisk0:vmlinux-3.9.0-2

You will see the following warning during boot:
&#8220;Init: Failed to create pty &#8211; disabling logging for job&#8221;
Note: This warning message will be repeated many times and is a bug on Ubuntu systems that do
not use an initramfs during boot. However it is nothing to worry about as the problem will 'correct
itself' later in the boot process.
Copying the kernel modules
Log into the Desktop and open a terminal window. 
Type ls /media and press return to view the mounted USB stick directory.
Assuming it is mounted as usbstick type the following command to copy the modules to the
/lib/modules directory.
sudo cp -rv /media/usbstick/3.9.0X1000 /lib/modules and press return
Enter your password and press return again.Type sudo shutdown &#8211;r now and press the return key to
reboot the system again. 
[/LIST]

---

### Post by este.el.paz on 2013-08-20
@rsavage & str8bs, et al:

Haven't seen too much activity on this thread for awhile . . . but, my testing is still continuing on my iBook and I think I may have found a solution to my "revive from suspend" failures . . . a little bit cumbersome, but better than switching to TTY and rebooting the system.  I'm finding that if I log out with the various windows, browser, email, etc . . . open, and then "suspend" from the log in window, that when I "revive" and log in, the windows will re-load, the browser will ask me if I want to "restore" the session, etc . . . and things are back to the way they were.  It's a little bit more time consuming, but if I just click "suspend" from the desktop it seems like every other time the desktop image loads, but clicking on stuff . . . as I've mentioned, does nothing and a reboot is the only option.  Possibly this has been mentioned in other threads, but not here, so I'm adding my hard gained insights into the public record, here . . . .

And, so the lonely testing continues . . . .

e.e.p.

---

### Post by frank18 on 2013-08-29
> **AnsonX10 said:**
> I've got this PowerBook G4 2002 TiBook, and finally got Ubuntu running on it. (I'm writing this on it right now.) Then I found this thread, and thought I'd post some info.

It's running 12.04 with all the updates as of right now. 

The Live CD couldn't make the HFS drive a bootstrap/yaboot compatible drive or something like that, the alternative CD could though, and did. I used dd on a PowerMac G4 running Leopard to write the ISOs to a 1gb USB drive, and booted the laptop off of that.

All versions 10 would not show anything on screen upon booting from the USB, save for a few lines.

The mini CD for 11 couldn't make the internal drive boot without help, but That was almost a week ago that I last tried that.

The reason I tried installing Ubuntu on this thing is because the Mac OS 10.5 system it had on it had terrible graphical glitches, to the point that you couldn't see anything. I had fixed it once by installing the system anew, but the disc drive doesn't work anymore. I thought it must be the logic board had gone out, but I wasn't sure. So when I found out that Ubuntu 12 fixed everything, I knew it must've been the system.

Bugs: 
The sound is not working right now, after I installed updates, but was working fine right after system install. I had/have to press fn with the volume buttons for them to work. However, the microphone level meter shows input when I'm yelling at the computer for not playing music. (lol) So the speakers and headphone output aren't working, but the microphone and sound input is. 
EDIT: Nevermind that. (look down for info)

The simulated right click isn't working now either after updates. Ctrl click doesn't even work on an i386 pc. So, being deprived of my spell checking abilities, there may be some typos in this post.
EDIT: Nevermind this too.

The display works great when the system is giving it a signal, without any glitches whatsoever. But when the screen isn't getting any signal, the backlight and power stay on, but the picture gets buggy like a cheap LCD screen when it's turned off. (The picture slowly fades away, but a lot more slowly than it usually does.) 

The screen also gives this response a few times during booting, but I find that almost natural. BUT when I change to a resolution other than the native (1280 by 854) it's the same thing. No signal. Luckily the timeout returned the screen to the previous resolution, restoring the picture without any further problems. 

I haven't tried rotation yet because I want to get this posted before risking it.
EDIT: I tried rotation, and strangely it gives me graphical glitches amazingly similar to the ones I had on Mac OS X before I wiped it and installed Ubuntu 12.04. It does this at all three non-normal settings. I can see enough to click the restore button, which brings back the crystal clear picture I've come to know and love from Ubuntu on this computer.

The brightness buttons don't work, but I believe someone else mentioned that.

The battery works when I unplug the laptop, but doesn't seem to have any settings or indicators anywhere. However it wasn't in the computer when I installed the system, nor for the first boot, so that may be my fault.

The system runs a lot hotter than Mac OS X did, but both fans work, which is more than OS X did most of the time. I'm not worried about this though. Taking the keyboard off and touching the heat sinks and metal covers is more painful than it was with OS X, but that's the only way I'd know it was running hotter. OS X probably should have been running like this. There are temp warnings in there after all.

The keyboard's num lock doesn't work, but this may not be a bug.

Pressing f11 doesn't work to make anything fullscreen, it seems to cut and move text around. This is probably a result of my own ignorance though. 

My "u" key keeps falling off. (The worst bug. FIX THIS NOW!) lol

Other than that everything seems to be working fine. As much as a community supported pre-released operating system should be anyway. Slight software incompatibilities, but I don't consider those bugs yet.

PS I accidentally just hit f12 and realized that it made a right click! I knew f12 was supposed to do that, but never had any luck with other computers. but I'm not going to go back and spell check everything because I'm feeling lazy. That and I have other more vital stuff to do. So maybe that means I'm feeling more diligent. lol

EDIT: I forgot to mention that this PowerBook doesn't have an AirPort card in it, so I can't say anything about that. But it does work with a Belkin USB Wireless antenna (F5D7050) that all Ubuntu versions have worked with since 7.10 (when I started using it.)

Also, a few more updates and a restart, sound seems to be working again. A few pops and such when starting audio, but it did that before as well. I have a feeling this one may have been my fault.

Simulated right clicking is working again as well.

I'm happy.

Hi .where did you get your mini Iso of Ubuntu 12.04? i 've tryed to install Ubuntu 12.4 12.10 ,13.04 with no success i would not pass the terminal so no desktop never,so iwent to Debian 7.Wheezy mini Iso and it installed right up but the thing i can have wireless ,no flas to runn uTUBE AND SEEMS SLOW dispite i upgraded to 1.4GB mem ram, maybe ubuntu will run better! thanks

---

### Post by phillw on 2013-08-29
Hi,

I'll make an official announcement next week about 13.10, but [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1066435](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1066435) now appears squished in the recent daily builds of PPC for 13.10. Beta 1 testing starts next week and I will be calling for volunteers. If you'd like to dip your toe in the water to see how it fares on your systems (or can't bear to wait until next week!) , head over to [http://iso.qa.ubuntu.com/qatracker/milestones/270/builds](http://iso.qa.ubuntu.com/qatracker/milestones/270/builds) and grab one :)

Regards,

Phill.

---

### Post by phillw on 2013-08-29
[QUOTE=....

And, so the lonely testing continues . . . .

e.e.p.[/QUOTE]

Hi,

PPC testing in lubuntu is carried out via the mailing list as people are scattered on different TZ's. [https://launchpad.net/~lubuntu-qa](https://launchpad.net/~lubuntu-qa) will allow you to join that mailing list and read the archives. PPC related things have the subject prefix [PPC] so that people can quickly see if a mail is relevant to them, or not. You are not alone in testing PPC and are more than welcome to join. As per my earlier thread, I will be making an announcement early next week as to where we are up to in readiness for the Beta1 testing. (I have to check with kubuntu as to if they need testers as well etc.) The lubuntu wiki area for PPC is at [https://wiki.ubuntu.com/Lubuntu/Testing/PPC%26Mac64](https://wiki.ubuntu.com/Lubuntu/Testing/PPC%26Mac64) I liase with kubuntu on the quality IRC channel so that we both know where we're upto :)

Regards,

Phill.

---

### Post by kinetonat on 2013-09-01
.

---

### Post by este.el.paz on 2013-11-01
@rsavage, et al:

Haven't gotten any notifications on this thread lately, but I'm very excited to announce that after a long period of undiagnosed kernel panicing I finally took the iLamp into a professional repair shop . . . and they found a bad RAM stick.  Since the problem turned out to be relatively simple I've had them boost the RAM to the maximum . . . 1GB!!!!  So, the G4 lives on . . . and my testing of 12.0.4 continues!!!  It looks like there are "303 updates available" from when I last tried to update as a way to escape the constant crashing . . . .  I'll be checking to see if the increased RAM will let the OSX partition upgrade to Leopard . . . so far using Leopard Assist has not fooled the installer . . . .

It's just interesting that the problem that was crippling the computer after 15 mins was not found in multiple tests of the RAM . . . of course the Apple Hardware Test is worth what I paid, but the Applejack test of the RAM was rather extensive . . . but failed to find a problem.  My personal ersatz testing seemed to point to the FW port as the problem . . . which is why I turned to the professionals.

Anyway . . . the exploration of 12.0.4 continues . . . .

e.e.p.

---

### Post by rsavage on 2013-11-05
eep, good to hear you fixed it!

---

### Post by este.el.paz on 2013-11-05
> **rsavage said:**
> eep, good to hear you fixed it!

rs:

Thanks for the post back.  Yeah, I'm glad to have the use of it again; still, since I posted there remains some "issues" on both partitions.  I'm planning to do a re-install of your 12.04 system, I had done my own retro nv driver install . . . but there's still a problem with "suspend" so when I get a free moment I'm going to your version of Xubuntu and see if that makes any difference . . . I've got the full 1GB RAM now so it should have a btter chance to do "suspend" . . . .

e.e.p.

---

### Post by rsavage on 2013-11-06
I don't know whether you can get suspend working on nvidia computers... have a look at the section in the FAQ.  Have you ever had it working on your iMac?

---

### Post by abtabt on 2013-11-06
> **este.el.paz said:**
> rs:

Thanks for the post back.  Yeah, I'm glad to have the use of it again; still, since I posted there remains some "issues" on both partitions.  I'm planning to do a re-install of your 12.04 system, I had done my own retro nv driver install . . . but there's still a problem with "suspend" so when I get a free moment I'm going to your version of Xubuntu and see if that makes any difference . . . I've got the full 1GB RAM now so it should have a btter chance to do "suspend" . . . .

e.e.p.

good to see you back with a upgraded mac 

i have used the live USB  for Lubuntu  12.04 and  13.04 and for me suspend works  (with usb 1.1 take some time to load but this is one way to test )  only do " dd " then you can testing  , no defekt/burning DVD/CD etc

but i use now  Lubuntu 13.04    persistent  (and this is the best , its easy to test and change things like yaboot and install program etc and its still there after a reboot )

but this need some more steps to get on a usb/hd/firewire 

its moore to say butt .....

---

### Post by este.el.paz on 2013-11-06
> **rsavage said:**
> I don't know whether you can get suspend working on nvidia computers... have a look at the section in the FAQ.  Have you ever had it working on your iMac?

@rsavage:

Alrighty, thanks for the follow-up, good question on the nvidia . . . it's been so long since anything has been working that I can't remember . . . .  I was thinking that ****maybe**** one of the mintppc versions had suspend, but even that is a question mark, since the computer started crashing around that time.  Using your CD does provide Suspend on my iBook . . . which has around 6xxMB of RAM . . . but w/o checking I think it isn't the nvidia card . . . .  Since there are now other issues cropping up on the iMac I'm not instantly going to make any Linux changes just yet; now the only time there are KPs is when waking from OSX sleep, and after that the computer seems to run fine.

@abtabt:

Thanks also for your post, I was going to check with you since I know we have about the same machine, I think I did test the 13.04 when Philw posted something about it . . . but . . . I like the LTS aspect of 12.04 rather than needing to change the system every year or whatever.  In the iBook the 12.04 has been fine and handles the upgrades without imploding on itself as we remember other versions having done . . . .

e.e.p.

---

### Post by este.el.paz on 2014-03-19
@rsavage:

Tried a search of the forum for any sign of the next incarnation of 'buntu for LTS in PPC, but nothing seemed to be relevant.  
So, that is the question, will the next LTS version be ported to a PPC friendly system?  I don't know if I'd bother to try to get it running on my iMac . . . unless an nv driver is available . . . .  But for the iBook with a radeon card it seems to be easier to get it going without too much consternation . . . .  Would that be a Lubuntu or Xu version and is that slated for July '14?

e.e.p.

---

### Post by phillw on 2014-03-19
> **este.el.paz said:**
> @rsavage:

Tried a search of the forum for any sign of the next incarnation of 'buntu for LTS in PPC, but nothing seemed to be relevant.  
So, that is the question, will the next LTS version be ported to a PPC friendly system?  I don't know if I'd bother to try to get it running on my iMac . . . unless an nv driver is available . . . .  But for the iBook with a radeon card it seems to be easier to get it going without too much consternation . . . .  Would that be a Lubuntu or Xu version and is that slated for July '14?

e.e.p.

Hi, 14.04 will be PPC and will be LTS **provided **it is tested :)

Head over to [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing) for details on testing lubuntu and a link to the PPC area.

Regards,

Phill.

---

### Post by este.el.paz on 2014-03-19
> **phillw said:**
> Hi, 14.04 will be PPC and will be LTS **provided **it is tested :)

Head over to [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing) for details on testing lubuntu and a link to the PPC area.

Regards,

Phill.

@Philw:

Thanks for the fast reply . . . I will endeavor to check it out, although I recall from the 13. 04 or .1 testing that it is a tad "involved" for those of us running on hyperdrive time wise . . . .  But, I can definitely try to download/burn the .iso and test it out for ease of boot up/run on both my iMac & iBook in the coming weeks.  Is there a "Testers wanted for 14.04 LTS PPC" thread going?

e.e.p.

---

### Post by phillw on 2014-03-19
This thread seems to have always been used as a rallying call for troops ever since we took on the mantle of PPC at lubuntu :) It has some good discussions that (new) people can review to get a better feel and linkage to other areas for FAQ's. I'm subscribed to this thread, so get a poke in my email in-box each time there is a new posting :)

Regards,

Phill.

---

### Post by rsavage on 2014-03-20
@ phil

Thanks for the info.  I had posted the same question as eep to the lubuntu-qa mailing list, but it seemed to have got gobbled by some spam filter.  I also wanted to advertise my sound thread [http://ubuntuforums.org/showthread.php?t=2209340](http://ubuntuforums.org/showthread.php?t=2209340) to the lubuntu-qa testers.  

Do you still have the ear of Colin Watson?  We need some patches going in for sound, but I'm loathed to make the effort and write them if they are just going to sit there and be unused.  They involve the debian-installer, casper and linux kernel packages.  The kernel one is the very important one, otherwise a certain section of users will have to mess around compiling kernel modules to get their sound working.  But, that also involves users testing 14.04!

---

### Post by phillw on 2014-03-20
I no longer have any contact with the release team what so ever. jsalsbury from the kernel team came across as a helpful soul when I last had an issue that needed the involvement of the kernel team. He may offer you advice / sponsorship to have said bugs addressed. 

Regards,

Phill.

---

### Post by xeno74 on 2014-03-21
> **phillw said:**
> Hi, 14.04 will be PPC and will be LTS **provided **it is tested :)

Head over to [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing) for details on testing lubuntu and a link to the PPC area.

Regards,

Phill.

[ATTACH=CONFIG]251357[/ATTACH]    [ATTACH=CONFIG]251358[/ATTACH]

Hi All,

The NG Amiga users test a lot the development branch of Lubuntu 14.04 PowerPC. And it works very well on the Sams PowerPC and AmigaOne X1000 PowerPC machines.

[http://forum.hyperion-entertainment.biz/viewtopic.php?f=52&t=2177&start=30](http://forum.hyperion-entertainment.biz/viewtopic.php?f=52&t=2177&start=30)

[http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2176](http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2176)

Screenshots:

[http://www.supertuxkart-amiga.de/amiga/Lubuntu_14.04_kernel_3.13_A1-X1000.jpg](http://www.supertuxkart-amiga.de/amiga/Lubuntu_14.04_kernel_3.13_A1-X1000.jpg) (Lubuntu 14.04 on an AmigaOne X1000 with the kernel 3.13.0)
[http://forum.hyperion-entertainment.biz/download/file.php?id=807](http://forum.hyperion-entertainment.biz/download/file.php?id=807) (Lubuntu 14.04 on an AmigaOne X1000 with the unofficial Mesa 10.0.3 and kernel 3.14-rc4)
[http://forum.hyperion-entertainment.biz/download/file.php?id=857](http://forum.hyperion-entertainment.biz/download/file.php?id=857) (Lubuntu 14.04 on an AmigaOne X1000 with the unofficial Mesa 10.1.0 and kernel 3.14-rc6)
[http://forum.hyperion-entertainment.biz/download/file.php?id=858](http://forum.hyperion-entertainment.biz/download/file.php?id=858) (Lubuntu 14.04 on an AmigaOne X1000)
[http://forum.hyperion-entertainment.biz/download/file.php?id=688](http://forum.hyperion-entertainment.biz/download/file.php?id=688) (Lubuntu 14.04 on an AmigaOne X1000 with the kernel 3.13-rc8)
[http://forum.hyperion-entertainment.biz/download/file.php?id=751](http://forum.hyperion-entertainment.biz/download/file.php?id=751) (Lubuntu 14.04 on an AmigaOne X1000 with the kernel 3.13.1)
[http://forum.hyperion-entertainment.biz/download/file.php?id=679](http://forum.hyperion-entertainment.biz/download/file.php?id=679) (Lubuntu 14.04 on an AmigaOne X1000 with the wrong colors issue)
[http://forum.hyperion-entertainment.biz/download/file.php?id=763](http://forum.hyperion-entertainment.biz/download/file.php?id=763) (Lubuntu 14.04 on a Sam440ep Flex with the kernel 3.14-rc1)
[http://forum.hyperion-entertainment.biz/download/file.php?id=754](http://forum.hyperion-entertainment.biz/download/file.php?id=754) (Lubuntu 14.04 on a Sam440ep Flex with MPlayer and the kernel 3.13.1)
[http://forum.hyperion-entertainment.biz/download/file.php?id=712](http://forum.hyperion-entertainment.biz/download/file.php?id=712) (Lubuntu 14.04 on a Sam440ep Flex with the kernel 3.13.0)
[http://forum.hyperion-entertainment.biz/download/file.php?id=875](http://forum.hyperion-entertainment.biz/download/file.php?id=875) (Lubuntu 14.04 on a Sam440ep Flex with the kernel 3.14-rc7)
[http://forum.hyperion-entertainment.biz/download/file.php?id=801](http://forum.hyperion-entertainment.biz/download/file.php?id=801) (Lubuntu 14.04 on a Sam460ex with kernel 3.14-rc4)


But there are two main issues. Mesa issued false colors in games. They appear to be ABGR instead of RGBA, thus blue becomes green, red becomes alpha etc. I've created a bug report on freedesktop.org. Bug report 72877: [https://bugs.freedesktop.org/show_bug.cgi?id=72877](https://bugs.freedesktop.org/show_bug.cgi?id=72877) and [http://lists.freedesktop.org/archives/mesa-dev/2013-December/050363.html](http://lists.freedesktop.org/archives/mesa-dev/2013-December/050363.html). I also created a bug report on bugs.launchpad.net. Bug report #1275042: [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1275042](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1275042). Additional I have posted the bug on the Mesa dev mailing list: [http://lists.freedesktop.org/archives/mesa-dev/2014-March/055510.html](http://lists.freedesktop.org/archives/mesa-dev/2014-March/055510.html). I have figured out what the problem is and I have fixed the problem in the MesaLib source code. More on [http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2137#p23996](http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2137#p23996). I have released some unofficial Mesa packages. Downloads: [http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html](http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html).

The x server has not been configured automatically on Lubuntu 14.04. You have to create manually a **xorg.conf** file. For  example my xorg.conf file as attachement. I had the problem that the  fonts were not displayed. The solution is to set the option "**RenderAccel**" to "**false**" in the xorg.conf file.

My xorg.conf file: [http://forum.hyperion-entertainment.biz/download/file.php?id=711](http://forum.hyperion-entertainment.biz/download/file.php?id=711)

We test Lubuntu 14.04 with some vanilla kernels and ported Ubuntu kernels. Kernels: [http://www.supertuxkart-amiga.de/amiga/x1000.html#downloads](http://www.supertuxkart-amiga.de/amiga/x1000.html#downloads) and [http://www.supertuxkart-amiga.de/amiga/sam.html#downloads](http://www.supertuxkart-amiga.de/amiga/sam.html#downloads). For OpenGL and sound tests we use a special AltiVec version of SuperTuxKart 0.8.1. There is also a SuperTuxKart 0.8.1 without AltiVec available. We have created some bug reports on bugs.launchpad.net.

Thank you very much to the developers of Lubuntu 14.04 PowerPC. You're doing a great job.

Rgds,
Christian

---

### Post by este.el.paz on 2014-03-31
Gents:

Since the conversation seems to have moved on to 14.04 here, I'll post my ersatz testing of a Lubun daily build on my G4 iBook & iMac here.  I sent this to the Lubun mailing list, but that was like the sound of one hand clapping . . . .  Portions of that email pasted below:

I burned the daily build from today 3/28/14 of Lu 14.04 .  . . and it booted up OK in the iBook, we got the 14.04 splash screen,  it showed a "b43 error" for the wifi, got the mouse, and a desktop with  the toolbars.  Only problem is/was desktop image was grainy  resolution--when I tried to change the desktop image all of them were  low resolution.  I opened Xterm and the window was fine and I ran  "lsmod"--no "radeon" & certainly no "nv" showed there.  The system  time was wrong so I wanted to set that before I opened my webmail, when I  launched the "Time and Date settings" app there was just the frame with  "Time and Date" across the top, and showing the Xterm data inside it.   "User settings" was the same--empty frame; but "customize look and feel"  was OK.  Synaptic had the frame problem, but Firefox did not, the  window showed the web stuff and I got to a Ubuntu page.

This morning I tried to boot the system in my iMac, first  using live video=ofonly and got the 1/3 green and 2/3 black screen; and I  rebooted and pressed tab and entered the same but added something like  "driverupdatesppc" and something "check powerpc" and got a thin sliver  of purple and the rest black . . . .  This problem is well known to guys  like "rsavage" and others working with the iMac, and there are some  terms like "forcenv" that I have buried somewhere in notes from a year  ago when I was trying to get the system running on the iMac, but no  time.  

The 800MHz G4 iMac runs best on the "nv" driver for the Nvidia card,  it doesn't seem to "run right out of the box" as is claimed, second  best is the what "fb" driver?  I heard that the nv driver is no longer  available to "retro-install" as I had to do with my 12.04 install; I'm  thinking it might not run 14.04.

But, on the positive side, yes, the iBook with radeon driver  ran pretty well on the Live DVD just hitting "return" and letting it do  its thing.  Only problem seems to be that some windows are not being  rendered and others are.  But, still overall the font rendering was a  tad rough, I guess I usually adjust that in preferences . . . which did  render OK in its window.

OK, that's my "report" on my experience with a daily build, as  Al or someone said, "It's not quite ready."  If there is something I  can run in this build again for someone I can do that, but, time is  limited; yesterday I was somewhere where the .iso could be downloaded in  8 mins, whereas at home that would take an hour, etc.

e.e.p.

---

### Post by frank18 on 2014-03-31
> **este.el.paz said:**
> Gents:

Since the conversation seems to have moved on to 14.04 here, I'll post my ersatz testing of a Lubun daily build on my G4 iBook & iMac here.  I sent this to the Lubun mailing list, but that was like the sound of one hand clapping . . . .  Portions of that email pasted below:

I burned the daily build from today 3/28/14 of Lu 14.04 .  . . and it booted up OK in the iBook, we got the 14.04 splash screen,  it showed a "b43 error" for the wifi, got the mouse, and a desktop with  the toolbars.  Only problem is/was desktop image was grainy  resolution--when I tried to change the desktop image all of them were  low resolution.  I opened Xterm and the window was fine and I ran  "lsmod"--no "radeon" & certainly no "nv" showed there.  The system  time was wrong so I wanted to set that before I opened my webmail, when I  launched the "Time and Date settings" app there was just the frame with  "Time and Date" across the top, and showing the Xterm data inside it.   "User settings" was the same--empty frame; but "customize look and feel"  was OK.  Synaptic had the frame problem, but Firefox did not, the  window showed the web stuff and I got to a Ubuntu page.

This morning I tried to boot the system in my iMac, first  using live video=ofonly and got the 1/3 green and 2/3 black screen; and I  rebooted and pressed tab and entered the same but added something like  "driverupdatesppc" and something "check powerpc" and got a thin sliver  of purple and the rest black . . . .  This problem is well known to guys  like "rsavage" and others working with the iMac, and there are some  terms like "forcenv" that I have buried somewhere in notes from a year  ago when I was trying to get the system running on the iMac, but no  time.  

The 800MHz G4 iMac runs best on the "nv" driver for the Nvidia card,  it doesn't seem to "run right out of the box" as is claimed, second  best is the what "fb" driver?  I heard that the nv driver is no longer  available to "retro-install" as I had to do with my 12.04 install; I'm  thinking it might not run 14.04.

But, on the positive side, yes, the iBook with radeon driver  ran pretty well on the Live DVD just hitting "return" and letting it do  its thing.  Only problem seems to be that some windows are not being  rendered and others are.  But, still overall the font rendering was a  tad rough, I guess I usually adjust that in preferences . . . which did  render OK in its window.

OK, that's my "report" on my experience with a daily build, as  Al or someone said, "It's not quite ready."  If there is something I  can run in this build again for someone I can do that, but, time is  limited; yesterday I was somewhere where the .iso could be downloaded in  8 mins, whereas at home that would take an hour, etc.

e.e.p.

So it means that this Ubuntu or Lubuntu 14.04 is not reliable on G5 PPC and i should not even try it?
I'd hate to erase my Good Debian wheezy7.1 install and to find out that this Ubuntu or Lubuntu 14.04 will not work out of the box,and have to install Debian again and go through all the work again to get sound and wireless working!
Please some one advise,when it's safe to say it will work and have good support,Thanks

---

### Post by este.el.paz on 2014-03-31
@frank18:

I see you are posting around, but, in terms of 14.04 that is "testing" right now . . . so I'm forgetting the categories, but "testing" is between "Sid" and "stable" . . . .  So, I'm seeing here that some folks are running 14.04 on their Mac's, but they probably had to do some CLI tweaking to do that? and that ***might**** not be on PPC machines.  I'm a GUI guy and have limited CL knowledge, so absolutely before I try an install it would be with the "RC" or regular release.  I just posted my report here because PhilW is looking for people to test out Lubun on PPC computers, for which there can be some issues with video card drivers and other such problems to get linux running . . . .

e.e.p.

---

