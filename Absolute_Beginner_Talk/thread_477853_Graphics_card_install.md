---
title: "Graphics card install"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by soul_motor on 2007-06-18
I finally figured out how to get Linux to work on my computer, but I'm using the onboard video card.  This means going into BIOS to switch off my ATI Radeon 9250.  How can I get Ubuntu to recognize how to use the Radeon card?  I'm pretty much a complete beginner here, and the information I've found so far seems useful, but I don't know how to get to the screens for editing:(  Thanks in advance.

---

### Post by SirShaggy on 2007-06-18
> **soul_motor said:**
> I finally figured out how to get Linux to work on my computer, but I'm using the onboard video card.  This means going into BIOS to switch off my ATI Radeon 9250.  How can I get Ubuntu to recognize how to use the Radeon card?  I'm pretty much a complete beginner here, and the information I've found so far seems useful, but I don't know how to get to the screens for editing:(  Thanks in advance.

 I think I would go here:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
grab the STABLE RELEASE  (0.9.5-0ubuntu2, released on June 17 2007)
download it and install it. Then log off your computer, into the BIOS, turn off the onboard graphics, turn on the AGP/PCI/PCI-E graphics card F10 to save the changes and reboot. When Grub comes up hit enter. It will get to a point with a blue screen that says your xserver didn't start with a yes option and the other option is (SKIP or STOP or something like that. hit tab key to skip seeing the output, then enter and enter a second time on the next screen.
This will drop you to a promt. Login with you usual user name and password. After that, simply type:
envy -t and hit enter. There will be like 8 options or so. Choose the one which says install the ATI graphics driver. Hit enter and let it go.
Now, I must say that I had lot's of issues with my ATI card, so bad in fact I switched to all Nvidia cards. Some drivers for ATI cards do not work with some ATI cards. You really should research this part before installing the driver I mentioned above.

Now, if your xserver crashes once you have tried to install the driver, just simply type this at the prompt:
sudo dpkg-reconfigure -phigh xserver-xorg and hit enter, type you password and enter again. That will rebuild your xorg.conf file so you can boot.

Print this post so you dont have to remember all this.

SirShaggy

---

### Post by soul_motor on 2007-06-18
Awesome, thanks a bunch.  I'll update as soon as I get to it!:KS

---

### Post by w4ett on 2007-06-18
Some have had quite a few problems with that card see:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/114520](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/114520)

We've been working on that bug for a number of weeks.

Some folks seem to be ok with that card. See:

[http://ubuntuforums.org/showthread.php?t=235693](http://ubuntuforums.org/showthread.php?t=235693)

Both  the 9200 and the 9250 cards have a bad rap, but with a little work, they can be made to work properly.  If you have troubles with it..we'll be here.

---

### Post by soul_motor on 2007-06-21
I've tried the envy, it seemed easy enough but it didn't seem to work, the last code for resetting the driver is awesome though, thanks!  I tried to follow the Ubuntu documentation page, but no luck with the command line:

$ dpkg-buildpackage -rfakeroot -uc -b

Everything else up to that point I was able to do...  What does that command do, and is it incorrect in it's syntax?  Thanks in advance.  It's great you guys help out us Ubuntu virgins...

---

