---
title: "Path to USB Stick?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by forevereating on 2007-05-28
I want to setup a dual boot configuration. I've done it once before and installed the GRUB in the HDD instead of the MBR. But you need a floppy to do that and my new computer doesn't have a floppy drive. So when it asks where to install GRUB what would the path be to my [USB Stick?]("http://www.sandisk.com/Products/Item(1922)-SDCZ6-2048-SanDisk_Cruzer_Micro_2GB_Black__New.aspx") For floppy it was /dev/fd0. Thanks in advance.

p.s.
 Is it actually /dev/sdb1?

---

### Post by mattva01 on 2007-05-28
I think you should look in /media for your usb stick.

---

### Post by Ek0nomik on 2007-05-28
Open a terminal:

```
sudo fdisk -l
```

You should be able to find your device, and it will tell you where it is located.  If you are unsure, post your terminal output and someone can help.

---

### Post by forevereating on 2007-05-29
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/sda2            1959       16708   118479375    f  W95 Ext'd (LBA)
/dev/sda5            1959        5874    31455238+   7  HPFS/NTFS

Disk /dev/sdb: 2048 MB, 2048729600 bytes
64 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         992     1999749+   b  W95 FAT32
ubuntu@ubuntu:~$ 


```

The first one should be my sata drive, and the second one should be the usb stick. So my question is, is it /dev/sdb or /dev/sdb1 or might it change?

---

### Post by Ek0nomik on 2007-05-29
It's /dev/sdb1

It might change if you put it into a different port, otherwise I *think* it will stay the same.

If you want, you can make the mount point permanent by editing your fstab file.  If you need help just ask.  :)

---

### Post by forevereating on 2007-05-29
Ok, thanks for the help, I think I got it now. I'm going to give it a try.

---

### Post by Ek0nomik on 2007-05-29
Alright.

If you have more questions, I can try to help while I am at work tomorrow morning.  :)

---

### Post by Inxsible on 2007-05-29
it might also change if you connect another external hard drive / usb stick to another port before you connect this particular USB stick.

Linux assigns drive letters sd* -- where * can be any letter in alphabetical order.

---

### Post by forevereating on 2007-05-29
Is it possible that I have 2 /home? Like /home and /home2 or perhaps name it something else? I'm only asking because the *unpartitioned* space is seperated into two sections, which makes it very annoying for me. I don't think I can combine these unpartitioned space.

---

### Post by Ek0nomik on 2007-05-29
> **forevereating said:**
> Is it possible that I have 2 /home? Like /home and /home2 or perhaps name it something else? I'm only asking because the *unpartitioned* space is seperated into two sections, which makes it very annoying for me. I don't think I can combine these unpartitioned space.

The unpartitioned space of what?  You have me confused.

There are only 2 home directories if you physically made 2.

All user accounts are stored in /home/username.

What device are you looking at, and what are you trying to do with it?

---

### Post by Inxsible on 2007-05-29
You can definitely create another partition from unallocated space...if that's what you are asking. Why name it home2....you can name it anything you want. I have an extra partition, that I named /shared.

That is where I keep my music and movies..which I "share" between my Ubuntu and Vista installs ;)

---

### Post by forevereating on 2007-05-29
I think a screenshot would explain it better. This would be my SATA drive btw.
[IMG]http://i89.photobucket.com/albums/k236/Revo_Avid/Miscellaneous/Screenshot.png[/IMG]

---

### Post by Inxsible on 2007-05-29
Are you only going to keep 15 GB for Windows ?

Then from the 82 Gigs you will have to create a /home drive -- I would suggest about 20 GB
a swap drive -- 1.5 to 2 times you RAM peaking at 1GB

The rest you can create as many partitions as you want
for eg.

/entertainment - for movies tv shows
/accounts - for your tax files or accounting software... 

Anymore you can think of....Go wild..........you have lots of space  ;)


EDIT : just saw that your sda5 was NTFS ....I would keep NTFS away from my linux install

i.e. I would make my sda5 ie 30 GB as a primary partition, then create logical partitions from the remaining.

this is how I set up my drive

160 GB total
Primary 1 --- 25GB Windows ( Its a Vista Premium install so it wont take any less )
Primary 2 --- 25 GB Windows Data ( install games software etc for Windows)
Primary 3 --- 74 GB /shared (EXT3 -- my music and movies and pics)
Extended --
   9 GB for  / (root)
  20 GB for /home
  1 GB for swap

Hope that gives you a better idea

---

### Post by Ek0nomik on 2007-05-29
It's separated because you have the 82.99 GB as part of an extended partition, while the 104.89 GB is a partition of its own.

What is it **exactly** that you are trying to do?  I personally don't use any extended partitions, just primary ones.  I have a dual boot setup on my laptop, and I just have a partition of NTFS, EXT3, and Swap.  Nothing more, nothing less.

Hope I can help some more.  :)

---

### Post by forevereating on 2007-05-29
Oh, those were already setup because of Windows' doing. I was thinking of making the 83GB into FAT32 for sharing between the OS' and the 105GB for / /home /swap /extra. Oh, should my swap be at the beginning or the end of the harddrive?

Edit: to clarify, the 15GB is C:\, and the 30GB is D:\ which has been previously formatted.

---

### Post by Inxsible on 2007-05-29
> **forevereating said:**
> Oh, those were already setup because of Windows' doing. I was thinking of making the 83GB into FAT32 for sharing between the OS' and the 105GB for / /home /swap /extra. Oh, should my swap be at the beginning or the end of the harddrive?

You can have swap anywhere, but if you do a default Ubuntu installation, it puts it at the end of the drive...and so most people try and put it at the end.

if you want, you can make the 83 GB as a shared drive 
      FAT32 -accessed by both by default 
      NTFS -- accessed by Linux using ntfs-3g and ntfs-config
      EXT3 -- accessed by Windows using fs-driver

From the 105 GB you can create your / /home /extra and the swap

---

