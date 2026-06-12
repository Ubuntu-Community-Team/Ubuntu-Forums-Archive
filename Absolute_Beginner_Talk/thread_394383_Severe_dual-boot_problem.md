---
title: "Severe dual-boot problem"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Bracken on 2007-03-26
I installed Ubuntu 6.10 (for the second time) about two weeks ago as a dual-boot with no problems.  Since then I have been exclusively using Ubuntu.  Today, however, I rebooted into Windows to do a quick checkup ("Hi, still there?  Still running?  Good, good...").  Everything involving Windows acted normal, so I tried to reboot back into Ubuntu.  I got the normal BIOS setup screen, but on the "loading Grub..." screen, it cut out half way and my machine rebooted.  Back to the BIOS setup screen, "loading Grub...", and it rebooted again.  I couldn't boot into either OS because it would never get as far as the boot prompt.  Not knowing what else to do, I ran my live CD and re-installed Ubuntu.

The first time installing Ubuntu a different - but similar - booting problem occurred.  The first time I booted into Windows it ran chkdisk, booted and ran properly, and when I rebooted to get back into Ubuntu it froze (in the same place that it rebooted in the previous statement).  Using the live CD I re-installed Ubuntu.
The reason I mention this incident second is because there were other problems occurring at the time - the reason for freezing before the boot prompt may not have anything to do with the first problem, which came as a complete surprise.  I add it so as to show that this isn't the first time I've had boot prompt problems (say that three times fast!).

Windows isn't that important to me, but I don't want to lose it completely and I would like to be able to boot into it sometimes without this happening.  Any help on why this might have happened, whether this will be a recurring problem, and/or how to fix it is appreciated.  (I'm a newbie, so please go easy on me.  Thanks)

Laptop:
Toshiba Satellite M105 S3064

Thank you,
Bracken

---

### Post by lamalex on 2007-03-26
I'm not really sure what the actual problem is, but my advice is to download the GRUB cd and just reinstall GRUB instead of ubuntu, probably save yourself some headache.

---

### Post by codesplice on 2007-03-26
Hi Bracken,
What steps did you use for configuring your dual installation?

It might be worth trying to go through the installation steps again, following the instructions on [this page](https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo).  It seems like either OS may have done something to cause your bootloader to stop working - since your recent Ubuntu install is pretty fresh, it would probably be easier just to reinstall it properly rather than muck about with repairing your boot loader.

Good luck!

---

### Post by Bracken on 2007-03-26
Thank you both for your responses!

I didn't do much for configuring, just:
backed up my Windows data, 
defragged, 
booted to the live CD and partitioned the harddrive (most for Ubuntu, 1GB swap)

I'm not sure what I could have done differently to make the installation work properly.

---

### Post by codesplice on 2007-03-26
I don't really know what may have been screwed up... - did you verify the disk image before the install?  

/me is just shooting in the dark here... ;)

---

