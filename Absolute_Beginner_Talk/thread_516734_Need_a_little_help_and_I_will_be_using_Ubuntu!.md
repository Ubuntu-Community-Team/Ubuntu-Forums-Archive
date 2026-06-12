---
title: "Need a little help and I will be using Ubuntu!"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by icett on 2007-08-03
> **Tyggna said:**
> Step by step, how I would do it:
**Note, this will take a long time--no matter how fast your computer**

First off, Windows is ego-centric.  It would like to be on your harddrive first.  I would install older versions first, then the newer ones.  

Your best starting point would be a live CD of Ubuntu, just to set the stage.  In Ubuntu 7.07 on the live CD click on the "system" at the top of the screen, select the administration, and click on GNOME partition editor.

***Note:  You are about to wipe your harddrive and lose any data on it***

Delete all of the exsisting partitions.  Simply click on the partition and press the delete key (or right click and select delete).   Click on apply and wait for it to finish.

Once GNOME partition editor is showing all gray, make your first partition at the beginning of the drive.  As you are running Windows 98, you'll want to partition this in FAT32.  Select the size, and then apply.  Once that's safely made, make another NTFS partition right after it.  When you're done with that, make an ext3 partition and a linux-swap partition in any order you want to.  (You don't need to make the swap partition more than 1000 megabytes).  

Once all these partitions are put on your hard drive, shutdown the live CD and go through the windows 98 install.  Put 98 on your FAT32 partition.  When 98 is up and running, go to "run" on your start menu, and type cmd.  When the black command prompt comes up, type either

chkdsk /r (preferred the first time you run this command, as this will fix any damaged sectors on your harddrive, but take a long time)

OR

chkdsk /f (the minimum requirement before a new install.

It might say that it can't preform a chkdsk at this time and if you'd like to do it on the next restart.  Say yes, and then reboot.  Let it run, and when it's done, reboot your computer twice before doing anything else.

After you've gone through two solid reboots, repeat this process for XP.  Same commands, same procedure.  XP should take control of your MBR (master boot record, it's used to tell the computer where to find your OS), and allow you to dual boot.  As you don't really need to dual boot using the windows uitility, I would NOT select any dual boot options that windows gives you, as this can screw up the linux dual boot utility (which is, sad to say, much better than windows'). 

Do your best to not let XP see 98.  When XP is done installing, run the command prompt again. ("Run" then type cmd)

From the command prompt:
Switch to the drive that XP is installed on (usually C:\, you just have to type CD [DRIVE LETTER]:\)
chkdsk /f

It will ask you if it can do this on reboot.  Say yes, then reboot.
Let it run, then reboot twice.

Now you're ready to install Linux.

Linux should see the partitions you made for it when you install.  From a feisty fawn live CD, select your region options and all that jazz.  When you get to the partitioning area, select your ext3 partition and right click.  Click on "edit" and then in the mount point option, type a single /

This tells Linux that you want it to run from that drive.  Linux should then be like, Okay!  Great, I know where to go, and I see everything else that's on this drive.

When the partition is made, it should ask you if you want to install GRUB.  say yes.  Grub should see XP and 98.  If you have any problems, then post again asking "how do I dual boot two windows os's with Grub," as I'm sure someone knows.

Once linux is installed, it'll be set as your default.  When you boot up, you'll see the grub menu, which will list two Ubuntus to start, and then have an "Other OS" section that should show both windows.

I hope that was helpful.







I have finally managed to create two fat 32 partitions for both the windows and installed them successfully. But for the two partitions I have created for Linux, I am not able to format them even with GNOME Partition Editor. With my live CD still in the CD Rom still there are two files I can see:


1- Filesystem

2-Lost+Found (Because of this I can not create partition for Linux.)


Please let me know how I can remove all the Linux data from the two Linux partitions. Are there some hidden files also? I wish to completely format them before I install Ubuntu again. Also I would like to scan my two partitions where I installed windows to see if there remains any hidden file or something relating to Linux. Please inform me how to. Thanks for your guidance before and I remain thankful to you. Best regards to the Ubuntu community!:KS

---

### Post by startherepodcast on 2007-08-03
Hi,

The Problem might be you do not have root privileges.

Try Running gparted on the live cd by entering

```
sudo gparted 
```

Enter this code in the terminal!

Good Luck

Adsized

---

### Post by Hospadar on 2007-08-03
I'm a little confused as to the exact setup of your partitions, could you list them as they appear in the partitioner in the ubuntu installer? (I think if you go to manual partitioning it will show full detailed info about all the partitions)

You should have a small swap partition and a large ext3 partition for linux.  If these are installed as described in the post, there shouldn't be anything on the ext3 partition, nor should you need to format it again (as you already formatted it).  I think that your confusion may stem from the fact that while using the livecd, it will show a filesystem, but that does not actually exist on the disc until/if you install linux.

Let me know about your configuration.

---

### Post by icett on 2007-08-03
> **Hospadar said:**
> I'm a little confused as to the exact setup of your partitions, could you list them as they appear in the partitioner in the ubuntu installer? (I think if you go to manual partitioning it will show full detailed info about all the partitions)

You should have a small swap partition and a large ext3 partition for linux.  If these are installed as described in the post, there shouldn't be anything on the ext3 partition, nor should you need to format it again (as you already formatted it).  I think that your confusion may stem from the fact that while using the livecd, it will show a filesystem, but that does not actually exist on the disc until/if you install linux.

Let me know about your configuration.




Below is the exact setup of my partitions:


(1)


/dev/sda1           
fat 32      
/media/disk-2                    
26.14 GiB (Size)   
754.46 MiB (Used)
25.40 Gib (Unused)
boot, lba
Contains Windows 98 SE


(2)


/dev/sda2
fat 32
/media/disk-1
26.14 GiB (Size)
3.86 GiB (Used)
22.27 GiB lba
Contains Windows XP Pro


(3)



Unable to Apply to create ext3 for Linux
21.00 GiB (Size)
759.20 MiB (Used)
20.26 GiB (Unused)



(4)



/dev/sda-4 
linux-swap
1.26 GiB (Size)
(Unused)




I earlier installed Ubuntu but it corrupted my system and I formatted and created all these partitions again and successfully installed both windows. But I am unable to install Ubuntu now. If the "Filesystem" is created because of live CD then its clear that its not in my hard drive? If so there is only one thing which is causing problem i.e. 



Lost+Found 



I am unable to delete it. Could you please guide me as how could I delete it. Also if there are any hidden files please let me know as I wish to scan and delete any hidden etc. linux files from my windows partitions as well as from the linux partitions if they really exist. I await your guidance. Best regards.:)

---

### Post by floke on 2007-08-03
I think I can safely say that 'Lost and Found' is NOT the cause of your problem!

Can you post the output of 'sudo fdisk -l'

and also 'df -h' (both from terminal), please, and we'll see what we can do.

---

### Post by icett on 2007-08-04
> **startherepodcast said:**
> Hi,

The Problem might be you do not have root privileges.

Try Running gparted on the live cd by entering

```
sudo gparted 
```

Enter this code in the terminal!

Good Luck

Adsized




I tried but could not find "gparted" or its terminal on the live cd. Please let me know how to do it. Thanks





> **floke said:**
> I think I can safely say that 'Lost and Found' is NOT the cause of your problem!

Can you post the output of 'sudo fdisk -l'

and also 'df -h' (both from terminal), please, and we'll see what we can do.



You mean from the terminal of gparted? Or from somewhere else? Please let me know and if I am getting it wrong I would request to guide me please.


:)

---

### Post by ugm6hr on 2007-08-04
See the link in my signature about Code entries in Terminal for details abouyt what Terminal is, and how to enter commands.

---

### Post by forestpixie on 2007-08-04
you run 

sudo fdisk -l (that a lowercase L )

df -h

from terminal it'll be in accessories

Edit - and that too ugm6hr :)

Edit 2 - and run gparted from the terminal - sudo gparted 
but be careful

---

### Post by icett on 2007-08-04
I found the terminal and from it I managed to open gparted. I also wrote the command "sudo fdisk-l" as well as tried many methods to format or delete the mentioned file but nothing worked. But I did not use the "df-h" and "ugm6hr" as I dont know whether I have to add "sudo" before them. Please guide me as to how I could delete lost+found file and format the drive. I hope there must be a practical easy way. Please help!:confused:

---

### Post by ugm6hr on 2007-08-04
> **icett said:**
> I found the terminal and from it I managed to open gparted. I also wrote the command "sudo fdisk-l" as well as tried many methods to format or delete the mentioned file but nothing worked. But I did not use the "df-h" and "ugm6hr" as I dont know whether I have to add "sudo" before them. Please guide me as to how I could delete lost+found file and format the drive. I hope there must be a practical easy way. Please help!:confused:

:lolflag: ugm6hr is my username - not a command!

Did you actually try to do anything in Gparted?  It should bring up a window that looks a bit like the shot linked below.  That's my hard-drive.

You can right-click on any partition you want and delete, resize, format....

If you are planning on installing Ubuntu - I would actually recommend you just **delete** both Linux partitions you created.  Then when you use the installer from the LiveCD, just choose the "Guided - use largest continuous free space" option.  That way you won't have to answer any difficult questions, and it will pick appropriate sizes for everything for you.

PS: to run GParted - it should really be:
```
gksu gparted
```

---

### Post by icett on 2007-08-04
> **ugm6hr said:**
> :lolflag: ugm6hr is my username - not a command!

Did you actually try to do anything in Gparted?  It should bring up a window that looks a bit like the shot linked below.  That's my hard-drive.

You can right-click on any partition you want and delete, resize, format....

If you are planning on installing Ubuntu - I would actually recommend you just **delete** both Linux partitions you created.  Then when you use the installer from the LiveCD, just choose the "Guided - use largest continuous free space" option.  That way you won't have to answer any difficult questions, and it will pick appropriate sizes for everything for you.

PS: to run GParted - it should really be:
```
gksu gparted
```




So if I install Ubuntu again after deleting both Linux partitions I created what would happen to the "lost+found" file I am unable to delete. Would the installer overwrite the "lost+found" file? If so would it perfectly reinstall Ubuntu on my PC? Before when I created all this mess, I did choose the "Guided - use largest continuous free space" option and at that time I did not have any free space just three equal fat 32 partitions with windows on two and related installed software on one. Now there are just two fat 32 partitions and if I delete both linux partitiions it would create a free space for Linux to go into. So I just wish to confirm from you if there is any chance that it would again interfere with my two fat 32 windows partitions? Please let me know. Also if I run GParted with "gksu gparted" code would I be able to delete the "lost+found" folder? Please inform. Thanks for your cooperation.:)

---

### Post by ugm6hr on 2007-08-04
> **icett said:**
> So if I install Ubuntu again after deleting both Linux partitions I created what would happen to the "lost+found" file I am unable to delete. Would the installer overwrite the "lost+found" file? If so would it perfectly reinstall Ubuntu on my PC? Before when I created all this mess, I did choose the "Guided - use largest continuous free space" option and at that time I did not have any free space just three equal fat 32 partitions with windows on two and related installed software on one. Now there are just two fat 32 partitions and if I delete both linux partitiions it would create a free space for Linux to go into. So I just wish to confirm from you if there is any chance that it would again interfere with my two fat 32 windows partitions? Please let me know. Also if I run GParted with "gksu gparted" code would I be able to delete the "lost+found" folder? Please inform. Thanks for your cooperation.:)

Please ignore the lost and found folder.  It will not be an issue if you delete both linux partitions.  It is totally irrelevant.

And yes - provided you have at least 10GB free space - **unallocated** in Gparted, with only 2 other **primary** fat32 partitions - then the **Guided - use largest continuous free space** will work flawlessly.

If you need confirmation of these facts - delete the 2 linux partitions, as advised, and then take a screenshot and post here for me to see.  But if you understand the situation - there should be no problems.

---

### Post by icett on 2007-08-04
> **ugm6hr said:**
> Please ignore the lost and found folder.  It will not be an issue if you delete both linux partitions.  It is totally irrelevant.

And yes - provided you have at least 10GB free space - **unallocated** in Gparted, with only 2 other **primary** fat32 partitions - then the **Guided - use largest continuous free space** will work flawlessly.

If you need confirmation of these facts - delete the 2 linux partitions, as advised, and then take a screenshot and post here for me to see.  But if you understand the situation - there should be no problems.




Thanks for your kind support. Ok now I will be installing Ubuntu and I would inform you the result very soon. :)

---

