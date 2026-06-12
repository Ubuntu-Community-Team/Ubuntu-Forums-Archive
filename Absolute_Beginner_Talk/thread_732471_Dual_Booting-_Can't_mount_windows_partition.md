---
title: "Dual Booting- Can't mount windows partition?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Metro Gnome on 2008-03-22
I'm a newbie to Linux and am running the Beta 8.04 (I know that's crazy, but it's the only version that worked with my sound card driver by default).

Anyway, things are great until i tried unsuccessfully to run dual screens, and then when i rebooted, i somehow no longer had access to my windows partition. This is useful to me because i want to access my music and stuff from this partition.

What can i do?

---

### Post by kbless7 on 2008-03-23
Did you close out of windows properly? I.E. by pressing the power button vs. holding the power button. I think hibernating also causes this problem

---

### Post by Oldsoldier2003 on 2008-03-23
> **kbless7 said:**
> Did you close out of windows properly? I.E. by pressing the power button vs. holding the power button. I think hibernating also causes this problem

if so reboot into windows and properly shut down the computer, and Ubuntu will allow the partition to mount on its next startup. It probably wouldn't hurt to chkdsk and defrag while you have windows booted...

---

### Post by ajmorris on 2008-03-23
> **Metro Gnome said:**
> I'm a newbie to Linux and am running the Beta 8.04 (I know that's crazy, but it's the only version that worked with my sound card driver by default).

Anyway, things are great until i tried unsuccessfully to run dual screens, and then when i rebooted, i somehow no longer had access to my windows partition. This is useful to me because i want to access my music and stuff from this partition.

What can i do?

  Hi there, when you say you no longer have access to your windows partition. Do you mean you dont have access to your files on your windows partition from linux? or that you cant boot your windows partition? if the latter, you need to add the option to /boot/grub/menu.lst

so down the bottom of that file add this:

```

title Your version of Windows
rootnoverify (hd#,#)  (replace the #'s with teh numbers of your hard disk and partition number for windows, -1, so if windows is on Hard Disk 1 on partition 1, this would be root (hd0,0) (fdisk -l can tell you what hard disk and partition))
makeactive 
chainloader +1
```if this is not what you meant, and i have just made an idiot of myself, and its that you cant access your windows partition from linux, do ```
sudo apt-get install ntfs-3g
```you can then mount your windows partition via sudo ntfs-3g /dev/windows partition /media (or mnt)/windows mount point

then you can add an option to /etc/fstab to do this automagically on boot. just do an entry like your others, but in the partition type section put ntfs-3g


AJ

---

