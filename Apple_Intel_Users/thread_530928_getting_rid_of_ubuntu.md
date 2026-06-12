---
title: "getting rid of ubuntu"
date: 2007-08-21
forum: Apple Intel Users
---

### Post by jnev on 2007-08-21
hey guys, I need your help (again). I installed ubuntu feisty on my macbook pro, and honestly, I never use it. I love ubuntu (use it all the time on my desktop), but my laptop I use for photography, and unfortunately none of the programs I use are compatible with linux. I'd like to free up the 10gb of space and give it back to os x. now, what would be the easiest way of doing this? no (free) program that I've found for os x recognizes ubuntu and gives me a way to just delete the partition and converge that partition with my main one. I use refit to choose what to boot if it matters...

thanks

---

### Post by zero244 on 2007-08-21
Hello: I think you just answered your own question. What you mentioned should do the trick.
I havent really used OS-X that much.......If you need the hard drive space and dont need Ubuntu you might as well delete it.

---

### Post by jnev on 2007-08-21
> **zero244 said:**
> Hello: I think you just answered your own question. What you mentioned should do the trick.
I havent really used OS-X that much.......If you need the hard drive space and dont need Ubuntu you might as well delete it.

umm... yah. that WAS my question. HOW do I delete it? what program will do what I need it to? I'm pretty sure gparted won't do it (or at least that's what I've read)...

---

### Post by alephsmith on 2007-08-21
If you can boot from a live cd it should be pretty easy to erase the partition using parted.

---

### Post by cyberdork33 on 2007-08-21
> **jnev said:**
> umm... yah. that WAS my question. HOW do I delete it? what program will do what I need it to? I'm pretty sure gparted won't do it (or at least that's what I've read)...
You can delete the partition easily, it is resizing (increasing) your HFS+ partition that is the difficult part. Can you try booting your OSX install DVD and using DiskUtility to resize the partition? I think that it can do that, but if you try to repartition then you will have to wipe the entire drive. The problem is that there are not really any open tools that can create HFS+. If you can do a complete backup and reinstall, you may have better luck.

---

### Post by ivesjd on 2007-08-21
I beleive that you can format it NTFS or FAT32 with Gparted and then use the bootcamp assistant to resize your HFS+ partition.

---

### Post by Salgat on 2007-08-22
Yeah like mentioned above, use GParted, its a standalone partition manager that will allow you to format your ubuntu partition into a useable format for your OS X.

---

### Post by KingCharles on 2007-08-22
what did you use to install ubuntu? I think if you used boot camp, boot camp will resize the partition automatically if you delete the ubuntu installation with it :]

---

### Post by jnev on 2007-08-23
ok well I deleted the partition with gparted, but as already stated, I don't know how to merge it with my main hfs partition. boot camp wouldn't do it, and when I tried booting off my os x cd and running disk utility from there it said that it would wipe the entire drive when it merged the two partitions, so that's not an option. I'll try using gparted to format that partition as fat32 and then see if bootcamp will do it.

thanks for the help guys.

---

### Post by LordCount on 2007-08-25
Hello

I had the exact same problem as you yesterday night and it took me 4 hours to find a solution.
The method you mentioned probably works, but I found another one that worked for me yesterday and I thought I could share it with you.

My problem was:
- I installed bootcamp
- I installed rEFIt
- I ran "diskutil resizeVolume" in order to make my OSX partition smaller and create a Linux and Windows partition behind it on the same hard-drive.

Now my problem was: I had not created a BootCamp driver CD. And now, after partitioning my drive with diskutil, I could not even start BootCamp any more, because, of course, the drive had not been partitioned with BootCamp and BootCamp doesn't like that, so I just got an error message saying something like "Your drive has not been partitioned with BootCamp. BootCamp can only be installed if your drive contains only one OSX-formatted partition."
I was stuck with a running OSX and two empty partitions for Linux and Windows. I could not install Windows because I had forgotten to create a BootCamp driver disk and I could not delete the two partitions with diskutil or the Disk Utility from OSX.
I thought I could use a partition-tool from an Ubuntu Live CD in order to delete the two Linux and Windows partitions, but unfortunately, the Ubuntu 7.04 Live CD failed to boot properly on my MBP (Santa Rosa).

In the end, I found this great turotial that explains how to get rid of the partitions without the need of any external tools. All one needs is the OSX install DVD.

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp#Restoring_your_Mac_to_its_original_state](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp#Restoring_your_Mac_to_its_original_state)

So, in your case, as you have already deleted the partitions you wanted to get rid of, you just need to merge OSX with the empty space that is behind it.
- Have BootCamp create a new Windows partition (no matter how big or small)
- Reboot
- Have BootCamp get rid of the Windows partition by merging your OSX and Windows partition.
That should do it.

Hope this helps

---

### Post by stimpack on 2007-08-26
GParted liveCD. Its not a hassle either, these things are always handy to have around.

---

### Post by tylerdurden on 2007-08-26
So bootcamp can grow HFS+ partitions?  I was under the impression that you can take away from an HFS+ partition but not grow it (merging partitions)... Has the above methods worked for anyone personally? Thanks.

---

### Post by LordCount on 2007-08-26
The method from the link I posted worked 100% for me.

Thanks for suggesting the Gparted live CD, I'll get one for next time. :)

---

### Post by cyberdork33 on 2007-08-26
> **tylerdurden said:**
> So bootcamp can grow HFS+ partitions?  I was under the impression that you can take away from an HFS+ partition but not grow it (merging partitions)... Has the above methods worked for anyone personally? Thanks.
Bootcamp can grow HFS+, gparted cannot.

---

