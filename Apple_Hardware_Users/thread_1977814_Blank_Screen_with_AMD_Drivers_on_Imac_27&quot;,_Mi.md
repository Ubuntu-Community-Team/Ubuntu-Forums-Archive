---
title: "Blank Screen with AMD Drivers on Imac 27&quot;, Mid 2011 with 12.04"
date: 2012-05-10
forum: Apple Hardware Users
---

### Post by lukeco11 on 2012-05-10
Had 11.10 running well on my 27" iMac (12,4) from mid 2011, however recently tried installing Precise several times and it boots fine, but then when I install the ATI/AMD Drivers via Jockey or from command-line it boots up, shows the Ubuntu purple screen with the animated dots, and then goes completely black. I can't use the F keys to get to a command line, and although I can hear the hard-drive still spinning it is totally unresponsive. I can never seem to get to the login prompt. The only difference my machine has from stock is more ram installed and the i7 chip. I am booting from rEFIT with EFI64 emulation. 

I can get to a command prompt in recovery mode, and if I run startx it says something along the lines of "no usable screens found." 

Anyone have any idea how to fix this? I would love to get the drivers working so I can use multiple monitors at full resolution with decent speed. Changes to xorg.conf don't seem to make a difference, but I have only tried the ATI configured version, vesa version, and nothing. 

Thanks for your help!

Luke

---

### Post by yinnus on 2012-05-15
i have the same computer and always had issues with ati drivers.  my work around is do a clean install of 12.04, disable restricted drivers before doing any updates.  after doing this i had no problems booting up.  no need for the ati drivers.  12.04 seems to recognize the apple display and the resolution is set to 2560x1440 automatically.

hope this works for you..

---

### Post by lukeco11 on 2012-05-15
Thanks for the reply. I can definitely run the standard drivers, but with multiple monitors they are painfully slow and nearly unusable. I was hoping to use the ATI drivers to speed things up a bit, otherwise, sadly, I am stuck in Mac OSX. 

Any one have any ideas on what to check or change to prevent this blank screen at boot?

Thank you!

---

### Post by pindar on 2012-05-15
> **lukeco11 said:**
> Thanks for the reply. I can definitely run the standard drivers, but with multiple monitors they are painfully slow and nearly unusable. I was hoping to use the ATI drivers to speed things up a bit, otherwise, sadly, I am stuck in Mac OSX. 

Any one have any ideas on what to check or change to prevent this blank screen at boot?

Thank you!
This is an issue of the interplay between kernel, firmware, xorg, and the binary drivers, so it's not a simple issue of checking something to prevent this - there is a good chance that your particular combination will just not work. With older kernels, I have had some success with older versions of the ati catalyst drivers. You would have to uninstall the version offered by ubuntu and just try older versions (there's a debian script sgfxi which makes this less tedious). But it will be a pretty clumsy process because it's just hit or miss; any particular version might or might not work, and every kernel upgrade might break it. Sorry, I have a mid-2011 22" imac, and that's just the way it is with this graphics card.

---

### Post by DoubleClicker on 2012-05-16
I had this same issue when I did an upgrade install, but with a clean install the driver worked with no problems.

If you don't want to do a clean install, i would recommend booting in recovery mode, without starting xorg. 

sudo aptitude purge xserver-xorg-video-radeon xserver-xorg-video-radeonhd xserver-xorg-video-ati fglrx fglrx-modaliases fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev

reboot into recovery mode again,
sudo rm -r /etc/ati
sudo rm -rf /usr/share/ati
sudo rm /etc/X11/xorg.conf*
sudo aptitude install fglrx 
(if you get any errors, report them here.)

reboot into normal mode

---

### Post by 3togo on 2012-06-23
Not working :(

> **DoubleClicker said:**
> I had this same issue when I did an upgrade install, but with a clean install the driver worked with no problems.

If you don't want to do a clean install, i would recommend booting in recovery mode, without starting xorg. 

sudo aptitude purge xserver-xorg-video-radeon xserver-xorg-video-radeonhd xserver-xorg-video-ati fglrx fglrx-modaliases fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev

reboot into recovery mode again,
sudo rm -r /etc/ati
sudo rm -rf /usr/share/ati
sudo rm /etc/X11/xorg.conf*
sudo aptitude install fglrx 
(if you get any errors, report them here.)

reboot into normal mode

---

### Post by Lunarts on 2012-06-28
Add ¨nopat¨ at the side of ¨quiet splash¨ at the grub entry configuration relative to your installed ubuntu 12.04. 

Also, say this bug affects you too below:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1004546](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1004546)

---

### Post by rliegh on 2013-05-05
I have had this problem with Lubuntu 12.10 (Ubuntu 12.04 worked just fine for me). Adding "nopat" didn't work for me, but adding "nomodeset" after "quiet splash" did work.

---

