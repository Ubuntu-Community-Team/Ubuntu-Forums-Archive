---
title: "so confused"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by ticked on 2007-08-29
i just setup Ubuntu, wish i read more first, I didn't know that Ubunto (Linux) didn't like to be set up on a partition. I set up two partitions on my hard drive, installed win2k on the first one, saved the files i didn't want to lose to both of them, then tried to setup Ubuntu on the second partition, of course it wiped out both partitions, now i lost everything i wanted to save. now not only am i trying to learn Ubuntu, but i am trying to learn Wine as well because i have some file recovery software that i am trying to run to see if i can get some of it back. every time i try to run the app i am told that i don't have administration rights to run the app. nothing i installed with wine runs( trying to get some games to run on here so my wife wont mind i put Ubunto on here). they wont run either. so it looks like i am gonna have to take the time to re-do my partitions and setup winxp on here again then get another drive to run and learn Ubuntu. so far its been frustrating and a major pain, but i think i am gonna learn to like the whole Linux experience after i get things going. right now i am just overwhelmed trying to learn the basics and trying to learn some data recovery, and trying to make the wife happy. but I am learning stuff. I guess i would be happiest if someone could just tell me how i can setup my dsl connection so i don't have to run the sudo pon dsl-provider command every time i have to restart my computer.
well its my first time here and i have already written a story, so i will stop now before i aggravate everyone before i get down to learn and ask all the typical newbie stuff.
have a nice day.

---

### Post by splintercellguy on 2007-08-29
Please be more succint next time, I had trouble reading through all the text. Did you do use entire disk when you installed?

---

### Post by tyggna1 on 2007-08-29
> **ticked said:**
> 
I set up two partitions on my hard drive, installed win2k on the first one, saved the files i didn't want to lose to both of them, then tried to setup Ubuntu on the second partition, of course it wiped out both partitions, now i lost everything i wanted to save. 

If you've already lost everything, use the GNOME partition manager (system, administration, GNOME partition manager) off the Ubuntu live CD and make an NTFS partition, a swap partition and an ext3 partition.  The swap partition should be 150% the size of your computers ram at least.  

Next, Install whatever windows you want, but do so using the existing NTFS partition.  After that's installed and you've updated it and rebooted a few times with it--click on "run" and type in cmd, then type in chkdsk /f and press "y" at the prompt--reboot the computer.  Let windows load up after it's done scanning.  Reboot your computer two more times--then install Ubuntu.  When you install Ubuntu, reformat the ext3 partition, and have the "mounting point" set at "/" which means root.  In other words, you're telling Ubuntu to boot and run off of that partition, and that it can set it up in what ever way it likes.  After that,  I would recommend installing the GRUB loader at the end of the Ubuntu install (though LILO has worked well for me in the past), so you can dual boot.

If GNOME partition manager isn't seeing anything, then skip that, and do this instead:
Install windows and let it take all of your drive--then run your recovery software to see what you can get.  When that's done, do the chkdsk /f again, and reboot twice (this secures the windows partition, and ensure that any logs or saved configuration folders won't interfere with the Ubuntu installation).  
Once that's done, then boot into the live CD, and select "resize existing partition" from the GNOME Manager (or from the install, it doesn't matter, though I find the manager to be more reliable).  Resize it so you have enough empty space to fit both 150% of your total RAM on your swap, and to have comfortable working space in Ubuntu--remember that Ubuntu can also read your windows folder if you install the right utility--so you may want to just calculate the absolute essential space for Ubuntu programs and packages. (Most people figure this to be a minimum of 10 gigs)

After that space is available, install from the live CD and use the available space to format the swap partition and the ext3 partition.

If you have any questions, please, just post.

---

### Post by ticked on 2007-08-29
thanks for the info, next time i am going to ask first. screw up second.
I am just wondering if i would save myself a ton of trouble by just putting a second  hard drive in. install windows on one and ubuntu on the other? i have a couple of hard drives kicking around

---

### Post by LaRoza on 2007-08-29
> **ticked said:**
> thanks for the info, next time i am going to ask first. screw up second.
I am just wondering if i would save myself a ton of trouble by just putting a second  hard drive in. install windows on one and ubuntu on the other? i have a couple of hard drives kicking around

That is not neccessary, but if you have them, do it. 

I wish I had hard drives to spare.

---

### Post by dptxp on 2007-08-29
Do not make one single huge partition for Ubuntu. Make / partition of 6 GB to 10 GB, ext3 format. Mount your data space as /home. You can have more data partitions. If you format the /home and/or data partitions in FAT32, Windows will read them without extra effort. But FAT32 is a dirty format. If you use ext3 format you need to install ext2ifs in Windows to see them and r/w, but you / partition too would be accessible from Windows.

Separate /home or data partitions allow you to reinstall or install other OS without disturbing data.

---

### Post by oomingmak on 2007-08-30
> **ticked said:**
> thanks for the info, next time i am going to ask first. screw up second.
I am just wondering if i would save myself a ton of trouble by just putting a second  hard drive in. install windows on one and ubuntu on the other? i have a couple of hard drives kicking around
That is a good option (and it's what I do) but a word of warning; Ubuntu will write to the MBR unless you specifically tell it not to. 

Even when you find the obscure, badly-labelled option (hidden away in the installer) to tell Ubuntu *not* to write to your MBR, you will still wind up with an unbootable system because the Grub installation method that Ubuntu uses is rubbish (it doesn't cater for BIOS based boot device switching).

It's fairly easy to solve (by editing /boot/grub/menu.lst) but if you are new to Linux then it's pretty hellish to sort out. 

Make sure you understand how to access the grub menu during boot and how to edit menu.lst and you'll save yourself a lot of stress (I learned this the hard way after Ubunu trashed my Windows MBR).

---

### Post by mcduck on 2007-08-30
> **dptxp said:**
> Do not make one single huge partition for Ubuntu. Make / partition of 6 GB to 10 GB, ext3 format. Mount your data space as /home. You can have more data partitions. If you format the /home and/or data partitions in FAT32, Windows will read them without extra effort. But FAT32 is a dirty format. If you use ext3 format you need to install ext2ifs in Windows to see them and r/w, but you / partition too would be accessible from Windows.

Separate /home or data partitions allow you to reinstall or install other OS without disturbing data.

/home can't be FAT partition. It has to be some Linux file system (like Ext3) as there are some files that need to have certain permissions and owner but windows file systems are not able to save Linux file permissions.

---

### Post by quinnten83 on 2007-08-30
there are some good howto's on how to dualboot, read them first before installing anything.
also install WXP first and then Ubuntu, as this seems to give the least headaches.

---

### Post by steve.horsley on 2007-08-30
The easiest way to install if you want to dual boot a single drive (assuming one NTFS partition fills the whole drive) is to use the installer option to reduce the size of the NTFS partition. The installer can then make all the other partitions it wants to.

If (as the OP had) you have 2 partitions and you want to use one for Ubuntu, then the wasiest approach is to delete the unwanted partition completely. Then choose the installer option to use the largest free space on the disk. The installer is likely to create 3 partitions (including an extended partition) but you don't need to worry about that - just let the installer use the free space.

---

### Post by captainwitherspoon on 2007-08-31
Hey, I recently used this to recover my data. I'm not sure if our problem is the same but maybe it will help. 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by wolfen69 on 2007-08-31
> **LaRoza said:**
> That is not neccessary, but if you have them, do it. 

***I wish I had hard drives to spare.***

having 5 drives is wonderful!!!

1 for xp(never use it)
1 for ubuntu
2 for storage/backup
1 for distro testing

if you're going to go with 2 drives, you might want to disconnect one drive while installing on the other. that way neither drive can "interfere" with the other.

---

