---
title: "Help Please!! Partitioning Went Bad!"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by s0L1Tud3 on 2008-04-07
Okay OMG so last night I decide to install ubuntu... I used partition magic in windows to create an Ext 2 partition off half of my c:\ drive (which is where windows also is) ... and it reboots and begins the process. 10 or 15 minutes into it (step 1 or 3) it , it gives me an error and i have to turn off the computer. I forgot what the error was, but I don't think it got to partitioning anyhting yet. When i rebooted i got the windows startup option menu (safe mode/normally/last good config that worked etc) and on all of them , it wil show the windows XP screen for a moment and then go to the blue screen saying thers an error and it shutdown to prevent future damage. I had not expected partition magic to have lost its magic so I didn't back up my c:\ data. 

Thank GOD that I had burned the ubuntu cd, which is what I'm running off right now and i Love it. 

A couple friends of mine think that the partition magic messed with the MBR or something, Honestly, I don't really have any use for windows right now and instead of focusing on fixing that issue, what I want to do is get all my years of coding/images/notes/documents off my c:\ drive and put it onto my external , which mounts fine and I am able to see/use the music I had put on it previously. But when I try to open the C:\ drive it says "Unable to mount drive" ! Says either to safely remove the hardware with windows (which i cant), or to force mount, which doesn't work either since I"m not root... Ugh I am so confused, I don't know Linux very well at all and I just want to mount the drive so I can recover the data I need, and then install ubuntu on the C:\ for good... So if ANYONE Knows how I can do this, I would soooooooo appreciate this help. 

sincerely, Adam

---

### Post by louieb on 2008-04-07
The Ubuntu live CD is a fine demo and desktop  CD. But for data rescue from your windows partition I use and recommend the [Knoppix Linux]("http://www.knoppix.net/") CD.

Almost as good,  just a little harder to use is [Puppy Linux]("http://www.puppylinux.com/") the advantage here its a much smaller download. 

Try booting windows into safe mode 1st. For me at least windows has fixed itself just by doing that. Form what you described it looks like the MBR is ok theres something else wrong with windows.

If you can't get one of those CDs I see if I can find my Ubuntu CD and  walk you through using it.

---

### Post by s0L1Tud3 on 2008-04-07
well I really just want to know how to mount the c:\ drive from this ubunutu... Do i really need to download a whole other distro to do that?! My friend said to get "gparted live" to try and fix the MBR (assuming thats the problem) , but i need to find a friend who will let me use his computer do get that... But again, isnt there another way besides downloading another distro?! I just want to get this drive mounted so i can see what got deleted (if anything).. thanks

oh and btw, I can't boot into safe mode, it shows the windows XP logo for a second and then goes to the blue screen.

---

### Post by twin_57103 on 2008-04-07
I've had better luck with Knoppix than Puppy (I'm a Windows-user-who-is-still-learning-Linux).  If you need to restore the MBR, you can also use [Super Grub]("http://supergrub.forjamari.linex.org/").  It's a small download and I've used it for this in the past (the hard drive that held Ubuntu and Grub failed).  Good luck!

---

### Post by InfinityCircuit on 2008-04-07
If you can see the Windows XP logo I doubt that your MBR is screwed up.  In any case, if you need to rewrite the Windows XP MBR you need the disk that you installed Windows off of.

To mount the C drive, you should do the following:

1. Boot the Ubuntu LiveCD
2. Go to Applications -> Accessories -> Terminal
3. Run "sudo fdisk -l" You will get an output that lists a hard drive (of the form /dev/sdaX) that says "NTFS" for the filesystem (here's my sample output:)
```
root@skynet:~# fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        3334     1180777+  82  Linux swap / Solaris
/dev/sda3   *        3335        4864    12289725   83  Linux

```

4. Run "sudo mount /dev/sdaX" where X is the partition with NTFS on it.

---

### Post by s0L1Tud3 on 2008-04-07
Hey I tried that, but it gave me an error. Here is what I did:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000ad45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab


Any ideas?  I really hope I didn't lose all my info.
---------------------------------------



> **InfinityCircuit said:**
> If you can see the Windows XP logo I doubt that your MBR is screwed up.  In any case, if you need to rewrite the Windows XP MBR you need the disk that you installed Windows off of.

To mount the C drive, you should do the following:

1. Boot the Ubuntu LiveCD
2. Go to Applications -> Accessories -> Terminal
3. Run "sudo fdisk -l" You will get an output that lists a hard drive (of the form /dev/sdaX) that says "NTFS" for the filesystem (here's my sample output:)
```
root@skynet:~# fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        3334     1180777+  82  Linux swap / Solaris
/dev/sda3   *        3335        4864    12289725   83  Linux

```

4. Run "sudo mount /dev/sdaX" where X is the partition with NTFS on it.

---

### Post by mrsteveman1 on 2008-04-07
So your windows partition is sda1.

To mount it safely, do this:

```

sudo mkdir /windows
sudo ntfs-3g /dev/sda1 /windows
```

Then you can get to the data and move it around if you need to. Ntfs-3g is installed by default with gutsy so you should have it already.

In this case there isn't anything knoppix can do that the ubuntu cd can't, especially if you need to install something else to fix things quickly.

If that doesn't mount the partition there are other ways to fix it, but i doubt there is anything wrong with the system. Once you see the windows boot menu, the system has already loaded the volume boot record code and loaded ntldr (the windows boot loader, like grub) from the disk, so that stuff is probably all fine, and XP doesn't really care about what's in the MBR unless the partition info is wrong, which might be the case, you'll have to see if the windows drive mounts to know that.

---

### Post by s0L1Tud3 on 2008-04-07
Thank YOU SO MUCH! YOU ARE A LIFE SAVER! I can get all my windows files now!  Thanks so much man. Now, one more question... do you guys reccomend I try to fix the windows partition, or just install ubuntu directly on C:\ and overwrite everything after i back it up.. I'm probably getting a windows laptop within a couple months and I honestly don't use my computer for anything except visual basic programming & chat... I'm thinking about learning Delphi to replace VB anyways, and I believe that is for both windows and Linux.... Thanks again so much!

> **mrsteveman1 said:**
> So your windows partition is sda1.

To mount it safely, do this:

```

sudo mkdir /windows
sudo ntfs-3g /dev/sda1 /windows
```

Then you can get to the data and move it around if you need to. Ntfs-3g is installed by default with gutsy so you should have it already.

In this case there isn't anything knoppix can do that the ubuntu cd can't, especially if you need to install something else to fix things quickly.

If that doesn't mount the partition there are other ways to fix it, but i doubt there is anything wrong with the system. Once you see the windows boot menu, the system has already loaded the volume boot record code and loaded ntldr (the windows boot loader, like grub) from the disk, so that stuff is probably all fine, and XP doesn't really care about what's in the MBR unless the partition info is wrong, which might be the case, you'll have to see if the windows drive mounts to know that.

---

### Post by ant2ne on 2008-04-07
boot from you Win Install CD. Goto a Prompt (I think it is R for repair) and type chkdsk c: /P /R Let that run. It should bring back your win OS

---

### Post by Saint Angeles on 2008-04-07
hehe...

whats a C:\ drive?

:lolflag:

---

### Post by ant2ne on 2008-04-09
> **Saint Angeles said:**
> hehe...

whats a C:\ drive?

:lolflag: That is the thing the business world stores their feeble OS because they are too scared to try something new.

---

### Post by mrsteveman1 on 2008-04-10
No one will ever need more than 26 drive letters :D

---

### Post by ant2ne on 2008-04-11
> **mrsteveman1 said:**
> No one will ever need more than 26 drive letters :DOr more than 64k of memory. How long did that last? a week?

---

