---
title: "(grub) Ended up with not-ideal boot situation"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by mikeymikec on 2006-06-09
I have two disks.  The first is my main disk (Windows, FreeBSD, 4 partitions).  In this situation, I didn't bother doing any boot management, preferring to just set the active partition in the OS in order to boot the other. (primary master)

I didn't want to get rid of FreeBSD, so I got an old 10GB disk I had spare, which is plugged into the secondary master, and installed ubuntu on that.  The disk is in a removable hard disk caddy, as it is summer and when I'm not running Linux, I don't want the disk plugged in.

However, Ubuntu has taken over boot management, ignored FreeBSD, and I can't boot from the primary master if the secondary master isn't plugged in (grub error).

I get the feeling that if I use the Win2k setup CD to fix the MBR back to Windows, that I won't be able to boot Ubuntu, no matter what.  Is there some way to make grub just be on the secondary master, and not the primary?

I remember ages ago setting up win2k to be the boot manager for linux/win2k, but I don't know if that would work here.

---

### Post by elamericano on 2006-06-09
sudo grub-install /dev/hdb (or whatever you secong drive is)
Then you can restore your Windows mbr. Grub will boot when that disk is the selected boot device otherwise it will be the active partition on your first disk.

If you really want, you can have the Windows bootloader load Ubuntu: [http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49](http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49)

I'm like you. I prefer to switch active partitions. I run a script/batch file to change the active partition and reboot. No need to wait for a menu.

---

### Post by mikeymikec on 2006-06-09
Thanks for your help, looks easy too :)

---

### Post by mikeymikec on 2006-06-09
Ok, I tried what you suggested, though the hard disk with Ubuntu on is /dev/hdc on my machine (verified with the 'disks' GUI utility).

I ran the command you suggested (with /dev/hdc instead of /dev/hdb), but when I used 'fixmbr' (windows recovery console), Win2k was usable then (and boot management back to normal), but I told the BIOS to boot from the Linux disk, and grub failed to boot Linux.

Any ideas for recovering the Linux installation?  It's not the end of the world if a reinstall is the only option for me, but I'd prefer not to if I don't have to.

At the end of the day, what I'd like is to be able to interchange between booting win2k/freebsd/linux without problems, and to be able to boot into FreeBSD/Windows without the Linux disk plugged in.  With Grub doing boot management, I don't know how that is possible, because Windows didn't seem to like trying to name C:\ as the active partition after Linux was installed.

Any help or suggestions would be much appreciated.

---

### Post by mikeymikec on 2006-06-10
*bump*

---

### Post by catlett on 2006-06-10
You would have to use the Ubuntu "alternate install cd". This gives you a text mode installation. Then you would have to make a small boot partition on your first drive (the windows/free bsd drive). This has to be at the start of the 1st drive. Encompassing the first sector, mbr and a little more. Small meaning mb, 50mb is plenty.
Then install ubuntu with both drives connected. When you get to partitioning put the /boot partition on the first drive. (this should be /dev/hda1 and the rest of your install will go on /dev/hdc) When you get to grub let it install on the mbr (make sure the win/bsd drive is the master and ubuntu is the slave when doing this).
Now you will have grub booting to windows and ubuntu. You may not get bsd right away but you can edit grub to get it to boot. This setup will allow you to boot to win/bsd when the ubuntu drive isn't connected and  will boot ubuntu when they are both connected.
The explanation. When you earlier put grub on the mbr you kept the grub folder on the ubuntu drive in /boot. The grub on the mbr is very small (something like 512bytes) stage one justs boots to stage 1.5 and that stage is just a go between 1 and 2. Anyways when you did it earlier grub worked on the mbr. Stage 1 sent the boot to the grub folder on your slave to activate stage 1.5 but it couldn't because it was disconnected. 
This configuration solves that problem with a bot partition on the 1st drive. Now stage 1 grub on the mbr can always access stage 1.5 in the grub folder because it is now on the boot partition right next to it.

---

