---
title: "Ubuntu and the asus zenbook (UX302)"
date: 2014-02-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by bug-track on 2014-02-15
This thread is to gather information and coordinate work to support Asus Zenbook UX302(LA/LG) ultrabooks.

Rules:
- Please visit UX302 help [page]("https://help.ubuntu.com/community/AsusZenbookUX302"). If you found some outdated information please correct it.
- If you found some bug related to this hardware and it is not reported, report it upstream and link it here and on launchpad.
- If you have workaround, do not propagate it. It should be fixed - please report it.

---

### Post by bug-track on 2014-02-15
For those who has problems with integrated Webcam (1bcf:2987 Sunplus Innovation Technology Inc.), use can use my [patch]("http://pastebin.com/9yXes2J1") for testing. It can by applied on kernel 3.14 source.

---

### Post by pantale on 2014-02-17
Would be nice if the same could be done for the UX301LA.

---

### Post by bug-track on 2014-02-20
How big is the difference between ux301 and ux302? can you please provide output of lspci, lsusb and /proc/cpuinfo.

---

### Post by brycekinney91 on 2014-02-20
Hey guys, somewhat new to ubuntu, currently on 13.10 with kernel 3.13. I can't seem to get the ubuntu to boot up properly without nomodeset. I really want to get the graphics working because the software rendering is killing my battery(2 hours tops). Anyone have any suggestions?

Also if anyone has gotten the brightness changer working, that would be awesome too!

---

### Post by soft0 on 2014-02-20
i just tried booting 14.04 alpha 2, still black (but lit) screen, is this a known bug?

---

### Post by bug-track on 2014-02-21
Try this kernel. It should work:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2014-02-13-trusty/linux-image-3.14.0-999-generic_3.14.0-999.201402130457_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2014-02-13-trusty/linux-image-3.14.0-999-generic_3.14.0-999.201402130457_amd64.deb)

if not, try this:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/current/linux-image-3.13.0-994-generic_3.13.0-994.201402201823_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/current/linux-image-3.13.0-994-generic_3.13.0-994.201402201823_amd64.deb)

I use selfcompiled kernel from here:
[https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git)

It works for me.

---

### Post by bug-track on 2014-02-21
And do not forget to press "Affectd me" butteon on this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1265544](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1265544)

---

### Post by pantale on 2014-02-21
Here are the informations concerning the UX301 LA DE 002H

[COLOR=#ff0000]**See attachments...**[/COLOR]

---

### Post by bug-track on 2014-02-21
Most parts seems to be simmilar. Do you have same bugs as ux302? For example webcam, sdcard reader, blank screen?
You are free to edit this page and add some notices about your hardware:
[https://help.ubuntu.com/community/AsusZenbookUX302](https://help.ubuntu.com/community/AsusZenbookUX302)
Results of lspci and lsusb - please create a attachment.

---

### Post by pantale on 2014-02-21
I do not have the same bugs as yours.
Webcam is working fine (tested using cheese)
Sdcard reader works out of the box
Never had a blank screen...

---

### Post by bug-track on 2014-02-21
Then it probably makes no sense to combine ux302 and ux301 on same page.

---

### Post by cylehunter33 on 2014-02-22
Neither the wireless or ethernet drivers seem to have installed. It's strange, it connected fine during the try now, but after installing nothing. Everything else seems to work, with the exception of the nomodeset shenanigans...

---

### Post by cylehunter33 on 2014-02-22
The fix mentioned in this SO resolved the wireless driver issue for me, just be sure to have a computer with internet access and a usb handy:

[http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63](http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63)

---

### Post by bug-track on 2014-02-22
Thank you for info! I updated the wiki.

---

### Post by brycekinney91 on 2014-02-24
@bug-track Are those concerning my issue or soft0?

---

### Post by brycekinney91 on 2014-02-24
> **bug-track said:**
> Try this kernel. It should work:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2014-02-13-trusty/linux-image-3.14.0-999-generic_3.14.0-999.201402130457_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2014-02-13-trusty/linux-image-3.14.0-999-generic_3.14.0-999.201402130457_amd64.deb)

if not, try this:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/current/linux-image-3.13.0-994-generic_3.13.0-994.201402201823_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/current/linux-image-3.13.0-994-generic_3.13.0-994.201402201823_amd64.deb)

I use selfcompiled kernel from here:
[https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git)

It works for me.

The first one you linked worked, I didn't have to use nomodeset and now it is not running in software rendering mode, THANK YOU SO MUCH. Ive spent hours trying to figure this out and now it works!

---

### Post by rifak on 2014-03-01
> **brycekinney91 said:**
> The first one you linked worked, I didn't have to use nomodeset and now it is not running in software rendering mode, THANK YOU SO MUCH. Ive spent hours trying to figure this out and now it works!

I've installed the first link as well (kernel 3.14.0.999-generic, here: [http://kernel.ubuntu.com/~kernel-ppa...0457_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa...0457_amd64.deb)) and it has seemed to fix the blank screen/nomodeset issue on boot. However, anytime my screen turns off (ie, display turning off after some time and/or suspend), the screen will not come back...it's lit, but black. I've tested this on both kernels, 3.13.0.14 in 14.04 daily and the above 3.14.0.999, and this resume screen issue seems to only be a problem with the 3.14.0.999 kernel. Is anyone else seeing this same behavior? Any ideas? For reference, currently using the Asus Zenbook UX302LA.

---

### Post by rifak on 2014-03-01
Alright, we got some good news. 

Background/Problems: I'm currently using an Asus Zenbook UX302LA with Ubuntu 14.04 daily build. The kernel progression right now in 14.04 is on the 3.13 kernel, which is having some major issues when it comes to the display, even with nomodeset boot parameter (blank screen on boot and other screen problems when resuming, etc). I installed the 3.14 kernel daily build, which fixed the boot screen staying black. However, it did not address the problem of the screen staying blank after any time the display turns off (suspend, auto-display-off after some time). I think I've found a solution to all these issues though.

Solution: In the mainline kernel ppa ([http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)), there is a drm-intel-nightly build ([http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/)) which, from what I understand, is dealing with some of the newer Intel chipsets. Going through some of the changelogs of the more recent drm-intel-nightly builds, there seems to be some work on display handling, both on boot and system resuming/display-back-on. I went ahead and installed the newest build (headers and image, [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2014-03-01-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2014-03-01-trusty/) at the time of writing this), which has turned out to work really well. Specifically dealing with the display, I can now boot with default parameters resulting in no display problems, along with suspend-resume working seemingly perfect.

Other findings:
1) No problems with Wifi.
2) Some Fn keys do not work. To get all of the Fn keys to do their proper job, I put "acpi_osi=" in the grub boot paramters:
```

$ gksudo gedit /etc/default/grub

```
Changed GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=" then save. Then run:
```

$ sudo update-grub

```

3) For suspending, everything works after the above install of the drm-intel-nightly kernel. However, if you have an external USB mouse plugged in, the movement of the mouse will wake the computer from suspend. For me, this is not desirable. I solved this by editing the "wakeup" definitions:
I checked the wakeup definitions by doing:
```

$ cat /proc/acpi/wakeup

```
Which gave me this:
```

Device	S-state	  Status   Sysfs node
RP01	  S4	*disabled  pci:0000:00:1c.0
PXSX	  S4	*disabled
RP03	  S4	*disabled
PXSX	  S4	*disabled
RP05	  S4	*disabled
PXSX	  S4	*disabled
RP06	  S4	*disabled
PXSX	  S4	*disabled
RP07	  S4	*disabled
PXSX	  S4	*disabled
RP08	  S4	*disabled
PXSX	  S4	*disabled
PXSX	  S4	*disabled  pci:0000:02:00.0
RP04	  S4	*disabled  pci:0000:00:1c.3
PXSX	  S4	*disabled  pci:0000:03:00.0
WLA    S3	*disabled
USB2	  S3	*disabled
XHC1	  S3	*enabled  pci:0000:00:14.0
EHC1	  S3	*disabled
EHC2	  S3	*disabled
XHC	  S3	*disabled
HDEF	  S4	*disabled  pci:0000:00:1b.0
TPD4	  S4	*disabled
TPD7	  S0	*disabled
TPD8	  S0	*disabled
SLPB	  S4	*enabled 

```

There are two devices that were enabled, XHC1 (USB 3.0 interface) and SLPB (not sure what this one is). I wanted to disable just the XHC1 device, since this is where my mouse is plugged into. To disable this:

```

$ sudo su
$ echo XHC1 > /proc/acpi/wakeup

```

If you do a "cat" on this again, you will see now that the XHC1 device is disabled. You can test out everything that you want to wakeup from suspend and enable/disable these devices accordingly. The names of these are pretty cryptic, but you may have some luck connecting them to what they actually are with an "lspci".

This change is not permanent (will revert to defaults after computer restarts) so to make them permanent you have to add them to the boot inits. Create a file in /etc/init.d/ with:
```

$ gksudo gedit /etc/init.d/usb_wake_disable.sh

```

Add the following contents, replacing/adding all of the devices that you want disabled by default:
```

#!/bin/sh
echo XHC1 > /proc/acpi/wakeup

```

Finally, you have to add it into the init:
```

$ sudo chmod +x /etc/init.d/usb_wake_disable.sh
$ sudo update-rc.d /etc/init.d/usb_wake_disable.sh defaults

```

4) All USB ports work.
5) SD card reader does not work, and am pretty sure that there's no solution to this yet.
6) Touchscreen works, along with multitouch
7) Have not tested the video-out ports yet.

As I go further, I'll be posting back here with updates or changes if they're needed. Hope this helps.

8) Headphone jack works.
9) Hardware upgrades cause no problems. Stock computer comes with 2GB soldered RAM and 2GB SODIMM slot. I upgraded the only available 2GB stick to an 8GB ([http://www.amazon.com/gp/product/B006YG8X9Y/ref=oh_details_o01_s00_i00?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B006YG8X9Y/ref=oh_details_o01_s00_i00?ie=UTF8&psc=1)), taking it to 10GB RAM which is the maximum this computer can handle. Also, removed the 500GB HDD and replaced it with a 128GB SSD ([http://www.bestbuy.com/site/q-series-pro-128gb-internal-serial-ata-3-0-solid-state-drive-for-laptops/1783025.p?id=1219063715521&skuId=1783025&st=toshiba%20ssd&cp=1&lp=2](http://www.bestbuy.com/site/q-series-pro-128gb-internal-serial-ata-3-0-solid-state-drive-for-laptops/1783025.p?id=1219063715521&skuId=1783025&st=toshiba%20ssd&cp=1&lp=2)).

---

### Post by bug-track on 2014-03-02
Hi [[COLOR=#000000]ego-sum-deus[/COLOR]]("http://ubuntuforums.org/member.php?u=613004"), thank you for your info.

---

### Post by brycekinney91 on 2014-03-04
> **bug-track said:**
> Hi [[COLOR=#000000]ego-sum-deus[/COLOR]]("http://ubuntuforums.org/member.php?u=613004"), thank you for your info.

I had the same issue with the screen off/suspension not working, and ego-sum-deus' information helped mine too! Thanks ego!

---

### Post by fuzze on 2014-03-05
I can confirm that the HDMI output does work with the kernel you link to.
Hopefully all theis will be solved in 14.04

---

### Post by motley-slate on 2014-03-07
[SIZE=2]Hello, I just located this thread.  When I first bought my UX302LA there wasn't any info to be found so I had to fix these things on my own. Glad to see others working on these Asus models now as well!  Just wanted to share my journey.  [/SIZE] There are a few guys on the Arch forum working on this as well (link below).  [SIZE=2]Over the past few weeks,  I have been playing with and providing a custom kernel to fix the suspend/resume issue for the UX302LA and LG models to run Arch Linux (I run Antergos). I simply provide a script that downloads the latest mainline kernel from kernel.org (currently 3.14 rc5) and then it applies a patch originally [/SIZE][SIZE=2]created by [/SIZE][FONT=Bitstream Vera Sans Mono][COLOR=#333333]Alberto Aguirre ([https://launchpadlibrarian.net/166248804/0001-drm-i915-Add-quirk-for-ASUS-UX302LA-G-to-fix-blank-s.patch](https://launchpadlibrarian.net/166248804/0001-drm-i915-Add-quirk-for-ASUS-UX302LA-G-to-fix-blank-s.patch)).  I just had to tweak the patch to allow it to be applied to mainline since some of the Intel quirk patches either don't seem to make it in, or they are lagging behind for whatever reason. 

I will be curious to study the [/COLOR][/FONT]drm-intel-nightly [FONT=Bitstream Vera Sans Mono][COLOR=#333333]git repo for the  kernel PPA you are using to see what is different from mainline. I am assuming the git is here: [/COLOR][/FONT]http://cgit.freedesktop.org/~danvet/drm-intel

[FONT=Bitstream Vera Sans Mono][COLOR=#333333]In case anyone is interested here are the links for the stuff I have been working on. For the most part, we are all stumbling upon the same solutions one way or another.[/COLOR][/FONT]
[https://bitbucket.org/motley/kernel_asus_ux302](https://bitbucket.org/motley/kernel_asus_ux302)
[https://bbs.archlinux.org/viewtopic.php?id=177296&p=1](https://bbs.archlinux.org/viewtopic.php?id=177296&p=1)

[COLOR=#333333][FONT=Bitstream Vera Sans Mono][SIZE=2]
[/SIZE]Cheers, glad to see we can enjoy these nice machines on Linux!



[/FONT][/COLOR]

---

### Post by rifak on 2014-03-07
> **motley-slate said:**
> [SIZE=2]Hello, I just located this thread.  When I first bought my UX302LA there wasn't any info to be found so I had to fix these things on my own. Glad to see others working on these Asus models now as well!  Just wanted to share my journey.  [/SIZE] There are a few guys on the Arch forum working on this as well (link below).  [SIZE=2]Over the past few weeks,  I have been playing with and providing a custom kernel to fix the suspend/resume issue for the UX302LA and LG models to run Arch Linux (I run Antergos). I simply provide a script that downloads the latest mainline kernel from kernel.org (currently 3.14 rc5) and then it applies a patch originally [/SIZE][SIZE=2]created by [/SIZE][FONT=Bitstream Vera Sans Mono][COLOR=#333333]Alberto Aguirre ([https://launchpadlibrarian.net/166248804/0001-drm-i915-Add-quirk-for-ASUS-UX302LA-G-to-fix-blank-s.patch](https://launchpadlibrarian.net/166248804/0001-drm-i915-Add-quirk-for-ASUS-UX302LA-G-to-fix-blank-s.patch)).  I just had to tweak the patch to allow it to be applied to mainline since some of the Intel quirk patches either don't seem to make it in, or they are lagging behind for whatever reason. 

I will be curious to study the [/COLOR][/FONT]drm-intel-nightly [FONT=Bitstream Vera Sans Mono][COLOR=#333333]git repo for the  kernel PPA you are using to see what is different from mainline. I am assuming the git is here: [/COLOR][/FONT]http://cgit.freedesktop.org/~danvet/drm-intel

[FONT=Bitstream Vera Sans Mono][COLOR=#333333]In case anyone is interested here are the links for the stuff I have been working on. For the most part, we are all stumbling upon the same solutions one way or another.[/COLOR][/FONT]
[https://bitbucket.org/motley/kernel_asus_ux302](https://bitbucket.org/motley/kernel_asus_ux302)
[https://bbs.archlinux.org/viewtopic.php?id=177296&p=1](https://bbs.archlinux.org/viewtopic.php?id=177296&p=1)

[COLOR=#333333][FONT=Bitstream Vera Sans Mono][SIZE=2]
[/SIZE]Cheers, glad to see we can enjoy these nice machines on Linux!



[/FONT][/COLOR]

Awesome. I'm glad to see two different entities converging on what seems to be similar solutions. I haven't had any extended time to study the details of what the drm-intel kernel is providing that's not in the mainline, besides just generally keeping up with the changelog. I'm definitely thinking that the Intel quirks are what's causing all of these fixes to function properly though. Do you know if/when they're going to make it into the main kernel?

Also, FYI, the drm-intel-nightly is located here: [http://cgit.freedesktop.org/drm-intel](http://cgit.freedesktop.org/drm-intel) (which is a slightly different link that you've provided...it's just been migrated away from the danvet).

---

### Post by motley-slate on 2014-03-08
> **ego-sum-deus said:**
> Awesome. I'm glad to see two different entities converging on what seems to be similar solutions. I haven't had any extended time to study the details of what the drm-intel kernel is providing that's not in the mainline, besides just generally keeping up with the changelog. I'm definitely thinking that the Intel quirks are what's causing all of these fixes to function properly though. Do you know if/when they're going to make it into the main kernel?

Also, FYI, the drm-intel-nightly is located here: [http://cgit.freedesktop.org/drm-intel](http://cgit.freedesktop.org/drm-intel) (which is a slightly different link that you've provided...it's just been migrated away from the danvet).
 
Thanks for clarifying the git repo being used. I do recall Daniel Vetter saying something about it being moved. I did a full source compare of the nightly intel-drm repo vs mainline rc5 for /drivers/gpu/drm/i915/* and there are still quite a few differences.  Since the "suspend and then resume to black screen" is fixed in the nightly, I have verified that they have fixed it in a different manner than the ignore bpp clamping quirk patch I am using. The next next rc for mainline will include tag 'drm-intel-fixes-2014-03-04'.  When mainline rc6 comes out, I will go back to testing without the extra patch to verify if it no longer needed for mainline. If not, then this is great news.  There is so much rearrangement and activity going for i915. It is a bit scary for regression testing, but they are indeed on a worthy mission to make it better. This is exactly why I bought a machine for Linux that had pretty much everything Intel ;).

---

### Post by rifak on 2014-03-10
> **motley-slate said:**
> Thanks for clarifying the git repo being used. I do recall Daniel Vetter saying something about it being moved. I did a full source compare of the nightly intel-drm repo vs mainline rc5 for /drivers/gpu/drm/i915/* and there are still quite a few differences.  Since the "suspend and then resume to black screen" is fixed in the nightly, I have verified that they have fixed it in a different manner than the ignore bpp clamping quirk patch I am using. The next next rc for mainline will include tag 'drm-intel-fixes-2014-03-04'.  When mainline rc6 comes out, I will go back to testing without the extra patch to verify if it no longer needed for mainline. If not, then this is great news.  There is so much rearrangement and activity going for i915. It is a bit scary for regression testing, but they are indeed on a worthy mission to make it better. This is exactly why I bought a machine for Linux that had pretty much everything Intel ;).

Awesome. Thanks for all the info motely, this has been great. rc6 just came out today, so I'll be testing on my end as well and post back later tonight with my findings.

---

### Post by motley-slate on 2014-03-10
> **ego-sum-deus said:**
> Awesome. Thanks for all the info motely, this has been great. rc6 just came out today, so I'll be testing on my end as well and post back later tonight with my findings.

Cool, I saw that as well. I kicked off an rc6 build before I left for work (without the suspend patch I was using).  I'll give it a try later tonight when I return home.

---

### Post by motley-slate on 2014-03-10
Update: mainline 3.14 rc6 still requires the QUIRK_IGNORE_BPP_CLAMPING patch. Without the patch, the laptop still fails to come out of suspend mode. Applied the patch, built again, and now all is good.  I am now getting a new error on boot related to backlight. It doesn't affect function, but it is interesting that it cropped up in rc6.  I will investigate more when I have time.

I updated my script on bitbucket: [https://bitbucket.org/motley/kernel_asus_ux302/commits/all](https://bitbucket.org/motley/kernel_asus_ux302/commits/all)

And the journey continues!

---

### Post by SgtMunky on 2014-03-12
I have never had so many problems with a computer and a Linux install as with this one! Awesome computer but man this has turned into a pain. Has anyone here had issues with graphics drivers? I've install the intel ones but it won't pick them up, it still uses the gallium. This wouldn't bother me if the gallium driver actually did what I wanted it to do, like support video out port and backlight. 

I'm trying out the 3.13 kernel here soon so I'll report if that helps out or not.

---

### Post by motley-slate on 2014-03-12
> **SgtMunky said:**
> I have never had so many problems with a computer and a Linux install as with this one! Awesome computer but man this has turned into a pain. Has anyone here had issues with graphics drivers? I've install the intel ones but it won't pick them up, it still uses the gallium. This wouldn't bother me if the gallium driver actually did what I wanted it to do, like support video out port and backlight. 

I'm trying out the 3.13 kernel here soon so I'll report if that helps out or not.

Hi SgtMunky, yes new hw can be a PIA! For best support with this laptop, you should run the latest 3.14 mainline kernel that provides the best up to date i915/DRM haswell gpu support (see [COLOR=#000000]ego-sum-deus's posts above for the recommended kernel deb to install for Ubuntu). Many of these commits are making it into stable [/COLOR]3.13.6 as well, but I have not spent time testing 3.13 over the last few releases, so I am not sure how it compares. 
 
As far as the Intel drivers, they should just work. Kernel module i915 should be loaded automatically and the mesa/intel DRI drivers stack should just work. However, I am not sure what versions of mesa Ubuntu/Debian allow you to use. With Arch (Antergos), I am running mainline kernel 3.14 rc6 with mesa/intel dri 10.1.0-2. 3D support and compositing work great.  A simple glxgears test yields a consistent 60 FPS and I get about 18,000 in the Octane benchmark in Chrome. That said, I have not done any intensive gaming or other benchmarking.  For my needs, I am happy and the machine is stable. 

[COLOR=#333333][FONT=sans-serif]From what I have read, ILO Gallium3D is still experimental, doesn't have the full feature set, and will be outperformed by the classic Intel Mesa driver in most cases.[/FONT][/COLOR]

For full backlight support, you will need kernel boot cmdline parameter "[COLOR=#333333][FONT=sans-serif]acpi_osi=" (no value is correct).

Hope this helps. [/FONT][/COLOR]

---

### Post by SgtMunky on 2014-03-14
> **motley-slate said:**
> Hi SgtMunky, yes new hw can be a PIA! For best support with this laptop, you should run the latest 3.14 mainline kernel that provides the best up to date i915/DRM haswell gpu support (see [COLOR=#000000]ego-sum-deus's posts above for the recommended kernel deb to install for Ubuntu). Many of these commits are making it into stable [/COLOR]3.13.6 as well, but I have not spent time testing 3.13 over the last few releases, so I am not sure how it compares. 
 
As far as the Intel drivers, they should just work. Kernel module i915 should be loaded automatically and the mesa/intel DRI drivers stack should just work. However, I am not sure what versions of mesa Ubuntu/Debian allow you to use. With Arch (Antergos), I am running mainline kernel 3.14 rc6 with mesa/intel dri 10.1.0-2. 3D support and compositing work great.  A simple glxgears test yields a consistent 60 FPS and I get about 18,000 in the Octane benchmark in Chrome. That said, I have not done any intensive gaming or other benchmarking.  For my needs, I am happy and the machine is stable. 

[COLOR=#333333][FONT=sans-serif]From what I have read, ILO Gallium3D is still experimental, doesn't have the full feature set, and will be outperformed by the classic Intel Mesa driver in most cases.[/FONT][/COLOR]

For full backlight support, you will need kernel boot cmdline parameter "[COLOR=#333333][FONT=sans-serif]acpi_osi=" (no value is correct).

Hope this helps. [/FONT][/COLOR]

I've tried a lot of different boot params but the only one that does work is the "nomodeset" command, I'll keep fiddling around with that mess. 

I too am not particularly worried about gaming, but being able to use multiple monitors would be nice considering the kind of work I do. Some Mindcraft wouldn't hurt either (haven't tried that yet actually). Are the 3.14 releases stable for the most part? This machine is one I use to work from home (which is where I primarily work) so I do need it to work fully.

---

### Post by motley-slate on 2014-03-15
> **SgtMunky said:**
> I've tried a lot of different boot params but the only one that does work is the "nomodeset" command, I'll keep fiddling around with that mess. 

I too am not particularly worried about gaming, but being able to use multiple monitors would be nice considering the kind of work I do. Some Mindcraft wouldn't hurt either (haven't tried that yet actually). Are the 3.14 releases stable for the most part? This machine is one I use to work from home (which is where I primarily work) so I do need it to work fully.

The 3.14 release candidates have been very stable for me, I am currently on the latest rc6. The only reason I use mainline (plus adding the patch to get suspend to work) is because it is more stable and the hardware works better than with any of the the stable release kernels I have tried. Haswell is still young on Linux, especially the integrated GPU drivers. This is why the 3.14 rc is necessary in my opinion. I recently tried my Ethernet dongle and it works right out of the box.  I have all function keys etc. working in XFCE, brightness/keyboard backlight/suspend/volume etc. The only thing I know isn't working is the SDCard slot. My best Octane score in Chrome with 512MB video RAM allocated is 18,585.  I was getting right around 18,000 with 128MB allocated. My son can play Minecraft easily using OpenJDK 1.7, so that won't be a problem.  So yes, I would call this complete and stable.  It is a country mile from where I was when I first installed a couple distros to do some testing.

I don't see anything for drm/i915 staged in master for 3.14 rc7 yet. We'll have to see if they merge more stuff this weekend before the deadline.

---

### Post by motley-slate on 2014-03-18
[COLOR=#333333][FONT=sans-serif]Updates:
 
1) I upped my mainline kernel install script to 3.14 rc7. Everything is still working fine. There were not any changes to Intel i915/drm in rc7, so the QUIRK_IGNORE_BPP_CLAMPING patch is still required for successful resume.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif][https://bitbucket.org/motley/kernel_asus_ux302](https://bitbucket.org/motley/kernel_asus_ux302)

2) They still are not comfortable with the patch for the kernel that causes us to use "acpi_osi=" to allow the function keys to work. Last comment: "[FONT=arial]The patch is deemed too hacky and will not make it into mainline I'm afraid. [/FONT][FONT=arial]It's not clear why firmware would declare 16 output devices while the SPEC only [/FONT][FONT=arial]allow 8. I don't see how we can proceed here, I suppose you will have to [/FONT][FONT=arial]continue to use acpi_osi= cmdline option for the time being unless we found [/FONT][FONT=arial]something new later."[/FONT]
 
Bug report:
[https://bugzilla.kernel.org/show_bug.cgi?id=70241](https://bugzilla.kernel.org/show_bug.cgi?id=70241)

The aforementioned "hacky" workaround patch is here for those interested. I don't apply in my kernel, I just use  "acpi_osi=" 
[https://bugzilla.kernel.org/attachment.cgi?id=125571&action=diff](https://bugzilla.kernel.org/attachment.cgi?id=125571&action=diff)




[/FONT][/COLOR]

---

### Post by motley-slate on 2014-03-25
Updated to mainline rc8 today. There were a couple i915/drm fixes, but things are still the same as far as the suspend/resume patch I need to apply and the silly empty value kernel command line parameter "acpi_osi=".

[https://bitbucket.org/motley/kernel_asus_ux302/commits/all](https://bitbucket.org/motley/kernel_asus_ux302/commits/all)

---

### Post by SgtMunky on 2014-03-30
I've got the 3.14 kernel up and running finally. Fixed graphics driver issues, got some Kerbals Mun bound now that it can render things. :) I too need that 'acpi_osi=' boot param but in reality this is much easier an option than editing the kernel, at least with my 'meh' programming knowledge.

---

### Post by bug-track on 2014-04-13
Good news for every one who has UX302 or linux laptop with Alcor Micro AU6601 SD controller. **It's Alive!!!!**

After some time of RE, i was able to reconstruct registers important for data transfer and make initial linux driver.&#65279;

---

### Post by Shajahan_K._Miah on 2014-04-14
ASUS was and still is a great motherboard company. I still 
would build my own custom PCS with the same 
motherboards offered by ASUS. 

When I used to run any flavor of Linux
I used to do it on my custom PCS. 

I recommend ASUS for any type of 
Linux OS installation; especially Ubuntu. Forget 
the cloud when it comes down to that. 

ASUS Zenbook would be a great example 
of Ubuntu Installation.

---

### Post by micucci on 2014-04-21
No way to install 14.04 on my UX302LG :(
I put an Crucial M500 in place of the original 750GB hard disk : I can show it in the 'BIOS' but it isn't recognize by Ubuntu. (The M500 is safe, and initialy installed in my old laptop with Ubuntu 13.10)
Any idea ?

---

### Post by motley-slate on 2014-04-27
Now running 3.15 rc2. [COLOR=#000000]'acpi_osi=' is still needed for screen brightness keys from userland. [/COLOR]Lots of changes are still being merged upstream for the Intel DRM/i915 drivers. I no longer need the [COLOR=#000000]quirk_ignore_bpp_clamping patch to get suspend to work as I did in 3.14.0 stable, so this is good news.  I am going to keep tracking 3.15 mainline to see how things go. A new release comes out every week or so.
[/COLOR]
[https://bitbucket.org/motley/kernel_asus_ux302/src/df7872b37e90d5f14c17f7bde87a57d4e58f93a4?at=master](https://bitbucket.org/motley/kernel_asus_ux302/src/df7872b37e90d5f14c17f7bde87a57d4e58f93a4?at=master)

> **bug-track said:**
> Good news for every one who has UX302 or linux laptop with Alcor Micro AU6601 SD controller. **It's Alive!!!!**

After some time of RE, i was able to reconstruct registers important for data transfer and make initial linux driver.&#65279;

Great work, thanks! I assume these are your changes here? [http://www.spinics.net/lists/linux-mmc/msg25836.html](http://www.spinics.net/lists/linux-mmc/msg25836.html)
I will merge with the testing kernel I build above and give it a try. Is there a git repo I can track for changes?

---

### Post by micucci on 2014-04-27
I put  kernel 3.15rc3 (image and headers)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc3-utopic/linux-headers-3.15.0-031500rc3_3.15.0-031500rc3.201404280035_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc3-utopic/linux-headers-3.15.0-031500rc3_3.15.0-031500rc3.201404280035_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc3-utopic/linux-image-3.15.0-031500rc3-generic_3.15.0-031500rc3.201404280035_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc3-utopic/linux-image-3.15.0-031500rc3-generic_3.15.0-031500rc3.201404280035_amd64.deb)

and make changes of Grub like explained by ego-sum-deus here [http://ubuntuforums.org/showthread.php?t=2205704&p=12944072#post12944072](http://ubuntuforums.org/showthread.php?t=2205704&p=12944072#post12944072)
and everythings seems to work...

---

### Post by motley-slate on 2014-04-28
> **bug-track said:**
> Good news for every one who has UX302 or linux laptop with Alcor Micro AU6601 SD controller. **It's Alive!!!!**

After some time of RE, i was able to reconstruct registers important for data transfer and make initial linux driver.&#65279;

> **motley-slate said:**
> Great work, thanks! I assume these are your changes here? [http://www.spinics.net/lists/linux-mmc/msg25836.html](http://www.spinics.net/lists/linux-mmc/msg25836.html)
I will merge with the testing kernel I build above and give it a try. Is there a git repo I can track for changes?

Update: your patch is working fine on 3.15 rc2. The only thing I had to change in the patch for 3.15 rc2 was the variable cmd_timeout_ms is now busy_timeout in struct mmc_command in core.h. So, I just renamed the variable in two places in au6601_send_cmd{} within au6601.c. 

Speeds are limited as you had explained in your patch, but it is very nice to have the sd card working nonetheless. Again, great work my friend!

P.S. I am seeing these in the kernel log. Are you seeing the same thing on 3.14? The sd card mounts fine and is working from userland (Toshiba 8GB SDHC class 4)
```
[    1.008093] BUS width 1 [    1.008102] time 0. set freq 150000, c8, 0
[    1.008113] BUG: scheduling while atomic: kworker/u8:5/89/0x00000002
[    1.008192] Modules linked in: atkbd libps2 ahci libahci libata xhci_hcd scsi_mod au6601 usbcore usb_common i8042 serio sdhci_acpi sdhci mmc_core
[    1.008218] CPU: 1 PID: 89 Comm: kworker/u8:5 Tainted: G        W     3.15.0-rc3-mainline-motley #1
[    1.008222] Hardware name: ASUSTeK COMPUTER INC. UX302LA/UX302LA, BIOS UX302LA.204 09/03/2013
[    1.008235] Workqueue: kmmcd mmc_rescan [mmc_core]
[    1.008238]  ffff88011ee93100 ffff880037f01b18 ffffffff814a6178 ffff880037f01c60
[    1.008245]  ffff880037f01b28 ffffffff814a3180 ffff880037f01c30 ffffffff814a8728
[    1.008250]  ffff880037ef9aa0 ffff880037f01fd8 0000000000013100 0000000000013100
[    1.008256] Call Trace:
[    1.008272]  [<ffffffff814a6178>] dump_stack+0x4d/0x6f
[    1.008279]  [<ffffffff814a3180>] __schedule_bug+0x47/0x55
[    1.008287]  [<ffffffff814a8728>] __schedule+0x768/0x7a0
[    1.008297]  [<ffffffff81099285>] ? log_store+0x165/0x1f0
[    1.008304]  [<ffffffff8108e99d>] ? up+0x2d/0x50
[    1.008311]  [<ffffffff814a8784>] schedule+0x24/0x70
[    1.008319]  [<ffffffff814a7bf6>] schedule_timeout+0x116/0x1a0
[    1.008331]  [<ffffffff8105bc60>] ? migrate_timer_list+0x60/0x60
[    1.008336]  [<ffffffff8105c8df>] msleep+0x2f/0x40
[    1.008343]  [<ffffffffa00ab05e>] au6601_set_power+0x5e/0x80 [au6601]
[    1.008349]  [<ffffffffa00ab373>] au6601_sdc_set_ios+0x253/0x3f0 [au6601]
[    1.008359]  [<ffffffffa0002455>] mmc_set_chip_select+0x35/0xb0 [mmc_core]
[    1.008370]  [<ffffffff8125f9ca>] ? __delay+0xa/0x10
[    1.008381]  [<ffffffffa000774f>] mmc_go_idle+0x6f/0xc0 [mmc_core]
[    1.008390]  [<ffffffffa00035dd>] mmc_rescan+0x23d/0x2e0 [mmc_core]
[    1.008398]  [<ffffffff810683ed>] process_one_work+0x13d/0x390
[    1.008404]  [<ffffffff81068d39>] worker_thread+0x119/0x3a0
[    1.008409]  [<ffffffff81068c20>] ? manage_workers.isra.26+0x2a0/0x2a0
[    1.008417]  [<ffffffff8106eecd>] kthread+0xcd/0xf0
[    1.008424]  [<ffffffff8106ee00>] ? kthread_create_on_node+0x180/0x180
[    1.008433]  [<ffffffff814b0fcc>] ret_from_fork+0x7c/0xb0
[    1.008440]  [<ffffffff8106ee00>] ? kthread_create_on_node+0x180/0x180



```

---

### Post by micucci on 2014-05-02
Hello motley
Sorry for my newbie level, but how do you put your patch ? (I found it here [https://bitbucket.org/motley/kernel_asus_ux302/src](https://bitbucket.org/motley/kernel_asus_ux302/src) )
Thanks

---

### Post by marc25 on 2014-05-07
Hello!

Sorry, but I am still not sure how to install Ubuntu at all.
Searched the forums, but I found no clear explaination /instruction.
So, as most of you here own this Ultrabook, do you know a kind
of quick installation tutorial? What troubles me is that ubuntu (14.04 and 14.10) does not
offe me an option to install ubuntu alongstide windows 8 and many
wrothe, that the ultrabook doesnt recognize ubuntu after the installation.

Hope you can help me. Thank you!

---

### Post by bug-track on 2014-05-11
Hm... for some reasons i don't get notification from this forum. Just accidentally visited it.

If you use RFC version, then it's time to update. Here is latest version [http://www.spinics.net/lists/linux-mmc/msg26292.html](http://www.spinics.net/lists/linux-mmc/msg26292.html)
Suddenly i didn't got any response  from MMC devs. Don't know if there all so busy or afraid of the word "reverse engineering".

---

### Post by bapoumba on 2014-05-11
> **bug-track said:**
> Hm... for some reasons i don't get notification from this forum. Just accidentally visited it.


    Top right forums page > Settings > General Settings > Message & Notification item.

---

### Post by bug-track on 2014-05-11
Thx. It works.

---

### Post by motley-slate on 2014-05-24
> **bug-track said:**
> Hm... for some reasons i don't get notification from this forum. Just accidentally visited it.

If you use RFC version, then it's time to update. Here is latest version [http://www.spinics.net/lists/linux-mmc/msg26292.html](http://www.spinics.net/lists/linux-mmc/msg26292.html)
Suddenly i didn't got any response  from MMC devs. Don't know if there all so busy or afraid of the word "reverse engineering".

Nice work, thanks!  I am using the latest version with 3.15 rc6 and the speeds are now as expected. 

I am still getting the following mmc rescan kernel messages and am wondering if you see them as well. Any idea to what is causing them?
```
[  135.804767] CPU: 0 PID: 80 Comm: kworker/u8:3 Tainted: G        W  O  3.15.0-rc6-mainline-motley #1[  135.804771] Hardware name: ASUSTeK COMPUTER INC. UX302LA/UX302LA, BIOS UX302LA.204 09/03/2013
[  135.804790] Workqueue: kmmcd mmc_rescan [mmc_core]
[  135.804794]  ffff88011ee13480 ffff8801192c5a48 ffffffff814b7674 0000000000000000
[  135.804800]  ffff8801192c5a58 ffffffff81079f09 ffff8801192c5b60 ffffffff814b918d
[  135.804805]  ffff88011906d8c0 0000000000013480 ffff8801192c5fd8 0000000000013480
[  135.804811] Call Trace:
[  135.804825]  [<ffffffff814b7674>] dump_stack+0x4d/0x6f
[  135.804836]  [<ffffffff81079f09>] __schedule_bug+0x49/0x60
[  135.804842]  [<ffffffff814b918d>] __schedule+0x5dd/0x7c0
[  135.804847]  [<ffffffff814b9394>] ? schedule+0x24/0x70
[  135.804853]  [<ffffffff814b8801>] ? schedule_timeout+0x151/0x1b0
[  135.804857]  [<ffffffff814b9394>] ? schedule+0x24/0x70
[  135.804862]  [<ffffffff814b8801>] ? schedule_timeout+0x151/0x1b0
[  135.804867]  [<ffffffff814b9394>] schedule+0x24/0x70
[  135.804872]  [<ffffffff814b87c6>] schedule_timeout+0x116/0x1b0
[  135.804878]  [<ffffffff8105eee0>] ? migrate_timer_list+0x60/0x60
[  135.804885]  [<ffffffff8107ebc0>] ? wake_up_process+0x40/0x40
[  135.804891]  [<ffffffff8105f8df>] msleep+0x2f/0x40
[  135.804908]  [<ffffffffa0144370>] au6601_set_power.isra.6+0x90/0xb0 [au6601]
[  135.804923]  [<ffffffffa01454da>] au6601_sdc_set_ios+0x1ea/0x475 [au6601]
[  135.804942]  [<ffffffffa00025b5>] mmc_set_chip_select+0x35/0xb0 [mmc_core]
[  135.804949]  [<ffffffff8126d73a>] ? __delay+0xa/0x10
[  135.804968]  [<ffffffffa0007aff>] mmc_go_idle+0x6f/0xc0 [mmc_core]
[  135.804988]  [<ffffffffa00087a8>] mmc_sd_get_cid+0x38/0x210 [mmc_core]
[  135.805006]  [<ffffffffa000909a>] mmc_sd_init_card+0x4a/0x790 [mmc_core]
[  135.805029]  [<ffffffffa0009a57>] mmc_attach_sd+0x87/0x170 [mmc_core]
[  135.805052]  [<ffffffffa0003810>] mmc_rescan+0x270/0x2d0 [mmc_core]
[  135.805059]  [<ffffffff8106bd62>] process_one_work+0x142/0x3b0
[  135.805065]  [<ffffffff8106c6fd>] worker_thread+0x12d/0x3d0
[  135.805071]  [<ffffffff8106c5d0>] ? manage_workers.isra.26+0x2c0/0x2c0
[  135.805078]  [<ffffffff810727d6>] kthread+0xd6/0xf0
[  135.805086]  [<ffffffff81072700>] ? kthread_create_on_node+0x180/0x180
[  135.805092]  [<ffffffff814c218c>] ret_from_fork+0x7c/0xb0
[  135.805099]  [<ffffffff81072700>] ? kthread_create_on_node+0x180/0x180
[  136.087579] mmc0: host does not support reading read-only switch. assuming write-enable.
[  136.092156] BUG: scheduling while atomic: kworker/u8:3/80/0x00000002
[  136.092164] Modules linked in: vboxdrv(O) fuse bnep nls_cp437 vfat fat arc4 cdc_ether usbnet uvcvideo videobuf2_vmalloc ecb videobuf2_memops videobuf2_core btusb videodev r8152 media mii bluetooth joydev intel_rapl mousedev x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel iwlmvm kvm mac80211 crct10dif_pclmul crc32_pclmul crc32c_intel ghash_clmulni_intel aesni_intel asus_nb_wmi ip6t_REJECT iTCO_wdt aes_x86_64 asus_wmi lrw sparse_keymap iTCO_vendor_support gf128mul glue_helper iwlwifi ablk_helper cryptd cfg80211 xt_hl pcspkr microcode mei_me i915 evdev ip6t_rt i2c_i801 mei rfkill psmouse snd_hda_codec_realtek snd_hda_codec_generic shpchp serio_raw thermal wmi lpc_ich snd_hda_intel i2c_algo_bit nf_conntrack_ipv6 snd_hda_controller nf_defrag_ipv6 tpm_tis drm_kms_helper tpm dw_dmac snd_hda_codec
[  136.092263]  battery video dw_dmac_core snd_hwdep ipt_REJECT drm snd_pcm 8250_dw i2c_hid xt_comment intel_gtt spi_pxa2xx_platform xt_LOG snd_timer ac i2c_core snd soundcore processor button xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables ext4 crc16 mbcache jbd2 hid_generic hid_multitouch sd_mod crc_t10dif crct10dif_common hid_logitech_dj usbhid hid atkbd libps2 ahci libahci au6601 libata xhci_hcd scsi_mod usbcore usb_common i8042 serio sdhci_acpi sdhci mmc_core



```

---

### Post by bug-track on 2014-05-24
You can try to remove or reduce msleep() insight of au6601_set_power().

---

### Post by motley-slate on 2014-05-24
> **bug-track said:**
> You can try to remove or reduce msleep() insight of au6601_set_power().

Thanks, I'll play around with that when I get a chance. If [COLOR=#000000]au6601_set_power is called periodically after init, perhaps I will make a module parameter so I can adjust the sleep time to see what works best.[/COLOR] Would that be worth a try?
 
I have to say, after the kinks have been worked out, this is quite a nice little machine for Linux.  I just ordered a 120GB mSATA and the 8GB DDR3L, so I am likely looking at a rebuild next week.  Windows 8 will be removed completely this time :).

Cheers

---

### Post by bug-track on 2014-05-24
I don't think it is worth to have module parameter for it. Theoretically i should not even try to use msleep in atomic context. I used it because windows driver is doing that. Like i said, we can try to remove msleep.

---

### Post by motley-slate on 2014-06-10
> **bug-track said:**
> I don't think it is worth to have module parameter for it. Theoretically i should not even try to use msleep in atomic context. I used it because windows driver is doing that. Like i said, we can try to remove msleep.

Hi, I just wanted to report back. I am now running 3.15 stable with the msleep removed. The system and MMC are running great!

Here is the latest script/patch I use with Arch Linux in case anyone is interested. I just updated it today for 3.15 stable.
[https://bitbucket.org/motley/kernel_asus_ux302](https://bitbucket.org/motley/kernel_asus_ux302)

---

### Post by micucci on 2014-07-03
Hi, 
I discover[ed Prime ]("http://doc.ubuntu-fr.org/prime")which have installed correctly the 2 graphics cards NVidia + Intel. It's very usefull (thanks to** [Hayawane]("http://forum.ubuntu-fr.org/viewtopic.php?pid=17382641#p17382641") )**

btw, if motley-slate or bug-track can explain me how compling the card reader driver, it's should be very very kind ;-)

EDIT : found a driver for SD card reader compiled for Ubuntu here : [https://launchpad.net/~iacobs/+archive/ubuntu/au6601/+packages](https://launchpad.net/~iacobs/+archive/ubuntu/au6601/+packages) (thanks to Sabin Iacobs)

---

### Post by cylehunter33 on 2014-07-11
Updated my kernal from 3.11 to the latest 3.16 kernal last night and it killed my wifi and the display no longer wakes up from sleep mode. Will try downgrading to the latest stable release, and if all else fails revert back to 3.11....

---

### Post by cylehunter33 on 2014-07-13
The stable 3.15 seems to have resolved the problems I was having earlier.

---

### Post by excetara2 on 2014-07-24
Has anyone had problems with mounting partition in fstab?

I have an ntfs partition on a dual-boot system setup in raid0. I can mount the drive using the mount command just fine but when I add it to fstab I get the error:

mount: wrong fs type, bad option, bad superblock on /dev/mapper/isw_djifjjhhid_ASUS_OS7,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


These are the lines from my fstab file with the bottom line being added by me:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/md126p5 during installation
UUID=d4f9468b-a655-491f-b0d1-c4322fae9550 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/md126p2 during installation
#UUID=A262-7052  /boot/efi       vfat    defaults        0       1
# /home was on /dev/md126p6 during installation
UUID=39f3f991-5c9c-4a3c-9e64-b4ca39837cb4 /home           ext4    defaults        0       2
# swap was on /dev/md126p8 during installation
UUID=c674745a-934a-4730-bdfb-267fda2fcb78 none            swap    sw              0       0
UUID=A262-7052  /boot/efi       vfat    defaults        0       1
UUID=691F1BB67AE18A58 /mnt/data                           ext4    defaults      0        2


Any ideas?

---

