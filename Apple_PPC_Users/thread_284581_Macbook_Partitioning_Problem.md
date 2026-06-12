---
title: "Macbook Partitioning Problem"
date: 2006-10-25
forum: Apple PPC Users
---

### Post by hanjet on 2006-10-25
Hi.
I recently tried to repartition my HD so I could triple boot on my Macbook. 

I tried many times, but I kept getting the "no space" error. 
Here is a log:

[I]Last login: Wed Oct 25 19:53:06 on ttyp1
Welcome to Darwin!
[user]:~ [username]$ sudo diskutil list
Password:
/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *74.5 GB  disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS Mac HD             74.2 GB   disk0s2
[user]:~ [username]$ sudo diskutil resizeVolume disk0s2 29.2G Linux Ubuntu 22.5G "MS-DOS FAT32" WinXP 22.5G
Started resizing on disk disk0s2 Mac HD
Verifying
Resizing Volume

Resizing encountered error No space left on device (28) on disk disk0s2 Mac HD
[user]:~ [username]$ sudo diskutil resizeVolume disk0s2 28G Linux Ubuntu 22.5G "MS-DOS FAT32" WinXP 22.5G
Started resizing on disk disk0s2 Mac HD
Verifying
Resizing Volume

Resizing encountered error No space left on device (28) on disk disk0s2 Mac HD
[user]:~ [username]$ sudo diskutil resizeVolume disk0s2 29200M Linux Ubuntu 22500M "MS-DOS FAT32" WinXP 22500M
Password:
Started resizing on disk disk0s2 Mac HD
Verifying
Resizing Volume

Resizing encountered error No space left on device (28) on disk disk0s2 Mac HD
[user]:~ [username]$ sudo diskutil resizeVolume disk0s2 29000M Linux Ubuntu 22500M "MS-DOS FAT32" WinXP 22500M
Started resizing on disk disk0s2 Mac HD
Verifying
Resizing Volume

Resizing encountered error No space left on device (28) on disk disk0s2 Mac HD
[user]:~ [username]$ sudo diskutil resizeVolume disk0s2 28000M Linux Ubuntu 22500M "MS-DOS FAT32" WinXP 22500M
Password:
Started resizing on disk disk0s2 Mac HD
Verifying
Resizing Volume

Resizing encountered error No space left on device (28) on disk disk0s2 Mac HD
[user]:~ [username]$ [/I]

As you can see, I tried different sizes and tried MB/GB. Neither worked. Does anyone here know what the problem is? I'd really appreciate the help.

Thanks

edit: no one has ever had this problem??

---

### Post by rdwtux on 2006-10-27
I've had this problem when I was trying to increase the size of my HFSPlus partition (MacOS partition). 

You might want to try booting off of the Mac OSX cd 1 of the install and then running Disk Utill.. check your limits first and then try the resize (limits is "sudo diskutil resizeVolume disk0s2 limits". 

Not sure this will work, but resizing while unmounted might help. 

Good luck.

---

### Post by ruicovelo on 2006-11-16
Hi!

I'm getting this too. Well, I got to this thread by searching google...

Just installed Mac OS X on my macbook with 60GB hard drive and I'm following this how to:
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

But I can't resize the disk...

Anyone got this and solved it?

---

### Post by ruicovelo on 2006-11-17
I've got around by running the mac osx install again but partitioning the disk  before installing osx.

---

### Post by Patraman on 2008-07-01
Same problem here guys! I have no clue why it says I have no space, cause i checked the limits and it's all fine (i have enough space to do what i want to do)...
If i find anything out I'll let you guys know.

I don't want to re-install the OSX in a smaller partition, too much work!

Cheers,
Pato

---

### Post by stream303 on 2008-07-01
You may want to visit the current Apple forum to get wider exposure:

[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

The threads here are in a reply-only archive, and are specific for ppc.  The current Apple thread now hosts both ppc and intel architectures, and it is more likely to provide the help you seek with Macbooks.

---

### Post by johnsmith5082 on 2008-07-04
It has been a battle, but I finally got my Macbook  Pro configured as a dual boot machine. Did you know about parallels. I regularly kill my windows virtual machines and re-install them. Installing parallels and windows takes me about 2 hours, most of which is just windows installation disk ticking over......So I work on other stuff in Os X meanwhile.....
-------------------
johnsmith

[Used Apple Laptops]("http://applelaptopshop.com")

---

### Post by bigpimpin on 2008-07-22
i found this solution- didnt work for me, might work for someone else:

In some case, the diskutil resizeVolume reports "Resizing encountered error No space left on device (28) on disk" even you've used "diskutil list" command to confirm that disk space has enough apace. Do this work around will fix the errors;
 
1. Resize the current partion size first; 

  sudo diskutil resizeVolume disk0s2 60G
Reboot it. 

2. Creat the rest of partions; 

  sudo diskutil resizeVolume disk0s2 60G "Linux" "Linux" 17G "MS-DOS FAT32" "Windows" 15G



[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

---

