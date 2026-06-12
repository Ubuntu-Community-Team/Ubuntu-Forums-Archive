---
title: "Live cd cannot acces ext3 paritition!"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by noodles12 on 2006-07-29
I'm in the live cd, i go to system>disks> and the harddrive partition linux is on. Here is what it shows:

Device:          /dev/sda4
File system:      extended 3
Access Path       
size:            7.91 GiB
Status:          Inaccessible

I press the enable button and nothing happens. Am i correct in that if this is inaccessible, than I won't be able to fix any of my problems from the live cd since it cannot access my linux partition? 

It shows up on fdisk -l, but i guess i can't access it.

---

### Post by aysiu on 2006-07-29
Try this: ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/sda4 /recovery
gksudo nautilus
``` And then press **Control-L** and type ```
/recovery
``` and **Enter**.

---

### Post by noodles12 on 2006-07-29
Thank you for the suggestion. However, my input and output reads as following:

$sudo mount -t ext3 /dev/sa4 /recovery
mount: special device /dev/sda4 does not exist

---

### Post by aysiu on 2006-07-29
Did you type ```
/dev/sa4
``` or ```
/dev/sda4
```?

---

### Post by noodles12 on 2006-07-29
sda  sorry for mistype.

---

### Post by aysiu on 2006-07-29
Can you post the output of ```
sudo fdisk -l
```?

---

### Post by noodles12 on 2006-07-29
device      boot     start   end    blocks      ID     System
/dev/sda1    *        1     2550    20482843+   7       hpfs/ntfs
/dev/sda2            3698   9728    48444007+   f    W95 Ext'd LBA)
/dev/sda3           2551   2677     7020127+  82 Linux Swap/solaris
/dev/sda4            2678   3697    8193150     83   Linux
/dev/sda5            3698    9728    48443976    7    hpfs/ntfs

partition table entries are not in disk order

---

### Post by aysiu on 2006-07-29
/dev/sda4 is there and it says *linux*. I'm not sure why it's saying it doesn't exist...

---

### Post by noodles12 on 2006-07-29
i know, that's what has me stumped as well. It says linux, but when i boot it up it says doesn't exist. And also when i use the live cd , it shows under disk management that it's ext3, but inaccessible. 

Is there any possible remote reason why it would recognize it as linux, but maybe not for ubuntu and therefore won't read from that partition at all?

Thank you for your continued help aysiu, you're like one of hte only responses i've gotten for my problem. 

Just a quick informational incase it makes a difference.
Asus s96j VBI notebook from powernotebooks.com
t2400 1.86 ghz duo core 
2gb of corsair 667 ddr2 RAM
80gb 7200rpm hitachi hd
dvd burner

---

### Post by aysiu on 2006-07-29
Unfortunately, my responses aren't very helpful.

Do you happen to have a Knoppix CD? A Ubuntu CD can be used for recovery purposes, but a Knoppix CD is *designed* for recovery and automounts partitions automatically.

---

### Post by noodles12 on 2006-07-30
I have downloaded and burned the knoppix live cd, what do i do now?

---

### Post by aysiu on 2006-07-30
> **noodles12 said:**
> I have downloaded and burned the knoppix live cd, what do i do now?
Reboot your computer with the Knoppix CD in the drive.

/dev/sda4 should appear on your desktop. Click it.

---

### Post by noodles12 on 2006-07-30
Wow knoppix live-cd is awesome!

Well anyway it loades up all my partitions automatically as /media/sda4 and all that. I tried editing my grub menu just so windows could boot first but i dont' have write access to any of hte drivers from knoppix >.<, so i think i need to figure out how to do that and i'm one step closer.

Ok, so i write click on the sda partition and changed the read/write access so i can write. I then make a copy of the menu.lst to menu.lst_backup just fine. The weird thing is i still don't have access to changing any of these files. Also, gedit does not work in the knoppix cd for some reason. it says 

edit: sorry, knoppix uses kwrite instead of gedit. 

Where do i mount the sda4 partition for it to boot up as my linux partition?

---

### Post by aysiu on 2006-07-30
You can browse as root. There should be Konqueror super-user mode somewhere in the KMenu.

If not, in the terminal type ```
su
konqueror
```

---

### Post by noodles12 on 2006-07-30
Where should I mount my linux partition so that grub will recognize my ubuntu?

---

### Post by aysiu on 2006-07-30
> **noodles12 said:**
> Where should I mount my linux partition so that grub will recognize my ubuntu?
I'm not sure what the mount point has to do with Grub.

---

### Post by noodles12 on 2006-07-30
Like where do i moutn that partititon so that my ubuntu will work?

---

### Post by aysiu on 2006-07-31
> **noodles12 said:**
> Like where do i moutn that partititon so that my ubuntu will work?
I still don't understand. Why isn't your Ubuntu working?

What's your partition scheme look like?

The mounting you do with Knoppix is only temporary so that you can make changes. Are you talking about changing permanent mount points in your Ubuntu's /etc/fstab file?

---

### Post by noodles12 on 2006-07-31
Yes I am talking about making permanent mounting changes in my etc/fstab. 

My problem. 
- Start Ubuntu
- mounting root filesystem
- waiting for root filesystem        
- drops to a shell, /dev/sda4 does not exist

/dev/sda4 is where my linux partition is. 
My partitions are stated earlier in this post, my fdisk -l output. 

I was trying to mount /dev/sda4 again because it seems like ubuntu won't do it. 

I changed my menu.lst in knoppix and it was permanent. Is there a way to mount the partition with knoppix and make it permanent?

---

### Post by aysiu on 2006-07-31
You mount in Knoppix to make *changes* to *files*.

As you said already, you changed your menu.lst *file* and the change was permanent.

I don't know what you mean about mounting a partition with Knoppix and making that mount permanent. Mounts in a live CD session are temporary by definition--once you reboot, there is no Knoppix any more... so there is no mounted partition any more.

---

### Post by noodles12 on 2006-07-31
So is there no way to mount /dev/sda4 if my ubuntu won't recognize it?

---

