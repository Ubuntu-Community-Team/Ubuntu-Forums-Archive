---
title: "New Macbook Ubuntu Ready???"
date: 2008-10-14
forum: Apple Hardware Users
---

### Post by Leetbumble on 2008-10-14
So the big question is...

What in the new Macbook ([http://www.apple.com/macbook/](http://www.apple.com/macbook/)) has changed if anything that would prevent me from upgrading that perfect case with an OS worthy such beauty?

I've seen the upgrade HowTo that makes a Macbook into a working Ubuntu system ([https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)) but I am concerned hardware changes will limit functionality in this new release. And its just to damn expensive to not have all the bells and whistles working.

~Thanks~

---

### Post by schauerlich on 2008-10-14
For one I doubt you'll be able to switch between the two graphics cards seamlessly anymore. there may also be some issues with the trackpad, or there may not. No one will really know until someone tries to install it.

---

### Post by danbuter on 2008-10-14
I'm pretty sure  only the Pro comes with 2 graphics cards (which is one too many, IMO).

---

### Post by schauerlich on 2008-10-14
> **danbuter said:**
> I'm pretty sure  only the Pro comes with 2 graphics cards (which is one too many, IMO).

I say get rid of all the video cards! These CPUs have been getting it easy, having their own personal slave to do all the hum-drum work while they get to do fun things like calculating pi to the 4E+24 digit. I demand G/CPU equality!

</sarcasm>

---

### Post by cyberdork33 on 2008-10-14
Looking at the available specs, there is no show stopper, but the nvidia cards have given trouble in the past when they first came out. I think we have most of the touchpad stuff situated (though if it doesn't have a button anymore, that means we will need to make sure that tapping is setup by default.) As soon as someone gets a hold of one and gets at least an lspci output from it, then we can speculate a bit more.

---

### Post by kosumi68 on 2008-10-15
Wow... it looks like an MBA with dvd drive. My guess would be that the touchpad is the bcm5974, and that - as you all said already - the new graphics card will pose some initial problems. There will also be problems with the fans and temperature settings initially, but at least we should be able to fix those things quickly.

---

### Post by kosumi68 on 2008-10-15
> **cyberdork33 said:**
> (though if it doesn't have a button anymore, that means we will need to make sure that tapping is setup by default.)

The next upstream version of synaptics automatically turns on features based on machine capability. I can see single tap will work out-of-the-box. I guess there are several choices as how to enable multi-finger taps on this one... suggest something, and I'll consider it :-)

---

### Post by cyberdork33 on 2008-10-15
> **kosumi68 said:**
> The next upstream version of synaptics automatically turns on features based on machine capability. I can see single tap will work out-of-the-box. I guess there are several choices as how to enable multi-finger taps on this one... suggest something, and I'll consider it :-)
yea should at least have one-finger tap for single click and two-finger tap for right click at least. something consistent anyway. more advanced functions can be configured by the user. Right-Click was a big enough issue back in the day so we should hit this one on the head as it is a bit more pressing :)

---

### Post by Leetbumble on 2008-10-15
Well I'm about to place my order so I should have a system soon to test on. 

Another spin off question - is it possible just to destroy the mac install and load Ubuntu **without** OS-X.whatever on the system assuming that the system will run Ubuntu at all???

---

### Post by Charlie708 on 2008-10-15
That would be even easier than trying to preserve the OS X install.  However, I would go with dual boot, because you are paying the software, and there really isn't any reason to tank it unless you really need the space.

---

### Post by mabovo on 2008-10-15
They did it again. I am very impressed.

A good product even better than before.

Hope Ubuntu comes to a high level for this nice hardware.

---

### Post by cyberdork33 on 2008-10-15
> **Charlie708 said:**
> That would be even easier than trying to preserve the OS X install.  However, I would go with dual boot, because you are paying the software, and there really isn't any reason to tank it unless you really need the space.

Plus it will help us make sure it is working as it did before OK as well. Even if you don't want to keep it that way, it would be most helpful from an informational standpoint.

---

### Post by Spark* on 2008-10-17
Actually the whole trackpad is a (physical) button, so tap to click should rather be disabled by default, since it would be rather redundant.

---

### Post by kosumi68 on 2008-10-17
> **Spark* said:**
> Actually the whole trackpad is a (physical) button, so tap to click should rather be disabled by default, since it would be rather redundant.

Oh... there was room for misinterpretation here - thanks for clearing that up! This means it will appear as a normal single-button mouse, for which the tapping is off by default. Two-finger and three-finger click will work, as will two-finger scrolling.

---

### Post by cyberdork33 on 2008-10-17
> **kosumi68 said:**
> Oh... there was room for misinterpretation here - thanks for clearing that up! This means it will appear as a normal single-button mouse, for which the tapping is off by default. Two-finger and three-finger click will work, as will two-finger scrolling.
Yes, good info. I saw something that suggested that recently, but wasn't sure about it. This helps a lot!

I wonder if it will need to handle multi-finger taps differently then...

---

### Post by jackoverfull on 2008-10-17
hi, i just bought a new macbook pro (i'm waiting for it…) and i'll installa a linux distro in dual boot with os x, probably ubuntu. I'll report here once tryed…:)

---

### Post by Spark* on 2008-10-17
I'm also waiting for my order, but the known details seem to be this:

- The pad can be pressed down anywhere to activate a single click (obviously)

- For dragging, one can also use a second finger to make a click and it will be smart enough to register the click at the first finger's position (this sounds like it would conflict with a two-finger-tap gesture if it does anything else)

- It is possible to configure that clicks (or taps, not sure right now) in the bottom right corner of the pad register as second mouse button.

- Two and three finger gestures are the same, but there are also the new four finger gestures (up for show desktop, down for expose, left or right for application switcher).

---

### Post by kosumi68 on 2008-10-17
> **Spark* said:**
> 
- For dragging, one can also use a second finger to make a click and it will be smart enough to register the click at the first finger's position (this sounds like it would conflict with a two-finger-tap gesture if it does anything else)


I wonder if the new macbook can still be configured to give a right click on a two-finger click.

> **Spark* said:**
> 
- It is possible to configure that clicks (or taps, not sure right now) in the bottom right corner of the pad register as second mouse button.


This can be done with the available version of synaptics.

> **Spark* said:**
> 
- Two and three finger gestures are the same, but there are also the new four finger gestures (up for show desktop, down for expose, left or right for application switcher).


there is no technichal difficulty here, only that it needs a change upstream, in synaptics, and in the applications... We might go for the MPX stuff while we're at it. It takes a big joint effort to get these things in place, but we will eventually get there.

---

### Post by Spark* on 2008-10-17
> **kosumi68 said:**
> I wonder if the new macbook can still be configured to give a right click on a two-finger click.

It seems so:

[img]http://images.macworld.com/images/news/graphics/136063-trackpad_original.jpg[/img]

The image is from this article: [http://www.macworld.com/article/136063/2008/10/macbook_first_look.html](http://www.macworld.com/article/136063/2008/10/macbook_first_look.html)

---

### Post by cyberdork33 on 2008-10-17
> **Spark* said:**
> It seems so:

The image is from this article: [http://www.macworld.com/article/136063/2008/10/macbook_first_look.html](http://www.macworld.com/article/136063/2008/10/macbook_first_look.html)
There is a difference though... there is tap-to-click, and there there is clicking when two fingers are on the touchpad. This is already implemented in current Macbooks. However, on the new machine, both of these could essentially be the same gesture which is why the concern...

---

### Post by Leetbumble on 2008-10-17
Im all about the details of the clicking... but to be honest I can live without the gesture gimmicks and as long as I get left and right click I'll be more than happy.

My main concerns I guess are the graphics, wireless, audio, and touch pad does basic (mouse like stuff). More than that ehh... it is gonna be running Ubuntu anyways.:) Thanks for all the great content and replies

---

### Post by jackoverfull on 2008-10-17
> **Leetbumble said:**
> Im all about the details of the clicking... but to be honest I can live without the gesture gimmicks and as long as I get left and right click I'll be more than happy.
me too.
having the gestures would be nice, not having them wouldn't be a problem at all.
also, for the right click it's surely possible to configure f12 or f11 to do it, like on older macs…


>  My main concerns I guess are the graphics, 
yeah: what about the 2 graphic cards?

> wireless, 
in the macbook there seems to be a broadcom card (oh no: not another one!), still no idea about the pro. i have a strong feeling that something like ndiswrapper will be required.:(

> audio, and touch pad does basic (mouse like stuff). hopefully they will from the first moment.

---

### Post by MikeTheC on 2008-10-18
Just went to my local Apple Store tonight to have a look at the new MBs and MBPs.

Is it me, or did this all suddenly become way more over-designed/over-engineered than it needs to be? The gestures sound great on paper, but as for actual practice... um, no. Thank you.

They otherwise look nice, and for what it's worth the cases are made from whole blocks of aluminum here in the U.S. (yeah, something made in the U.S. for a change!) so they have no seams or joins. Just joints for the hinge mount, holes for ports, that sort of thing.

---

### Post by cyberdork33 on 2008-10-18
> **jackoverfull said:**
> in the macbook there seems to be a broadcom card (oh no: not another one!), still no idea about the pro. i have a strong feeling that something like ndiswrapper will be required.:(
The wl driver ought to support it.

---

### Post by waldobeer on 2008-10-18
I just got my macbook today and here is what I have found:

rEFIt 0.11 currently will not boot another partition.  However the subversion repository for rEFIt has updates that appear to support the new hardware.  No idea when the new version will be build/released, so I ended up using rEFIt for the partition tool, then booting into ubuntu by holding down alt during boot and selecting the "Windows" drive.

I installed the 32-bit Ubuntu 8.10 beta.  The regular install cd appeared to work just fine, but I ended up using the alternative cd (stupidly hoped for LVM).  To make the alternative cd boot, I had to disable the framebuffer with the "nofb" option, otherwise I would hang on a black screen before install.

What works "out of the box": (quotes due to lots of package upgrades from iso)
 * nvidia chipset - just use the restricted drivers tool for nvidia 177
 * wireless - worked out of the box, no problems, no restricted drivers
 * suspend - takes about 15-30 seconds to wake up, but everything works.
 * bluetooth - works

What doesn't work:
 * sound - alsa seems to recognize the card as nvidia alc885, but no sound.
 * mouse - Trackpad and left click work fine, changes for right click/scrolling listed here: [https://help.ubuntu.com/community/MacBook_Santa_Rosa#Fix%20Touchpad](https://help.ubuntu.com/community/MacBook_Santa_Rosa#Fix%20Touchpad) do not work.  Errors about the mouse not being recognized by the synaptic driver.

Another thing to note, right now my system only recognizes 2.7Gb of ram.  From what I have read this is a cpu limit when in 32-bit mode in combination with part of the ram being shared with the integrated video card.

Mouse occasionally stops responding for a few seconds, but I've experienced the same behaviour with OS X.  Mildly annoying.

I'll post more updates as I have them.  Hopefully someone else is working on this and will post here too.

-David

---

### Post by kosumi68 on 2008-10-19
Glad to hear it booted!

> * mouse - Trackpad and left click work fine, changes for right click/scrolling [...] do not work. Errors about the mouse not being recognized by the synaptic driver.

And most likely the bcm5974 driver does not recognize the trackpad, either. It would be enormously helpful if you would like to post the output of the commands listed here: [http://ubuntuforums.org/showpost.php?p=5982275&postcount=4](http://ubuntuforums.org/showpost.php?p=5982275&postcount=4). With that information, we can proactively fix a lot of problems.

---

### Post by jackoverfull on 2008-10-19
> **cyberdork33 said:**
> The wl driver ought to support it.
with or without a windows driver/firmware?

> **waldobeer said:**
> I just got my macbook today and here is what I have found:

rEFIt 0.11 currently will not boot another partition. However the subversion repository for rEFIt has updates that appear to support the new hardware. No idea when the new version will be build/released, so I ended up using rEFIt for the partition tool, then booting into ubuntu by holding down alt during boot and selecting the "Windows" drive.

better than nothing, i guess…


>   I installed the 32-bit Ubuntu 8.10 beta. 

shouldn't a 64 bit version be a more appropriate choice, unless you need the 32 bit one?

>   * nvidia chipset - just use the restricted drivers tool for nvidia 177
:neutral:

>   * wireless - worked out of the box, no problems, no restricted drivers
:guitar:
and in the mb this reportedly *is* a broadcom card! :-D
> 
 * suspend - takes about 15-30 seconds to wake up, but everything works.
 * bluetooth - works
:)

>   * sound - alsa seems to recognize the card as nvidia alc885, but no sound.
:(
but maybe a bit of tuning is enough to make alsa work, if the card is recognized…

> * mouse - Trackpad and left click work fine
that's enough for starting, at least for me.:)

>   Errors about the mouse not being recognized by the synaptic driver.
what do you mean?

> Another thing to note, right now my system only recognizes 2.7Gb of ram. From what I have read this is a cpu limit when in 32-bit mode in combination with part of the ram being shared with the integrated video card.
maybe with a 64 bit os…

>  Mouse occasionally stops responding for a few seconds, but I've experienced the same behaviour with OS X.  Mildly annoying.
:confused:

---

### Post by Nikos.Alexandris on 2008-10-19
Hi all!

Would this page [1] from *[www.ifixit.com](www.ifixit.com)* be of any help? There are some part numbers listed.

I would like to ask about whether one could use Samsung memory SODIMMS (2GB 2Rx8 PC2 - 5300S - 555 - 12 - E3 (CE6) in a new MacBookPro.

Regards, Nikos

[1] [http://www.ifixit.com/Guide/First-Look/Mac/MacBook-Pro-Unibody/Page-8#top](http://www.ifixit.com/Guide/First-Look/Mac/MacBook-Pro-Unibody/Page-8#top)

---

### Post by cyberdork33 on 2008-10-19
> **kosumi68 said:**
> It would be enormously helpful if you would like to post the output of the commands listed here: [http://ubuntuforums.org/showpost.php?p=5982275&postcount=4](http://ubuntuforums.org/showpost.php?p=5982275&postcount=4). With that information, we can proactively fix a lot of problems.Yes please! I would particularly like to know the version number of the machine, and some of the specifics of the hardware components.

> **jackoverfull said:**
> with or without a windows driver/firmware?

No (separate) firmware needed. Broadcom recently released the windows driver components as a Linux driver (with a binary blob in there.)

---

### Post by kosumi68 on 2008-10-19
> **Nikos.Alexandris said:**
> 
Would this page [1] from *[www.ifixit.com](www.ifixit.com)* be of any help? There are some part numbers listed.


Thanks, ifixit has been useful in the past, by identifying the trackpad chip to be the same in the iphone and macbook air models. So far I did not see this chip amongst their listed numbers, though. They will most likely put more information up there eventually.

---

### Post by waldobeer on 2008-10-19
> **jackoverfull said:**
> 
shouldn't a 64 bit version be a more appropriate choice, unless you need the 32 bit one?


I used to stick with the 64-bit version religiously, but it just hasn't been worth it.  On Gutsy 64-bit flash would work the first 2 times, then I would have to restart firefox and kill nsplugin.  It simply works on 32-bit.  Rather shallow reason, but I switched to Ubuntu from years of gentoo because I want everything to just work.


> **jackoverfull said:**
> 
:(
but maybe a bit of tuning is enough to make alsa work, if the card is recognized&#8230;


Ok, this is weird.  This morning I booted from OS X into Ubuntu and magically the sound worked.  Going to do a little testing later to see if this is a warm boot fluke.



> **jackoverfull said:**
> 
[QUOTE=waldobeer;5991761]
... Errors about the mouse not being recognized by the synaptic driver.

what do you mean?
[/QUOTE]

From /var/log/Xorg.0.log:

```
(II) Synaptics touchpad driver version 0.15.2
Synaptics Touchpad no synaptics event device found
(**) Option "Device" "/dev/psaux"
(**) Option "SHMConfig" "on"
(**) Option "LeftEdge" "20"
(**) Option "RightEdge" "1200"
(**) Option "TopEdge" "20"
(**) Option "BottomEdge" "370"
(**) Option "FingerLow" "10"
(**) Option "FingerHigh" "20"
(**) Option "MaxTapTime" "100"
(**) Option "MaxTapMove" "100"
(**) Option "MaxDoubleTapTime" "200"
(**) Option "VertScrollDelta" "10"
(**) Option "HorizScrollDelta" "10"
(**) Option "VertEdgeScroll" "0"
(**) Option "HorizEdgeScroll" "0"
(**) Option "VertTwoFingerScroll" "1"
(**) Option "HorizTwoFingerScroll" "1"
(**) Option "TapButton2" "3"
(**) Option "TapButton3" "2"
(**) Option "PressureMotionMinZ" "10"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
```


> **jackoverfull said:**
> 
maybe with a 64 bit os&#8230;

Yea, running the 64-bit version would probably fix it, however I'm not going to blow it all away right now to try.


One last question for those of you who have used linux on a macbook before, where did my insert and pgup/down keys go?  Typing up this message made me realize how much I use them.  Is there any known way to map them to fn+something for both the console and in X?  Slapping "|more" on the end of every command is like hopping in the DeLorian w/ Doc. Brown.

---

### Post by waldobeer on 2008-10-19
> **kosumi68 said:**
> Glad to hear it booted!

> * mouse - Trackpad and left click work fine, changes for right click/scrolling [...] do not work. Errors about the mouse not being recognized by the synaptic driver.

And most likely the bcm5974 driver does not recognize the trackpad, either. It would be enormously helpful if you would like to post the output of the commands listed here: [http://ubuntuforums.org/showpost.php?p=5982275&postcount=4](http://ubuntuforums.org/showpost.php?p=5982275&postcount=4). With that information, we can proactively fix a lot of problems.

Done.  Results are attached.

---

### Post by kosumi68 on 2008-10-19
Excellent! Here is a dkms package with an updated version of bcm5974 to test. Also attached the source file patch, in case you compile your own kernel.

One important question for the mapping of device ids: is your keyboard the US (ANSI) version?

---

### Post by kosumi68 on 2008-10-19
Actually, the SMC scan is slightly incomplete, apparently the number of keys is now larger than 256. I am attaching a new version of the scan-smc.sh script which should give the complete list.

---

### Post by waldobeer on 2008-10-19
> **kosumi68 said:**
> Excellent! Here is a dkms package with an updated version of bcm5974 to test. Also attached the source file patch, in case you compile your own kernel.

One important question for the mapping of device ids: is your keyboard the US (ANSI) version?

The keyboard should be the US (ANSI) version, bought in the US.

I'll give that package a shot in a bit.  Right now fighting with gparted to get a LVM partition.

---

### Post by jackoverfull on 2008-10-19
> **cyberdork33 said:**
> 
No (separate) firmware needed. Broadcom recently released the windows driver components as a Linux driver (with a binary blob in there.)
:guitar::guitar::guitar:

> **waldobeer said:**
> I used to stick with the 64-bit version religiously, but it just hasn't been worth it. On Gutsy 64-bit flash would work the first 2 times, then I would have to restart firefox and kill nsplugin. It simply works on 32-bit. Rather shallow reason, but I switched to Ubuntu from years of gentoo because I want everything to just work.



i see…
Well, i'm coming from ppc, so at least i will not miss flash…:lolflag:


 
>   Ok, this is weird. This morning I booted from OS X into Ubuntu and magically the sound worked. Going to do a little testing later to see if this is a warm boot fluke.
 
 
 :guitar:


 > 
 One last question for those of you who have used linux on a macbook before, where did my insert and pgup/down keys go? Typing up this message made me realize how much I use them. Is there any known way to map them to fn+something for both the console and in X? Slapping "|more" on the end of every command is like hopping in the DeLorian w/ Doc. Brown.
mmmh… if i remember correctly the last time i used ubuntu on my ibook the fn+arrows and fn+fkays worked out of the box…

---

### Post by waldobeer on 2008-10-19
> **kosumi68 said:**
> Excellent! Here is a dkms package with an updated version of bcm5974 to test. Also attached the source file patch, in case you compile your own kernel.


I dropped the package and still have no right click/scroll on the touchpad.  The logs are reporting that the mouse is still unrecognisable as a synaptic pad.  I've attached my xorg.conf and startup log.  Any ideas would be helpful.

---

### Post by kosumi68 on 2008-10-19
Yes - it has been a while since we had the initial problems with new device ids, so I simply forgot that the device needs to be masked from HID. Several alternatives:

1. Edit /etc/modprobe.d/bcm5974, making sure you get a line like this:
```

options usbhid quirks=0x05ac:0x0236:0x00020800

```
then 'sudo depmod -a' and reboot is necessary.

2. Remove the package and install the attached replacement.

It might even be needed to add the quirks line to /etc/initramfs-tools/options, followed by 'sudo update-initramfs -u -v -k `uname -r`', although we never did that back then.

The output of the attached script bcm5974-diagnostics.sh should be able to give you hints as to the problem, should it persist after the update.

---

### Post by waldobeer on 2008-10-19
> **kosumi68 said:**
> Actually, the SMC scan is slightly incomplete, apparently the number of keys is now larger than 256. I am attaching a new version of the scan-smc.sh script which should give the complete list.

Updated SMC scan is attached.

---

### Post by waldobeer on 2008-10-19
> **kosumi68 said:**
> Yes - it has been a while since we had the initial problems with new device ids, so I simply forgot that the device needs to be masked from HID. Several alternatives:

1. Edit /etc/modprobe.d/bcm5974, making sure you get a line like this:
```

options usbhid quirks=0x05ac:0x0236:0x00020800

```
then 'sudo depmod -a' and reboot is necessary.

2. Remove the package and install the attached replacement.

It might even be needed to add the quirks line to /etc/initramfs-tools/options, followed by 'sudo update-initramfs -u -v -k `uname -r`', although we never did that back then.

The output of the attached script bcm5974-diagnostics.sh should be able to give you hints as to the problem, should it persist after the update.

The good news is that after installing the package and rebooting, X recognises the mouse as a touchpad.  Bad news is that now the mouse stopped working, lol.  Attaching diagnostic output.  Also I disabled all the options in my xorg.conf in case that was the problem (also attached).

Also, running "synclient -m 1" shows nothing when using the trackpad.

---

### Post by Nikos.Alexandris on 2008-10-19
Dear All,

excuse for interrupting the flow of the discussion. There might be an opportunity to get a new MBP with a student rebate. But I can't imagine working without Ubuntu. I've seen OSX in a friends (previous MBP) but I can't say I was moved.

So, the newbie question (although I think I can handle the command line to perform any hack):

* Would you recommend to get one of these strong machines and install Ubuntu on it?

* I don't mind loosing OSX and even not have all of the whistles and bells working. But I would need to use the strong graphic card it has got on.

* What about using "conventional" 2GB SODIMMS in a (new) MBP (...sorry for repeating the question)?

* An *advanced* memory question: in the "ifixit" page [1] they state about the new MBP "...the Montevina chipset appears to support up to 8GB". Could it be possible to use 8GB on this machine?

* Is there a newMBP overview/wikipage from an expert to list what works and what not? (I understand that the new machine is tested now by you guys but an interested newbie kind of easily looses the overview)?

Thank you in advance, Nikos

[1] [http://www.ifixit.com/Guide/First-Look/Mac/MacBook-Pro-Unibody/Page-4](http://www.ifixit.com/Guide/First-Look/Mac/MacBook-Pro-Unibody/Page-4)

---

### Post by kosumi68 on 2008-10-19
Here is an updated binary module for applesmc, it should match your system and kernel version. To try it, simply
```

sudo rmmod applesmc; sudo insmod ./applesmc-with-MB51-2.6.27-7-generic-i386.ko

```

To test it, running
```

sensors

```
should suffice. If it works fine, I'll send the patch on upstream.

---

### Post by kosumi68 on 2008-10-19
> **waldobeer said:**
> The good news is that after installing the package and rebooting, X recognises the mouse as a touchpad.  Bad news is that now the mouse stopped working, lol.


Puzzling. The usb device spec seems identical to the older versions, but to start making sure we have a touchpad, you can enable debug output to the bcm5974 module, by
```

sudo rmmod bcm5974; sudo modprobe bcm5974 debug=99

```
and hopefully see some raw output with
```

tail -f /var/log/debug

```

And while at it, I was going to ask about the raw device dimensions anyways, in order to calibrate the driver. One way is to move the finger from one corner to the next, all around, and record the extreme values in the x and y directions.

---

### Post by waldobeer on 2008-10-19
> **kosumi68 said:**
> Here is an updated binary module for applesmc, it should match your system and kernel version. To try it, simply
```

sudo rmmod applesmc; sudo insmod ./applesmc-with-MB51-2.6.27-7-generic-i386.ko

```

To test it, running
```

sensors

```
should suffice. If it works fine, I'll send the patch on upstream.

Hmm, Looks like it works.

```

beer:~> sensors
applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :  1995 RPM  (min = 2000 RPM)
temp1:       +35.8°C                                    
temp2:       +35.8°C                                    
temp3:       +35.2°C                                    
temp4:       +35.8°C                                    
temp5:       +64.0°C                                    
temp6:       +58.5°C                                    
temp7:       +64.2°C                                    
temp8:       +58.0°C                                    
temp9:       +65.0°C                                    
temp10:      +64.0°C                                    
temp11:      +56.2°C                                    
temp12:      +55.5°C                                    
temp13:      +33.8°C                                    
temp14:      +43.5°C

```

---

### Post by kosumi68 on 2008-10-19
> **waldobeer said:**
> Hmm, Looks like it works.


Great - if we are *really* lucky, we can squeeze this into intrepid, it being a minor change.

---

### Post by waldobeer on 2008-10-19
> **kosumi68 said:**
> Puzzling. The usb device spec seems identical to the older versions, but to start making sure we have a touchpad, you can enable debug output to the bcm5974 module, by
```

sudo rmmod bcm5974; sudo modprobe bcm5974 debug=99

```
and hopefully see some raw output with
```

tail -f /var/log/debug

```

And while at it, I was going to ask about the raw device dimensions anyways, in order to calibrate the driver. One way is to move the finger from one corner to the next, all around, and record the extreme values in the x and y directions.

The mouse started working again (no clue what caused it), but the output of the diagnostics now reports:

```
* Kernel version: 2.6.27-7-generic
* Synaptics version: 0.15.2-0ubuntu7
* USB device: Bus 001 Device 005: ID 05ac:0236 Apple, Inc.
* /lib/modules/2.6.27-7-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: has quirks, good
* /lib/modules/2.6.27-7-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is NOT registered
Please double-check the quirks settings in /etc/modprobe.d/bcm5974
```

This is after I uninstalled (using "apt-get remove") the bcm5974 package, rebooted, reinstalled, and rebooted again.  Guessing I'm doing something wrong.

---

### Post by waldobeer on 2008-10-19
Sound update:

After adding this line to /etc/modprobe.d/options:
```

options snd_hda_intel model=mbp3
```

sound works, but only for headphones.

---

### Post by kosumi68 on 2008-10-19
> **waldobeer said:**
> The mouse started working again (no clue what caused it), but the output of the diagnostics now reports:

* /proc/bus/input/devices: module is NOT registered

This is after I uninstalled (using "apt-get remove") the bcm5974 package, rebooted, reinstalled, and rebooted again.  Guessing I'm doing something wrong.

I think youre are doing things right, it all makes sense given the following assumptions:

1. When removing the bcm5974 module from within X, X gets confused and, rather than reload the driver, reloads the fallback mouse driver. By pressing CTRL-ALT-F1 to go to a text screen, and then back again with ALT-F7, the bcm5974 driver takes effect again - in your case by having the mouse freeze.

2. The quirk settings in /etc/modprobe.d/option sometimes fails. This happened back in May, too. I believe this might be connected to HID being loaded as part of the initrd. Could be worth trying that initramfs suggestion a few posts back. Bottom line is: whenever this happens, the module will not get registered.

In order to get a grip on this problem, I think having a look at the driver raw data is worthwhile. It is not dependent on any of the Xorg issues, and a confirmation that the basic trackpad data gets through would be good.

---

### Post by kosumi68 on 2008-10-19
> **waldobeer said:**
> Sound update:

After adding this line to /etc/modprobe.d/options:
```

options snd_hda_intel model=mbp3
```

sound works, but only for headphones.

This might be as easy as turning the external speaker on in the switches section of the sound configs (double-click on the volume control to pop-up). At least this happened to me in one of the latest updates.

---

### Post by waldobeer on 2008-10-19
> **kosumi68 said:**
> This might be as easy as turning the external speaker on in the switches section of the sound configs (double-click on the volume control to pop-up). At least this happened to me in one of the latest updates.

I tried all of them, and no luck.  Probably gonna have to open a bug w/ alsa.

---

### Post by waldobeer on 2008-10-19
> **kosumi68 said:**
> 
2. The quirk settings in /etc/modprobe.d/option sometimes fails. This happened back in May, too. I believe this might be connected to HID being loaded as part of the initrd. Could be worth trying that initramfs suggestion a few posts back. Bottom line is: whenever this happens, the module will not get registered.

In order to get a grip on this problem, I think having a look at the driver raw data is worthwhile. It is not dependent on any of the Xorg issues, and a confirmation that the basic trackpad data gets through would be good.

I added the option lines and rebuild the initrd and it is working, or not working in the predictable way now.  Attached is the raw data debug.  One thing to notice is that the system disconnects from wireless momentarily when this module is loaded.  Attached is the debug info including insmod, moving around on the mouse, clicking, and rmmod.

Spolier: Lots of ```

Oct 19 19:10:25 mccoy kernel: [  303.717895] bcm5974: bad trackpad package, length: 58
```

---

### Post by kosumi68 on 2008-10-20
> **waldobeer said:**
> One thing to notice is that the system disconnects from wireless momentarily when this module is loaded.


They both appear in the log, but are you sure they are related?

> **waldobeer said:**
> 
  Attached is the debug info including insmod, moving around on the mouse, clicking, and rmmod.

Spolier: Lots of ```

Oct 19 19:10:25 mccoy kernel: [  303.717895] bcm5974: bad trackpad package, length: 58
```


Ah. So Apple changed the trackpad protocol. This one will take some time to fix (not indefinitely, though). I bet the length changes to something else if you put *two* fingers on the trackpad. Knowing that length would help me get going on the protocol update. Please? :-)

Thanks a bundle for all the test!

---

### Post by kosumi68 on 2008-10-20
Here is a script to make a more thorough test of the applesmc module. Your model has a motion sensor, an ambient light sensor, one fan, and 14 temperature sensors. They should all work :-)

---

### Post by waldobeer on 2008-10-20
> **kosumi68 said:**
> They both appear in the log, but are you sure they are related?



Ah. So Apple changed the trackpad protocol. This one will take some time to fix (not indefinitely, though). I bet the length changes to something else if you put *two* fingers on the trackpad. Knowing that length would help me get going on the protocol update. Please? :-)

Thanks a bundle for all the test!

One finger:```

Oct 20 08:12:39 mccoy kernel: [ 4571.526088] bcm5974: bad trackpad package, length: 58
```
Two fingers:```

Oct 20 08:12:43 mccoy kernel: [ 4575.149071] bcm5974: bad trackpad package, length: 86
```
Three fingers:```

Oct 20 08:12:45 mccoy kernel: [ 4577.295079] bcm5974: bad trackpad package, length: 114
```

Attached full log.  Perhaps a version of the module that dumps the hex of the package to the log along with a specific touching path would help?

---

### Post by waldobeer on 2008-10-20
> **kosumi68 said:**
> Here is a script to make a more thorough test of the applesmc module. Your model has a motion sensor, an ambient light sensor, one fan, and 14 temperature sensors. They should all work :-)
```

 ./applesmc-test.sh 
accelerometer: present, readable, output: (-2,1,250)
fan:           present, readable, output: 2000
light:         present, readable, output: (0,0)
leds:          present,
 led:                   readable, output: 0
temperatures:  present,
 temperature:           readable, output: 50750
 temperature:           readable, output: 43750
 temperature:           readable, output: 40750
 temperature:           readable, output: 26000
 temperature:           readable, output: 32000
 temperature:           readable, output: 27000
 temperature:           readable, output: 27000
 temperature:           readable, output: 26250
 temperature:           readable, output: 27000
 temperature:           readable, output: 50500
 temperature:           readable, output: 46000
 temperature:           readable, output: 51000
 temperature:           readable, output: 45500
 temperature:           readable, output: 65000
performance:   reading all temperatures
 fail frequency:        0
 reads per second:      50

```

---

### Post by kosumi68 on 2008-10-20
> **waldobeer said:**
> One finger:```

Oct 20 08:12:39 mccoy kernel: [ 4571.526088] bcm5974: bad trackpad package, length: 58
```
Two fingers:```

Oct 20 08:12:43 mccoy kernel: [ 4575.149071] bcm5974: bad trackpad package, length: 86
```
Three fingers:```

Oct 20 08:12:45 mccoy kernel: [ 4577.295079] bcm5974: bad trackpad package, length: 114
```

Attached full log.  Perhaps a version of the module that dumps the hex of the package to the log along with a specific touching path would help?

We might be lucky here - it seems only the protocol header size changed, and that is actually not used. Here is a new version of the dkms package. Given the same debug treatment, it might show more than just error output. Fingers crossed.

---

### Post by kosumi68 on 2008-10-20
> **waldobeer said:**
> ```

 ./applesmc-test.sh 
accelerometer: present, readable, output: (-2,1,250)
fan:           present, readable, output: 2000
light:         present, readable, output: (0,0)
leds:          present,
 led:                   readable, output: 0
temperatures:  present,
 temperature:           readable, output: 50750
 temperature:           readable, output: 43750
 temperature:           readable, output: 40750
 temperature:           readable, output: 26000
 temperature:           readable, output: 32000
 temperature:           readable, output: 27000
 temperature:           readable, output: 27000
 temperature:           readable, output: 26250
 temperature:           readable, output: 27000
 temperature:           readable, output: 50500
 temperature:           readable, output: 46000
 temperature:           readable, output: 51000
 temperature:           readable, output: 45500
 temperature:           readable, output: 65000
performance:   reading all temperatures
 fail frequency:        0
 reads per second:      50

```

It looks good, but the light reading (0,0) is puzzling... Do you always get that? This might be a difference between the 2.0GHz and 2.4GHz version of the machine. Do you have keyboard backlight? You could try turning it on with
```

echo 255 | sudo tee -a /sys/class/leds/smc\:\:kbd_backlight/brightness

```

---

### Post by waldobeer on 2008-10-20
> **kosumi68 said:**
> We might be lucky here - it seems only the protocol header size changed, and that is actually not used. Here is a new version of the dkms package. Given the same debug treatment, it might show more than just error output. Fingers crossed.

> **kosumi68 said:**
> It looks good, but the light reading (0,0) is puzzling... Do you always get that? This might be a difference between the 2.0GHz and 2.4GHz version of the machine. Do you have keyboard backlight? You could try turning it on with
```

echo 255 | sudo tee -a /sys/class/leds/smc\:\:kbd_backlight/brightness

```

I'll give these a shot when I get home tonight.

---

### Post by waldobeer on 2008-10-20
> **kosumi68 said:**
> It looks good, but the light reading (0,0) is puzzling... Do you always get that? This might be a difference between the 2.0GHz and 2.4GHz version of the machine. Do you have keyboard backlight? You could try turning it on with
```

echo 255 | sudo tee -a /sys/class/leds/smc\:\:kbd_backlight/brightness

```

This works just fine, Backlight comes on.

> **kosumi68 said:**
> We might be lucky here - it seems only the protocol header size changed, and that is actually not used. Here is a new version of the dkms package. Given the same debug treatment, it might show more than just error output. Fingers crossed.

Good news, with this one scrolling works fine, including two-finger scroll-wheel emulation.  Bad news, clicking doesn't work.

Attached are two debugging outputs; one where I touch the center of the trackpad, go to the top right corner, then trace around the edge of the pad in a clockwise fashion.  The second is clicks, I click with one finger, then two, then three.  Then I click with one finger in the bottom right, then bottom left of the pad (no clue why).

---

### Post by kosumi68 on 2008-10-20
> **waldobeer said:**
> This works just fine, Backlight comes on.



Good news, with this one scrolling works fine, including two-finger scroll-wheel emulation.  Bad news, clicking doesn't work.

Attached are two debugging outputs; one where I touch the center of the trackpad, go to the top right corner, then trace around the edge of the pad in a clockwise fashion.  The second is clicks, I click with one finger, then two, then three.  Then I click with one finger in the bottom right, then bottom left of the pad (no clue why).

We're getting there! Here is a drop-in replacement that should be quick to test, using
```

sudo rmmod bcm5974; sudo insmod ./bcm5974-0.66-rc4-2.6.27-7-generic-i386.ko debug=99

```
It contains debug output for the presumed button interface. Hopefully you will see something.

---

### Post by waldobeer on 2008-10-20
> **kosumi68 said:**
> We're getting there! Here is a drop-in replacement that should be quick to test, using
```

sudo rmmod bcm5974; sudo insmod ./bcm5974-0.66-rc4-2.6.27-7-generic-i386.ko debug=99

```
It contains debug output for the presumed button interface. Hopefully you will see something.

Still no click luck, here's the debug

---

### Post by kosumi68 on 2008-10-20
Ok... here is a long shot, it just might...

---

### Post by cyberdork33 on 2008-10-20
wow. Lots of stuff getting done. Good job!

Just a suggestion getting the change into Intrepid, I am sure that if you explain this hardware came out just after the drop dead date then they will hopefully allow it. Especially if it is so minor.

---

### Post by waldobeer on 2008-10-20
> **kosumi68 said:**
> Ok... here is a long shot, it just might...

no luck, more debug.  This is three cycles of one finger, two finger, then three finger clicks.

---

### Post by kosumi68 on 2008-10-20
> **waldobeer said:**
> no luck, more debug.  This is three cycles of one finger, two finger, then three finger clicks.

Ok, last try for today; time to be brutal ;-)

---

### Post by waldobeer on 2008-10-20
> **kosumi68 said:**
> Ok, last try for today; time to be brutal ;-)

Hah, another pile of data for you.  Same test procedure as last time.

---

### Post by kosumi68 on 2008-10-20
> **waldobeer said:**
> Hah, another pile of data for you.  Same test procedure as last time.

... and I believe I found the button in there :-)

It makes sense. The header protocol was extended with four bytes, to accomodate for button data (and something yet unknown). This is a natural development from Apple, because the button was oddly treated in its own interface in the first multi-touch version half a year ago.

---

### Post by waldobeer on 2008-10-20
> **kosumi68 said:**
> ... and I believe I found the button in there :-)

It makes sense. The header protocol was extended with four bytes, to accomodate for button data (and something yet unknown). This is a natural development from Apple, because the button was oddly treated in its own interface in the first multi-touch version half a year ago.

And we have a winner!  Great job.

---

### Post by kosumi68 on 2008-10-20
> **waldobeer said:**
> And we have a winner!  Great job.

And you are officially the first person on the planet with a somewhat functional linux on the new unibody MacBook :-)

It will take a couple of days for the dust to settle, but this will definitely go upstream soon.

Cheers!

---

### Post by waldobeer on 2008-10-21
> **kosumi68 said:**
> And you are officially the first person on the planet with a somewhat functional linux on the new unibody MacBook :-)

It will take a couple of days for the dust to settle, but this will definitely go upstream soon.

Cheers!

Haha, thanks for your work on this, w/o it I probably would have returned this thing already.

I found some of that dust you were talking about.  Right now two finger horizontal scrolling does not seem to be working.  It is enabled in the gnome mouse menu.

After running the diagnostic program I see:
```
-    HorizEdgeScroll         = 0
-    HorizScrollDelta        = 0
-    HorizTwoFingerScroll    = 1
+    HorizEdgeScroll         = 1
+    HorizScrollDelta        = 32
+    HorizTwoFingerScroll    = 0
...
-    VertEdgeScroll          = 0
-    VertScrollDelta         = 40
-    VertTwoFingerScroll     = 1
+    VertEdgeScroll          = 1
+    VertScrollDelta         = 32
+    VertTwoFingerScroll     = 0
```

Although my config has VertTwoFingerScroll disabled (assumed from the 0 value), two finger vertical scrolling works, but horizontal scrolling (which has the same value) does not work.

This next one is a very weird case, but bear with me.  When using two fingers to right click, you cannot move the mouse without releasing the click.  I.e. Press down with two fingers to activate a right-click menu, then move both fingers to select a menu option.  The mouse will not move until either one or both fingers are removed from the mousepad.  If only one finger is removed, the menu will go away, if both fingers are released the menu will stay.

Attached debugs, with the following behaviors:

debug-hscroll: 3 attempts at using two finger horizontal scroll
debug-rclick: 3 attempts, two finger right click, then moving both fingers to select an item from the menu.  Mouse cursor does not move on screen during this time.  Then one finger is released and the mouse is able to move again, but the menu disappears.

---

### Post by tiffanyjewelry on 2008-10-21
you know the problem is very big ,so .......

---

### Post by kosumi68 on 2008-10-21
> **waldobeer said:**
> 
Right now two finger horizontal scrolling does not seem to be working.  It is enabled in the gnome mouse menu.

After running the diagnostic program I see:
```
-    HorizEdgeScroll         = 0
-    HorizScrollDelta        = 0
-    HorizTwoFingerScroll    = 1
+    HorizEdgeScroll         = 1
+    HorizScrollDelta        = 32
+    HorizTwoFingerScroll    = 0
...
-    VertEdgeScroll          = 0
-    VertScrollDelta         = 40
-    VertTwoFingerScroll     = 1
+    VertEdgeScroll          = 1
+    VertScrollDelta         = 32
+    VertTwoFingerScroll     = 0
```

Although my config has VertTwoFingerScroll disabled (assumed from the 0 value), two finger vertical scrolling works, but horizontal scrolling (which has the same value) does not work.


There is a problem with synaptics and the new device detection mechanism provided by hal fdi and xorg. Basically, the settings you are looking at are not in effect. Something to try:

* Move /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi some place. Restart hal and X. Or

* Add this to your /etc/X11/xorg.conf:
```

Section "ServerFlags"
    Option "AutoAddDevices" "off"
EndSection

```
and restart X.


> **waldobeer said:**
> 
This next one is a very weird case, but bear with me.  When using two fingers to right click, you cannot move the mouse without releasing the click.  I.e. Press down with two fingers to activate a right-click menu, then move both fingers to select a menu option.  The mouse will not move until either one or both fingers are removed from the mousepad.  If only one finger is removed, the menu will go away, if both fingers are released the menu will stay.


Given that the button and trackpad are integrated, we are bound to get some kind of problem from it. The attached version uses a simple, but hopefully effective, way to deal with this:

* If the internal button is pressed, disregard the finger last added to the trackpad.

It should make 'normal' button presses with the second hand appear as usual. Odd effects are anticipated if pressing the button with one hand and several fingers. :-)

---

### Post by waldobeer on 2008-10-21
> **kosumi68 said:**
> There is a problem with synaptics and the new device detection mechanism provided by hal fdi and xorg. Basically, the settings you are looking at are not in effect. Something to try:

* Move /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi some place. Restart hal and X. Or

* Add this to your /etc/X11/xorg.conf:
```

Section "ServerFlags"
    Option "AutoAddDevices" "off"
EndSection

```
and restart X.


This worked.  Once I made the change to xorg.conf and added in options for horiz/vert scrolling, I could scroll.  A weird side effect is that now after doing a two finger scroll and releasing, the mouse will not move.  I'm guessing this has to do with the right-click change.




> **kosumi68 said:**
> 
Given that the button and trackpad are integrated, we are bound to get some kind of problem from it. The attached version uses a simple, but hopefully effective, way to deal with this:

* If the internal button is pressed, disregard the finger last added to the trackpad.

It should make 'normal' button presses with the second hand appear as usual. Odd effects are anticipated if pressing the button with one hand and several fingers. :-)

Hehe, right click went away.  It appears to register as a left-click now.


Attached debugs:
hscroll: using vertical scrolling, then trying to move the mouse.  Mouse cursor does not move
rclick: 3 two-finger clicks (which register as a left-click), 3 one-finger clicks.

---

### Post by kosumi68 on 2008-10-21
> **waldobeer said:**
> 
Hehe, right click went away.  It appears to register as a left-click now.

That was intentional; it seems from your logs you actually press the button with a single hand. Of course one can do this in different way, but the idea here was that if one keeps two fingers on the trackpad, then click with the second hand, this should be interpreted as a right-click.

A second factor here is the options for finger clicking:
```

        Option          "ClickFinger1"  "1"
        Option          "ClickFinger2"  "3"
        Option          "ClickFinger3"  "2"

```

Regarding the stuck pointer after scroll, I am not sure it got solved here, but I made a small change that may affect how synaptics interprets the data. Restarting X before testing is recommended.

---

### Post by waldobeer on 2008-10-21
> **kosumi68 said:**
> That was intentional; it seems from your logs you actually press the button with a single hand. Of course one can do this in different way, but the idea here was that if one keeps two fingers on the trackpad, then click with the second hand, this should be interpreted as a right-click.


I attempted using two hands to right click, but the result was the same.  The testing was done after a full reboot of the system (lots of updates last night).

I'll give the new module a shot when I get home tonight and post the results, including one-hand vs. two-hand right clicking.

---

### Post by jackoverfull on 2008-10-21
ok, my macbook pro should arrive in ten days, finally. :)

these patchs should work on it too, right?


i suppose that the answer will be "no one will know until someone will have tried…:lolflag:

---

### Post by kosumi68 on 2008-10-21
> **jackoverfull said:**
> 
i suppose that the answer will be "no one will know until someone will have tried…

How could you tell ;-)

The recent findings in this thread are most likely relevant also for the macbook pro, so it might be as easy as adding some device ids.

---

### Post by jackoverfull on 2008-10-21
> **kosumi68 said:**
> How could you tell ;-)

my predictive powers never failed me.8-)


>  The recent findings in this thread are most likely relevant also for the macbook pro, so it might be as easy as adding some device ids.
I think that too. :)

well, less of a couple of weeks to wait…:popcorn:

---

### Post by waldobeer on 2008-10-21
> **kosumi68 said:**
> That was intentional; it seems from your logs you actually press the button with a single hand. Of course one can do this in different way, but the idea here was that if one keeps two fingers on the trackpad, then click with the second hand, this should be interpreted as a right-click.

A second factor here is the options for finger clicking:
```

        Option          "ClickFinger1"  "1"
        Option          "ClickFinger2"  "3"
        Option          "ClickFinger3"  "2"

```

Regarding the stuck pointer after scroll, I am not sure it got solved here, but I made a small change that may affect how synaptics interprets the data. Restarting X before testing is recommended.

Alright, loaded the module, restarted X.  Same behavior.  The mouse does not move when moving one finger around the mouse pad, two fingers do vert/horiz scroll.

Also tried right-clicking using two fingers on one hand, and one from each hand.  Neither method worked.  Tried after adding the above lines to my xorg.conf and restarting X.

Debugs:
move - just moving one finger around the trackpad, mouse does not move on the screen.  Occasionally it will jerk a few pixels, but then stop.
rclick - 3x clicking with one finger from each hand, 3x two fingers from one hand.

---

### Post by kosumi68 on 2008-10-21
> **waldobeer said:**
> Alright, loaded the module, restarted X.  Same behavior.  The mouse does not move when moving one finger around the mouse pad, two fingers do vert/horiz scroll.


With the fdi file removed, we might be back to the original problems with xorg.conf settings. I would recommend using precisely these settings [http://web.comhem.se/rydberg/Bits/xorg-settings-without-tapping.html](http://web.comhem.se/rydberg/Bits/xorg-settings-without-tapping.html) during testing, topped with the FingerClick settings from the previous post.

Looking at your move log, I see the pressure data is completely saturated, indicating the new trackpad has more sensitive settings. In conjunction with bad xorg settings for FingerPress and some others I cannot recall, the effect might well be what you describe. In particular because the pointer does move occasionally.

> **waldobeer said:**
> 
Also tried right-clicking using two fingers on one hand, and one from each hand.  Neither method worked.  Tried after adding the above lines to my xorg.conf and restarting X.


Pardon my persistence, but two fingers from one hand and one clicking finger from the other means three fingers; I did not see any three-finger actions in the logs.

rc10 adjusts the pressure settings to something more reasonable, and makes another adjustment to the event report mechanism, which may or may not help.

---

### Post by kosumi68 on 2008-10-21
Actually, looking back at the removal of the fdi file and/or inserting the ServerFlag, it seems we have been looking at an xorg configuration problem since rc8. Most likely, the only noticable change between rc8 and rc10 is the pressure scale adjustment, otherwise I believe they all work as intended. The big question is: does it work well? :-)

---

### Post by waldobeer on 2008-10-21
> **kosumi68 said:**
> 
Pardon my persistence, but two fingers from one hand and one clicking finger from the other means three fingers; I did not see any three-finger actions in the logs.


Ah, ok that may be my problem.  I'm using only two fingers to do right click.  Is this correct, or should I be doing something else?

---

### Post by kosumi68 on 2008-10-21
> **waldobeer said:**
> Ah, ok that may be my problem.  I'm using only two fingers to do right click.  Is this correct, or should I be doing something else?

The multi-finger click actions are supposed to work like this:

1 finger and click: left button
2 fingers and click: right button
3 fingers and click: middle button
1 finger and hold click: drag

The confusion is about the trackpad also being the button. Clicking near the bottom of the pad, where the button used to be, one expects basically the same behavior as if the button was there. Inevitably, the finger that clicks the imaginary button is *on the trackpad*. If the trackpad driver reports all fingers as usual, the multi-finger click actions all get confused, since there is one finger too many reported. That is why I added the somewhat odd feature that when clicking the trackpad, the last finger added is disregarded. This finger is normally the clicking finger. Effectively, when clicking, the number of fingers reported is reduced by one, which restores the behavior to the one described above.

---

### Post by waldobeer on 2008-10-21
> **kosumi68 said:**
> With the fdi file removed, we might be back to the original problems with xorg.conf settings. I would recommend using precisely these settings [http://web.comhem.se/rydberg/Bits/xorg-settings-without-tapping.html](http://web.comhem.se/rydberg/Bits/xorg-settings-without-tapping.html) during testing, topped with the FingerClick settings from the previous post.

Looking at your move log, I see the pressure data is completely saturated, indicating the new trackpad has more sensitive settings. In conjunction with bad xorg settings for FingerPress and some others I cannot recall, the effect might well be what you describe. In particular because the pointer does move occasionally.

Pardon my persistence, but two fingers from one hand and one clicking finger from the other means three fingers; I did not see any three-finger actions in the logs.

rc10 adjusts the pressure settings to something more reasonable, and makes another adjustment to the event report mechanism, which may or may not help.

Dropped in your xorg.conf changes and I can now move the mouse.  Right-click does work with the three-finger click.  I went back and re-read the config lines and it makes sense.

Is there any way to have two-fingers right click?  I switched the xorg.conf settings to:```

    Option          "ClickFinger1"  "1"
    Option          "ClickFinger2"  "2"
    Option          "ClickFinger3"  "3"
```

After restarting X two-fingers don't work to right-click.  Is there a reason for this, or am I missing a config option?

---

### Post by kosumi68 on 2008-10-21
> **waldobeer said:**
> 
```

    Option          "ClickFinger1"  "1"
    Option          "ClickFinger2"  "2"
    Option          "ClickFinger3"  "3"

```

The above settings give you middle click on two fingers, and right click on three fingers. The previously posted settings give you right click on two fingers, and middle click on three fingers.

---

### Post by waldobeer on 2008-10-21
> **kosumi68 said:**
> The multi-finger click actions are supposed to work like this:

1 finger and click: left button
2 fingers and click: right button
3 fingers and click: middle button
1 finger and hold click: drag

The confusion is about the trackpad also being the button. Clicking near the bottom of the pad, where the button used to be, one expects basically the same behavior as if the button was there. Inevitably, the finger that clicks the imaginary button is *on the trackpad*. If the trackpad driver reports all fingers as usual, the multi-finger click actions all get confused, since there is one finger too many reported. That is why I added the somewhat odd feature that when clicking the trackpad, the last finger added is disregarded. This finger is normally the clicking finger. Effectively, when clicking, the number of fingers reported is reduced by one, which restores the behavior to the one described above.

Hmm, this behavior is different from how osx is handling the trackpad.  Left clicking happens with only a single finger on the pad.  If you have two fingers on the pad when you click, it registers as a right-click.  Now this may only be because I use a single hand on the mouse.

---

### Post by waldobeer on 2008-10-21
> **kosumi68 said:**
> The multi-finger click actions are supposed to work like this:

1 finger and click: left button
2 fingers and click: right button
3 fingers and click: middle button
1 finger and hold click: drag

The confusion is about the trackpad also being the button. Clicking near the bottom of the pad, where the button used to be, one expects basically the same behavior as if the button was there. Inevitably, the finger that clicks the imaginary button is *on the trackpad*. If the trackpad driver reports all fingers as usual, the multi-finger click actions all get confused, since there is one finger too many reported. That is why I added the somewhat odd feature that when clicking the trackpad, the last finger added is disregarded. This finger is normally the clicking finger. Effectively, when clicking, the number of fingers reported is reduced by one, which restores the behavior to the one described above.

I just realized why this feels weird on the trackpad itself.  What is really happening for me while using one hand is the following:
1 finger: left-click
2 fingers: left-click
3 fingers: right-click
4 fingers: middle-click

On OSX it's
1 finger: left
2 fingers: right
3 fingers: middle

These are fingers in contact with the touchpad.

---

### Post by kosumi68 on 2008-10-21
> **waldobeer said:**
> Hmm, this behavior is different from how osx is handling the trackpad.  Left clicking happens with only a single finger on the pad.  If you have two fingers on the pad when you click, it registers as a right-click.  Now this may only be because I use a single hand on the mouse.

Interesting. So how does it handle the drag action? With a single finger? If this is the case, it is all a lot simpler than I thought :-)

---

### Post by waldobeer on 2008-10-21
> **kosumi68 said:**
> Interesting. So how does it handle the drag action? With a single finger? If this is the case, it is all a lot simpler than I thought :-)

yup, single finger drag.  Haha, all our problems were tester fail ;).

---

### Post by kosumi68 on 2008-10-21
> **waldobeer said:**
> yup, single finger drag.  Haha, all our problems were tester fail ;).

And I thought we converged pretty quickly, after all ;-)

One more click question: If you want to select from the menu, via a point-and-click-and-select-and-release action, how do you do it in OSX?

---

### Post by waldobeer on 2008-10-21
> **kosumi68 said:**
> And I thought we converged pretty quickly, after all ;-)

One more click question: If you want to select from the menu, via a point-and-click-and-select-and-release action, how do you do it in OSX?

* Press down, drag to item, release
-or-
* Press down, release, move to item, press down, release.

---

### Post by kosumi68 on 2008-10-21
> **waldobeer said:**
> * Press down, drag to item, release
-or-
* Press down, release, move to item, press down, release.

So holding with one hand and selecting with the other does not work? What happens if one does that?

---

### Post by waldobeer on 2008-10-21
> **kosumi68 said:**
> So holding with one hand and selecting with the other does not work? What happens if one does that?

Haha, you had to make it more difficult.

So it turns out the mouse supports both the model I have been using (one hand, let's call it) and the one you implemented (two handed).

To answer your question, the method you described above also works.

---

### Post by kosumi68 on 2008-10-21
> **waldobeer said:**
> Haha, you had to make it more difficult.

So it turns out the mouse supports both the model I have been using (one hand, let's call it) and the one you implemented (two handed).

To answer your question, the method you described above also works.

Yep, this is what I thought. And from our discussion, it should be painfully obvious that it will take some pretty complex logic to make it work both ways.

On a technical note, this cannot be resolved within the bcm5974 driver: a new button (BTN_TOOL_PRESS) will need to be added to the kernel, and subsequently to the synaptics driver, where the logic will have to be worked out.

I believe this is as far as we get today. :-)

Cheers!

---

### Post by cyberdork33 on 2008-10-21
Can someone with both one of the new Macbook Pros and the new Macbook post the output of 

```
sudo dmidecode| grep Product
```

---

### Post by luckycatfu on 2008-10-22
Evidently the trackpad is going to take some work - but how about everything else?

Displayport video output, webcam, audio? Are these all working?

---

### Post by waldobeer on 2008-10-22
> **cyberdork33 said:**
> Can someone with both one of the new Macbook Pros and the new Macbook post the output of 

```
sudo dmidecode| grep Product
```
```

sudo dmidecode | grep 'Product Name:'
	Product Name: MacBook5,1
	Product Name: Mac-F42D89C8

```
> **luckycatfu said:**
> Evidently the trackpad is going to take some work - but how about everything else?

Displayport video output, webcam, audio? Are these all working?

As I posted earlier, the sound works, but only through headphones.  The speakers are not working.  Yes, I have tried clicking on all the options, and disabling mute in the mixer.

---

### Post by kosumi68 on 2008-10-22
applesmc patch sent upstream: [http://lkml.org/lkml/2008/10/22/351](http://lkml.org/lkml/2008/10/22/351)

---

### Post by cyberdork33 on 2008-10-22
> **waldobeer said:**
> ```

    Product Name: MacBook5,1
```

Thanks!

I think the iSight has been redesigned, so it likely has a new Device ID and won't work...

---

### Post by kosumi68 on 2008-10-22
Ok, here is a "final" release candidate for bcm5974, which does the following:

* Properly detects the MacBook5

* Sends a BTN_LEFT event when the integrated button is pressed

* Sends a BTN_TOOL_PRESS (0x148\) event when the integrated button is pressed. This (not yet available) button can be used in synaptics to perform non-trivial logic for the multi-finger actions.

* Sends a BTN_TOOL_QUADTAP (0x14f) when four fingers are touching the touchpad, rather than the current BTN_TOOL_TRIPLETAP. This (not yet available) button is necessary to properly handle three-finger actions when using a second hand (fourth finger) to click the button.

Out of the two clicking strategies discussed in this thread, this version implements the simpler one, where pressing the trackpad with one hand works nicely. Additional strategies are pushed onto user space and the synaptics driver.

Updates to the upstream xserver-xorg-input-synaptics package, to utilize the new buttons, will follow.

Please test the attached debian package. On positive confirmation, the patches will go upstream.

---

### Post by waldobeer on 2008-10-22
> **kosumi68 said:**
> Ok, here is a "final" release candidate for bcm5974, which does the following:

* Properly detects the MacBook5

* Sends a BTN_LEFT event when the integrated button is pressed

* Sends a BTN_TOOL_PRESS (0x148\) event when the integrated button is pressed. This (not yet available) button can be used in synaptics to perform non-trivial logic for the multi-finger actions.

* Sends a BTN_TOOL_QUADTAP (0x14f) when four fingers are touching the touchpad, rather than the current BTN_TOOL_TRIPLETAP. This (not yet available) button is necessary to properly handle three-finger actions when using a second hand (fourth finger) to click the button.

Out of the two clicking strategies discussed in this thread, this version implements the simpler one, where pressing the trackpad with one hand works nicely. Additional strategies are pushed onto user space and the synaptics driver.

Updates to the upstream xserver-xorg-input-synaptics package, to utilize the new buttons, will follow.

Please test the attached debian package. On positive confirmation, the patches will go upstream.

Hmm, I installed the deb, rebooted and at first mouse clicks were not working, but two finger scrolling was.  While generating the debug info clicks started working and scrolling stopped.  When I attempt two finger scroll now, the cursor just moves.

clicks: 1 finger click, 2 finger, 3 finger.  2 finger scroll up, down.

---

### Post by luckycatfu on 2008-10-22
I've opened a wiki page for the new macbooks here: [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

Obviously it's very bare - I'll document when I pick one up in the next few weeks, otherwise I'm sure plenty of people will appreciate any extra detail anyone can add.

waldobeer, I've quoted you directly under Basic Instructions, hope that's ok. Please edit if not.

---

### Post by Nikos.Alexandris on 2008-10-22
I was about to do that (start a new overview page) but I didn't dare since I am very new to all this. In fact I don't know if I will finally get a Mac. But a friend of mine has already one (4.1) and I am thinking of spending (everything I got!) if Ubuntu works on it (...and don't spend any money for the next half year :-))

Cheers, Nikos

---

### Post by Nikos.Alexandris on 2008-10-22
> **luckycatfu said:**
> I've opened a wiki page for the new macbooks here: [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

Obviously it's very bare - I'll document when I pick one up in the next few weeks, otherwise I'm sure plenty of people will appreciate any extra detail anyone can add.

waldobeer, I've quoted you directly under Basic Instructions, hope that's ok. Please edit if not.

In your new page you don't mention rEFIt 0.12! It's out and it supports the new MB(P). Check it out... [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Cheers, Nikos

---

### Post by cyberdork33 on 2008-10-22
> **Nikos.Alexandris said:**
> In your new page you don't mention rEFIt 0.12! It's out and it supports the new MB(P). Check it out... [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Cheers, Nikos
You can edit it... It is a wiki ;)

I made a couple of minor edits to the page.

---

### Post by bazzwaa on 2008-10-23
Hey all, I got one of the first Macbook pro, 5,1 and am on Ubuntu 8.04(tried to use 8.10, but the OS did not boot at all.)

So far I have the webcam(out of box), basic graphics acceleration of the integrated gpu,wireless, my work stuff(cisco vpn, sip client...ect).

I got the sound card and speakers to play music, but it comes out all messed up(like someone is blending it.)

I cannot get the back light keyboard, multi touch pad, blue tooth, 9600m gt graphics acceleration or hybrid functionality, and the function key to work.

If anyone has some suggestions or would like to work on it, that would be wonderful. I am a linux newb, but know some basic commands.

my hardward profile is attached in a notepad.


If you need any other information, please ask and I will do my best to provide.

Thanks!

ps.
dmidecode| grep Product:	
Product Name: MacBookPro5,1
Product Name: Mac-F42D86C8

---

### Post by kosumi68 on 2008-10-23
bazzwaa,

Great! So we got the PCI information in your first post. We also need to know more about the USB. Could you please provide the defails listed in this post: [http://ubuntuforums.org/showpost.php?p=5982275&postcount=4](http://ubuntuforums.org/showpost.php?p=5982275&postcount=4), and we should be able to fix the accelerometer, light sensor, keyboard backlight, temperature sensors, and multitouch for you.

PS: If you could edit your previous post and move the long text into an attached file instead, that would be super. The pages of this thread are tough to read - even with two-finger scroll ;-)

---

### Post by kosumi68 on 2008-10-23
> **waldobeer said:**
> Hmm, I installed the deb, rebooted and at first mouse clicks were not working, but two finger scrolling was.  While generating the debug info clicks started working and scrolling stopped.  When I attempt two finger scroll now, the cursor just moves.

clicks: 1 finger click, 2 finger, 3 finger.  2 finger scroll up, down.

Oops.

After fixing all the details regarding buttons, it seems I managed to leave out the part that actually reports them :-)

The sudden change in behavor indicates moving from the bcm5974 input to standard mouse input, which happens when the module is forcefully removed when we test. The ctrl+alt+f1-and-alt+f7 trick helps.

From your log, it seems the pressure scale is *not* changed much after all. The click-with-moving-finger strategy generally means pressing harder on the trackpad. Adjusted the range somewhat in this version.

---

### Post by waldobeer on 2008-10-23
> **kosumi68 said:**
> Oops.

After fixing all the details regarding buttons, it seems I managed to leave out the part that actually reports them :-)

The sudden change in behavor indicates moving from the bcm5974 input to standard mouse input, which happens when the module is forcefully removed when we test. The ctrl+alt+f1-and-alt+f7 trick helps.

From your log, it seems the pressure scale is *not* changed much after all. The click-with-moving-finger strategy generally means pressing harder on the trackpad. Adjusted the range somewhat in this version.

This one works.  The only thing that is a little bothersome is that you cannot do right-click dragging: right-click down, move mouse, release.    I'm guessing right now it is sending mousewheel scroll because two fingers are moving, but the mouse cursor isn't.  Is there any way to do this without the extra changes you were talking about to the synaptic driver?

drag: right-click down, move mouse, release

---

### Post by Nikos.Alexandris on 2008-10-23
> **waldobeer said:**
> ... The only thing that is a little bothersome is that you cannot do right-click dragging: right-click down, move mouse, release.

Is this a "normal" feature? I can't do that on my laptop (Ubuntu 8.04) using a mouse.

---

### Post by waldobeer on 2008-10-23
> **Nikos.Alexandris said:**
> Is this a "normal" feature? I can't do that on my laptop (Ubuntu 8.04) using a mouse.

Yup, right-click down anywhere in firefox, and the menu comes up.  Move your mouse to the menu item you want.

---

### Post by Nikos.Alexandris on 2008-10-23
> **waldobeer said:**
> Yup, right-click down anywhere in firefox, and the menu comes up.  Move your mouse to the menu item you want.

Ahh... I see! I thought dragging a desktop item (file or folder).
Thanks

---

### Post by kosumi68 on 2008-10-23
> **waldobeer said:**
> This one works.  The only thing that is a little bothersome is that you cannot do right-click dragging: right-click down, move mouse, release.    I'm guessing right now it is sending mousewheel scroll because two fingers are moving, but the mouse cursor isn't.  Is there any way to do this without the extra changes you were talking about to the synaptic driver?


The scrolling is all detected in the synaptics driver. Don't worry, it will get updated :-)

EDIT: The bcm5974 module can now be downloaded using the normal package manager, from the mactel PPA. If you do not already have it there, add these lines to /etc/apt/sources.list:
```

deb http://ppa.launchpad.net/mactel-support/ubuntu intrepid main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu intrepid main

```

Then update and install the bcm5974-dkms package:
```

sudo apt-get update; sudo apt-get install bcm5974-dkms

```


Kernel patches are off:

[http://lkml.org/lkml/2008/10/23/279](http://lkml.org/lkml/2008/10/23/279)
[http://lkml.org/lkml/2008/10/23/280](http://lkml.org/lkml/2008/10/23/280)
[http://lkml.org/lkml/2008/10/23/283](http://lkml.org/lkml/2008/10/23/283)
[http://lkml.org/lkml/2008/10/23/285](http://lkml.org/lkml/2008/10/23/285)

Thanks for testing!

---

### Post by bazzwaa on 2008-10-23
I attached the output, 
could not get an output for  scan-smc.sh
sorry if I am missing something obvious.

---

### Post by waldobeer on 2008-10-23
> **bazzwaa said:**
> I attached the output, 
could not get an output for  scan-smc.sh
sorry if I am missing something obvious.

the scan-smc.sh script is attached to an earlier post in this thread.

[http://ubuntuforums.org/showthread.php?p=5994349&highlight=scan+smc#post5994349](http://ubuntuforums.org/showthread.php?p=5994349&highlight=scan+smc#post5994349)

---

### Post by kosumi68 on 2008-10-23
> **bazzwaa said:**
> I attached the output, 
could not get an output for  scan-smc.sh
sorry if I am missing something obvious.

Thanks!

1. The USB device to show more details on is 05ac:0236. Please resend those details, so we can make sure nothing new popped up here.

2. You are lucky! This is the same device id which we just fixed for MacBook5,1. Thus bcm5974-0.66 should work for you, too :-)

3. Apart from downloading the script, scan-smc.sh requires the applesmc module to be loaded.

Cheers!

---

### Post by bazzwaa on 2008-10-23
ya I added it it my bin earlier, but it gives no output, just drops down to the next line.(with sudo) without sudo I just get a bunch of lines that say permission denied. "/bin/scan-smc.sh: line 10: key_at_index: Permission denied"

the other stuff is attached.

applesmc is loaded too btw.

---

### Post by kosumi68 on 2008-10-23
bazzwaa,

what kernel version are you running? You need intrepid kernel 2.6.27-7 or later, or you will need to install an updated applesmc. If the command stays thinking for some time before returning with empty output, that is most likely the case.

*remembers* Right, you are running hardy... most likely updated to 2.6.24-21... I will fix a module.

---

### Post by bazzwaa on 2008-10-23
yes, I am using Ubuntu 8.04, I tried to upgrade to 8.10, but the beta would not boot into OS after installation. I am going to upgrade to the new kernel when the official release comes out, possibly this will correct that issue.  Unless you know a solution?

---

### Post by kosumi68 on 2008-10-23
> **bazzwaa said:**
> yes, I am using Ubuntu 8.04, I tried to upgrade to 8.10, but the beta would not boot into OS after installation. I am going to upgrade to the new kernel when the official release comes out, possibly this will correct that issue.  Unless you know a solution?

Assuming you are running the 2.6.24-21 kernel on i386 (not amd64), this should work:

1. unpack the attached file

2. run

```

sudo rmmod applesmc; sudo insmod ./applesmc-2.6.24-21-generic-i386.ko

```

after this, you should be able to run the scan-smc.sh script.

---

### Post by calebio on 2008-10-23
Hello,

I have a MacBook **Pro** (late 2008 ), and have not had any success installing 8.10 beta nor 8.04. I have tried Desktop and alternate install CDs of both, and first the 64-bit version, then the 32 bit version when none of those worked.

When installing 8.10 beta, I get only a blinking cursor on boot after successful install. When installing 8.04, I get a message of 'no boot device found' or something of the sort.

Any help is appreciated. How can I start to debug this?

Thanks!

---

### Post by cyberdork33 on 2008-10-23
> **bazzwaa said:**
> yes, I am using Ubuntu 8.04, I tried to upgrade to 8.10, but the beta would not boot into OS after installation. I am going to upgrade to the new kernel when the official release comes out, possibly this will correct that issue.  Unless you know a solution?
Can you give any more details about how it "does not boot" any messages? What do you see?

---

### Post by cyberdork33 on 2008-10-23
> **calebio said:**
> Hello,

I have a MacBook **Pro** (late 2008 ), and have not had any success installing 8.10 beta nor 8.04. I have tried Desktop and alternate install CDs of both, and first the 64-bit version, then the 32 bit version when none of those worked.

When installing 8.10 beta, I get only a blinking cursor on boot after successful install. When installing 8.04, I get a message of 'no boot device found' or something of the sort.

Any help is appreciated. How can I start to debug this?

Thanks!

Please try 8.10 again, but install rEFIt first, and follow the instruction in the linked thread below to sync partitions.

[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by bazzwaa on 2008-10-23
I am running a 64 bit edition of the os.

the 8.10 doesnt boot as the screen just stays in the white "bios" like firmware.  I left it sitting there for 10 minutes just to be sure.  Even now, I have about a 10-15 second delay of that white screen before Ubuntu grub starts to load.

---

### Post by cyberdork33 on 2008-10-23
> **bazzwaa said:**
> I am running a 64 bit edition of the os.

the 8.10 doesnt boot as the screen just stays in the white "bios" like firmware.  I left it sitting there for 10 minutes just to be sure.  Even now, I have about a 10-15 second delay of that white screen before Ubuntu grub starts to load.
are you dual-booting or did you just install Ubuntu overtop everything?

---

### Post by bazzwaa on 2008-10-23
Ubuntu over everything, I have no use for any other operating system than Linux.

---

### Post by cyberdork33 on 2008-10-23
> **bazzwaa said:**
> Ubuntu over everything, I have no use for any other operating system than Linux.

You will likely want OSX for firmware updates... I have to say there will very likely be at least one since that machine is so new. 

Anyway, in that case, you need to bless the partition. The EFI system is searching for EFI executables. See the FAQ.

---

### Post by calebio on 2008-10-23
cyberdork33,

Syncing the partitions in rEFIt (as well as re-enabling it under OSX) worked! Thanks for your suggestion. Now to update the trackpad per this discussion, enable NVidia support, and such.

Thanks!

---

### Post by kosumi68 on 2008-10-23
> **bazzwaa said:**
> I am running a 64 bit edition of the os.

the 8.10 doesnt boot as the screen just stays in the white "bios" like firmware.  I left it sitting there for 10 minutes just to be sure.  Even now, I have about a 10-15 second delay of that white screen before Ubuntu grub starts to load.

In case you havent ran off to install Intrepid, here is a 64-bit version:-)

---

### Post by bazzwaa on 2008-10-23
k, I will try to find a way to bless it. btw, just so you know, I have a plan for that.  I keep an image of osx on an external drive, along with images of every computer I use.  This way if there is a firmware update, just image it, get osx, download, flash, image back to ubuntu.

---

### Post by bazzwaa on 2008-10-23
you are so helpful its crazy.

---

### Post by bazzwaa on 2008-10-23
here you go, output is attached, thanks for that kernel info.

anything else you need?

---

### Post by bazzwaa on 2008-10-23
bcm5974-dkms_0.66_all.deb did not make any multitouch features function.

"echo 255 | sudo tee -a /sys/class/leds/smc\:\:kbd_backlight/brightness" - this did get my backlight on and functioning.  I do not have ambient affect on keyboard though.
anything else I can do?

---

### Post by calebio on 2008-10-23
> **kosumi68 said:**
> In case you havent ran off to install Intrepid, here is a 64-bit version:-)
So i took system updates after the clean install. Any chance of a 2.6.27 version of the 64-bit file applesmc ?

> 
caleb@BookerT:~/Desktop$ ls
applesmc-2.6.24-21-generic-amd64.ko  applesmc-2.6.24-21-generic-amd64.ko.gz
caleb@BookerT:~/Desktop$ sudo insmod ./applesmc-2.6.24-21-generic-amd64.ko
[sudo] password for caleb: 
insmod: error inserting './applesmc-2.6.24-21-generic-amd64.ko': -1 Invalid module format
caleb@BookerT:~/Desktop$ uname -a
Linux BookerT 2.6.27-7-generic #1 SMP Wed Oct 22 01:30:40 UTC 2008 x86_64 GNU/Linux
caleb@BookerT:~/Desktop$ 


---

### Post by kosumi68 on 2008-10-24
> **bazzwaa said:**
> here you go, output is attached, thanks for that kernel info.

anything else you need?

Thanks - attached is the module with your temperature set included. Same procedure to load it. To test it, please use this script [http://ubuntuforums.org/attachment.php?attachmentid=88935&d=1224488583](http://ubuntuforums.org/attachment.php?attachmentid=88935&d=1224488583)

---

### Post by kosumi68 on 2008-10-24
> **bazzwaa said:**
> bcm5974-dkms_0.66_all.deb did not make any multitouch features function.


Output of [http://ubuntuforums.org/attachment.php?attachmentid=88865&d=1224441875?](http://ubuntuforums.org/attachment.php?attachmentid=88865&d=1224441875?)

---

### Post by kosumi68 on 2008-10-24
> **calebio said:**
> So i took system updates after the clean install. Any chance of a 2.6.27 version of the 64-bit file applesmc ?

Here is a debian dkms package, which will install on all kernels and architectures. It will be available through the mactel repo in a couple of days.

---

### Post by kosumi68 on 2008-10-24
Ok, applesmc is now in the mactel PPA. In /etc/apt/sources.list, add
```

deb http://ppa.launchpad.net/mactel-support/ubuntu intrepid main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu intrepid main

```
Then go to the package manager, and search for applesmc-dkms. Install. This works for both Hardy and Intrepid.

Enjoy!

---

### Post by bazzwaa on 2008-10-24
output is attached.

What next?

---

### Post by kosumi68 on 2008-10-24
> **bazzwaa said:**
> output is attached.

What next?

The output, showing 12 sensors (equal to the generic macbookpro), suggests the module did not take effect. Did you reboot? There should be no errors (missing sensors) when running the test script.

---

### Post by kosumi68 on 2008-10-24
> **bazzwaa said:**
> output is attached.

What next?

Regarding the non-registered touchpad driver, what do you see when
```

grep 0236 /etc/modprobe.d/bcm5974

```
There should be an uncommented line there (not starting with #)

If this is ok, you may need to
```

sudo cp /etc/modprobe.d/bcm5974 /etc/initramfs-tools/
sudo update-initramfs -u -v -k `uname -r`

```
then reboot. This prevents the touchpad from being claimed by the wrong module during the boot process. Sometimes it matters, sometimes not (don't know why)

---

### Post by bazzwaa on 2008-10-24
which module are you asking me to add in the above post, you didn't have anything there so I assumed it was the kernel upgrade, I did that successfully. after reboot the output still had errors.  it is attached.

---

### Post by bazzwaa on 2008-10-24
grep 0236 /etc/modprobe.d/bcm5974 output:

options usbhid quirks=0x05ac:0x0236:0x00020800

I ran both commands.
will reboot and see if that worked.

---

### Post by kosumi68 on 2008-10-24
> **bazzwaa said:**
> which module are you asking me to add in the above post, you didn't have anything there so I assumed it was the kernel upgrade, I did that successfully. after reboot the output still had errors.  it is attached.

Ok, I did a maneuvre just a little while ago, perhaps somewhat premature:

1. The applesmc module can now be downloaded using the normal package manager, from the mactel PPA. If you do not already have it there, add these lines to /etc/apt/sources.list:
```

deb http://ppa.launchpad.net/mactel-support/ubuntu intrepid main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu intrepid main

```
Open the package manager, click reload, search for applesmc, and install the package named applesmc-dkms. Make sure the line 'applesmc' is present in /etc/modules. That's it. This will work for everyone, regardless of kernel version. And it will work next year too, for the macbooks to come. If there is an update, you will get it through your normal updates.

2. Because of the stupendous amount of old attachments in this thread, I simply removed all the old ones, to avoid accidental errors (or irrelevant bug reports ;-))

Being somewhat narrowminded, i assumed the above would be clear from my adding the comment "use the mactel PPA"... :-P

---

### Post by bazzwaa on 2008-10-24
that is exactly what i had done.  After this latest reboot, I got some functionality, but very unreliable, sometimes the pad doesn't even detect movement at all.  It did zoom at some point, but I was unable to replicate it.

---

### Post by kosumi68 on 2008-10-24
> **bazzwaa said:**
> that is exactly what i had done.  After this latest reboot, I got some functionality, but very unreliable, sometimes the pad doesn't even detect movement at all.  It did zoom at some point, but I was unable to replicate it.

applesmc: looks good! slight error frequency, but you have a large number of sensors, so it is ok. This one can be considered closed, and a patch will go off upstream shortly.

bcm5974: since you are running hardy, you need to have a matching set of parameters in /etc/X11/xorg.conf. Please copy the ones found here:
[http://web.comhem.se/rydberg/Bits/xorg-settings-without-tapping.html](http://web.comhem.se/rydberg/Bits/xorg-settings-without-tapping.html)

That should give you a working touchpad.

---

### Post by bazzwaa on 2008-10-24
2 finger scroll works, zoom works, rotate does not function as on osx.  All in all this is good news, we have the touch pad working for multitouch on macbook pro. Congrats.

whats the next step?

---

### Post by kosumi68 on 2008-10-24
> **bazzwaa said:**
> 2 finger scroll works, zoom works, rotate does not function as on osx.  All in all this is good news, we have the touch pad working for multitouch on macbook pro. Congrats.


Great!

> 
whats the next step?


What would you like to do? :-)

---

### Post by bazzwaa on 2008-10-24
you think you could help me figure out the 9600m gt drivers?  Or did you want to figure out ambient sensor for Backlighting?  Or bluetooth?  More features for multitouch?  I am really down for whatever you feel like.  This is fun.  I would love to learn to do what your doing.

---

### Post by cyberdork33 on 2008-10-24
> **bazzwaa said:**
> you think you could help me figure out the 9600m gt drivers?  Or did you want to figure out ambient sensor for Backlighting?  Or bluetooth?  More features for multitouch?  I am really down for whatever you feel like.  This is fun.  I would love to learn to do what your doing.

Just my opinion, I think the graphics is a priority issue closely followed by bluetooth if it is not working... The other two items are more or less "extras".

---

### Post by kosumi68 on 2008-10-24
> **bazzwaa said:**
> you think you could help me figure out the 9600m gt drivers?  Or did you want to figure out ambient sensor for Backlighting?  Or bluetooth?  More features for multitouch?  I am really down for whatever you feel like.  This is fun.  I would love to learn to do what your doing.

Thanks, but I really don't know much about the graphics cards, but there are others here that should be able to help you. The ambient sensor setup is currently a nightmare due to hal and gnome-power-manager, and I would really recommend leaving it off for now. The backlight buttons: I have a fix for it, I might package it soon. Meanwhile, you may want to checkout this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125918](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125918). It explains the problem with the backlight.

More features for multitouch: yeah, but it is a bit of work... Anyways, in case you are interested, the package is xserver-xorg-input-synaptics, or [email]xf86-input-synaptics@freedesktop.org[/email] for the upstream package (where I am involved).

Cheers!

---

### Post by bazzwaa on 2008-10-24
I guess we will just have to wait to see who will release a graphics driver that works next.

---

### Post by kosumi68 on 2008-10-24
The bcm5974 driver is now available in the mactel ppa (see previous post), as package bcm5974-dkms.

Enjoy!

---

### Post by calebio on 2008-10-24
> **kosumi68 said:**
> ...
1. The applesmc module can now be downloaded using the normal package manager, from the mactel PPA. If you do not already have it there, add these lines to /etc/apt/sources.list:
```

deb http://ppa.launchpad.net/mactel-support/ubuntu intrepid main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu intrepid main

```
Open the package manager, click reload, search for applesmc, and install the package named applesmc-dkms. That's it. ...

My apologies if i'm being dense, but when I do this, searching 'applesmc' still returns no results in Synaptic package manager. I'm running the late 2008 MacBookPro ("sudo dmidecode| grep Product" gives MacBookPro5,1 // Mac-F42D86C8 ).

Thanks!

---

### Post by kosumi68 on 2008-10-24
> **calebio said:**
> My apologies if i'm being dense, but when I do this, searching 'applesmc' still returns no results in Synaptic package manager.

what do you see when running this?
```

sudo apt-get update
sudo apt-get install applesmc-dkms

```

---

### Post by calebio on 2008-10-24
> **kosumi68 said:**
> what do you see when running this?
```

sudo apt-get update
sudo apt-get install applesmc-dkms

```

I'll spare you the details of the output, but those two commands in terminal worked. I had been trying to use the synaptic package manager UI. Is there a disconnect there?

---

### Post by kosumi68 on 2008-10-24
> **calebio said:**
> I'll spare you the details of the output, but those two commands in terminal worked. I had been trying to use the synaptic package manager UI. Is there a disconnect there?

It should work too. Anyways, you got it, so it should be fine now :-)

Cheers!

---

### Post by kosumi68 on 2008-10-25
applesmc support for MacBook Pro 5 sent upstream: [http://lkml.org/lkml/2008/10/25/40](http://lkml.org/lkml/2008/10/25/40)

---

### Post by kosumi68 on 2008-10-25
The hal-applesmc package, now available in the mactel ppa, adds support for keyboard backlight via the applesmc sysfs interface.
```

sudo apt-get install hal-applesmc

```
then restart X (logout).

Enjoy!

---

### Post by kosumi68 on 2008-10-26
A mactel version of gnome-power-manager is available in the PPA, which solves the problem of non-responsive LCD brightness keys at startup on some Macbooks. If you have this problem, try this one out by selecting the mactel version in the synaptics package manager.

---

### Post by calebio on 2008-10-29
> **kosumi68 said:**
> A mactel version of gnome-power-manager is available in the PPA, which solves the problem of non-responsive LCD brightness keys at startup on some Macbooks. If you have this problem, try this one out by selecting the mactel version in the synaptics package manager.

I have installed hal-applesmc, bcm5974-dkms, and applesmc-dkms but touchpad (tap-to-click and two-finger scrolling, for instance) as well as backlighting still don't work. Can anyone provide more detailed instructions on the step necessary to enable these features? I'd be very happy to have them posted to [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

One note, /sys/class/leds/ doesn't exist on my system.

Another note, I installed the 32-bit version thinking it might get package support more quickly. As a result, ubuntu only recognizes 3 of my 4 GB of RAM.

---

### Post by kosumi68 on 2008-10-30
> **calebio said:**
> I have installed hal-applesmc, bcm5974-dkms, and applesmc-dkms but touchpad (tap-to-click and two-finger scrolling, for instance) as well as backlighting still don't work. Can anyone provide more detailed instructions on the step necessary to enable these features? I'd be very happy to have them posted to [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)


One detail that might have slipped: the applesmc module needs to be added to /etc/modules.

Regarding the trackpad, try running the script /usr/src/bcm*/scripts/bcm5974-diagnostics

---

### Post by cyberdork33 on 2008-10-30
> **calebio said:**
> I have installed hal-applesmc, bcm5974-dkms, and applesmc-dkms but touchpad (tap-to-click and two-finger scrolling, for instance) as well as backlighting still don't work. Can anyone provide more detailed instructions on the step necessary to enable these features? I'd be very happy to have them posted to [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

One note, /sys/class/leds/ doesn't exist on my system.
As kosumi68 already pointed out, you have to make sure the applesmc module loaded. adding it to /etc/modules as suggested and rebooting will do that for you.

> **calebio said:**
> Another note, I installed the 32-bit version thinking it might get package support more quickly. As a result, ubuntu only recognizes 3 of my 4 GB of RAM.That is normal. In a 32 bit environment, only 3GB of RAM is addressable. You should upgrade to the 64bit edition if you want to make sure you can use all 4GB. (64bit is very well supported)

---

### Post by ercoppa on 2008-10-30
Hi, I have a new MacBook (Unibody) 2.0Ghz. Can I help you (mactel team) in any way?

I have installed Ubuntu 8.10 and I have same trouble of calebio. The applesmc is loaded:
```
ercoppa@ercoppa-laptop:~$ lsmod | grep apple
applesmc               28592  0 
led_class              12164  1 applesmc
input_polldev          11912  1 applesmc
appleir                12544  0 
usbcore               148848  7 bcm5974,uvcvideo,appleir,usbhid,ehci_hcd,ohci_hcd

```
I have installed: bcm5974-dkms, gnome-power-manager 2.24.0-1mactel3,  applesmc-dkms, 

I am very interested to manage brightness (for battery life), how I can do this?

Other question:
- why the battery, also if attached with AC power, don't charging? Maybe the notebook uses all power capacity fornited by AC, it's possible? 
- how I can disable bluetooth (for battery life)?
- when I restart tha splash screen is only for half of the screen, how i can fix?

Thanks for the help

---

### Post by calebio on 2008-10-30
> **kosumi68 said:**
> Regarding the trackpad, try running the script /usr/src/bcm*/scripts/bcm5974-diagnostics

That output is as follows:
```
* Kernel version: 2.6.27-7-generic
* Synaptics version: 0.15.2-0ubuntu7
* USB device: Bus 003 Device 003: ID 05ac:0236 Apple, Inc.
* /lib/modules/2.6.27-7-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: has quirks, good
* /lib/modules/2.6.27-7-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is NOT registered
Please double-check the quirks settings in /etc/modprobe.d/bcm5974

```

And so, the only uncommented line from /etc/modprobe.d/bcm5974 reads
```
## quirks for the Macbook Pro Penryn (ANSI keyboard)
options usbhid quirks=0x05ac:0x0230:0x00020800

```

---

### Post by kosumi68 on 2008-10-30
> **calebio said:**
> 
* USB device: Bus 003 Device 003: ID 05ac:0236 Apple, Inc.

options usbhid quirks=0x05ac:0x0230:0x00020800


Now there is your culprit. If you had nothing installed before, and got this from the package, something is wrong in the post-install of the package. Something to watch out for.

Did you try commenting out the right line manually? For your model, that would be 0236.

---

### Post by calebio on 2008-10-30
> **kosumi68 said:**
> Now there is your culprit. If you had nothing installed before, and got this from the package, something is wrong in the post-install of the package. Something to watch out for.

Did you try commenting out the right line manually? For your model, that would be 0236.

This is a clean install. I re-installed 64-bit 8.10 to get all 4 GB of RAM (and to get 8.10 Release instead of beta). The only modifications i've made are to manually install applesmc-dkms, hal-applesmc, and bcm5974. Then i added applesmc to /etc/modprobe. I tried both the 0230 and the 0236 lines. neither seems to work (same '* /proc/bus/input/devices: module is NOT registered' line).

I added the following to xorg.conf:
```
Section "InputDevice"
          Identifier "Synaptics Touchpad"
          Driver "synaptics"
          Option "SendCoreEvents"          "True"
          Option "Protocol"                "auto-dev"
          Option "SHMConfig"               "True"
EndSection
```

---

### Post by windfix on 2008-10-31
I could use some follow up help - I must not have the correct repo enabled because I can't find hal-applemc via gui or command line.  Command line returns: 

Couldn't find package applesmc-dkms

and I don't know what the PPA is, help?

---

### Post by kosumi68 on 2008-10-31
> **windfix said:**
> I could use some follow up help - I must not have the correct repo enabled because I can't find hal-applemc via gui or command line.  Command line returns: 

Couldn't find package applesmc-dkms

and I don't know what the PPA is, help?

Hot off the presses: [https://help.ubuntu.com/community/Mactel PPA](https://help.ubuntu.com/community/Mactel PPA)

---

### Post by m.musashi on 2008-10-31
Has anyone had an issue where when rebooting it hangs and then the laptop starts beeping kind of loudly and you have to hard shutdown? Anyone know why and how to stop it?

---

### Post by kosumi68 on 2008-10-31
> **calebio said:**
> This is a clean install. I re-installed 64-bit 8.10 to get all 4 GB of RAM (and to get 8.10 Release instead of beta). The only modifications i've made are to manually install applesmc-dkms, hal-applesmc, and bcm5974. Then i added applesmc to /etc/modprobe. I tried both the 0230 and the 0236 lines. neither seems to work (same '* /proc/bus/input/devices: module is NOT registered' line).


Short version: it seems we now need to put this line earlier in the boot process, which is done by:

1. Make sure you use the 0236 line, it is the only correct one.

2. Copy that line into the file /etc/initramfs-tools/modules:
```

echo "options usbhid quirks=0x05ac:0x0236:0x00020800" | sudo tee -a /etc/initramfs-tools/modules

```

3. Run depmod:
```

sudo depmod -a

```

4. Update the ramdisk:
```

sudo update-initramfs -u -v -k `uname -r`

```

5. Reboot

Long version: Ok, time to talk about *why* this line is added. HID is the master input system in the linux kernel. It brings tremendous power, because it can recognize and intrepret just about any Human Interface Device out there. This standard is also used by Apple in the keyboard and trackpad interfaces.

However, in the bcm5974 version, the keyboard and trackpad are governed by the *same* USB device, only using different parts of it. This creates a problem, because HID finds the keyboard, and the trackpad, and happily adds them to its list of handled (and claimed) devices. When the bcm5974 driver comes in, which knows how to handle the multi-touch feature of the device, it cannot claim the interface, because it is already claimed by HID. To get things working, we need to tell HID to ignore the trackpad part of the device. This is what the quirks line does. ([https://help.ubuntu.com/community/RunDepmodAndReboot](https://help.ubuntu.com/community/RunDepmodAndReboot))

This worked most of the time in hardy. However, it is still not entirely solved, because Ubuntu uses a two-phase booting process, which is needed in order to determine what modules to load in the boot process. This two-phase booting is achieved using the ramdisk. The HID module is very central, so it gets loaded early, in the first phase. Thus, in order to fully tell HID to ignore the trackpad, we need to put this quirk line also on the ramdisk. ([https://help.ubuntu.com/community/Update the Ramdisk](https://help.ubuntu.com/community/Update the Ramdisk))

---

### Post by kosumi68 on 2008-10-31
> **m.musashi said:**
> Has anyone had an issue where when rebooting it hangs and then the laptop starts beeping kind of loudly and you have to hard shutdown? Anyone know why and how to stop it?

Beeping could be the hardware complaining. I does not sound good. Intrepid seems to have introduced something that does this; it happens sometimes to me during shutdown of my MBA, but it is not everytime, and not so serious.

Something to watch out for. Someone with more apple hardware knowledge ought to be able to tell what it is.

---

### Post by phoenix_snake on 2008-10-31
can I ask something here? why would regular users want linux on a mac?

---

### Post by hanzomon4 on 2008-10-31
A working Ubuntu install on a macbook pro changes the soul of the machine. With a good theme and good compiz settings Ubuntu simply shines on this apple hardware. I Now have a perfect setup(all things working) except for a sound issue that's causing flash and videos to stutter and act stupid. OSX does everything I need, however Ubuntu is simply different and thats where the appeal lies for me.

---

### Post by phoenix_snake on 2008-10-31
so compiz is the only reason? I don't think there is anything special about it at all, its just compositing something OS X has done since 10.0 ;)

---

### Post by ercoppa on 2008-10-31
> why would regular users want linux on a mac?
Because Mac OS X is not GNU/Linux. See GNOME/KDE, some killer-app (also only text-based), the comunity, the philosophia under this OS.

> Has anyone had an issue where when rebooting it hangs and then the laptop starts beeping kind of loudly and you have to hard shutdown? Anyone know why and how to stop it?
Also me (only during reboot).
[QUOTE=me in precedent post]
- why the battery, also if attached with AC power, don't charging? Maybe the notebook uses all power capacity fornited by AC, it's possible?[/QUOTE]
Now Ubuntu charges my battery :).

My output:
```
ercoppa@ercoppa-laptop:~$ /usr/src/bcm*/scripts/bcm5974-diagnostics
-----------------------------------------------------------------------
* Kernel version: 2.6.27-7-generic
* Synaptics version: 0.15.2-0ubuntu7
* USB device: Bus 003 Device 003: ID 05ac:0237 Apple, Inc.
* /lib/modules/2.6.27-7-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: has quirks, good
* /lib/modules/2.6.27-7-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is NOT registered
Please double-check the quirks settings in /etc/modprobe.d/bcm5974

```

//EDIT with this in xorg.conf:
```
Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents"          "True"
        Option "Protocol"                "auto-dev"
        Option "SHMConfig"               "True"
	Option          "ClickFinger1"  "1"
	Option          "ClickFinger2"  "2"
	Option          "ClickFinger3"  "3" 
EndSection

```
The trackpad work good. Right click with two finger click, and scrolling with two finger.

Any idea for the brightness?

---

### Post by cyberdork33 on 2008-10-31
> **phoenix_snake said:**
> can I ask something here? why would regular users want linux on a mac?

> **ercoppa said:**
> Because Mac OS X is not GNU/Linux. See GNOME/KDE, some killer-app (also only text-based), the comunity, the philosophia under this OS.

There is a recent thread discussing this same topic. Please discuss there.
[http://ubuntuforums.org/showthread.php?t=959743](http://ubuntuforums.org/showthread.php?t=959743)

phoenix_snake, it would be much appreciated if you could not make such an off topic reply. You are welcome to make new threads for new topics. Thanks.

---

### Post by _mario_ on 2008-10-31
> **kosumi68 said:**
> 
2. Copy that line into the file /etc/initramfs-tools/modules:
```

echo "options usbhid quirks=0x05ac:0x0236:0x00020800" | sudo tee -a /etc/initramfs-tools/modules

```
4. Update the ramdisk:
```

sudo update-initramfs -u -v -k `uname -r`

```
This worked most of the time in hardy. However, it is still not entirely solved, because Ubuntu uses a two-phase booting process, which is needed in order to determine what modules to load in the boot process. This two-phase booting is achieved using the ramdisk. The HID module is very central, so it gets loaded early, in the first phase. Thus, in order to fully tell HID to ignore the trackpad, we need to put this quirk line also on the ramdisk.
is this really necessary? this way? i mean: the whole /etc/modprobe.d/* tree gets incorporated into the ramdisk. have a look with:
```
sudo gunzip -cd /boot/initrd.img-2.6.27-7-generic | cpio --list
``` so there should be no reason to patch /etc/initramfs-tools/modules, a file that is supposed to tell which additional modules to include. it is neither a modules file, nor do option lines make sense there.

sorry for this boldfaced comment, but i think we should fix things the right way and adding a file in /etc/modprobe.d/ and rebuilding the ramdisk should suffice.

ciao,
Mario

---

### Post by phoenix_snake on 2008-10-31
> **cyberdork33 said:**
> There is a recent thread discussing this same topic. Please discuss there.
[http://ubuntuforums.org/showthread.php?t=959743](http://ubuntuforums.org/showthread.php?t=959743)

phoenix_snake, it would be much appreciated if you could not make such an off topic reply. You are welcome to make new threads for new topics. Thanks.

no problem, thanks for pointing to the thread :)

---

### Post by kosumi68 on 2008-10-31
> **_mario_ said:**
> is this really necessary? this way? i mean: the whole /etc/modprobe.d/* tree gets incorporated into the ramdisk. have a look with:
```
sudo gunzip -cd /boot/initrd.img-2.6.27-7-generic | cpio --list
``` so there should be no reason to patch /etc/initramfs-tools/modules, a file that is supposed to tell which additional modules to include. it is neither a modules file, nor do option lines make sense there.

sorry for this boldfaced comment, but i think we should fix things the right way and adding a file in /etc/modprobe.d/ and rebuilding the ramdisk should suffice.

ciao,
Mario

Thanks mario, doing things the right way *is* the right way, so no sorries on my behalf. However, in my experience, the method you describe does not work properly. It would take some digging to sort out precisely why; I suppose it fell down pretty far on my list, but as an example: On my MBA, there is a device I want HID to ignore. Putting the quirk line in /etc/modprobe.d/* only, it still pops up in X. Putting the quirks line in etc/initramfs-tools/modules makes it disappear from HID and consequently from X.

PS: it might have to do with the two-phase booting: [https://help.ubuntu.com/community/Update the Ramdisk](https://help.ubuntu.com/community/Update the Ramdisk)

---

### Post by _mario_ on 2008-10-31
> **kosumi68 said:**
> Thanks mario, doing things the right way *is* the right way, so no sorries on my behalf. However, in my experience, the method you describe does not work properly.
good point. and very funny. according its header the syntax for /etc/initramfs-tools/modules is: 'module_name [args ...]'. so there must be a module called 'options'...

ciao,
Mario

---

### Post by kosumi68 on 2008-10-31
> **_mario_ said:**
> good point. and very funny. according its header the syntax for /etc/initramfs-tools/modules is: 'module_name [args ...]'. so there must be a module called 'options'...

ciao,
Mario

It does say that, but try it!

Now, since you have pointed at this, it is only fair that you come up with a proper way of doing it. That's how it works, you know ;-)

---

### Post by _mario_ on 2008-10-31
> **kosumi68 said:**
> It does say that, but try it!
Now, since you have pointed at this, it is only fair that you come up with a proper way of doing it. That's how it works, you know ;-)

ok, here we go ;-): i tried to add the line
```
options usbhid quirks=0x05ac:0x0236:0x00020800
``` as you suggested to /etc/initramfs-tools/modules and rebuilt the ramdisk.

after restoring the old state and unpacking both ramdisks the only difference was:
```
diff -r clean/conf/modules test/conf/modules
0a1
> options usbhid quirks=0x05ac:0x0236:0x00020800

``` (clean and test being the top-level directories).

grepping inside these files yields that the conf/modules file is evaluted in scripts/functions function load_modules at line 279 and following. this functions reads this file line by line (skipping empty lines and comments) and calls modprobe thereafter, e.g.:
```
modprobe options usbhid quirks=0x05ac:0x0236:0x00020800
```
that cannot work, since there's no module called 'options'. so we either remove the first word 'options' for this statement to have any effect, or completely remove it. it is very interesting that such a line actually does work for you. some sort of timing bug?

however, since this scripts calls modprobe (from the ramdisk), which in turn evaluates the files in /etc/modprobe.d/ (also in the ramdisk) to load modules with the right parameters, what's the difference?

ciao,
Mario

---

### Post by kosumi68 on 2008-10-31
> **_mario_ said:**
> ok, here we go ;-): i tried to add the line
```
options usbhid quirks=0x05ac:0x0236:0x00020800
``` as you suggested to /etc/initramfs-tools/modules and rebuilt the ramdisk.

after restoring the old state and unpacking both ramdisks the only difference was:
```
diff -r clean/conf/modules test/conf/modules
0a1
> options usbhid quirks=0x05ac:0x0236:0x00020800

``` (clean and test being the top-level directories).

grepping inside these files yields that the conf/modules file is evaluted in scripts/functions function load_modules at line 279 and following. this functions reads this file line by line (skipping empty lines and comments) and calls modprobe thereafter, e.g.:
```
modprobe options usbhid quirks=0x05ac:0x0236:0x00020800
```
that cannot work, since there's no module called 'options'. so we either remove the first word 'options' for this statement to have any effect, or completely remove it. it is very interesting that such a line actually does work for you. some sort of timing bug?

however, since this scripts calls modprobe (from the ramdisk), which in turn evaluates the files in /etc/modprobe.d/ (also in the ramdisk) to load modules with the right parameters, what's the difference?

ciao,
Mario

Mario, you rock :-)

The thing I still don't understand is what actions are performed during phase one of the boot, and what actions are performed during phase two. Could it be that 'this script' is performed during phase two only?

---

### Post by _mario_ on 2008-10-31
> **kosumi68 said:**
> The thing I still don't understand is what actions are performed during phase one of the boot, and what actions are performed during phase two. Could it be that 'this script' is performed during phase two only?
i don't know. really. in particular what is phase 1 or 2. i mean: an initial ramdisk is essentially a compressed file system that is loaded by the boot loader (e.g., grub) for the kernel to perform certain actions before the root file system gets mounted. the most notable example is loading a driver for the root filesystem (in earlier days we had to compile it in).

this compressed file system after uncompression is "mounted" to /. to be more precisely it is directly uncompressed into the kernel's filesystem buffer (where I/O operations are cached). after the root filesystem is mounted to / those stuff gets dropped.

ideally the initial ramdisk and the real filesystem are consistent. that's why we have to rebuild it sometimes. everything else is completely equal to normally running linux, except for some nice scripting/configuration mechanism to load/unload modules or start servers (e.g., ssh to wait for a pass-phrase to decrypt the root filesystem).

but that doesn't affect modules. modules that are loaded from the ramdisk remain loaded after starting the "traditional" boot process (starting init, calling runlevel scripts, ...). its the same running kernel, isn't it. the only notable difference is: a module that was loaded from the ramdisk, isn't "reloaded" later. that means an option missing in the ramdisk, but being present in the filesystem (e.g., in /etc/modprobe.d/) won't have any effect.

ciao,
Mario

---

### Post by kosumi68 on 2008-10-31
I was wrong.

I just ran some ten reboots, testing this again. It seems there is a strange randomness to what options take effect. Sometimes the excess device appears as an input device, sometimes it does not. Thus, the line starting with 'options' has no effect, just as you say. Removing 'options' seems to yield a predictable result, though, so at least something is logical. I will change the recommendations accordingly.

I am also leaning towards adding these quirks to the hid-dkms module, since that is where it will eventually end up, upstream. It would remove the quirks problem once and for all.

It must be halloween that does it. :-)

---

### Post by kosumi68 on 2008-10-31
Ok, version 1.1.0 of bcm5974-dkms is out. This version should solve the configuration problems for the new unibody macbooks. The /etc/modprobe.d/bcm5974 file has been removed; there is no longer any need to think about ramdisks or the like. Just install it from the mactel PPA (reload the sources first to get the new version).

---

### Post by manjeera on 2008-10-31
I would like to know this too.

---

### Post by manjeera on 2008-10-31
Anypone foudn the answer yet?

---

### Post by manjeera on 2008-10-31
Macbook is really limited:(

---

### Post by jackoverfull on 2008-10-31
> **manjeera said:**
> Anypone foudn the answer yet?
what is the question?

> Macbook is really limited:sad:
i don't think so.

---

### Post by cyberdork33 on 2008-11-01
> **manjeera said:**
> I would like to know this too.

Did you read the thread first?

---

### Post by calebio on 2008-11-02
I have updated [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) with some of these changes that worked for me.

---

### Post by lynks on 2008-11-02
> **calebio said:**
> I have updated [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) with some of these changes that worked for me.

With this configuration, the two finger horizontal scroll doesn't run, i've added those lines in /etc/X/xorg.conf to solve this.

How is possible that i had to add this lines in /etc/X/xorg.conf if they are already in the "hal policy file"  /etc/hal/fdi/policy/11-x11-synaptics.fdi ?

> 
Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents"          "True"
        Option "Protocol"                "auto-dev"
        Option "SHMConfig"               "True"
	Option          "ClickFinger1"  "1"
	Option          "ClickFinger2"  "3"
	Option          "ClickFinger3"  "2"
	Option		"TapButton1"    "0"
	Option          "TapButton2"    "0"
        Option          "TapButton3"    "0"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"
EndSection



Another one. Somebody has achieve to run the backlight level with the FN keys? 

thanks for your time

---

### Post by kosumi68 on 2008-11-02
> **lynks said:**
> 
How is possible that i had to add this lines in /etc/X/xorg.conf if they are already in the "hal policy file"  /etc/hal/fdi/policy/11-x11-synaptics.fdi ?


The xorg.conf way and the fdi way don't play well together - you need t remove your synaptics section all together from your xorg.conf file to make sure things work as expected.

---

### Post by beauman on 2008-11-02
Hi!

A few questions concerning a MacBook 4,1 and Ubuntu:

- Did somebody has found a way to make the mic work? 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289552]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289552")

- Now as I have extracted the usb-driver for the iSight, I like
  to use it in skype. Has anybody managed to make a video conference
  with skype?

- On the Mac side I tried to install an ext3fs driver. I installed "Ext2FS_1.4d4.dmg", but it complains about a corrupt ext3fs file system.
Can somebody recommend a good driver?

- Did somebody experience problems burning CD's? It seems I can't burn Medion CD's. Strange...

- Did somebody manage to make a dualhead setup?

Thanks and friendly regards,
beauman

P.S.: There is a little summary of my installation of Ibex on the MacBook using refit as bootmanager,
[http://ubuntuforums.org/showthread.php?t=958326](http://ubuntuforums.org/showthread.php?t=958326)

---

### Post by lynks on 2008-11-02
> **kosumi68 said:**
> The xorg.conf way and the fdi way don't play well together - you need t remove your synaptics section all together from your xorg.conf file to make sure things work as expected.

Thanks a lot, i have solved with your advice, but I've had to run it (two fingers horizontal scroll) through gsynaptics.


Other question for the forum :), when I reboot or halt the computer, a hardware sound appears, the screen becomes dark but doesn't halts.

---

### Post by beauman on 2008-11-02
> **lynks said:**
> ... when I reboot or halt the computer, a hardware sound appears, the screen becomes dark but doesn't halts.

Do you mean you have installed refit on your macbook and it does
not start it? Then you have to run the enable script under OS X
in a terminal. See the remarks of my install off refit 
on the link I posted above.

---

### Post by cyberdork33 on 2008-11-02
> **beauman said:**
> Do you mean you have installed refit on your macbook and it does
not start it? Then you have to run the enable script under OS X
in a terminal. See the remarks of my install off refit 
on the link I posted above.
he is talking about shutdown. Many people have mentioned this.

---

### Post by cyberdork33 on 2008-11-02
> **beauman said:**
> P.S.: There is a little summary of my installation of Ibex on the MacBook using refit as bootmanager,
[http://ubuntuforums.org/showthread.php?t=958326](http://ubuntuforums.org/showthread.php?t=958326)
Beauman, I noticed that you linked to the main MacBook wiki page. Since you are dealing with the MacBook4,1 you should check this one:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

That page applies to both MacBook3,1 and MacBook4,1. If there is anything there that needs to be updated please do so!

---

### Post by kosumi68 on 2008-11-02
... there is also the option of creating a new page, specifically for MacBookPro4,1 and Intrepid. Many things changed (to the better) with Intrepid. The page becomes much cleaner, and less confusing both to Hardy and Intrepid users. Checkout this page: [https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid](https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid)

---

### Post by jackoverfull on 2008-11-02
> **beauman said:**
> Hi!


- On the Mac side I tried to install an ext3fs driver. I installed "Ext2FS_1.4d4.dmg", but it complains about a corrupt ext3fs file system.
Can somebody recommend a good driver?

i'd avoid that driver: it's old and very buggy.
Unluckily, it seems to be the only driver on the net…

---

### Post by cyberdork33 on 2008-11-02
> **jackoverfull said:**
> i'd avoid that driver: It's old and very buggy.
Unluckily, it seems to be the only driver on the net…
+1

---

### Post by windfix on 2008-11-02
> **phoenix_snake said:**
> can I ask something here? why would regular users want linux on a mac?

Speaking for me:

1. I can't stand Apple's overall philosophy: Do it Steve's way, and shut up.  Simple example: OSX power management - no option to leave your laptop running when you close the lid.  It's either Sleep, or nothing.  I HATE that.

2. Linux is just a better model.  Software for any purpose available without hassles. Worldwide community of smart people cooperating.

I needed OSX so I can support users in my organisation that are Mac fanatics.  Hence, I dual boot, and doing OSX on Mac hardware is the only legal way to do that - but I rarely touch OSX.

---

### Post by jackoverfull on 2008-11-02
> **windfix said:**
> Speaking for me:

1. I can't stand Apple's overall philosophy: Do it Steve's way, and shut up.  Simple example: OSX power management - no option to leave your laptop running when you close the lid.  It's either Sleep, or nothing.  I HATE that.

[http://support.apple.com/kb/HT3131?locale=it_IT](http://support.apple.com/kb/HT3131?locale=it_IT)

Anyway, this is not the right topic to talk about that.

---

### Post by beauman on 2008-11-03
> **cyberdork33 said:**
> Beauman, I noticed that you linked to the main MacBook wiki page. Since you are dealing with the MacBook4,1 you should check this one:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

That page applies to both MacBook3,1 and MacBook4,1. If there is anything there that needs to be updated please do so!

Ok. Give me a little time. I am thinking of a meta page for
all the different wiki pages for the macbook. It should contain some
kind of a matrix with supported features over hardware. It should
also guide the user to the right wiki.

I will make a concept and then start a discussion thread here.
Maybe I can find wiki mentainers for all different MacBooks. I
could also be the mentainer for the MB 4,1 spezific wiki.

Regards, beauman

---

### Post by cyberdork33 on 2008-11-03
> **beauman said:**
> Ok. Give me a little time. I am thinking of a meta page for
all the different wiki pages for the macbook. It should contain some
kind of a matrix with supported features over hardware. It should
also guide the user to the right wiki.

I will make a concept and then start a discussion thread here.
Maybe I can find wiki mentainers for all different MacBooks. I
could also be the mentainer for the MB 4,1 spezific wiki.

Regards, beauman

Already ahead of you:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

We have started trying to consolidate a lot of information in order to better maintain it. I already have a single page for iSight that is just linked to from each top level wiki page. Kosumi has also been sorting things out a bit. If there is anywhere that you can contribute, please do! 

We probably need to create more pages under the MactelSupportTeam Page linked above (guidelines for the documentation?) P.S. Let's try to keep these management-type discussions in separate threads though if we can... we tend to take over support threads too often.

---

### Post by beauman on 2008-11-03
> **jackoverfull said:**
> i'd avoid that driver: it's old and very buggy.
Unluckily, it seems to be the only driver on the net…

I tried today to load the driver by hand in a terminal under OS X.
It showed a "bluescreen" in all kind of languages including chineese
that I have to hold the power button for 5 sec :lolflag:

---

### Post by jackoverfull on 2008-11-03
> **beauman said:**
> I tried today to load the driver by hand in a terminal under OS X.
It showed a "bluescreen" in all kind of languages including chineese
that I have to hold the power button for 5 sec :lolflag:
a kernel panic…

---

### Post by beauman on 2008-11-03
> **cyberdork33 said:**
> Already ahead of you:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

We have started trying to consolidate a lot of information in order to better maintain it. I already have a single page for iSight that is just linked to from each top level wiki page. Kosumi has also been sorting things out a bit. If there is anywhere that you can contribute, please do! 

We probably need to create more pages under the MactelSupportTeam Page linked above (guidelines for the documentation?) P.S. Let's try to keep these management-type discussions in separate threads though if we can... we tend to take over support threads too often.

Ok. I have a close look on what exists at the moment.

I installed ubuntu on the mac two weeks ago for the first time.
And I can just say, that the pages are a bit confusing.

You have noticed, that I looked in the wrong wiki.
I did know about the Santa Rosa pages, I found them in the
literature list of an article about installing ubuntu on a mac
book in the german magazine "CT". But I didn't care about it, because
1) its written for gutsy 2) I don't know what Santa Rosa is.
The "Mac geek" in my department didn't knew about it today either.

The MacBook has this really really great feature to give an unique
hardware identification. So, if anybody refers to a MacBook in a wiki
it should always be "MacBook, + identification string".

A newbee like me should be able to find the right wiki in just a matter
of seconds. This also means, that the actual page "MacBook ubuntu user documentation" must be renamed.

Yesterday I logged into the ubuntu wiki pages to see, how I can edit it.
I found so many wikis about the macbook, I never saw before. And I
googled it about a million times.

I also think, sombody how likes to install ubuntu will/should always 
use the latest version. So all wikis should be up-to-date
with the RC comming out.

Please give me some time. I really like to see what you already did
and use it. I also like to discuss everything here. Nobody can do
this alone, because it needs a lot of MacBook owners to report
their experiences.

I make up my mind and then I'am going to start a new thread, as you suggested.

Friendly Regards!
Beauman

---

### Post by cyberdork33 on 2008-11-03
> **beauman said:**
> I make up my mind and then I'am going to start a new thread, as you suggested.
I am going to go ahead and make one.
[http://ubuntuforums.org/showthread.php?t=969360](http://ubuntuforums.org/showthread.php?t=969360)

---

### Post by lynks on 2008-11-03
I have noticed that, since the keyboard backlight runs the MAYUS key led doesn't work.

I read that gnome-power-manager (mactel version) fixes the LCD backlight control, but it doesn't work for me.

Any suggestion?

Thanks all. ):P

---

### Post by kosumi68 on 2008-11-03
You need the applesmc-dkms module, and the line 'applesmc' in /etc/modules. Also, get rid of (uninstall) mouseemu. Restart. Hopefully this helps!

---

### Post by lynks on 2008-11-03
> **kosumi68 said:**
> You need the applesmc-dkms module, and the line 'applesmc' in /etc/modules. Also, get rid of (uninstall) mouseemu. Restart. Hopefully this helps!

I have uninstalled mouseemu and WORKS FOR ME !!!!!. Mayus led runs good.

Thanks for your tip.

---

### Post by FLCLFan on 2008-11-05
Does anyone know where the source for applesmc-dkms so I can try to compile it in Arch Linux? Or will this compile and work in Arch?

---

### Post by cyberdork33 on 2008-11-05
> **FLCLFan said:**
> Does anyone know where the source for applesmc-dkms so I can try to compile it in Arch Linux? Or will this compile and work in Arch?
Go here:
[https://edge.launchpad.net/~mactel-support/+archive](https://edge.launchpad.net/~mactel-support/+archive)

Then click the triangle next to "applesmc-dkms" and you can see the downloads for it.

---

### Post by kosumi68 on 2008-11-05
> **FLCLFan said:**
> Does anyone know where the source for applesmc-dkms so I can try to compile it in Arch Linux? Or will this compile and work in Arch?

If you can install debian packages, you can certainly try to install it. Given that the dependencies are fulfilled, it should work. Source: like with all debian packages, just do 'apt-get source package-name' ;-)

---

### Post by kayalion on 2008-11-08
Hello,

Great work has been done here! I'm pretty amazed to see me skyping using the iSight and built-in mic out of the box. Thanks to all involved.

I still have a problem with the trackpad though. Only left mouse click and movement seem to work.

I've followed the instructions on [https://help.ubuntu.com/community/MacBook%20Aluminum]("https://help.ubuntu.com/community/MacBook%20Aluminum") to install the system, but used the released 8.10, 64 bit version instead.

When reading this thread, I assume the patches made during are mainstream now?

In Xorg.0.log I noticed the following:
```
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 2.0.99
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device applesmc
(**) applesmc: always reports core events
(**) applesmc: Device: "/dev/input/event11"
(II) applesmc: Found x and y absolute axes
(WW) applesmc: Don't know how to use device
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "applesmc"
(EE) config/hal: NewInputDeviceRequest failed

```

The applesmc module is listed in lsmod.

This log snippet is without mouseemu. I did reinstall it since it gives me the right mouse click with F12. 

Can somebody help me getting this work?

Another different thing I noticed is my fn key doesn't work, so I have no page up, page down, home and end. I've read this should work out of the box, but not on my system. Anyone the same problem? Clues?

Thanks in advance

---

### Post by Nikos.Alexandris on 2008-11-08
> **kayalion said:**
> Hello,

Great work has been done here! I'm pretty amazed to see me skyping using the iSight and built-in mic out of the box. Thanks to all involved.

[...]

Do you really got the mic working? I am trying *hard* different options but no luck. Do you mind sharing some sound options?

Thank you, Nikos

---

### Post by cyberdork33 on 2008-11-08
> **kayalion said:**
> When reading this thread, I assume the patches made during are mainstream now?
Check for newer packages here:
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

### Post by kayalion on 2008-11-09
> **Nikos.Alexandris said:**
> Do you really got the mic working? I am trying *hard* different options but no luck. Do you mind sharing some sound options?

Thank you, Nikos

Well, first my mic didn't work, so I opened my volume control. In the preferences of this you have at the bottom 3 options with input source, I checked them all. Then in the volume control, under the tab options, I selected front mic in the 3 input source select boxes. 

In skype, I also set the sound in and sound out to HDA NVidia (hw:NVidia,0)

This seemed to get my mic working in skype.

Now today, I noticed my audio cd's aren't working with these options, So now I selected in one of the input sources, CD and rebooted which made my audio cd work again. skype still works but they do not work at the same time ...

Hope this helps.

> **cyberdork33 said:**
> Check for newer packages here:
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

Alright, this seemed to do the trick. Maybe there should be a link to that page on [https://help.ubuntu.com/community/MacBook%20Aluminum?](https://help.ubuntu.com/community/MacBook%20Aluminum?)

Anyway, thank you.

---

### Post by Nikos.Alexandris on 2008-11-09
> **kayalion said:**
> Well, first my mic didn't work, so I opened my volume control. In the preferences of this you have at the bottom 3 options with input source, I checked them all. Then in the volume control, under the tab options, I selected front mic in the 3 input source select boxes. 

In skype, I also set the sound in and sound out to HDA NVidia (hw:NVidia,0)

This seemed to get my mic working in skype.

Now today, I noticed my audio cd's aren't working with these options, So now I selected in one of the input sources, CD and rebooted which made my audio cd work again. skype still works but they do not work at the same time ...

Hope this helps.


Yep, it did it! I wonder what I was doing wrong... I thought I had tried them all. I just used the first "Capture" column under Recordings tab which corresponds to the first "Input source" in the Options tab.

The problem that skype and others don't work together is (at least for me) known also in other computers. I never really got it working so I just got used to it :-) But it would be nice if they could work together.

Thank you, Nikos

---

### Post by Tidaku on 2008-11-09
I've installed intrepid 64bit on the new MacBook and the trackpad, iSight and nvidia chipset work.

However, I am encountering problems with suspend / resume. It takes about 20 seconds to enter suspend mode, and about 30 seconds to resume. Comparing this with OSX... it's annoying.

Trying to solve this problem:
I've installed 'laptop-mode-tools' and enabled it '/etc/default/acpi-support'.

Tried this "fix": [here]("http://www.spinthiras.net/2008/07/20/ubuntu-resume-from-sleep-slow-problem-fixed/"), in short: disable everything except 'auto lo' in '/etc/network/interfaces'.

Next I tried editing '/etc/laptop-mode/laptop-mode.conf' with various settings.

After all this still no succes. Is this a common problem? Can I help to fix this?

---

### Post by Nikos.Alexandris on 2008-11-09
> **Tidaku said:**
> 
However, I am encountering problems with suspend / resume. It takes about 20 seconds to enter suspend mode, and about 30 seconds to resume. Comparing this with OSX... it's annoying.

Trying to solve this problem:
I've installed 'laptop-mode-tools' and enabled it '/etc/default/acpi-support'.

Tried this "fix": [here]("http://www.spinthiras.net/2008/07/20/ubuntu-resume-from-sleep-slow-problem-fixed/"), in short: disable everything except 'auto lo' in '/etc/network/interfaces'.

Next I tried editing '/etc/laptop-mode/laptop-mode.conf' with various settings.

After all this still no succes. Is this a common problem? Can I help to fix this?

Same problem here. Takes too long and after waking up the LCD turned on at full brightness!! Anything that could help the brightness issue?

---

### Post by cyberdork33 on 2008-11-09
> **kayalion said:**
> Alright, this seemed to do the trick. Maybe there should be a link to that page on [https://help.ubuntu.com/community/MacBook%20Aluminum]("https://help.ubuntu.com/community/MacBook%20Aluminum?")
The PPA is mentioned in section 5 of that wiki page.

---

### Post by kayalion on 2008-11-10
> **cyberdork33 said:**
> The PPA is mentioned in section 5 of that wiki page.

True, but it says to install only hal-applesmc and applesmc-dkm while you need more than this ...

Maybe put the link in that section to get an overview of the packages in that repository?

---

### Post by cyberdork33 on 2008-11-10
> **kayalion said:**
> True, but it says to install only hal-applesmc and applesmc-dkm while you need more than this ...

Maybe put the link in that section to get an overview of the packages in that repository?
Ah OK. I see now. I will do that. Thanks.

---

### Post by eternalsword on 2008-11-13
anyone have any luck with getting the built in speakers working?

---

### Post by Nikos.Alexandris on 2008-11-13
> **eternalsword said:**
> anyone have any luck with getting the built in speakers working?

Yes! Several people got them working and I got only the "right" speaker working :D

Look here: [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

Good Luck!

---

### Post by eternalsword on 2008-11-14
I was able to get the sound working, thanks.  I got the wireless working with the restricted broadcom driver, however I have not yet been able to get it working with wpa enterprise.  Any help would be appreciated.

---

### Post by joka. on 2008-11-16
For those of you who got a Macbook Pro and installed Ubuntu on it. I'm about to go down the same path, but with triple boot [Vista and Ubuntu]. I was just wondering if the blacklit keyboard works as well in Ubuntu? Also, what does "nvidia chipset - just use the restricted drivers tool for nvidia 177" mean? Can someone put it in different terms? Thanks.

Maybe I should wait a couple more weeks and see if everything gets fixed before getting it. heh

---

### Post by jackoverfull on 2008-11-16
my macbok pro finally arrived. (after 26 days…)

yesterday i tried to boot kubuntu (i plan to install ubuntu, but i wanted to give a look at kde4, since i never did before…) it booted, but the gui was all like every item was magnified, totally unusable. :confused:

the safe-graphic mode only led to a black screen. 

Any hint?

---

### Post by dmanskiman on 2008-11-16
I tried using the live cd with Hardy on the original MacBookPro and everything worked just fine, wireless and all.  Obviously things like multitouch and isight don't work out of the box.  The problem probably with the new mbp is it has two graphics cards some how;at least one I heard is pretty non standard.  Is there any way to boot ubuntu up in lower graphics (card) mode?

---

### Post by m.musashi on 2008-11-16
> **jackoverfull said:**
> my macbok pro finally arrived. (after 26 days&#8230;)

yesterday i tried to boot kubuntu (i plan to install ubuntu, but i wanted to give a look at kde4, since i never did before&#8230;) it booted, but the gui was all like every item was magnified, totally unusable. :confused:

the safe-graphic mode only led to a black screen. 

Any hint?

Not exactly a hint, but I used virtualbox in OSX to try out Kubuntu. Like you I wanted to see what it was like but after using it a bit I like regular Ubuntu better. I know that installing Ubuntu on a macbook works with a few tweaks. I know that in my case I had warnings about low resolution mode when I installed an only after installing the nvidia driver did things work right. It may be that kubuntu isn't handling that quite as well but that's just a guess. Once you install it, see if installing the nvidia driver helps. If not, then I'm not sure. If you have the dual graphics version of the MBP then that may also have something to do with it.

---

### Post by jackoverfull on 2008-11-16
> **m.musashi said:**
> Not exactly a hint, but I used virtualbox in OSX to try out Kubuntu. 

exactly what i did then, with qemu…:)

anyway, i will install ubuntu with gnome. ;-)

---

### Post by Yellowbelly on 2008-11-17
I'm seriously considering getting a new macbook and throwing ubuntu and windows 7 when it comes out on it. Is this a good idea or is it really more trouble than it's worth. For the record, I'm not a crazy unix hacker so any kinda coding I do to make stuff work is borrowed. What kinda trouble would I run into if I got a new macb? Would I be better off with getting something else?

---

### Post by m.musashi on 2008-11-17
> **Yellowbelly said:**
> I'm seriously considering getting a new macbook and throwing ubuntu and windows 7 when it comes out on it. Is this a good idea or is it really more trouble than it's worth. For the record, I'm not a crazy unix hacker so any kinda coding I do to make stuff work is borrowed. What kinda trouble would I run into if I got a new macb? Would I be better off with getting something else?

Definitely a nice machine for running Ubuntu but as they are not designed for Ubuntu (or any Linux) you will probably have to encourage it a bit. However, the longer they are out the more issues that will get fixed. However, I can't see any good reason for buying windows to put on one. They come with OSX which is probably a better all around OS than windows. Yes, if you are a gamer then it may be more of an issue but I think less so than several years ago. If you really want windows then just buy a windows PC and put Ubuntu on with it. Most worthwhile software also runs on OSX so I never really understood why people wanted to run windows on a mac and if it's for games macs were generally not great gaming hardware anyway (although the new ones I think are changing that perception a bit).

Anyway, having put Ubuntu on a new mac I can say it's pretty painless. There are a few issues and there some easy solutions - you just have to follow a few directions and most are described or pointed to in this thread. As it stands, mine has most things working now. One downside at the moment is you can adjust screen brightness. I'm sure there will be a fix for that before long but for now it's just stuck at all or nearly all brightness.

---

### Post by the_29 on 2008-11-19
Ahoi!

Sry if that answer is already in the thread, but i just read some pages.

In the HowTo for the Macbook 5,1 (have Macbook 5,1 2.4ghz with LG Panel) is described that the "Left-click, basic trackpad and two-finger vertical scrolling work out of the box."
But for me that isnt working :(

And when i modified /etc/hal/fdi/policy/11-x11-synaptics.fdi and set this entries:
<merge key="input.x11_options.TapButton1" type="string">1</merge>
  <merge key="input.x11_options.SHMConfig" type="string">True</merge>
Tapping is also not working!

Anyone knows why?

---

### Post by stillingen on 2008-11-19
I´m running in to a problem with installing Grub on my Macbook

I´ve followed the instructions on the wiki page, but the installation is failing at 94% and an error saying. "Executing &#501;rub-install /dev/sda´ failed 

**Print from messages**

Nov 19 16:09:22 mint grub-installer: info: Installing grub on '/dev/sda'
Nov 19 16:09:22 mint grub-installer: info: grub-install supports --no-floppy
Nov 19 16:09:22 mint grub-installer: info: Running chroot /target grub-install  --no-floppy  "/dev/sda"
Nov 19 16:09:22 mint grub-installer: Probing devices to guess BIOS drives. This may take a long time.
Nov 19 16:09:22 mint grub-installer: Searching for GRUB installation directory ... 
Nov 19 16:09:22 mint grub-installer: found: /boot/grub
Nov 19 16:09:27 mint grub-installer: The file /boot/grub/stage1 not read correctly.
Nov 19 16:09:27 mint grub-installer: error: Running 'grub-install  --no-floppy  "/dev/sda"' failed.

I´ve googled, but haven´t found any solution that sorts my problem. Anyone else run in to this issue and got a fix for it?

---

### Post by joka. on 2008-11-20
> **bazzwaa said:**
> 2 finger scroll works, zoom works, rotate does not function as on osx.  All in all this is good news, we have the touch pad working for multitouch on macbook pro. Congrats.

whats the next step?

Hey, I've been reading along and a bit confused... do you mind editing/posting on [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) how you got the multitouch to work and any other things you have to do for the touchpad? Thanks.

I'm about to get the new MBP, but I want to wait til everything is set before getting it.

Also, can anyone tell me if the backlight on the keyboard works? I think I read somewhere in this post that it doesn't? If not can someone explain how to fix it?

To everyone: How are your MBP running so far? What other problems need to be addressed?

---

### Post by Tidaku on 2008-11-20
> **joka. said:**
> Hey, I've been reading along and a bit confused... do you mind editing/posting on [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) how you got the multitouch to work and any other things you have to do for the touchpad? Thanks.

I'm about to get the new MBP, but I want to wait til everything is set before getting it.

Also, can anyone tell me if the backlight on the keyboard works? I think I read somewhere in this post that it doesn't? If not can someone explain how to fix it?

To everyone: How are your MBP running so far? What other problems need to be addressed?

Fixing the multitouch is playing with the settings and reading the first few pages of this topic.

Annoying problems with Ubuntu on the new MB:
[LIST]
[*]Full brightness, not adjustable by keyboard buttons
[*]Suspund / resume is veeeeerry slow
[*]Airport is very slow when resuming
[/LIST]

---

### Post by cyberdork33 on 2008-11-20
> **stillingen said:**
> I´m running in to a problem with installing Grub on my Macbook

I´ve followed the instructions on the wiki page, but the installation is failing at 94% and an error saying. "Executing &#501;rub-install /dev/sda´ failed 

I´ve googled, but haven´t found any solution that sorts my problem. Anyone else run in to this issue and got a fix for it?Unfortunately the installer messes some things up and I think that is what causes the issue although the error you get only appears to affect Linux Mint users. See this thread:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

If you use refit to sync the partitions and then install grub manually after that, you should be OK.

---

### Post by paoletto on 2008-11-23
So could someone make a short resume  about how Intrepid work on the latest macbook unibody (5.1)?

I suppose that the major issues could be 

1) graphics card and chipset (NVIDIA MCP79 mobile)
2) Touchpad
3) new airport?
4) webcam

im seriously considering to get one, but i want to use linux as main OS..

---

### Post by jackoverfull on 2008-11-23
installed ubuntu on my MBP, finally…

The open source drivers where enough to activate the acceleration for one of the graphic cards (not sure on wich one), but caused the problem that i described above (extremely big items), albeit i noticed it only in the gdm login screen. When i try to install the closed source nvidia drivers from the "hardware drivers" control panel the panel hangs, but upon reboot the driver seems to be installed.:confused:

The acceleration is now fully up, open arena and the compisiting mode of metacity works well, but compiz says something about an "unsupported graphic card" and refuses to start.
With the nvidia drivers i can also dual-head without problems.:)

The wireless works out of the box on the installed system, scanning included, but doesn't work without the proprietary driver on the ubuntu live cd and scanning doesn't work anyway on it.

No luck with the audio, for now.

The cam works.

The trackpad works with right click and scrolling after installing one of the packages pointed out in the wiki, but i'll need to tune down the responsiveness.

No ideas about the backlight or the screen brightness settings. I don't use the sensors.

Sleep works, but touching the touchpad (without clicking) is enough to wake the system.:confused:

Didn't tried hibernation but i doubt it wil lwork.

Shutdown and reboot often doesn't finish, leaving the machine in a semi booted state, in wich i can only press the power button (wich make the system repeat the shutdown sequence again, with no results) or ctrl-alt-delete, wich does the same for the reboot sequence, so i have to force a shutdown holding the power button.

---

### Post by joka. on 2008-11-24
> **paoletto said:**
> So could someone make a short resume  about how Intrepid work on the latest macbook unibody (5.1)?

I suppose that the major issues could be 

1) graphics card and chipset (NVIDIA MCP79 mobile)
2) Touchpad
3) new airport?
4) webcam

im seriously considering to get one, but i want to use linux as main OS..

I'm in the same spot as you are. Except I'm planning on triple booting with Vista [for gaming and video/audio editing] and Linux. I'm waiting for a little longer until some more issues are fixed, people are really getting a crack on them. Or I might order 1 and use Vista if I run into trouble, seeing how it takes about 20-30 days to get 1 unless you get the ones that are already built in stores. jackoverfull is missing some info tho...

> **jackoverfull said:**
> No luck with the audio, for now.

The trackpad works with right click and scrolling after installing one of the packages pointed out in the wiki, but i'll need to tune down the responsiveness.

No ideas about the backlight or the screen brightness settings. I don't use the sensors.

I'm not an expert, but you 2 should read this page:
[https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

If you read this whole thread [page 11-15ish?] It kinda explains how to fix the trackpad. You have to play with the settings a bit from what I was told. Apparently people got the multitouch to work completely? [correct me if I'm wrong]

The KEYBOARD backlight I think you might need to add some script to make it work?

The SCREEN brightness can now be changed, but the function buttons for it does not work... you can change it in the terminal and switching back to X. They're currently working on it. See: [http://ubuntuforums.org/showthread.php?t=977558](http://ubuntuforums.org/showthread.php?t=977558)

Audio works, you need to put in a script found on the 1st link and then see this thread for the internal speakers: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

Other problems that are known and a couple that are currently being figured out are found on the bottom of the 1st link's page. Which include battery life, how Linux runs very hot, and the suspend/reboot.

---

### Post by paoletto on 2008-11-25
Thanks for the link that i didnt know.
So it seems it's quite supported by linux so far (except maybe the brightness keys, which will probably require 9.04 before they will work, right?)
Which fixes are you waiting for?
(ps im also going to triple boot it, but with xpsp2, not sVista : ))

---

### Post by joka. on 2008-11-25
> **paoletto said:**
> Thanks for the link that i didnt know.
So it seems it's quite supported by linux so far (except maybe the brightness keys, which will probably require 9.04 before they will work, right?)
Which fixes are you waiting for?
(ps im also going to triple boot it, but with xpsp2, not sVista : ))

I'm not sure what you mean by 9.04... what are you referring to? Better to ask someone else lol... like I said I'm a Linux nub.

I was waiting for them to fix the brightness thing, but they got it to somewhat work... I'll be ordering the laptop soon hopefully and hopefully when it arrives, that will be fixed and a couple more problems from the list... mainly how Linux runs hotter than OS X [I think that will also fix the battery life problem too].

I was thinking of installing XP... I'm really not sure which to do. Windows 7 [uses a lot less resources] is coming out in a year or 2 so I donno if I should go out and spend $200+ for Vista [I don't want to dl it off Limewire or w/e cuz seeing how this is a new system I don't want to risk messing anything up.] and then having to go out and buy Windows 7.

On the side note: I don't plan on using OS X at all... originally I was trying to find a way to move OS X into an external hd and completely out of the internal so the comp is clean slate for me to install Windows and Linux. I only like the new macbook pros because it's the cheapest for almost top of the line hardware configs/specs... Alienware laptops would run me ~$1k more than the macbook pros. I'm not a Mac fan at all and very disappointed at the limited options they give you: only up to 2.8ghz 2 core duo... no 2 core extreme processors, no blu-ray player. The graphics card is a kinda funky setup... I think they're kinda retarded to put in 2 when they could of just use 1 really good 1 which would be better and take some weight off the laptop. Resolution isn't the best either. Only 2 USB ports etc etc... haha yea I'm very picky.

---

### Post by jackoverfull on 2008-11-25
> **joka. said:**
> 
I'm not an expert, but you 2 should read this page:
[https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

Done already while i was  installing. But i see that the page has changed a bit, will try…

> The KEYBOARD backlight I think you might need to add some script to make it work?

Sure. But i don't know how to control it.
> 
The SCREEN brightness can now be changed, but the function buttons for it does not work... you can change it in the terminal and switching back to X. They're currently working on it. See: [http://ubuntuforums.org/showthread.php?t=977558](http://ubuntuforums.org/showthread.php?t=977558)

Audio works, you need to put in a script found on the 1st link and then see this thread for the internal speakers: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

interesting, thanks.

---

### Post by Nikos.Alexandris on 2008-11-25
> **joka. said:**
> 
[...]
Audio works, you need to put in a script found on the 1st link and then see this thread for the internal speakers: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

FWIW,

I can't confirm audio *working* with this script. In fact on my system (MBP5,1) I have audio (although it is only Mono and not Stereo) without any script (just switch to 6ch on the respective Sound Settings). The above mentioned script *breaks* my Sound Settings (it causes the Volume Control dialog (tab Options) to loose the three Input sources.

Regards

---

### Post by joka. on 2008-11-25
> **Nikos.Alexandris said:**
> FWIW,

I can't confirm audio *working* with this script. In fact on my system (MBP5,1) I have audio (although it is only Mono and not Stereo) without any script (just switch to 6ch on the respective Sound Settings). The above mentioned script *breaks* my Sound Settings (it causes the Volume Control dialog (tab Options) to loose the three Input sources.

Regards

Did you upgrade alsa? That's weird it should be working fine... post in that thread and see if anything can help you because from what I was reading in that thread, people got their audio working perfectly and it seems from the wiki page, they resolved it. Maybe you did something wrong? If you can get it fixed please post up step by step instructions on how to do it.

---

### Post by stillingen on 2008-11-25
> **cyberdork33 said:**
> 
If you use refit to sync the partitions and then install grub manually after that, you should be OK.

Thank you for your reply. Yes, it´s Mint alright ;) 

I synced and installed grub manually. When I select Tux from the boot menu I end up with the Grub prompt, and it´s locked, it not responding to anything.  Have i missed something?

---

### Post by Nikos.Alexandris on 2008-11-25
> **joka. said:**
> Did you upgrade alsa? That's weird it should be working fine... post in that thread and see if anything can help you because from what I was reading in that thread, people got their audio working perfectly and it seems from the wiki page, they resolved it. Maybe you did something wrong? If you can get it fixed please post up step by step instructions on how to do it.

Hi joka.

Sorry, I am not willing to destroy my system one more time. I don't have the time to re-fixit. I tried twice the script but it did what I already have written in several threads (here, in another "Solved" thread, in soundcheck's thread where the script is provided as well).

I did exactly what other people did. No luck. I will postpone this "test" for later.

Regards, Nikos

---

### Post by cyberdork33 on 2008-11-25
> **stillingen said:**
> Thank you for your reply. Yes, it´s Mint alright ;) 

I synced and installed grub manually. When I select Tux from the boot menu I end up with the Grub prompt, and it´s locked, it not responding to anything.  Have i missed something?

by grub prompt, you mean "grub>" ? If so, your grub was installed incorrectly (it cannot find where the config file is).

---

### Post by jackoverfull on 2008-11-26
ok, i just booted up after a couple of days to fix the sound. I can't remember what i did last time, but the sound is now working on both internal and external speakers, although not so loudly.:)

i have this in /etc/modprobe.d/options:```
options snd_hda_intel model=mbp3
```and i had to swith from 2ch to 6ch in gnome volume control.

---

### Post by jackoverfull on 2008-11-26
ok, now the screen brighthness works too, according to that:

[http://ubuntuforums.org/showthread.php?t=977558](http://ubuntuforums.org/showthread.php?t=977558)

:)

still no luck in tapping.

---

### Post by jackoverfull on 2008-11-26
```
modprobe usbhid quirks=0x05ac:0x0236:0x00020800
```rebooted and tapping works too.:)
the only things really missing now are the backlight of the keyboard and swapping fn keys.

---

### Post by m.musashi on 2008-11-26
> **jackoverfull said:**
> the only things really missing now are the backlight of the keyboard and swapping fn keys.

Backlight works for me. I'm not sure what fixed it but it's been working for a while. I think one of the packages in the mactel PPA did the trick.

---

### Post by stillingen on 2008-11-26
> **cyberdork33 said:**
> by grub prompt, you mean "grub>" ? If so, your grub was installed incorrectly (it cannot find where the config file is).


Yes, that´s right. So what what´s the next step? Do I have to remove grub and install again, or can I change the reference to where the config file is?

---

### Post by jackoverfull on 2008-11-30
after some time i found out that something was interfering with my keyboard.

at first i experienced sporadic freezes of x11, then the keyboard stopped responding at all after every startup: i could use the trakpad, but not the keyboard (internal or external).

after investigating for a while i found out that the problem was in the mbp_nvidia_bl module. i disabled it and now everything is normal again, although i can no longer change my brightness settings.

---

### Post by cancerian on 2008-12-01
Hi,

I am new to this forum, ubuntu and mac's. So firstly, thank you for all your useful work. You have made setting up my mac fairly painless.

I have got most of the functionality I need (right click, scrolling) by following the wiki page, but I was wondering if anyone had found a fix for this:

> **waldobeer said:**
> The only thing that is a little bothersome is that you cannot do right-click dragging: right-click down, move mouse, release.    I'm guessing right now it is sending mousewheel scroll because two fingers are moving, but the mouse cursor isn't.  Is there any way to do this without the extra changes you were talking about to the synaptic driver?

drag: right-click down, move mouse, release

Am I suppose to change something in 11-x11-synaptics.fdi? If so, I would be grateful if someone could post the line required. Or could someone let me know if there is an alternative fix.

(Note: I have managed to find a middle button by holding down shift, which is useful for some operations)

Many thanks

---

### Post by _mario_ on 2008-12-02
> **jackoverfull said:**
> after some time i found out that something was interfering with my keyboard.

at first i experienced sporadic freezes of x11, then the keyboard stopped responding at all after every startup: i could use the trakpad, but not the keyboard (internal or external).

after investigating for a while i found out that the problem was in the mbp_nvidia_bl module. i disabled it and now everything is normal again, although i can no longer change my brightness settings.
(cyberdork33 pointed me to this post in the thread dealing with display backlight.) what did you do to disable the module? did you reboot the machine or did you just unload the module? 

ciao,
Mario

---

### Post by jackoverfull on 2008-12-02
> **_mario_ said:**
> (cyberdork33 pointed me to this post in the thread dealing with display backlight.) what did you do to disable the module? did you reboot the machine or did you just unload the module? 

ciao,
Mario


ok, at first my keyboard was completely unusable and i hadn't a clue about the problem, so i reinstalled everything.

then i added the module and started experiencing the x11 freeze probles again almost immediately. i immediately disabled the module and everything was fine again.

---

### Post by wolf4914 on 2008-12-05
> **jackoverfull said:**
> ok, i just booted up after a couple of days to fix the sound. I can't remember what i did last time, but the sound is now working on both internal and external speakers, although not so loudly.:)

i have this in /etc/modprobe.d/options:```
options snd_hda_intel model=mbp3
```and i had to swith from 2ch to 6ch in gnome volume control.

    I have the same thing and the sound finally works - but not the microphone. I am trying to figure what direction to digg since everybody reports it working out of the box ?

---

### Post by Nikos.Alexandris on 2008-12-05
> **wolf4914 said:**
> I have the same thing and the sound finally works - but not the microphone. I am trying to figure what direction to digg since everybody reports it working out of the box ?

1. System > Preferences > Volume Control

2. Under the "Options" tab select, for example, for the first "Input Source" field the "Front Mic"

3. Under the "Recording" tab unmute the "Capture" (the first column) channel

You should be able to test it with Sound Recorder or Skype or... whatever (?)

Regards, Nikos

---

### Post by jackoverfull on 2008-12-06
> **Nikos.Alexandris said:**
> 1. System > Preferences > Volume Control

2. Under the "Options" tab select, for example, for the first "Input Source" field the "Front Mic"

3. Under the "Recording" tab unmute the "Capture" (the first column) channel

You should be able to test it with Sound Recorder or Skype or... whatever (?)

Regards, Nikos

yeah, that worked for me, at least in sound recorder. haven't tried skype.

---

### Post by paoletto on 2008-12-09
I got another question, which was maybe already answered:

Under linux, do you still have this problem that the machine goes at 1000mhz instead than full speed without the battery placed?

---

### Post by jackoverfull on 2008-12-09
i think so.

And i don't consider that a problem at all.

---

### Post by awaler on 2008-12-11
Hi - I'm working with a new install of Hardy on my MB5.1, and following along with the wiki page.

With regards to the trackpad, this file doesn't exist on my install:

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

I've installed hal-applesmc and applesmc-dkms, but still no sign of that file. Any ideas?

Also, the whole installation seems to crash when I install the restricted NVIDIA accelerated graphics driver - after installation, the screen goes blank after the ubuntu progress bar finishes loading and I have to reinstall by ubuntu partition over again - any ideas on why that's happening there?

Thanks!

---

### Post by joka. on 2008-12-12
> Originally Posted by Nikos.Alexandris
The brightness regulation keys F(n)1 and F(n)2 work on the MBP 5,1 with the 3D-effects enabled (activate effects, shutdown, boot).

Can someone confirm if the Fn keys are working for adjusting the brightness in the MBP 5,1?

Screen brightness adjustment scripts found in: [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

---

### Post by jackoverfull on 2008-12-12
> **joka. said:**
> Can someone confirm if the Fn keys are working for adjusting the brightness in the MBP 5,1?

Screen brightness adjustment scripts found in: [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)
they were. But for me that kext caused problems.

---

### Post by tebbendj on 2008-12-30
I had the problem of not getting the trackpad to work for Right-Click and scrolling until I uninstalled pommed. I'm not positive this will work in your case but it helped me.

Correction:  I seems I had misspelled applesmc in /etc/modules.  (I had applemc.)  After fixing that my trackpad works again and I got the added bonus of my keyboard backlight to work.  I have not reinstalled pommed yet to see what happens since everything is working without it.

---

### Post by P@nk on 2009-02-15
Did any of you guys get to fix the reboot problem.. my macbook 5,1 (13in not pro) hangs at a blank black screen (somewhere before the BIOS) at reboot.. I am using intrepid (ubuntu 8.10), I also tried the new 2.6.28 kernel with no luck.. Not to mention all the proposed workarounds: alsa-utils, reboot=b, acpi off, cpufreq commands as part of the reboot sequence.. Nothing works for me, I even had the problem with Debian lenny.. I would really appreciate it if someone could help me, it's really annoying :P

---

### Post by Nikos.Alexandris on 2009-02-15
> **P@nk said:**
> ...my macbook 5,1 (13in not pro) hangs at a blank black screen (somewhere before the BIOS) at reboot...

Same problem here. I never managed to get this machine to reboot. I just shutdown and boot :-)

Regards, Nikos

P.S. Macs don't have a BIOS. Except if you mean something else...

---

### Post by Nikos.Alexandris on 2009-02-15
> **joka. said:**
> Can someone confirm if the Fn keys are working for adjusting the brightness in the MBP 5,1?

Screen brightness adjustment scripts found in: [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

joka,

_if_ I would have the time I would just make a video, upload it somewhere so there are no doubts that the Fn brightness regulation keys do work when I enable the 3D effects.

Regards, Nikos

P.S. MBP5,1

---

### Post by poliocough on 2009-02-20
Hello all.

This is my first post in the Ubuntu Forums. First of all - thank you all for being here! This is a pretty awesome community!!

I also have Macbook 5.1 (13") running 8.10. I echo some of the issues above.

The best that I could do for the brightness issue is install the latest nvclock (it's an NVidia utility?). After that, brightness can be adjusted as follows:
```

/usr/local/bin/nvclock -S [VALUE]

```
Where VALUE is a percentage between 15 and 100. I have this line in a script called "brightness". Very high-tech! I've not yet figured out a way to map that to the F1/F2 keys. Previously someone in this thread said it can be done with "3D effects" -- how?

Also - still have the reboot issue. I always do shutdown and never reboot. Also - when I do shutdown, the "ubuntu" splash screen is half-garbled by the graphics card. Anyone else get that?

Thx!

---

### Post by G|N| on 2009-02-20
> **poliocough said:**
> Also - when I do shutdown, the "ubuntu" splash screen is half-garbled by the graphics card. Anyone else get that?

I solved this by installing StartUp-Manager and setting the splash display resolution from 800x600 to 1024x768. 
I hope this helps you

---

### Post by woodward on 2009-03-04
I am still not satisfied with our touchpad functionality. First a quick recap after reading through this thread, in OS X there are two methods of right and left clicking.

Left Clicking:
1) with a single finger, point and click on the object you wish to move or or select

2) using two fingers, point with one and click with the other (often the thumb)

Right Clicking
1) With two fingers, use both fingers to point at the object, and both fingers to click down on the pad

2) With three fingers, use two to point at the object, and the third to click down on the pad (again often the thumb)

I am seeing option 1) for both right and left clicking from the current Mactel software. But in my opinion, option 2) is more natural.

As a quick alternative to option 1), could we make the bottom 1/4th of the trackpad a virtual button, with the left half being a left click and the right half being a right click? Clicking would be ignored on the top 3/4's and touching would be ignored on the bottom 1/4th.

Any thoughts on this? Thank you in advance

---

### Post by cyberdork33 on 2009-03-04
> **woodward said:**
> I am still not satisfied with our touchpad functionality. First a quick recap after reading through this thread, in OS X there are two methods of right and left clicking.

Left Clicking:
1) with a single finger, point and click on the object you wish to move or or select

2) using two fingers, point with one and click with the other (often the thumb)

Right Clicking
1) With two fingers, use both fingers to point at the object, and both fingers to click down on the pad

2) With three fingers, use two to point at the object, and the third to click down on the pad (again often the thumb)

I am seeing option 1) for both right and left clicking from the current Mactel software. But in my opinion, option 2) is more natural.

As a quick alternative to option 1), could we make the bottom 1/4th of the trackpad a virtual button, with the left half being a left click and the right half being a right click? Clicking would be ignored on the top 3/4's and touching would be ignored on the bottom 1/4th.

Any thoughts on this? Thank you in advance

but there is also tapping which pretty much works on all touchpads (on macs and other PCs). 

Plus, "clicking" the touchpad only works with your specific hardware. The drivers were are using have to work for yours and other hardware with the same touchpad, but they don't "click". that is what makes this difficult.

Additionally, the "pointing with more than one finger, and clicking a button" function is really an OS X specific funtion (because there is only one button... Most other PCs have a right button) that we have tried to implement here because we are working on Macs and some of us are used to that functionality.

There is also the hold CTRL while clicking method, but I dont really count that as a "right click"

---

### Post by sistoviejo on 2009-03-05
Im trying to install Intrepid (8.10 alternate i386) on one of the new 2009 White MacBook with Geforce 9400M video.
When I try to boot the CD, it crashes right after selecting "Install Ubuntu".
Two lines of text appear and then it crashes on a blank screen.
I tried adding "nofb" to the boot line but it didn't improve at all.
Any suggestions appreciated.
:)

UPDATE: Moved this issue to a different thread here: [http://ubuntuforums.org/showthread.php?p=6842526](http://ubuntuforums.org/showthread.php?p=6842526)

---

### Post by _mario_ on 2009-03-05
> **poliocough said:**
> 
The best that I could do for the brightness issue is install the latest nvclock (it's an NVidia utility?). After that, brightness can be adjusted as follows:
```

/usr/local/bin/nvclock -S [VALUE]

```
Where VALUE is a percentage between 15 and 100. I have this line in a script called "brightness". Very high-tech! I've not yet figured out a way to map that to the F1/F2 keys.

did you install the nvidia-bl-dkms package from the mactel PPA as described [here (at he end of the document)]("https://help.ubuntu.com/community/MacBook5-1/Intrepid")?
btw: the 'shift=2' option isn't necessary on jaunty anymore.

ciao,
Mario

---

### Post by woodward on 2009-03-05
> **kosumi68 said:**
> The multi-finger click actions are supposed to work like this:

1 finger and click: left button
2 fingers and click: right button
3 fingers and click: middle button
1 finger and hold click: drag

The confusion is about the trackpad also being the button. Clicking near the bottom of the pad, where the button used to be, one expects basically the same behavior as if the button was there. Inevitably, the finger that clicks the imaginary button is *on the trackpad*. If the trackpad driver reports all fingers as usual, the multi-finger click actions all get confused, since there is one finger too many reported. That is why I added the somewhat odd feature that when clicking the trackpad, the last finger added is disregarded. This finger is normally the clicking finger. Effectively, when clicking, the number of fingers reported is reduced by one, which restores the behavior to the one described above.


kosumi68, Do you still have the module or bcm5974.c file for this functionality (I believe you and waldobeer were calling it the "two hand" method). The current bcm5974 module implements the "one hand" method, and this is pretty painful to use. For example, if you are trying to drag something, you click down and drag all with one finger, but you quickly run out of trackpad realestate and have to let go, which releases all of the items you were dragging.

Thank you

---

### Post by woodward on 2009-03-06
I changed the bcm5974-dkms driver so that for "clickable trackpad macbooks (pros)" the bottom 1/4 of the track pad acts like a button. The rest of the trackpad operates normally. The functionality for non-clickable trackpads remains unchanged. Tested on a Macbook Pro 5,1 running intrepid. I have attached the new bcm5974.c file, installation instructions are at the top of the file.

Cheers

---

### Post by alexmurray on 2009-03-06
> **woodward said:**
> I changed the bcm5974-dkms driver so that for "clickable trackpad macbooks (pros)" the bottom 1/4 of the track pad acts like a button. The rest of the trackpad operates normally. The functionality for non-clickable trackpads remains unchanged. Tested on a Macbook Pro 5,1 running intrepid. I have attached the new bcm5974.c file, installation instructions are at the top of the file.

Cheers

woodward - nice work. I've cleaned it up a bit (use linux kernel coding standards etc) and made a patch against the bcm5974-dkms package in the mactel ppa - I also changed it to be the top 4/5 instead of just 3/4 as this gives a bit more usable room for scrolling etc - see attached patch. Its very nice to be able to click and drag with 2 fingers now - do you know if its possible though to change it so that we still get mouse movement and scrolling events from the entire trackpad area (since now the bottom section only acts as a button, and hence is like a dead area for mouse movements when no button is pressed) as this would be even more like the functionality on OSX?

Great work.

---

### Post by woodward on 2009-03-06
alexmurray - Thank you. 

> **alexmurray said:**
> do you know if its possible though to change it so that we still get mouse movement and scrolling events from the entire trackpad area (since now the bottom section only acts as a button, and hence is like a dead area for mouse movements when no button is pressed) as this would be even more like the functionality on OSX?


This is definitely possible. Only when a button press is detected "if(ibt)", the code would ignore fingers in the bottom 1/5th "abs_y > 4/5". But when I use a trackpad, I usually rest my thumb on the "button" and click as needed. Mac OS actually seems to allow this "resting the thumb" through some additional logic; in OS X if you rest your thumb and move the mouse around a bit, all without clicking, then move your thumb around, you see that they have actually enter a mode where the bottom 1/5th does not register mouse motion. This would take a lot more logic for us to handle properly. We probably need a survey of how people use this new trackpad in OS X.

Regardless of this new patch, there is still another problem. The usb device does not always report fingers in the order in which they were added to the pad. Which is what has been assumed in the bcm5974 code. This can result in the mouse jumping when you drop a second finger to make a right click. OS X must be remembering the location of the first finger and then making the new "first finger" the one that is closest to the old location. We need to implement something similar. This happens rarely, but is annoying when it does, especially when you are trying to do precision right-clicking.

---

### Post by inphektion on 2009-03-06
can any of you nice people get this into a jaunty package?  I've been fighting to get anything working there with the touchpad.

---

### Post by alexmurray on 2009-03-06
> **woodward said:**
> alexmurray - Thank you. 



This is definitely possible. Only when a button press is detected "if(ibt)", the code would ignore fingers in the bottom 1/5th "abs_y > 4/5". But when I use a trackpad, I usually rest my thumb on the "button" and click as needed. Mac OS actually seems to allow this "resting the thumb" through some additional logic; in OS X if you rest your thumb and move the mouse around a bit, all without clicking, then move your thumb around, you see that they have actually enter a mode where the bottom 1/5th does not register mouse motion. This would take a lot more logic for us to handle properly. We probably need a survey of how people use this new trackpad in OS X.

Regardless of this new patch, there is still another problem. The usb device does not always report fingers in the order in which they were added to the pad. Which is what has been assumed in the bcm5974 code. This can result in the mouse jumping when you drop a second finger to make a right click. OS X must be remembering the location of the first finger and then making the new "first finger" the one that is closest to the old location. We need to implement something similar. This happens rarely, but is annoying when it does, especially when you are trying to do precision right-clicking.
good points - something else that this patch changes is that now only left clicking works with the bottom 1/5th of the trackpad, two / three finger clicks get reported as just single clicks so if this could also be somehow fixed that would be awesome too.

The best way to use the patch (and I think to do more development with this driver) is to use git to make a copy of the bcm5974-dkms git repository and work with that:

To make a clone of the repo:
```
git clone http://bitmath.org/git/bcm5974-dkms.git
```

this will create a directory bcm5974-dkms which contains a clone of the git repo.

Then you can edit the driver (or apply the patch I posted above)
```

cd bcm5974-dkms
patch -p1 < bcm5974-4_5.patch

```

or

```

vim usr/src/dkms_source_tree/bcm5974.c
... make changes

```

then to compile the new version as a .deb that you can then install

```

[from within the bcm5974-dkms directory]
debuild -us -uc -i -I

```

then to install the deb (which is now sitting in the parent directory of the bcm5974-dkms directory)

```

sudo debi

```

now you can

```

rmmod bcm5974 && sudo modprobe bcm5974

```

to load your new module.

---

### Post by cyberdork33 on 2009-03-06
please make patches against the kernel version and update there.

If you'd like to update the ppa, you need to join the mactel-support team in launchpad, and you will have access to the ppa to upload. Someone has to approve your membership (but if you PM with your launchpad username so that I know who you are, I will approve it).

---

### Post by alexmurray on 2009-03-06
> **cyberdork33 said:**
> please make patches against the kernel version and update there.

I agree that any patches should be pushed upstream, but the method I outlined above is (IMHO) the easiest way to do development against the current driver. When this work is in a stage ready to be merged back upstream, then it should be relatively easy to just push the patches against the mactel bcm5974 module back to lkml.

---

### Post by woodward on 2009-03-06
> **alexmurray said:**
> something else that this patch changes is that now only left clicking works with the bottom 1/5th of the trackpad, two / three finger clicks get reported as just single clicks so if this could also be somehow fixed that would be awesome too.


I see what you are saying. This would take some additional logic. But this isn't a way that I use the trackpad; if I want to right click, I put two fingers on the top 4/5ths and click with my thumb in the bottom 1/5th. Just my 2 cents. Cheers

---

### Post by cyberdork33 on 2009-03-08
> **alexmurray said:**
> I agree that any patches should be pushed upstream, but the method I outlined above is (IMHO) the easiest way to do development against the current driver. When this work is in a stage ready to be merged back upstream, then it should be relatively easy to just push the patches against the mactel bcm5974 module back to lkml.
OK. My concern is that some of the driver code in the mactel ppa is already upstream. development work is, of course, fine to put in the PPA.

---

### Post by luke-nz on 2009-03-18
I had a problem for a long time with the new MB trackpad, which I have now resolved.  I'm posting the problem and solution here for anyone with the same issue.

The only way I could get the system to recognise changes to the config in /etc/hal/fdi/policy was by removing all the input sections in xorg.  I made that change and then restarted X and all was well (touch-click was disabled and two-finger right click worked).  After restarting my computer, however, I discovered I could no longer login to X as it did not respond to the keyboard or the trackpad.  I could still switch to a terminal (ctrl-alt-fn-f1), and once there I restarted gdm (sudo /etc/init.id/gdm restart).  X now detected my keyboard/trackpad and all was well.

I've been doing that for three months, and I finally got fed up enough with it to look into it a little more.  Seems gdm is usually started with a sequence number of 20, but the HAL daemon (at least on my install) is 24.  I assume that means that **gdm starts X before hardware information is available**, and if nothing is specified in Xorg it assumes there is no keyboard.

I had success with changing the gdm sequence number to 22 at all runlevels, though 25 would possibly make more sense?

If someone more knowledgeable than me could confirm this I'd be grateful.  I'm just happy the damned thing works now.

---

### Post by cornelius2 on 2009-04-06
alexmurray, thanks for the instructions.

I posted a patch (+ the deb package) for bcm5974-dkms to make click-and-drag work with Macbook 5,1:
**EDIT: Removed this one as it is obsolete now. See the next post instead.**

---

### Post by cornelius2 on 2009-04-06
I posted an improved version of the patch (+ the deb package) for bcm5974-dkms to make click-and-drag work with Macbook 5,1:
[https://bugs.edge.launchpad.net/mactel-support/+bug/356317](https://bugs.edge.launchpad.net/mactel-support/+bug/356317)

It does *not* make the bottom part of the touchpad a dead zone and does *not* disable two-finger-clicking, and it should resemble the behavior of OS X.

Please test the new patch or the package and let me know if you see any problems with it.

---

### Post by opensourcelife on 2009-06-12
I'm running Ubuntu here on my Macbook Pro 5,1 15.4".
Installed the debian package and tried it.  Click and drag works fine except for one thing:

I use my thumb to click and my index to drag.  If my index finger is not the first finger to touch the trackpad, it will not click and drag.

Additionally, it doesn't seem to be able to even move unless the first finger to touch the trackpad is the one doing the movement.  This is a bit awkward considering my thumb is usually the only finger that remains touching the keypad at all times.

---

### Post by touchdownjesus4 on 2009-06-14
I can't seem to get any of this working. I installed the bcm-5972 dmks and none of my trackpad features work except left clicking and moving the mouse. I also can't get the bluetooth working with my wireless might mouse. I am running ubuntu 9.04 and have a unibody macbook. Can someone please guide me through the process of getting my trackpad to work and also my bluetooth connection.

---

### Post by touchdownjesus4 on 2009-06-14
Cornelius 2, I installed the deb package, now what do I do with the patch?

---

### Post by cyberdork33 on 2009-06-15
> **touchdownjesus4 said:**
> Cornelius 2, I installed the deb package, now what do I do with the patch?
touchdownjesus, have you followed the configuration instructions on the documentation for your Mac?

[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

