---
title: "Live CD vs Wubi vs an actual instal"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Depressed Man on 2007-06-04
If I'm correct, the differences between them are efficiency (well and permanence) right? The Live CD doesn't actually change your system, it just puts everything into RAM and it gets lost when the computer is turned off. Wubi is an installer for Windows that lets you install virtual partitions into Windows' 'C' drive. And an actual install (installing it into a partition) is the most effective in efficiency. 

Is that correct? I currently have Linux installed thru Wubi and I'm wondering the differences between a Wubi install and a real install. One thing I've noticied is that my linux install has username@localhost in terminal while I see screenshots with other things after @. And I seem to have problems with localhost ports. 

Though after using Linux a while through this, I'm actually thinking about making a real installation of Linux. I'll resize the Vista partition using Vista's built in software then I'll install the current Ubuntu install in it. When I was installing Linux, did Wubi do anything for me? Like assisting me in installation? If so will I have more trouble setting up a real partition?

Also I will need to make three partitions right? What if I want to make a small FAT32 partition so I can swap files? I'm not comfortable with installing the NTFS-3G (that is what it's called right?) and having it write to my Vista partition. Though I guess I could just make that new partition NTFS as well? 

HDA0 is the first partition (in this case Windows) right?

I'm pretty sure I have a grasp, it's just nice to have someone check if I'm right or offer suggestions before I get started. So I avoid borking my laptop up completly.. lol Thank!

---

### Post by cmillican on 2007-06-04
I would recommend installing Ubuntu and just using the built in partition editor (it automatically runs in installation) automatically handling everything after you tell it how much you want to give Ubuntu. Another option would be to just go out and buy a cheap 80-100 gig HDD, put it in ur box, and install Ubuntu on that just to make sure you don't screw with anything on ur Windows partition. (My 1st Ubuntu intall botched my whole drive's data and it cost 1700 bux to get 5 years of family photos recovered from the then formatted and partially written over drive)

---

### Post by Depressed Man on 2007-06-04
I'm afraid I don't have that choice since it's a laptop. Can't put more HDDs in it. :(

---

### Post by AAM on 2007-06-04
You are correct - LiveCD is ephemeral, fleeting and useful for trial and install. WUBI lets you have a functional Linux system without partitioning. Install gives you a completely independent system. I have run all three.

I found that WUBI was identical to an INSTALL. I couldn't pick speed difference, networking was identical (i.e., eth0 was easy and wlan0 was a PITA!). The bit after the @ can be changed within your configuration setups where your are asked for your machine's name. When you install, the install gives you a default entry of "yourname-desktop" - hence the difference you see on screenshots.

The one limitation with WUBI is that because it is writing into a Windows partition, and the file can get BIG (several to many GBs), you can run into problems with space. Unfortunately until recently WUBI has been unable to be consigned to its own partition needing to be on the C:\ drive partition.

So, if you are going to install, you should make up some free space on you HDD. Then make three partitions - root partition (called / and made bootable and of ext3 type, size of 6-10GB), a swap partition (no need to tell type here, its automatic, twice RAM), and a home directory (called /home, ext3 type and non-bootable, rest of GB you have planned). If you don't want to  write to NTFS, don't do it, the NTFS driver permits you to read the directory anyway.

The drives are numbered from 0 (hda is the first HDD, and hda0 is the first partition on the first drive) ... I think!

---

### Post by jonward0690 on 2007-06-04
> **cmillican said:**
> I would recommend installing Ubuntu and just using the built in partition editor (it automatically runs in installation) automatically handling everything after you tell it how much you want to give Ubuntu. Another option would be to just go out and buy a cheap 80-100 gig HDD, put it in ur box, and install Ubuntu on that just to make sure you don't screw with anything on ur Windows partition. (My 1st Ubuntu intall botched my whole drive's data and it cost 1700 bux to get 5 years of family photos recovered from the then formatted and partially written over drive)
Well I would say just resize Win Vista with Win Vista I have seen a lot of people have problems resizeing Win Vista partitons with anything but Win Vista.

---

