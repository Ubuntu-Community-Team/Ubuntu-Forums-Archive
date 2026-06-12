---
title: "Ubuntu on a Mac Mini 2,1 (2007) for a Linux-novice?"
date: 2017-04-06
forum: Apple Hardware Users
---

### Post by strawbale on 2017-04-06
Hello,
I'm completely new to Linux, Ubuntu and this forum and would like some advice.
I've been on OSX since 2009, first on a (new) 2007 Mac Mini (2,1)* and since a few years on a (used) 2007 MBP (3,1)**. The former runs 10.6.8 (and won't go beyond 10.7), the latter on 10.11.6 (and won't go further). The MBP will die one day (soon?) and anyway will receive the last security update (probably) some time mid-2018. As I don't really need a laptop, one option for a new small desktop from mid-2018 (or earlier) would be a new Mac Mini, although it's not sure whether Apple will ever upgrade the current (2014) model, which, for instance, doesn't support 4k@60Hz (something I don't care about right now, but may/will do in a few years' time). Another option would be to go small desktop Linux (NUC?). To 'prepare' for a possible switch I've been thinking about trying to get to grips with Linux on my old MM, but after reading [https://ubuntuforums.org/showthread.php?t=2287767&highlight=macmini+2007](https://ubuntuforums.org/showthread.php?t=2287767&highlight=macmini+2007) I'm not at all sure it'll be doable for a novice like me. Another option is dual boot on my MBP, but as it already has severe booting issues with OSX (only works 1 in 4-10 times...) - so try to avoid rebooting - this option is not a very viable one. A third option would be to buy a cheap used PC that is known for running Linux (relatively) smoothly, but I'm hesitant to buy more stuff (than I need).
Any thoughts/advice is much appreciated - thanks!
Peter

* [http://www.everymac.com/systems/apple/mac_mini/specs/mac-mini-core-2-duo-2.0-specs.html](http://www.everymac.com/systems/apple/mac_mini/specs/mac-mini-core-2-duo-2.0-specs.html) (with 2GB RAM)
** [http://www.everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-2-duo-2.4-17-santa-rosa-specs.html](http://www.everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-2-duo-2.4-17-santa-rosa-specs.html) (with 4GB RAM)

---

### Post by mörgæs on 2017-04-07
The guide to which you linked is for 15.04. The problem 

> The first thing to note about the Mac Mini 2,1 is that while it has an x64 processor (Core 2 Duo), it has a 32-bit EFI implementation

is likely to have been at least partially solved in 17.04 so I suggest that you first try this version in a live boot. Let's wait a little with the actual install.

---

### Post by strawbale on 2017-04-07
> **mörgæs said:**
> The guide to which you linked is for 15.04. The problem 


is likely to have been at least partially solved in 17.04 so I suggest that you first try this version in a live boot. Let's wait a little with the actual install.

OK, thank you. I will google how to 'live boot' and take it from there. From USB-key or CD?

---

### Post by mörgæs on 2017-04-08
I don't know if a Mac is better at digesting one or the other but in the PC world I would begin with USB.

---

### Post by strawbale on 2017-04-08
> **mörgæs said:**
> I don't know if a Mac is better at digesting one or the other but in the PC world I would begin with USB.

OK - thanks!

---

### Post by dancheng on 2017-04-08
I have a Mac Mini 1,1 (2006).  After failing to install Ubuntu or Xubuntu 16.04 LTS to my Mac Mini 1,1 (very old hardware version) from a Ubuntu or Xubuntu i386 ISO burnt on a DVD, I have stumbled on a webpage with very useful information. It says that Mac Mini 1,1 firmware is very choosy - there must be only one bootloader in the ISO. Otherwise, the firmware will be confused and the ISO cannot be booted.

I thus googled around and found a Debian net-install i386 ISO specially made for mac with one bootloader. Lo and behold! This ISO boots OK. I have now installed Debian 8.7 (pretty up to date) on my MAc Mini 1,1. In my case, I have replaced the existing HD installed with Mac OS X by a blank unformatted 64GB SSD. Thus my Debian 8.7 is installed on an entire SSD without any issue with dual boot problem.

The Debian net-install i386 ISO for mac installs the base Debian linux only and requires internet connection so that it would download other desktop or server components. There are plenty desktops to choose from including GNOME, Xfce, KDE, Cinnamon, MATE and LXDE. Those who prefer Ubuntu could choose the GNOME desktop. I prefer Xubuntu and thus have chosen the Xfce desktop.

I am a Chrome user. But Google has stopped the support of its Chrome browser for i386 machine. To my relief, the open-source browser Chromium is still available for i386 cpu and it is pretty much identical to Google Chrome from a user perspective. I am now using it on my Mac Mini 1,1 as I editing this post.

Here are some links that I have found useful:

1. Debian net-install i386 ISO for mac 
[http://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-mac-8.7.1-i386-netinst.iso](http://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-mac-8.7.1-i386-netinst.iso)

2. Video tutorial of booting up the Debian ISO 
[https://www.youtube.com/watch?v=tZTXWSNYvKE](https://www.youtube.com/watch?v=tZTXWSNYvKE)

3. Things to do after installing Debian 8
[https://linuxpanda.wordpress.com/2014/03/02/things-to-do-after-installing-debian-8-jessie/](https://linuxpanda.wordpress.com/2014/03/02/things-to-do-after-installing-debian-8-jessie/)

4. Video tutorial to replace the HD of a Mac Mini
[https://www.youtube.com/watch?v=nV8EU2VMuCU](https://www.youtube.com/watch?v=nV8EU2VMuCU)

Some further comments following my post above.

The hard disk inside my Mac Mini 1,1 is very old - used since 2006. Thus well past its useful life after 7 years of continuous usage until 2013 when I retired this Mac mini. I fear, the hard drive could crash any time soon. It is also an old 5400rpm slow spinner - brutally slow to boot up the Mac OS X 10.6 in today's standard. 

A $50 investment for a cheap SSD is pretty good investment, in my view, to replace this end-of-life hard drive.

Opening up the case of my Mac Mini has one more benefit. I have managed to remove a spoonful of lint and dirt from its ventilation fan, thus allowing much better air flow to cool down its Intel cpu chip.

Your Mac Mini of 2007 may worth upgrading with a new SSD if you do go ahead with trying out Linux on it.

---

### Post by strawbale on 2017-04-09
> **dancheng said:**
> I have a Mac Mini 1,1 (2006).  After failing to install Ubuntu or Xubuntu 16.04 LTS to my Mac Mini 1,1 (very old hardware version) from a Ubuntu or Xubuntu i386 ISO burnt on a DVD, I have stumbled on a webpage with very useful information. It says that Mac Mini 1,1 firmware is very choosy - there must be only one bootloader in the ISO. Otherwise, the firmware will be confused and the ISO cannot be booted.

I thus googled around and found a Debian net-install i386 ISO specially made for mac with one bootloader. Lo and behold! This ISO boots OK. I have now installed Debian 8.7 (pretty up to date) on my MAc Mini 1,1. In my case, I have replaced the existing HD installed with Mac OS X by a blank unformatted 64GB SSD. Thus my Debian 8.7 is installed on an entire SSD without any issue with dual boot problem.

The Debian net-install i386 ISO for mac installs the base Debian linux only and requires internet connection so that it would download other desktop or server components. There are plenty desktops to choose from including GNOME, Xfce, KDE, Cinnamon, MATE and LXDE. Those who prefer Ubuntu could choose the GNOME desktop. I prefer Xubuntu and thus have chosen the Xfce desktop.

I am a Chrome user. But Google has stopped the support of its Chrome browser for i386 machine. To my relief, the open-source browser Chromium is still available for i386 cpu and it is pretty much identical to Google Chrome from a user perspective. I am now using it on my Mac Mini 1,1 as I editing this post.

Here are some links that I have found useful:

1. Debian net-install i386 ISO for mac 
[http://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-mac-8.7.1-i386-netinst.iso](http://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-mac-8.7.1-i386-netinst.iso)

2. Video tutorial of booting up the Debian ISO 
[https://www.youtube.com/watch?v=tZTXWSNYvKE](https://www.youtube.com/watch?v=tZTXWSNYvKE)

3. Things to do after installing Debian 8
[https://linuxpanda.wordpress.com/2014/03/02/things-to-do-after-installing-debian-8-jessie/](https://linuxpanda.wordpress.com/2014/03/02/things-to-do-after-installing-debian-8-jessie/)

4. Video tutorial to replace the HD of a Mac Mini
[https://www.youtube.com/watch?v=nV8EU2VMuCU](https://www.youtube.com/watch?v=nV8EU2VMuCU)

Some further comments following my post above.

The hard disk inside my Mac Mini 1,1 is very old - used since 2006. Thus well past its useful life after 7 years of continuous usage until 2013 when I retired this Mac mini. I fear, the hard drive could crash any time soon. It is also an old 5400rpm slow spinner - brutally slow to boot up the Mac OS X 10.6 in today's standard. 

A $50 investment for a cheap SSD is pretty good investment, in my view, to replace this end-of-life hard drive.

Opening up the case of my Mac Mini has one more benefit. I have managed to remove a spoonful of lint and dirt from its ventilation fan, thus allowing much better air flow to cool down its Intel cpu chip.

Your Mac Mini of 2007 may worth upgrading with a new SSD if you do go ahead with trying out Linux on it.

Wow, thank you! Lot to digest, for a complete novice.
My 2007 MM has been running from early 2009 to late 2013, when I started using a (used) MBP. Still use it occasionally, with Snow Leopard. If I get it running fine (first), I'd consider putting in an SSD.

---

### Post by dancheng on 2017-04-09
> **strawbale said:**
> Wow, thank you! Lot to digest, for a complete novice.
My 2007 MM has been running from early 2009 to late 2013, when I started using a (used) MBP. Still use it occasionally, with Snow Leopard. If I get it running fine (first), I'd consider putting in an SSD.

I recommend that you burn the above ISO (See URL 1 of my post) to a CD - yes a CD is big enough because it is Debian linux core system only.
Booting from CD is much easier than from a USB drive.
Insert the CD. 
Power up your Mac Mini while pressing the Option key on your mac keyboard (or Alt key on a PC keyboard)
DO NOT release the Option key (up to 10 or 20 seconds) until the Mac white screen appears showing your hard drive and the CD icons.
You can now release the Option key and use the left arrow or right arrow keys to select the CD icon.
Press the Return key on your mac keyboard (or Enter key on a PC keyboard)
Wait and see if your Mac Mini could boot up with the CD or not.
If booting up from the CD is OK, you should see the Debian boot up screen as shown on the video tutorial (see URL 2 of my post)
Now you can abort the installation process by power down the mac mini.

You have then achieve a major milestone! Congratulations.

In the next stage, I recommend that you watch completely the video tutorial (See URL 2 of my post) to see what to expect in the installation process. I watched it several times before I felt comfortable to do it myself.

When you are ready, repeat the boot up steps above and go through the whole installation process with confidence.

Good luck!

---

### Post by strawbale on 2017-04-10
> **dancheng said:**
> I recommend that you burn the above ISO (See URL 1 of my post) to a CD - yes a CD is big enough because it is Debian linux core system only.
Booting from CD is much easier than from a USB drive.
Insert the CD. 
Power up your Mac Mini while pressing the Option key on your mac keyboard (or Alt key on a PC keyboard)
DO NOT release the Option key (up to 10 or 20 seconds) until the Mac white screen appears showing your hard drive and the CD icons.
You can now release the Option key and use the left arrow or right arrow keys to select the CD icon.
Press the Return key on your mac keyboard (or Enter key on a PC keyboard)
Wait and see if your Mac Mini could boot up with the CD or not.
If booting up from the CD is OK, you should see the Debian boot up screen as shown on the video tutorial (see URL 2 of my post)
Now you can abort the installation process by power down the mac mini.

You have then achieve a major milestone! Congratulations.

In the next stage, I recommend that you watch completely the video tutorial (See URL 2 of my post) to see what to expect in the installation process. I watched it several times before I felt comfortable to do it myself.

When you are ready, repeat the boot up steps above and go through the whole installation process with confidence.

Good luck!

Can I try the above without wiping my HD (and thus OSX) first?

PS: glad it's 'only' 350MB as that'll take 1h30min to download at the moment :-(

---

### Post by strawbale on 2017-04-11
> **dancheng said:**
> I recommend that you burn the above ISO (See URL 1 of my post) to a CD - yes a CD is big enough because it is Debian linux core system only.
Booting from CD is much easier than from a USB drive.
Insert the CD. 
Power up your Mac Mini while pressing the Option key on your mac keyboard (or Alt key on a PC keyboard)
DO NOT release the Option key (up to 10 or 20 seconds) until the Mac white screen appears showing your hard drive and the CD icons.
You can now release the Option key and use the left arrow or right arrow keys to select the CD icon.
Press the Return key on your mac keyboard (or Enter key on a PC keyboard)
Wait and see if your Mac Mini could boot up with the CD or not.
If booting up from the CD is OK, you should see the Debian boot up screen as shown on the video tutorial (see URL 2 of my post)
Now you can abort the installation process by power down the mac mini.

You have then achieve a major milestone! Congratulations.

In the next stage, I recommend that you watch completely the video tutorial (See URL 2 of my post) to see what to expect in the installation process. I watched it several times before I felt comfortable to do it myself.

When you are ready, repeat the boot up steps above and go through the whole installation process with confidence.

Good luck!

I tried this, but the CD doesn't fully 'enter' in the MM (when it's off), so when I power up the MM like you describe the screen shows the HD, but not the CD. How do I 'force' the MM to full take the CD?

Edit: managed to push and keep it in (with another CD) whilst powering up - it worked! Thanks! 
I will now take some time to prepare for the next stage. Will that overwrite the OSX installed?

---

### Post by dancheng on 2017-04-12
> **strawbale said:**
> I tried this, but the CD doesn't fully 'enter' in the MM (when it's off), so when I power up the MM like you describe the screen shows the HD, but not the CD. How do I 'force' the MM to full take the CD?

Edit: managed to push and keep it in (with another CD) whilst powering up - it worked! Thanks! 
I will now take some time to prepare for the next stage. Will that overwrite the OSX installed?

Watch the video in full (URL 2 of my post).
There is a step where you can choose to (1) automatically partition the whole disk (i.e. overwriting OSX) or (2) manually partition e.g. using the available space on the disk (if there is empty and unpartitioned space).
I chose (1) on my empty SSD.
If you choose (1), debian 8 will overwrite your OSX.
If you choose (2), it may not be feasible if the OSX partition occupies the whole disk, even there are still space inside the OSX partition. Thus you need some utility (e.g. gpart) to shrink the OSX partition to make room for empty space on the disk.  I am not good at such a task. Some one else may help.
Furthermore, suppose you can shrink the OSX partition and Debian 8 installs OK.  There is still the unknown if your Mac Mini firmware can allow you to dual boot on OSX and Debian 8. No one knows until you try it.

All in all, installing Debian 8 on the whole disk is the simplest option.

If you care to keep the OSX hard disk, you can buy a SSD and swap out the harddisk.
More work like what I did. In my case, I judge the OSX hard disk may die any time soon after 7 years of continuous usage.

Regardless what option you choose, ensure your Mac mini is connected to internet (I used ethernet cable; but wifi will do too) so that Debian 8 installer can download desktop component of your choice. Without internet connection, it can only install Debian core which is text based and not very friendly to most users.

Also take your time and not rush to pushing any key during the installation process. Until the installer starts writing to your hard drive at the later phase of the intsallation process, you can always abort the process by powering down the man mini. Nothing has changed.

The most time consuming phase is downloading components from the internet and subsequently their installation. Allow at least 1 hour and work in a place without any distraction.

---

### Post by strawbale on 2017-04-12
> **dancheng said:**
> Watch the video in full (URL 2 of my post).
There is a step where you can choose to (1) automatically partition the whole disk (i.e. overwriting OSX) or (2) manually partition e.g. using the available space on the disk (if there is empty and unpartitioned space).
I chose (1) on my empty SSD.
If you choose (1), debian 8 will overwrite your OSX.
If you choose (2), it may not be feasible if the OSX partition occupies the whole disk, even there are still space inside the OSX partition. Thus you need some utility (e.g. gpart) to shrink the OSX partition to make room for empty space on the disk.  I am not good at such a task. Some one else may help.
Furthermore, suppose you can shrink the OSX partition and Debian 8 installs OK.  There is still the unknown if your Mac Mini firmware can allow you to dual boot on OSX and Debian 8. No one knows until you try it.

All in all, installing Debian 8 on the whole disk is the simplest option.

If you care to keep the OSX hard disk, you can buy a SSD and swap out the harddisk.
More work like what I did. In my case, I judge the OSX hard disk may die any time soon after 7 years of continuous usage.

Regardless what option you choose, ensure your Mac mini is connected to internet (I used ethernet cable; but wifi will do too) so that Debian 8 installer can download desktop component of your choice. Without internet connection, it can only install Debian core which is text based and not very friendly to most users.

Also take your time and not rush to pushing any key during the installation process. Until the installer starts writing to your hard drive at the later phase of the intsallation process, you can always abort the process by powering down the man mini. Nothing has changed.

The most time consuming phase is downloading components from the internet and subsequently their installation. Allow at least 1 hour and work in a place without any distraction.

Thanks again for your detailed approach. I will first move some stuff that I still occasionally use to anither Mac, before I dedice how to proceed (#1 or #2). I think I can shrink the OSX partition with disk utility (in OSX), if need be.
I will also need to decide what desktop to install afterwards - no idea (yet).

---

