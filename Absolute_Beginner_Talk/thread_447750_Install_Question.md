---
title: "Install Question"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by ol_smokey on 2007-05-18
Hi all,

After playing with the Live session for a couple of weeks all appears to be working fine so I'm ready for to install Feisty on a dual-boot. I'm just wondering how's best to do it.

I have 2 internal hard drives:
C: XP + all saved data (including a few gig of music) with about 10GB of the 30 GB capacity remaining (NTFS)
D: Empty 30GB drive again.

Now should I have my Feisty install on D: or should I keep the 2 OS's on C: and shift all of my data onto D:?

Also I noticed that in the live session I could get Totem to open files and play music and video from C: and I don't remember installing ntfs-3g, only the codec packages I needed, so does Feisty come with the ability to read/write to NTFS built -in?

Thanks

ol_smokey

---

### Post by Najand on 2007-05-18
You can install it on any of two partitions you wish.
Fesity comes with the default ntfs driver which enable users to use NTFS partitions for read only purposes. It means you can listen your music, copy them to your ext3 partition etc. but you won't be able to change them or move them inside NTFS partition. So if you need writing to ntfs filesystem, you would need ntfs-3g installed on your system.

---

### Post by netwerx on 2007-05-18
Install on D? Yes.
You will be able to read from a NTFS drive (most likely your XP drive is NTFS) you just won't be able to write without installing ntfs-3g

Good luck, and welcome to Ubuntu.

---

### Post by mikewhatever on 2007-05-18
It does not matter where you install Ubuntu, just, installing on a separate HDD can be a little trickier, in terms of GRUB configurations.
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
Feisty still can not write to ntfs, although ntfs-3g is in the repositories and ready for installation. You do not need any write access to play music,do you?

---

### Post by louieb on 2007-05-18
I like setting up 2 drives the way its described here [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by Najand on 2007-05-18
> **louieb said:**
> I like setting up 2 drives the way its described here [Dual Boot on Two Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot")

Louieb, seems that tips belongs to Edgy and releases before it... So, I donT think it would help him/her alot!

---

### Post by ol_smokey on 2007-05-18
Thanks guys and/or gals (I'm a guy by the way)

So what would be the benefits of installing Feisty and XP on seperate drives? ( I intend to keep the dual boot for the forseeable future due to a GIS app that I use being Windows only and having a map set that won't translate into any other format).

The data I currently have on my Windows drive (yes it is ntfs) is mainly media that I will only need to be able to read so it can stay where it is by the sounds of it.

I'm starting to lean towards keeping the OS's together as it seems an easier install.

Ta

ol_smokey

---

### Post by mikewhatever on 2007-05-18
Benefit, none whatsoever. You might want to do it if the Windows drive is really full, or you have very important data on it you cant loose (any installation can go wrong), or you plan on removing the Linux drive occasionally to use on another PC. There are no benefits in performance or ease of installation here.

---

### Post by ol_smokey on 2007-05-18
Well that appears to have settled it then.

I'm going to install Feisty on my C: drive and turn my D: drive into a nice big storage dump for my music and files:
C: will be: Windows (ntfs) Ubuntu / (ext3) Ubuntu /home (ext3) swap

Now that that you can write to ntfs with ntfs-3g does it make sense to have the shared drive (D: in my case)  as ntfs due to the limitations of FAT-32?

Thanks again

ol_smokey

---

### Post by Najand on 2007-05-18
What are the limitations of FAT-32?

---

### Post by ol_smokey on 2007-05-18
Re: FAT 32 - I was under the impression that it couldn't handle large files and it fragmented files a lot.

Have I got this wrong?

ol_smokey

---

### Post by Najand on 2007-05-18
Well, both are made by microsoft and they suck like each other... However FAT32 is completely supported by linux, though NTFS-3G cannot support it completely becuase microsoft has not brought any spec of NTFS to public. If you think NTFS handles large files better and FAT32 fragmented files a lot, then go with NTFS. You can also use EXT3 and install: [Ext2 Installable File System For Windows]("http://www.fs-driver.org/") on your windows.

---

### Post by louieb on 2007-05-18
> **louieb said:**
> I like setting up 2 drives the way its described here [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

> **Najand said:**
> Louieb, seems that tips belongs to Edgy and releases before it... So, I donT think it would help him/her alot!
Yea your right just looked at it. But not for the reason you might think.  The truth is all the Ubuntu install CDs since Breezy Badger could install  GRUB anywhere you wanted it. (you just had to look hard for the option). But it looks like it got merge with another thread. and now its all about using BIOS for the boot manager. 
   
But have changed the link to another thread. Linux on master XP on slave. Its still my favorite way to set up dual boot.

---

