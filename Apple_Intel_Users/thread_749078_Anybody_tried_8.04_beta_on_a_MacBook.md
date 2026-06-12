---
title: "Anybody tried 8.04 beta on a MacBook?"
date: 2008-04-08
forum: Apple Intel Users
---

### Post by SergioA on 2008-04-08
Hi there!

Just tried the 8.04 beta live-cd on my MacBook 1st gen: it seems fine, can also see my OSX partitions!!!

Has anybody already installed it on a MacBook? Any caveats/hints?

Thanks in advance ;-)

Sergio

---

### Post by viciouslime on 2008-04-08
On my second gen there are still issues with sound, and the wireless still doesn't work (madwifi have pushed this back to the 0.9.5 release so this isn't ubuntu's fault). Otherwise though, it's working nicely :)

---

### Post by mabovo on 2008-04-08
I am using Hardy Beta 8.04 amd64 on my MacBook without any kind of problems.

Intel 945GM runs smoothly with Compiz 7.4, FF3 play awesome adobe flashplayer and youtube with perfect sound and video, java open 6 running perfect out of the box. Isight built in perfect too. Wireless AR5418 with madwifi r3456 pretty good and fast no problems echanging from wired to wireless on NM-0.6.6.

The only issue I noticed here is related to pommed that sometimes it crashes. Same to the keyboard there is not a backlight but the green leds of caps lock and num lock don't light up and the red light of the headphone is on all the time. Microphone and headphones without problems using Skype 1.4.0.118. Hope that version 2.0 with webcam enabled could be released soon. 

I use refit for bootloader in OSX10.4 or Hardy with 30GB for OSX, 30GB for /system, 30GB for /home, 3GB for swap and 200MB fat32 for refit working nice the 4 partitions.

What else ?  I am very satified with Hardy and MacBook although comparing with OSX of course the hardware achieves its potentially of 100% with video performance fonts rendering etc.

One relevant aspect that the US keyboard is configured in Hardy for brazilian characters and only the grave tilde sign ~ is not correctly mapped in xmodmap. It is displaying the sign ^ instead of ~

---

### Post by mabovo on 2008-04-08
> **SergioA said:**
> Hi there!

Just tried the 8.04 beta live-cd on my MacBook 1st gen: it seems fine, can also see my OSX partitions!!!

Has anybody already installed it on a MacBook? Any caveats/hints?

Thanks in advance ;-)

Sergio

I forgot to answer your question.

Yes, you can see/read the HPFS partition.  I prefer to not write on it.

---

### Post by SergioA on 2008-04-08
Thanks guys!

Will report when done ;-)

---

### Post by benanzo on 2008-04-09
I've been running Hardy on my first-gen Macbook since about Alpha 6 and so far am quite impressed.  A couple things are broken though like the F1-F2 brightness controls dont work.  The LED lights on the CapsLock and NumLock keys don't light up when pressed.  The iSight module included in the Hardy kernel works but the udev rule for extracting the firmware is broken so the iSight doesn't work out of the box.

Other than those things everything works including audio out both headphones and built-in speakers.  Mic works perfectly.  Suspend/Hibernate both work flawlessly EVERY time.  Wifi works with WPA out of the box (as it did in Gutsy).  The IR receiver works great (as in Gutsy).

Brightness and CapsLock/NumLock bugs:
[https://bugs.launchpad.net/mactel-support/+bug/163725](https://bugs.launchpad.net/mactel-support/+bug/163725)
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/206921](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/206921)

uvcvideo bug:
[https://bugs.launchpad.net/ubuntu/+bug/185634](https://bugs.launchpad.net/ubuntu/+bug/185634)

---

### Post by viciouslime on 2008-04-09
> **mabovo said:**
> I am using Hardy Beta 8.04 amd64 on my MacBook without any kind of problems.

Intel 945GM runs smoothly with Compiz 7.4, FF3 play awesome adobe flashplayer and youtube with perfect sound and video, java open 6 running perfect out of the box. Isight built in perfect too. Wireless AR5418 with madwifi r3456 pretty good and fast no problems echanging from wired to wireless on NM-0.6.6.

The only issue I noticed here is related to pommed that sometimes it crashes. Same to the keyboard there is not a backlight but the green leds of caps lock and num lock don't light up and the red light of the headphone is on all the time. Microphone and headphones without problems using Skype 1.4.0.118. Hope that version 2.0 with webcam enabled could be released soon. 

I use refit for bootloader in OSX10.4 or Hardy with 30GB for OSX, 30GB for /system, 30GB for /home, 3GB for swap and 200MB fat32 for refit working nice the 4 partitions.

What else ?  I am very satified with Hardy and MacBook although comparing with OSX of course the hardware achieves its potentially of 100% with video performance fonts rendering etc.

One relevant aspect that the US keyboard is configured in Hardy for brazilian characters and only the grave tilde sign ~ is not correctly mapped in xmodmap. It is displaying the sign ^ instead of ~

Version 2 has been released... several months ago? :)

---

### Post by benanzo on 2008-04-09
Skype 2 is out of beta now.  It works great with the iSight (once you get the firmware extracted properly.)

[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

---

### Post by mabovo on 2008-04-09
> **benanzo said:**
> I've been running Hardy on my first-gen Macbook since about Alpha 6 and so far am quite impressed.  A couple things are broken though like the F1-F2 brightness controls dont work.  The LED lights on the CapsLock and NumLock keys don't light up when pressed.  The iSight module included in the Hardy kernel works but the udev rule for extracting the firmware is broken so the iSight doesn't work out of the box.

Other than those things everything works including audio out both headphones and built-in speakers.  Mic works perfectly.  Suspend/Hibernate both work flawlessly EVERY time.  Wifi works with WPA out of the box (as it did in Gutsy).  The IR receiver works great (as in Gutsy).

Brightness and CapsLock/NumLock bugs:
[https://bugs.launchpad.net/mactel-support/+bug/163725](https://bugs.launchpad.net/mactel-support/+bug/163725)
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/206921](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/206921)

uvcvideo bug:
[https://bugs.launchpad.net/ubuntu/+bug/185634](https://bugs.launchpad.net/ubuntu/+bug/185634)
 
Kernel Frreze is closer....
They did FFe for Hal, Compiz, NM-0.6.6 and not for iSight ?  :)

Skype 2 is only available for i386 not for amd64  :(

---

### Post by pierrelux on 2008-04-09
I have a Macbook Pro (fourth gen) and run Hardy 8.04 64-bit.

I first tried to install Feisty (i386 and 64 bit) but it failed to install Grub or Lilo... can't tell if there was a problem there. It did worked with Hardy then (under safe graphic mode) after I manually created the partitions.

---

### Post by BIGtrouble77 on 2008-04-09
Hardy 64bit works phenominally with my 3rd gen macbook. Had to compile madwifi, had to setup mouse keys for right click and that's about it.  Suspend actually works now!!!  Best Ubuntu release by far.  Gutsy was a huge disappointment for me, completely unstable on my mb.

-bt

---

### Post by cyberdork33 on 2008-04-09
> **benanzo said:**
> The iSight module included in the Hardy kernel works but the udev rule for extracting the firmware is broken so the iSight doesn't work out of the box. install the newer version of the isight firmware tools which uses hal rather than udev. It has been working great.> **mabovo said:**
> Skype 2 is only available for i386 not for amd64  :(It will work on 64bit... it is just a bit more complicated to get the libraries needed. getlibs is very helpful for that: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by ronocdh on 2008-04-10
> **mabovo said:**
> Kernel Frreze is closer....
They did FFe for Hal, Compiz, NM-0.6.6 and not for iSight ?  :)

Skype 2 is only available for i386 not for amd64  :(
As long as you have your iSight properly configured, you might be able to use the "force" dpkg and install the 32-bit Skype 2 and still use it. I've never tried it myself.

---

### Post by jdong on 2008-04-10
Success is inversely proportional to generation. original core duo and the two core 2 duo pre-santa rosas worked fine. However the new SR ones with the Broadcom card and updated touchpad, people are really reporting problems on Ubuntu.

---

### Post by cyberdork33 on 2008-04-10
> **jdong said:**
> Success is inversely proportional to generation. original core duo and the two core 2 duo pre-santa rosas worked fine. However the new SR ones with the Broadcom card and updated touchpad, people are really reporting problems on Ubuntu.
work is being done. The Broadcom cards work with ndiswrapper and progress is being made on the new touchpad hardware:
[http://tannewt.org/touch/](http://tannewt.org/touch/)

---

### Post by jdong on 2008-04-10
> **cyberdork33 said:**
> work is being done. The Broadcom cards work with ndiswrapper and progress is being made on the new touchpad hardware:
[http://tannewt.org/touch/](http://tannewt.org/touch/)


(1) Work in ndiswrapper is a very relative term. It usually comes with an asterisk of some sort, like randomly drops out, kernel panics one of every 10 suspends, cannot use NetworkManager, etc

(2) Yeah I've noticed that work is going into the Touchpad I'm just remarking it's not something that'll work well with Hardy or Gutsy.


I have no doubt that the open source folks **WILL** get all this stuff working, it's just a matter of time and downstream propagation delay. but when a person buys a notebook, I think they expect it to work **NOW** and to be honest currently I believe there's better products than the latest-revision Apple notebooks on the market if running Linux is an important consideration.

---

### Post by cyberdork33 on 2008-04-10
> **jdong said:**
> I have no doubt that the open source folks **WILL** get all this stuff working, it's just a matter of time and downstream propagation delay. but when a person buys a notebook, I think they expect it to work **NOW** and to be honest currently I believe there's better products than the latest-revision Apple notebooks on the market if running Linux is an important consideration.
I know that a lot of people complain about ndiswrapper, but I have always had good experiences with it myself. I actually prefer it on most of my hardware over the pseudo-open broadcom drivers (requiring firmware) out there, but touche.

I am in 100% agreement with you on your last comments, but those early macbook versions were not so well supported at first either. It takes time, and it always does... Some things take more work/time than others. (broadcom, ati, etc). I tell people all the time, if you are getting a machine to run Ubuntu, then do not get a Mac, get something compatible, especially if you plan to not use OSX at all!

---

### Post by jdong on 2008-04-10
Yeah, whenever someone asks me whether or not they should get $apple_product. My answer is always to make **sure** that you like it even if it only does what it's said to do out of the box. For an iPod, that means the stock firmware, non-jailbroken, etc. For a computer that means Mac OS X. Anything on top of that you can do on the device is purely an extra. Expect it might work today, might not after tomorrow's update, etc.

---

### Post by DGortze380 on 2008-04-13
Hardy is up and running on my 1st gen macBook. Love it.  Seems to run much smoother.  Everything worked fine out of the box except wireless and iSight.  Wireless is detecting networks but won't connect.  I think the problem is my school network, not the driver.  iSight does not work, and I still can't get rid of that whining noise.  Any suggestions would be awesome. Eye candy attached.

---

### Post by cyberdork33 on 2008-04-13
> **DGortze380 said:**
> Hardy is up and running on my 1st gen macBook. Love it.  Seems to run much smoother.  Everything worked fine out of the box except wireless and iSight.  Wireless is detecting networks but won't connect.  I think the problem is my school network, not the driver.  iSight does not work, and I still can't get rid of that whining noise.  Any suggestions would be awesome. Eye candy attached.somebody was claiming that you just have to stick the AppleUSBVideoSupport file in /lib/firmware and it loads. If that doesn't work, you need to get and use isight-firmware-tools.

---

### Post by DGortze380 on 2008-04-13
yeah, put the driver there, but still doesn't work.  I'll look into isight-firmware-tools

---

### Post by jdong on 2008-04-13
The camera requires i-f-t, it will not work by simply sticking ANY firmware in /lib/firmware.

---

### Post by cyberdork33 on 2008-04-13
> **jdong said:**
> The camera requires i-f-t, it will not work by simply sticking ANY firmware in /lib/firmware.
That's what I thought too... Someone recently said differently in a bug report;
[https://bugs.edge.launchpad.net/isight-firmware-tools/+bug/185634/comments/49](https://bugs.edge.launchpad.net/isight-firmware-tools/+bug/185634/comments/49)

anyway, install i-f-t and extract the firmware, then it will load it automatically via hal.

---

### Post by jdong on 2008-04-13
> **cyberdork33 said:**
> That's what I thought too... Someone recently said differently in a bug report;
[https://bugs.edge.launchpad.net/isight-firmware-tools/+bug/185634/comments/49](https://bugs.edge.launchpad.net/isight-firmware-tools/+bug/185634/comments/49)

anyway, install i-f-t and extract the firmware, then it will load it automatically via hal.

The commenter is misinformed. The failure to find video chains *means* that the device has no firmware and hence doesn't function as a webcam.

---

### Post by AnimalMachine on 2008-04-14
I just did an upgrade from 7.10 on my first gen macbook pro with this command:
```
sudo do-release-upgrade --devel-release
```
After hitting y a few times everything was upgraded and working fine. Wireless works, and my touchpad seems better too.

Edit: suspend ard hibernate both work well. I never tested isight since I don't use it...

---

### Post by cyberdork33 on 2008-04-14
> **jdong said:**
> The commenter is misinformed. The failure to find video chains *means* that the device has no firmware and hence doesn't function as a webcam.OK, that's what I thought too, but hestitated that there might be new info. Some people were upset that it requires i-f-t which is not in the Ubuntu repos...

---

### Post by jdong on 2008-04-14
> **cyberdork33 said:**
> OK, that's what I thought too, but hestitated that there might be new info. Some people were upset that it requires i-f-t which is not in the Ubuntu repos...

And I am one of them. IMO it's a regression from Hardy and the author of isight-firmware-tools should've been in closer contact with Ubuntu developers about this regression when it was introduced months ago rather than dropping a bombshell now.

Same goes to all the Hardy macbook testers for simply applying the 3rd party package without making it more clear that the functionality required for the camera isn't in the repositories. Well, looks like we'll be suffering 3rd party repos on this for the next 6.5 months.

---

### Post by cyberdork33 on 2008-04-14
> **jdong said:**
> And I am one of them. IMO it's a regression from Hardy and the author of isight-firmware-tools should've been in closer contact with Ubuntu developers about this regression when it was introduced months ago rather than dropping a bombshell now.

Same goes to all the Hardy macbook testers for simply applying the 3rd party package without making it more clear that the functionality required for the camera isn't in the repositories. Well, looks like we'll be suffering 3rd party repos on this for the next 6.5 months.
it was a hack before, they just didn't include the same hack in Hardy. If they were that worried about it, they would have done the same thing in Hardy as in Gutsy.

---

### Post by jdong on 2008-04-14
> **cyberdork33 said:**
> it was a hack before, they just didn't include the same hack in Hardy. If they were that worried about it, they would have done the same thing in Hardy as in Gutsy.

The thing is, I don't think anyone on the kernel team has Apple hardware or fully understood the ramifications of that patch they were merging in or dropping. They've got to manage a kernel codebase with thousands of new commits every month and it's not really reasonable to expect them to be superhuman (though I am increasingly convinced they are actually superhuman)

---

### Post by cyberdork33 on 2008-04-14
> **jdong said:**
> The thing is, I don't think anyone on the kernel team has Apple hardware or fully understood the ramifications of that patch they were merging in or dropping. They've got to manage a kernel codebase with thousands of new commits every month and it's not really reasonable to expect them to be superhuman (though I am increasingly convinced they are actually superhuman)
I understand, but you have to think, it must have been that way for a reason... Either way, this is not the first time a release has not natively supported something. It will make it in eventually.... I mean there are bigger issues that didn't make it, like some of the keyboard support.

---

### Post by jdong on 2008-04-14
> **cyberdork33 said:**
> I understand, but you have to think, it must have been that way for a reason... 

Well I think they saw the kernelspace hacks that went into loading firmware and decided it was a Bad Idea (tm) and just dropped the patches, thinking that someone in userspace world will pick up support. And someone did, only it's unfortunate this person chose not to work in collaboration with Ubuntu development and fork off into a PPA. And, for that matter, no testers blew the whistle on it either.

> 
Either way, this is not the first time a release has not natively supported something. It will make it in eventually.... I mean there are bigger issues that didn't make it, like some of the keyboard support.

Well we can't be everything all at the same time... yet... As you mentioned, it will make its way eventually. :)

---

### Post by cyberdork33 on 2008-04-14
> **jdong said:**
> Well I think they saw the kernelspace hacks that went into loading firmware and decided it was a Bad Idea (tm) and just dropped the patches, thinking that someone in userspace world will pick up support. And someone did, only it's unfortunate this person chose not to work in collaboration with Ubuntu development and fork off into a PPA. And, for that matter, no testers blew the whistle on it either.
Honestly, I personally had no reason to believe they were not aware of it.

We will support the release in the mactel-support PPA anyway along with other patches that are not included.

---

### Post by yousufinternet on 2008-04-15
hi 
i am using ubuntu 8.04 hardy on a macbook (core 2 duo)
the wireless is working through ndiswrapper 
the sound is perfect and better than 7.10 a thousand times 
the video card is working and the effects start automatically 
isight is not working even in ekiga or cheese 

what else do u need to know?? 
:)

---

### Post by thenes on 2008-04-15
On my mac mini I had some minor problems with Open Office and Firefox when I tried the beta. Firefox worked all right, but after I closed it, I would get an error message saying that it had closed unexpectedly. In OOo, the installation manager for language support would not open in a window big enough to work in.

Other than that, the graphic effects in Gnome were a little bit slow. Hibernation worked better than it does in 7.10, where I have to use suspend in stead of hibernation.

---

### Post by cyberdork33 on 2008-04-15
> **yousufinternet said:**
> isight is not working even in ekiga or cheeseYou need isight-firmware-tools
[https://edge.launchpad.net/isight-firmware-tools/](https://edge.launchpad.net/isight-firmware-tools/)

---

### Post by jdong on 2008-04-15
> **thenes said:**
> On my mac mini I had some minor problems with Open Office and Firefox when I tried the beta. Firefox worked all right, but after I closed it, I would get an error message saying that it had closed unexpectedly. In OOo, the installation manager for language support would not open in a window big enough to work in.

Other than that, the graphic effects in Gnome were a little bit slow. Hibernation worked better than it does in 7.10, where I have to use suspend in stead of hibernation.


Most of the problems you mentioned were known bugs at the time of the beta.

---

### Post by onjob on 2008-04-16
> **cyberdork33 said:**
> You need isight-firmware-tools
[https://edge.launchpad.net/isight-firmware-tools/](https://edge.launchpad.net/isight-firmware-tools/)

Thanks, helped for me too. ;-)

---

### Post by mustang on 2008-04-18
> **benanzo said:**
> I've been running Hardy on my first-gen Macbook since about Alpha 6 and so far am quite impressed.  A couple things are broken though like the F1-F2 brightness controls dont work.  The LED lights on the CapsLock and NumLock keys don't light up when pressed.  The iSight module included in the Hardy kernel works but the udev rule for extracting the firmware is broken so the iSight doesn't work out of the box.

Other than those things everything works including audio out both headphones and built-in speakers.  Mic works perfectly.  Suspend/Hibernate both work flawlessly EVERY time.  Wifi works with WPA out of the box (as it did in Gutsy).  The IR receiver works great (as in Gutsy).

Brightness and CapsLock/NumLock bugs:
[https://bugs.launchpad.net/mactel-support/+bug/163725](https://bugs.launchpad.net/mactel-support/+bug/163725)
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/206921](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/206921)

uvcvideo bug:
[https://bugs.launchpad.net/ubuntu/+bug/185634](https://bugs.launchpad.net/ubuntu/+bug/185634)

Hey benanzo long time no see.

How is battery life? Is suspend still temperamental?

---

### Post by bitfoo on 2008-04-18
I can't even get the RC to boot on my santa rosa MBP! Tons of errors about "squash_fs: sb_bread", and many more "buffer I/O error on device sr0, logical block <some_Number>."  So envious right now! :(

---

### Post by jdong on 2008-04-18
> **bitfoo said:**
> I can't even get the RC to boot on my santa rosa MBP! Tons of errors about "squash_fs: sb_bread", and many more "buffer I/O error on device sr0, logical block <some_Number>."  So envious right now! :(

Those are CD-ROM block errors. Try a different brand of CD or a different burner.

---

### Post by Rog-Mahal on 2008-04-18
I just upgraded to hardy using the update manager, and I have a couple problems. The biggest one right now is that using the new kernel, my keyboard is dead. The mouse works fine, but none of the keys work and the leds for the caps lock and num lock don't light up. Any ideas?

Second, when I boot into my old kernel everything works fine except for my right click. I had it mapped to the 'enter' key on the right side of the keyboard, but that no longer responds. I also can't seem to figure out where I can re-enable mouse keys. 

Thanks for the help

[EDIT] Second issue was solved, I just needed to restart X.

---

### Post by emptiness on 2008-04-20
I just upgraded to hardy last night and everything seems ok so far.My touchpad is working proper again(by default!), with two fingers acting as right click :). Haven't tried to set anything else up yet though...

I'm using a macbook 3,1

---

### Post by benanzo on 2008-04-21
mustang:
> Hey benanzo long time no see.

How is battery life? Is suspend still temperamental?

Battery life if reasonably better at about 2 hours.  Suspend is a *huge* improvement.  It works everytime without issue.  One out of twenty times after resuming I get a popup stating that the machine "Failed to suspend" -- which is wrong.  Just ignore it.

---

### Post by jdong on 2008-04-21
Battery life for me is 3:40 or so.

---

### Post by oskarloko on 2008-04-21
As others said, Ubuntu 8.04 beta works very well into a MacBook.

Hibernate and suspend are now working 100% rigth.

Ubuntu is improving each version, it can be noted from the first boot

Congratulations to the Ubuntu Team !!

:lolflag:



However, anybody with 8.04 beta and a 2.6.25 kernel ?

---

