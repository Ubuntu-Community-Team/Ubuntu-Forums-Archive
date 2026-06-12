---
title: "Not seeing new hard drive"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by gijoecam on 2008-03-13
Complete newbie, first post...  Please be gentle.  Been lurking for a few days, but now I'm stuck and can't find the answer on here.

I have an FIC motherboard (forget the model), P4 2.7Ghz proc, 1Gb RAM, that was previously running a 160 gig hard drive and a 17.2 gig hard drive (both IDE).  The 160 gig drive had the Windows installation, but died last week.  It's been replaced with a new 640 gig SATA hard drive and while I wait for a copy of WinXP to arrive, I wanted to try Linux.  The 640 is unformatted and unpartitioned (and I'm wondering if that may be the issue?) but registers in the BIOS just fine.

Ubuntu Linux 7.10 iso file burned fine.  After what seemed like an eternity, the Ubuntu desktop finally loaded from the CD.  When I attempt the install, it only sees the old 17.2 hard drive,m not the new one.  If I go to System-->Partition Editor, gparted opens and scans the devices.  However, it still doesn't see the new hard disc, only the old one.

Soooo....  Do I somehow have to format the new hard drive before gparted will recognize the drive?  Is there a tool I'm not seeing in Linux that can do it for me?

Thanks for any help you can give me!!

-Joe

---

### Post by ruy_lopez on 2008-03-13
Confirm that gparted cannot see the drive. 

Look at the top right drop-down menu (picture of drive, size), and see if it's listed.

---

### Post by theRightNee on 2008-03-13
btw safe graphics is going to be faster to load...and it doesn't look that much different =]

---

### Post by gijoecam on 2008-03-13
> **ruy_lopez said:**
> Confirm that gparted cannot see the drive. 

Look at the top right drop-down menu (picture of drive, size), and see if it's listed.

Thanks for the quick response!!

It's not there.  What's next?

---

### Post by ruy_lopez on 2008-03-13
What's the output from these commands:

```

sudo fdisk -l
sudo mount

```

---

### Post by gijoecam on 2008-03-13
Umm, here's where I display my complete newbieness...  where do I enter those two commands?

---

### Post by ruy_lopez on 2008-03-13
> **gijoecam said:**
> Umm, here's where I display my complete newbieness...  where do I enter those two commands?

No problem. "Applications-->Accessories-->Terminal".

---

### Post by gijoecam on 2008-03-13
sudo fdisk -1 results in 
> fdisk: invalid option -- 1

sudo fdisk -l results in it showing the single IDE drive, but not the SATA drive I want to use.

'sudo mount' results in about 10 lines that would take 20 minutes to copy from across the room...  I'm using my wife's computer to access the 'net at the moment...

---

### Post by gijoecam on 2008-03-13
Got it...  Connecting to the net was apparently MUCH easier than I thought it would be LOL!!

Here's the output: (note the -L not the -1)
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 17.2 GB, 17280442368 bytes
255 heads, 63 sectors/track, 2100 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fad2fac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2100    16868218+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
ubuntu@ubuntu:~$ 


Does that make sense?

---

### Post by ruy_lopez on 2008-03-13
> **gijoecam said:**
> 
Here's the output: (note the -L not the -1)

Does that make sense?

It looks as though you were right all along. The drive is not detected.

---

### Post by gijoecam on 2008-03-13
Yup...  now what?  If the BIOS detects it, shouldn't the OS?  Any ideas on how to work around it?

---

### Post by gijoecam on 2008-03-14
Searched for hours on here last night...  Still no idea...  If the BIOS sees the drive, why won't Ubuntu?  I tried unplugging the old drive from IDE2 (slave) and tried rebooting...  What came up was a bunch of squiggly lines streaming across the screen at a 45 degree angle...  I'm SO lost....  Never thought I'd say it, but I can't wait for Windows!!  At least Linux runs from the CD usually...  just takes 45 minutes to boot itself, that's all.

---

### Post by Mjölner on 2008-03-14
I sincerely hope your ms product takes you where you want to be.

---

### Post by marufaberlin on 2008-03-14
Try looking in the directory /proc/ide. Is your drive listed there (i assume not, but it's always worth a try)?

---

### Post by gijoecam on 2008-03-14
Well, I tried disconnecting the IDE drive and rebooting.  Now I get nothing whatsoever showing up for a drive in gparted, although the BIOS sees the drive just fine.  It's showing the drive is connected to IDE channel 2 (which are my SATA ports), master.  Any other idears?

---

### Post by gijoecam on 2008-03-15
update:

I posed my question in another forum where I know there are a few Linux users...  Someone mentioned something about the BIOS and an IDE emulator, and it got me thinking...  

I had to tweak the BIOS so that the SATA drive connections were set to channel 0 (instead of channel 2) and the optical drives were still on channel one.  My initial tweak hid the optical drives from the BIOS, so needless to say, I couldn't boot from the CD.  Upon further tweaking, I got it to see the drives, and gparted now recognizes the SATA drive.  I've currently got the old IDE drive disconnected, but that's fine...  I won't be needing it for a couple weeks yet...

Thanks for trying everyone!  Maybe someone else will find this thread helpful anyways...

Wish me luck!

-Joe

---

