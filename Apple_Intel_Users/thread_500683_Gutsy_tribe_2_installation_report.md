---
title: "Gutsy tribe 2 installation report"
date: 2007-07-14
forum: Apple Intel Users
---

### Post by blippy on 2007-07-14
OK. I tested Gutsy tribe 2 on my Intel iMac 20", UK keyboard.

INSTALLATION ATTEMPT 1

1. keyboard was responsive at boot prompt (a bit of a novelty!)
2. X server failed to start:
[INDENT]Fatal server error:
Caught signal 11. Server aborting[/INDENT]

INSTALLATION ATTEMPT 2
1. keyboard was unresponsive at boot prompt
2. X server came up OK.
3. Installer had problems with manual partitioning, when I hit the Back button (sorry, I can't provide any further detaisl as yet)

INSTALLATION ATTEMPTS 3 AND 4
1. keyboard was unresponsive at boot prompt
2. X server failed to start (same problem as attempt 1)


DISAPPOINTING

Sorry guys, let's just say that I had hoped for better. I know it's only an alpha version - let's hope this stuff gets ironed out for the main release.

BUG REPORTS

I haven't opened any bug reports, but I have annotated the following bugs that were already in existence:

[36342]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/36342") - grub (installer too) doesn't work with apple usb-keyboard on a pc-system

[62002]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/62002") - [i945] Installer X server startup fails

[120420]("https://bugs.launchpad.net/ubuntu/+bug/120420") - Tilde not working on iMac in UK (Feisty)

There appears to be problems with the installer, too, but with the persistent failure of the X server, I don't yet know how to test it.

---

### Post by thonuz on 2007-07-14
I had problems with manual partitioning also, but on tribe 1 it worked I believe. Other than that everything works on core 2 intel macbook. 
you should try installing again. Use qtparted to partition. You can install it live. Then try a dist-upgrade. The only other problem for me has been compiz. Gutsy is a big improvement over feisty otherwise. Updates will break wireless which requires you to recompile madwifi.

---

### Post by cyberdork33 on 2007-07-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/123341](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/123341) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				They failure to start Xorg is seemingly pretty common. Please go to my but report and confirm it. I have not had a problem during startup that last few times for some reason.

I have not actually tried to install gutsy on my Mac, but your problems with the partitioner seem consistent with what I experienced on another machine. I actually couldn't get it to install unless I just told it to use the entire disk.

The no keyboard in grub error is well known. It is a bug in Apple's firmware and probably will not be fixed anytime soon. I have found that unplugging and reconnecting my keyboard and the selection screen will get it to start working though.

---

### Post by blippy on 2007-07-14
> **thonuz said:**
> I had problems with manual partitioning also,.

Actually, reading someone's blog, the manual partitioning woes seems to be a known issue, and doesn't require reporting.

>  Gutsy is a big improvement over feisty otherwise. 

Sounds exciting. Actually, I'm quite happy that I've found Feisty drivers for my Quickcam Pro 5000, and now using (an upgraded) aMSN I can webcam with friends who are on MSN Messenger. 

I'm a newbie to iMacs (it's less than 3 months old) and Macs in general. Having played with OS X and Ubuntu, I now don't have OS X on my system. The Ubuntu repos are a big win for me. Plus, I think that OS X is a bit "black box"y for me.

What I also want to see in Gutsy is a more stable Firefox when viewing YouTube. Fingers crossed!

---

### Post by blippy on 2007-07-14
> **cyberdork33 said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/123341](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/123341) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				They failure to start Xorg is seemingly pretty common. Please go to my but report and confirm it. 

Done.

---

