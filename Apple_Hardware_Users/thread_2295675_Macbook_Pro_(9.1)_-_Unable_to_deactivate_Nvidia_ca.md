---
title: "Macbook Pro (9.1) - Unable to deactivate Nvidia card"
date: 2015-09-20
forum: Apple Hardware Users
---

### Post by Lyrx on 2015-09-20
Hello,

I recently installed Ubuntu on my Macbook Pro and run into an issue. I am not able to deactivate the Nvidia graphic card, which results in a lot of battery drain plus the fans are going crazy (more or less).

I figured out that I should use vgaswitcheroo in order to deactivate the nvidia card and only use the Intel one. So I went ahead and edited the grub file. I read that I am supposed to modify the "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" according to my card. That was my first issue - since I wasn't sure whether I should add the card I want to use here or the one I want to deactivate. I tried it with "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noveau.modeset=1"" first, updated the grub and rebooted my Macbook. Then I went ahead and used "sudo echo OFF > /sys/kernel/debug/vgaswitcheroo/switch" & "sudo echo IGD > /sys/kernel/debug/vgaswitcheroo/switch". Afterwards I checked the status of the cards using "sudo cat /sys/kernel/debug/vgaswitcheroo/switch" but it only shows "IGD" as "off" and DIS is still listed with "Pwr".
I tried the same using "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"" but it resulted in the same issue.

I am kinda lost here now since I've already read through every thread which could fit my issue but nothing helped.

---

### Post by este.el.paz on 2015-09-21
> **Lyrx said:**
> Hello,

I recently installed Ubuntu on my Macbook Pro and run into an issue. I am not able to deactivate the Nvidia graphic card, which results in a lot of battery drain plus the fans are going crazy (more or less).

I figured out that I should use vgaswitcheroo in order to deactivate the nvidia card and only use the Intel one. So I went ahead and edited the grub file. I read that I am supposed to modify the "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" according to my card. That was my first issue - since I wasn't sure whether I should add the card I want to use here or the one I want to deactivate. I tried it with "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noveau.modeset=1"" first, updated the grub and rebooted my Macbook. Then I went ahead and used "sudo echo OFF > /sys/kernel/debug/vgaswitcheroo/switch" & "sudo echo IGD > /sys/kernel/debug/vgaswitcheroo/switch". Afterwards I checked the status of the cards using "sudo cat /sys/kernel/debug/vgaswitcheroo/switch" but it only shows "IGD" as "off" and DIS is still listed with "Pwr".
I tried the same using "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"" but it resulted in the same issue.

I am kinda lost here now since I've already read through every thread which could fit my issue but nothing helped.

I think you might be over-complicating or making connections that might not apply . . . ????  Grub is to boot the OS.  You can select "additional drivers" from in Software Center and you should get some choices for your Nvidia card--that ***shouldn't**** be making the fans "go crazy" . . . .  The graphics card relates to the GUI, so, unless you have two cards then you probably don't want to shut it off, unless you are only doing CLI work.

For the fan issue check out the Mactel sticky at the top of the forum page . . . it can be a "known issue" as far as "fan control" problems with Intel Macs.  I found the threads by "mike braxner" and then got some hints on how to set up "macfancntrl"???  to help get all of the fan/temp sensors set up so the fan doesn't blow all the time at top speed.  On my MBPro there still is a tendency for linux to run "warmer" . . . than the OSX side . . . but, it does take some time to get it dialed in . . . .

e.e.p.

---

