---
title: "Disable nvidia card on Macbook Pro 9,1"
date: 2014-05-10
forum: Apple Hardware Users
---

### Post by gamblor01 on 2014-05-10
I'm running Ubuntu 13.10 on a MBP 9,1 (via rEFInd).  It's my work laptop so I don't need it for gaming or anything of that nature.  I'm trying to disable the nvidia card under Ubuntu for a few reasons:


- Returning from suspend/hibernate doesn't work.  The screen is just blank (though the system is clearly on) and the only thing I can do is hold the power button.
- Battery life is not stellar.
- I'm hoping it will resolve an issue with disconnecting my external monitor while running (which turns the laptop screen blank -- see issue #1).
- I'm hoping it will resolve an issue with the newer versions of Hip Chat (graphics are all garbled).




I have tried following these pages for advice:

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)


[http://askubuntu.com/questions/425851/nvidia-driver-for-macbook-pro-9-1](http://askubuntu.com/questions/425851/nvidia-driver-for-macbook-pro-9-1)


[http://ubuntuforums.org/showthread.php?t=2137538](http://ubuntuforums.org/showthread.php?t=2137538)


[http://ubuntuforums.org/showthread.php?t=2098304](http://ubuntuforums.org/showthread.php?t=2098304)




The final link suggests that using an older version of gfxCardStatus resolved the problem, but this still isn't working for me.  I have tried both 2.2.1 and 2.3 and setting it to integrated only doesn't work for me.  In fact, when I set integrated only, Ubuntu just boots up to a blank screen (just like my issues above).  It's clearly running as I was able to enter my password, CTRL+ALT+T, and then run sudo reboot.  After entering my password, sure it enough it rebooted.


So clearly it's an issue with the graphics driver but I'm not sure what I need to do.  Currently I'm running the nouveau driver:


```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 650M Mac Edition] (rev a1)


$ glxinfo | grep -i vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: nouveau
```


I have rolled back all of my changes except I left gfxCardStatus 2.2.1 installed in OS X.  Additionally, I passed in the following options at boot time so that vgaswitcheroo works:

```
i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0
```


Even if I try to echo DIGD into the switch file as the wiki says, it always seems to reboot with the nvidia card/nouveau driver active.  That's when I started looking around and found the gfxCardStatus suggestions to force integrated only, but I can't seem to get this to work.  So I'm basically back to where I started.  The graphics at least work, but it's still nouveau and I'm no closer to disabling the nvidia card.

Anyone have any suggestions?  I have *NOT* yet installed the Intel graphics driver for Linux.  Do I need to do that prior to setting integrated only with gfxCardStatus?

Thanks!

---

### Post by gamblor01 on 2014-05-12
So perhaps the first time around the I had a typo.  Rather than trying to disable the nvidia card, I went the exact opposite route and tried to disable the Intel card, and then install the proprietary nvidia driver.  This caused the system to hang on the boot splash every time.  Luckily I still had another initrd/kernel to boot from so I could remove the nvidia driver. Then I started back over from zero.

I went back and followed the second link above, and I even found this (which is likely where the author of that post got the instructions):

[https://wiki.debian.org/InstallingDebianOn/Apple/MacBookPro/9-1](https://wiki.debian.org/InstallingDebianOn/Apple/MacBookPro/9-1)


I carefully followed all of the information, rebooted into OS X, set integrated only in gfxCardStatus, and then booted Linux.  Presto!  I was able to power down the nvidia card and it worked this time!  Not only that, but glxinfo reported the Intel driver in the Open GL vendor string.  The good news is, that I was running on the HD4000 only, the latest Hip chat worked, and it would even properly suspend.

...Then I connected an external monitor to the display port and the system didn't even recognize it.  I tried connected to my TV and found the same thing.  Not being able to use an external monitor is a deal breaker for me.

So I rolled back all of the configuration and this time set discrete only in gfxCardStatus.  I'm back on the nouveau driver with the nvidia card, and powertop is reporting less wattage being drawn so by setting it to discrete only I have at least extended my battery life a bit, though not nearly as much as if I used the Intel card only.

I think for now I simply give up.  I'll just use the nouveau driver and continue to have worse battery life, use an older version of hip chat, and never be able to suspend.  Maybe I can find another laptop to use at work and give this to someone else that wants to run OS X.  We are hiring a few people...

Bottom line is that the instructions should still work, even with Ubuntu 14.04.  Basically you just need to:

1. Modify /etc/default/grub and add i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0 to the end of the GRUB_CMDLINE_LINUX_DEFAULT variable (inside the quotes).  Something like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=deadline i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0"
```

2. Add the following in /etc/grub.d/10_linux (as suggested, I put them after the line to insert the gzio module -- insmod gzio):

```

   echo "    outb 0x728 1" | sed "s/^/$submenu_indentation/"
   echo "    outb 0x710 2" | sed "s/^/$submenu_indentation/"
   echo "    outb 0x740 2" | sed "s/^/$submenu_indentation/"
   echo "    outb 0x750 0" | sed "s/^/$submenu_indentation/"

```

3. Run:

```
sudo update-grub
```


4. Reboot into OS X

5. Use gfxCardStatus 2.2.1 and set "Integrated only"

6. Reboot into Linux

7. Carry on compiling and configuring mbp_power (to properly wake from standby) and also feel free to echo OFF into /sys/kernel/debug/vgaswitcheroo/switch to power down the nvidia card completely.



It will definitely improve battery life and allow suspend to function.  Just beware that it won't support connecting an external monitor once you do so.  If you're only ever using it with the laptop's screen, then it should be fine.

---

### Post by alan26 on 2014-05-13
Curious, could this be adapted also to controlling different aspects of the MoBo on the Air?

---

### Post by gamblor01 on 2014-05-14
> **alan26 said:**
> Curious, could this be adapted also to controlling different aspects of the MoBo on the Air?

I'm not exactly sure which part of the motherboard you are looking to control.  From what I understand, the Macbook Air does *NOT* have dual video cards it in (what Nvidia refers to as their Optimus technology).  The Air will only contain an integrated Intel card, so none of these steps should apply to the Air.

---

### Post by Pham_Hong_Nhat on 2014-05-22
Why don't you follow my answer on askubuntu, which is in 2nd link. [COLOR=#000000]gfxCardStatus [/COLOR]does not help in my case. Just do after my instruction on askubuntu, you will get it.

However, the following problems that you stated:
[COLOR=#000000]1- Returning from suspend/hibernate doesn't work. The screen is just blank (though the system is clearly on) and the only thing I can do is hold the power button.[/COLOR]
[COLOR=#000000]2- Battery life is not stellar.[/COLOR]
[COLOR=#000000]3- I'm hoping it will resolve an issue with disconnecting my external monitor while running (which turns the laptop screen blank -- see issue #1).[/COLOR]
[COLOR=#000000]4- I'm hoping it will resolve an issue with the newer versions of Hip Chat (graphics are all garbled).[/COLOR]
while 1 and 2 will be solved, external monitor will not working at all with Intel card. I am not sure if it helps for 4

---

### Post by gamblor01 on 2014-05-23
> **Pham_Hong_Nhat said:**
> Why don't you follow my answer on askubuntu, which is in 2nd link.

You might want to go back a re-read my post.  I ***did*** get it working by following those instructions (which is why I marked this thread as SOLVED).  I guess the first time around I typed something wrong?  I don't know, but I eventually did get it to work:

> **gamblor01 said:**
> [COLOR=#000000]I carefully followed all of the information, rebooted into OS X, set integrated only in gfxCardStatus, and then booted Linux. Presto! I was able to power down the nvidia card and it worked this time!


The problem (as you know) is that it doesn't support using an external monitor, so it's not a viable option for me.  I have a 24" monitor I use every day at work and don't plan on giving that up to work solely on my 15" screen.  So I'm back on nouvea.  I'm actually trying to get the nvidia drivers installed (using the ones in the repo and *NOT* manually installing from nvidia.com).  I'm not having any luck:

[/COLOR]http://ubuntuforums.org/showthread.php?t=2224567&p=13025896#post13025896

---

