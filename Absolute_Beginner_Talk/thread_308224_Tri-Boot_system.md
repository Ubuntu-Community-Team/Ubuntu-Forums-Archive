---
title: "Tri-Boot system"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Josh_b on 2006-11-27
Hey,

I'm about to get Windows Vista and another SATA2 HDD to install it on. I've already got a SATA 2 with XP installed and an IDE with Ubuntu (I installed XP first, then Ubuntu and GRUB). My question is, do I have to do anything special (I know a lot of people had trouble with install Ubuntu the XP on the same hhd) since they are all going to be on seperate hard drives. I'm asking this beforehand, as I don't really want to have to reinstall XP or Ubuntu, so I don't want to stuff it up.

Any help would be appreciated.

Thanks
Josh

---

### Post by turbojugend_gr on 2006-11-27
I am not 100%, but 99% I am, VISTA as windows usually do will rewrite your MBR, thus deleting GRUB, so You need to restore grub after that. If you wish to do so follow [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and normally you should do it. Though I would suggest you searching this forums for other Vista users. They can make sure what I am saying is also after a Vista installation.

---

### Post by Josh_b on 2006-11-27
I did a brief search on the forums, but it seems everyone else wants to know how to do it on one hard drive. I want to do it on 3 seperate hard drives (As in 3 physical hard drives, not 3 partitions on the 1 physical hard drive). Will I still face the same problems? Doesn't each hdd have a seperate MBR and thus Vista wouldn't override the MBR on the Linux and XP hdd, or have I completely missed the mark?

Josh

---

### Post by gn2 on 2006-11-27
This might work: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by Josh_b on 2006-11-27
That's the information I wanted. Thank you. It just so happens, that's how I installed XP and Ubuntu in the first place (although, I didn't unplug the other hard drive). I was going to do that with Vista, but wasn't sure if anything would be overwritten or anything as it was Windows after Ubuntu, but that link answered my question. Although, what will I add to the /boot/grub/menu.lst file considering that it is Vista not Xp.

Josh

---

### Post by gn2 on 2006-11-28
There is no need to modify Grub at all, so long as you use the F8 list to select a boot device.

Load Vista and it's bootloader on a drive with both the others disconnected.

---

### Post by Josh_b on 2006-12-03
So does that mean I will have to unplug my other drives to run Vista? Or is that only during the install process? I would much prefer to use GRUB to choose which OS I want to use.

Josh

---

### Post by bodhi.zazen on 2006-12-04
I assume you are up and running with your current box ?

Just add you new drive, install vista, then you will need to re-install grub.

Then add a stanza in grub for vista and you should be fine....

Is there a step you need assistance with?

---

### Post by kakalaky on 2006-12-04
Just unplug them during the install.  Not sure what you would put in grub for vista.

---

### Post by Josh_b on 2006-12-04
Yes. Reintstalling GRUB and adding the required stanza. Although, I won't do it just yet, as the company I was going to buy the hard drives off has run out and will be ordering more, so I have to wait.

Thanks
Josh

---

### Post by autocrosser on 2006-12-04
I tri-boot XP, Edgy & Feisty with two drives--one that has XP & Feisty on it & one that just has Edgy--I'm using one MBR on the "main" drive (with XP & Feisty)--the Edgy drive was just formatted as EXT3. Grub is on the "main" only. My important area of menu.lst looks like:

## ## End Default Options ##

splashimage=(hd0,1)/boot/grub/splashimages/debsplash.xpm.gz

title        Edgy, kernel 2.6.17-10-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ht=on ro splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Edgy, kernel 2.6.17-10-generic (single-user mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Edgy, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

title        Feisty, kernel 2.6.19-7-generic root        (hd0,1)
kernel        /boot/vmlinuz-2.6.19-7-generic root=/dev/hda2 ht=on ro quiet splash
initrd        /boot/initrd.img-
2.6.19-7-generic savedefault
boot

title        Feisty, kernel 2.6.19-7-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.19-7-generic root=/dev/hda2 ro single
initrd        /boot/initrd.img-
2.6.19-7-generic boot

title        Feisty, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin 
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1


I would say that you could install Vista without anything else plugged in & then make sure that when you reboot the first time after replugging all the drives either:

1. F8 to your original MBR drive & then modify the menu.lst (identify your "new" drives id)

2.reset your bios to make sure that Vista is not first in boot order

3. all of the above

I think if you make your Vista drive the "third" in boot order, it would reflect (hd2,0) in the menu.lst--(of course this depends where you put it in boot order:rolleyes:)

I would get other opinions before finalizing this.

---

### Post by turbojugend_gr on 2006-12-04
> **bodhi.zazen said:**
> I assume you are up and running with your current box ?

Just add you new drive, install vista, then you will need to re-install grub.

Then add a stanza in grub for vista and you should be fine....

Is there a step you need assistance with?

second that.

---

