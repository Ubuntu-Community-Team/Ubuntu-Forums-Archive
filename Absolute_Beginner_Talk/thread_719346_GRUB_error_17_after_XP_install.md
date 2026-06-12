---
title: "GRUB error 17 after XP install"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by imnotryan on 2008-03-09
Had win2k and Gutsy dual booting just fine on two seperate hard drives.

Installed XP today figuring that this guide...

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

...would see me through this.

Ofcourse it did not.  I followed the instructions in that thread and everything appeared to have worked.  No errors were presented.

Upon reboot it still just boots into XP.

I switched the boot order of the hard drives and got my old grub screen showing windows 2000.   However NONE of the options work, citing error 17 when I select ubuntu, and error 13 when I select windows 2000.

So I can't get into my Ubuntu. :(

---

### Post by sandysandy on 2008-03-09
what r ur two Hdd.

was XP installed on the Gutsy hdd or the other hdd.

did u re-install grub using the thread mentioned above.

regards

---

### Post by imnotryan on 2008-03-09
> **sandysandy said:**
> what r ur two Hdd.

was XP installed on the Gutsy hdd or the other hdd.

did u re-install grub using the thread mentioned above.

regards

XP was installed over the win2k hard drive after a format.

The Ubuntu Gutsy hard drive is still in tact, when I boot using the live CD I can see my files.

I did reinstall grub using the thread as mentioned, and it apparently worked without a hitch according to the terminal.

---

### Post by EvilBro on 2008-03-09
Is your menu.lst correct? (I had problems with that [here](http://ubuntuforums.org/showthread.php?t=602367) and [here](http://ubuntuforums.org/showthread.php?t=645820)).

---

### Post by sandysandy on 2008-03-09
> **imnotryan said:**
> XP was installed over the win2k hard drive after a format.

The Ubuntu Gutsy hard drive is still in tact, when I boot using the live CD I can see my files.

I did reinstall grub using the thread as mentioned, and it apparently worked without a hitch according to the terminal.

it seems that ur grub needs to be installed again.

u may like to try out Super Grub Disk (SGD) to fix your grub.

SGD can be downloaded from net and burnt as iso image on CD. Boot from SGD and go thru the various options. u can use the option to fix boot of GNU/Linux.

u can also see whether the menu.lst is oK as suggested in post above.

regards

---

### Post by imnotryan on 2008-03-09
> **EvilBro said:**
> Is your menu.lst correct? (I had problems with that [here](http://ubuntuforums.org/showthread.php?t=602367) and [here](http://ubuntuforums.org/showthread.php?t=645820)).

Right now I'm on ubuntu using the livecd.  So that may explain any oddities in the following codes.

I checked my grub stage one and as you can see here, It was hd1,0.

> ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd1,0)
grub> quit
quit
ubuntu@ubuntu:~$ sudo gedit /media/disk/boot/grub/menu.lst


As you can see I than went into my menu.lst.  There I see this when the #'s end.

> ## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7c24b2ff-40d3-47e0-9961-a62b0ebf405f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7c24b2ff-40d3-47e0-9961-a62b0ebf405f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7c24b2ff-40d3-47e0-9961-a62b0ebf405f ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7c24b2ff-40d3-47e0-9961-a62b0ebf405f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Everything looks right, right?

Still, If one HD is set to boot primary I get winXP.  If the other is set to primary I get a grub screen full of error 17's and error 13's.

Would a fresh install of Gutsy over the existing installation fix anything?  Would it mess anything up?  

I usually keep everything backed up and never fear a fresh install but for once... I'm "that guy" who can't afford to reformat that hard drive right now. :(

---

### Post by EvilBro on 2008-03-10
> **imnotryan said:**
> Everything looks right, right?
I can find no fault with it. I'm assuming that changing the boot order doesn't change the designation of hd0 and hd1, but in case it does, you could change one of the linux entries to hd0. It should be noted that I don't know how safe this action is! (so you might want to wait for someone who actually knows what they are doing.)

---

