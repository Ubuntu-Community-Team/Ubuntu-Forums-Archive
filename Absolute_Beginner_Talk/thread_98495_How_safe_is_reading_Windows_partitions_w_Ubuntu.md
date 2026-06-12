---
title: "How safe is reading Windows partitions w/ Ubuntu?"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by kurzweilfreak on 2005-12-03
Hola everyone. My first post here. \\:D/

A few weeks ago I bought a new harddrive and stuck it in my Dell Dimension 8250 to be able to partition and run Ubuntu. It was a 250GB drive, and I partitioned 49 GB as my r00t Ubuntu section, 1 gig as Ubuntu swap space, and the other 150 GB to use as scratch disk for my graphic and audio programs in Windows. So, here I am. :D

Enough introductions, on to business: I'd like to be able to easily copy all my wallpapers, some music files, and a couple other things from my Windows without having to boot into Windows, burn a CD or whatever, and then boot back into Ubuntu. I read about how to mount Windows partitions and all that good stuff, but my question is just how safe is that for my Windows partition? I'd hate to do that, read some files, and then have it screw up my file system and ruin my booting back into Windows. 

I would ASSUME that it shouldn't be a problem since the instructions on mounting the drives don't make any mention or warning about it. Then again, mounting a drive is only getting Ubuntu to recognize that the drive is there, not about actually reading it, is this correct? What else would I need to do, if anything, to get Ubuntu to be able to read the NTFS partitions?

To be safe, I was hoping to be able to use my scratch partition kind of as my go-between for Ubuntu and Windows just to prevent Ubuntu from even going near my Windows system partition. The scratch partition would just be empty scratch disk to use for document storage, scratch space for Photoshop and audio editors, etc...

Any thoughts or advice on this topic?

---

### Post by cwaldbieser on 2005-12-03
[QUOTE=kurzweilfreak]Hola everyone. My first post here. \\:D/

A few weeks ago I bought a new harddrive and stuck it in my Dell Dimension 8250 to be able to partition and run Ubuntu. It was a 250GB drive, and I partitioned 49 GB as my r00t Ubuntu section, 1 gig as Ubuntu swap space, and the other 150 GB to use as scratch disk for my graphic and audio programs in Windows. So, here I am. :D

Enough introductions, on to business: I'd like to be able to easily copy all my wallpapers, some music files, and a couple other things from my Windows without having to boot into Windows, burn a CD or whatever, and then boot back into Ubuntu. I read about how to mount Windows partitions and all that good stuff, but my question is just how safe is that for my Windows partition? I'd hate to do that, read some files, and then have it screw up my file system and ruin my booting back into Windows. 

I would ASSUME that it shouldn't be a problem since the instructions on mounting the drives don't make any mention or warning about it. Then again, mounting a drive is only getting Ubuntu to recognize that the drive is there, not about actually reading it, is this correct? What else would I need to do, if anything, to get Ubuntu to be able to read the NTFS partitions?

To be safe, I was hoping to be able to use my scratch partition kind of as my go-between for Ubuntu and Windows just to prevent Ubuntu from even going near my Windows system partition. The scratch partition would just be empty scratch disk to use for document storage, scratch space for Photoshop and audio editors, etc...

Any thoughts or advice on this topic?[/QUOTE]

There are no drivers for actually writing to an NTFS partition included in Ubuntu.  Reading the partition can't really hurt it at all, and you can only mount an NTFS filesystem read only.

I used to do it more often before I had transferred all my files over from Windows, and I never had a problem.

---

### Post by kurzweilfreak on 2005-12-03
That's what I figured. Someone told me that writing was definitely a bad idea (but I can't anyway so not a problem :D ) and that regarding reading, it might be ok but better safe than sorry. :P

As for my scratch disk, maybe I should format it as Fat16? Something that both Windows and Ubuntu can read and write to. Fat16 or Fat32 or a better suggestion?

---

### Post by ckempo on 2005-12-03
Fat32 will be fine.

---

### Post by Freddie.Ruddick on 2005-12-03
Just thinking aloud here. Would it be benificial/easier/worthwhile to have the actual windows installation in one partition, then have the "scratch disc" seperate?

---

### Post by ckempo on 2005-12-03
As opposed to a scratch partition separated off on the same disk? 

For the amount of use it's going to get (copying a few files back and forth) I'd hardly say it matters - take whatever route is easiest for you. 

I've got two XP partitions, a scratch area like you, my /home, swap and / Ubuntu partitions all setup on one disk so it's not a problem. :)

---

### Post by JimmyBEng on 2005-12-03
I guess it depends on what you mean as 'seperate'.  If you mean as another partition, that is pretty much necesssary.  Windows prefers NTFS, so having another partition that is formated as FAT for data that needs to be shared, is a requirement for writing from both linux and windows. however, if you mean on a second hard drive this isn't necessary, in fact you can have all three partitions, one for win, another for ubuntu, and the FAT partition on the same disk if you need.  Or you can put them on different disks. That is up to you.  Hope this helps.

---

### Post by kurzweilfreak on 2005-12-03
Great, that pretty much answered my question. I do have my Windows partition and scratch partition on seperate physical harddrives. Thanks much guys. I'm learning this stuff and it's fun. :D

---

