---
title: "Need Help (gparted)"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-08-20
I have a small problem booting windows, when I select XP from GRUB menu windows boots but then gives error. Prior to using ubuntu (2 days ago) windows worked. During ubuntu install I loaded grub to MBR. After ubuntu install and reboot, Ubuntu worked flawlessly(almost :)) but Wimdows no longer worked. I attached a screenshot for better assistance to my problem.

I ONLY HAVE 1 HARDDRIVE INSTALLED (single HDD).

Also this:
```

payton@the-desktop:~$ fdisk -l
payton@the-desktop:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             66610548   2190600  61036260   4% /
varrun                  123728        96    123632   1% /var/run
varlock                 123728         0    123728   0% /var/lock
procbususb              123728        96    123632   1% /proc/bus/usb
udev                    123728        96    123632   1% /dev
devshm                  123728         0    123728   0% /dev/shm
lrm                     123728     33788     89940  28% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1             87891576   1644488  86247088   2% /media/disk
payton@the-desktop:~$ 

```

---

### Post by Happy_Man on 2007-08-20
What's the WIndows error say?

---

### Post by pgar23 on 2007-08-20
> **Happy_Man said:**
> What's the WIndows error say?

Windows error= a problem has beenm detected and windows has been shutdown to prevent damage to your computer.

Check for virus, remove any newly installed hard drives or hard drive controllers. Check hard drive make sure it is properly configured and terminated.

Thankks for the reply. Appreciate it.

---

### Post by pgar23 on 2007-08-20
will resizing the partition even solve my problem?

---

### Post by pgar23 on 2007-08-20
also, how do i get ubuntu.org to email me when someone replies to my thread?

---

### Post by pgar23 on 2007-08-20
This guy had a similiar problem to me.

[http://ubuntuforums.org/showthread.php?t=159575&highlight=gparted+cant+read+contents+of+filesystem](http://ubuntuforums.org/showthread.php?t=159575&highlight=gparted+cant+read+contents+of+filesystem)

"*To make changes, you can't be using GParted on the hard drive that is mounted.  Instead either download Ubuntu Live CD and use GParted off of it.    Applications > System Tools > **GParted*"

Am I on the harddrive that is mounted>?

---

### Post by Happy_Man on 2007-08-20
If you resized the partition using the LiveCD installer, that shouldn't apply. Did you defragment the XP before you resized and installed? If not, I fear that some important files sitting at the end of the partition may have been erased, preventing Windows from booting. Sorry.....

---

### Post by pgar23 on 2007-08-20
> **Happy_Man said:**
> If you resized the partition using the LiveCD installer, that shouldn't apply. Did you defragment the XP before you resized and installed? If not, I fear that some important files sitting at the end of the partition may have been erased, preventing Windows from booting. Sorry.....

I did defrag befor installing ubuntu. I didnt use the live cd. I used the Alternate cd with text install.

---

### Post by Happy_Man on 2007-08-20
Then I'm not sure. Perhaps the resizing screwed up the ntfs filesystem so much that it became unreadable to Windows. That's what happened to mine, only to a lesser extent, such that it becomes really really slow.

---

