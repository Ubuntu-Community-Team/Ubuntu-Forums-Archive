---
title: "Using dual boot ubuntu to save XP files?"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-04-14
:confused: My wife's system is a dual boot now... :D 

I installed ubuntu in a bunch of free space. The win XP install is frogged. (What a surprise!) Does anyone know how I can use the ubuntu to salvage her important documents and files? It is all fat32, so no issue there. (The xP is so bad she needs a boot cd to even run it) my son had tried to use partition magic to transfer her stuff from c:/ to d:/, but it didn't work. I may need to do a couple of things:

1- I need to figure out how to mount the xp partition so I can look at it. 
2- I need to increase the amount of free space on d:/ to handle the files. (Currently have ubuntu on 5 gigs of that 34 gig drive (XP has three gigs already) The c:/ drive is 9.4 gigs, and a lot of that needs to be saved for her.

3- Transferring these files, so I can zip and save to our website for storage.
4- Then, I would like to re-format the xp partition and re-install it.

I don't even know if this can be done. I can't back up her stuff to cd, cause the XP is so messed up, and would require many cd's and lots of the stuff is deletable.

Help or suggestions would be MUCH appreciated!

---

### Post by andlinux21 on 2006-04-14
do you have a second computer by chance?

---

### Post by aysiu on 2006-04-14
It's easy to mount.

Follow this guide
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

It assumes your partition is /dev/hda1, but it may be /dev/hda2 (use the command ```
sudo fdisk -l
``` to tell.

Then, once it's mounted, you can zip it to Ubuntu and upload it to your website from there...

---

### Post by Papa-san on 2006-04-14
I do. It is my ubuntu laptop. I haven't been able to get them networked yet though...  I am VERY new, and don't know much about ubuntu as yet! (Other than the fact that I LOVE it, and wont soil by box with XP again!)

---

### Post by Mustard on 2006-04-14
1. This website includes a basic guide to mounting an ntfs drive temporarily... [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

2. Gparted should be able to resize your partitions. It can only resize unmounted partitions from within your current install, but you could use the live Cd and that would enable you to resize any of the partitions. What is taking up all the other space on the drives?  Adding up the numbers you have in your post seems to account for 14.4 gigs?

3. After mounting the NTFS partition, you shouldn't have many issues transferring to whatever space you created.  If you create a seperate partiion just for storing this backup stuff, then that would need to be mounted at the same time (the URL guide above should give some idea on how this is basically done)
4. Reinstalling XP is going to overwrite grub.  So your going to need to study up on ways to restore grub.

I'm sure there are more things to say, but thats a start. :)

-edit-

Doh..ignore my references to 'NTFS.  My brain was switched off.  I should have been sayiing 'FAT. :)

---

### Post by Papa-san on 2006-04-14
It is hda1. I tried the mount commands from the site you linked to aisiu, but am not able to decipher the info I got. (Instructions for mounting) it didn't mount, I don't think...

Gotcha on the ntfs thing mustard! :-)

---

### Post by RRS on 2006-04-14
[Here's]("http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only") the auto-mount instructions for both file types from Mustard's link. The same basic instructions as aysiu's but I believe updated.

Follow Mustard's directions to create a fat32 partition in whatever freespace you have and then with the above link you'll be able to copy any files you want to save from the XP (NTFS) partiton to the new fat32 before reinstalling windows to the NTFS partition.

If you're short on space and unable to set up your network soon enough you could always use e-mail to transfer the files to your other computer, kinda' slow and clumsy but functional.

Hope we've been able to help.

Edit: confused on file types, doesn't XP use ntfs by default? Or do you have a fat32 partition seperate for your data?
System>Administration>Disks will show all partitions with their size and format.

---

### Post by Mustard on 2006-04-14
[QUOTE=Papa-san]It is hda1. I tried the mount commands from the site you linked to aisiu, but am not able to decipher the info I got. (Instructions for mounting) it didn't mount, I don't think...

Gotcha on the ntfs thing mustard! :-)[/QUOTE]

Basically described in what I hope are laymans terms the process is..

1. make a new folder in a standard place for using as a 'mount point'.  Usually this is in the /mnt/ or /media/ folders.

2. Execute a mount command, with the needed options for correct permissions, that mounts the relevant device on that specific 'mount point'.

3. Browse in Nautilus file browser to the relevant 'mount point' folder you created and transfer the files to whatever free storage you have setup previously, either using the Nautilus GUI or via command line options for copying.

All of these steps can be explained in more detail, but its basically the 'English' version of what those guides above are showing you how to do with linux commands.

Steps 1 and 2 above are these commands from the guide, with a generic 'mount point' and generic device name used in the example.

```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
```

Show us the command you are putting in each time too, and what the output is, and we can probably pick any errors or give further assistance from looking at the command entered and the subsequent output.

---

### Post by Papa-san on 2006-04-14
OK...got her mounted now... I'll work on the others in the morning, I can screw things up quick when I'm too tired. I'll activate her account at ubuntu forums in the morning, and will post as 'bleachedbluejeans'. that way I can cut and past if I need to...

Thanks all!

---

### Post by Mustard on 2006-04-14
[QUOTE=Papa-san]OK...got her mounted now... I'll work on the others in the morning, I can screw things up quick when I'm too tired. I'll activate her account at ubuntu forums in the morning, and will post as 'bleachedbluejeans'. that way I can cut and past if I need to...

Thanks all![/QUOTE]

Roger that.  *crackling radio sounds*  Over and out. :)

---

### Post by Bleachedbluejeans on 2006-04-15
OK...At least I am this far... lol
I'm in xp right now, so I'll reboor once she gets done checking her email...
I will be creating an ntfs partition? I am not really sure as to why...
Once I reboot I'll post results of sudo fdisk -l so you can see the mess I'm dealing with. (To answer an earlier question, there is still a LOT of free space on d:/

EDIT:
```
Disk /dev/hda: 10.2 GB, 10246569984 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1245    10000431    c  W95 FAT32 (LBA)

Disk /dev/hdd: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        1245    10000431    c  W95 FAT32 (LBA)
/dev/hdd2   *        1246        3632    19173577+  83  Linux
/dev/hdd3            3633        3738      851445    5  Extended
/dev/hdd5            3633        3738      851413+  82  Linux swap / Solaris

```

---

### Post by Bleachedbluejeans on 2006-04-15
OK. I updated and installed gparted. I am aincluding a screenshot of the info on it as well as the 'disk manager' which is looking at my d:/ drive. Windows XP defaults to the fat32 filesystem, but many users choose the ntfs filesystem. This system is using fat32 for the entirety of the windoze partitions. This shows 14+ gigs of free space within the ubuntu partition, but I think it could be made it's own partition? If I make it fat32, ubuntu can write to it, correct? Or should I boot into XP to move the files?

(Papa-san isn't the sharpest tool in the shed!)
EDIT:
Gparted won't change the partitions, and I cannot unmount it because I am using it. Evidently the ubuntu partition is 18+ gigs. My free space is within that. Should I use live cd to use some of that 14 gigs for another partition? How would I use it to make it an ntfs partition? I thought ubuntu couldn't write to ntfs... (Refer to tool sharpness, above!) :-)

---

### Post by Papa-san on 2006-04-15
I cannot figure out how the live cd can be used to do partitioning... Should I try the install cd?

---

### Post by aysiu on 2006-04-15
[QUOTE=Papa-san]I cannot figure out how the live cd can be used to do partitioning... Should I try the install cd?[/QUOTE] 

1. Boot the live CD.
2. Go to a terminal (Applications > Accessories > Terminal)
3. Type ```
sudo apt-get update
sudo apt-get install ntfsprogs gparted
sudo gparted
```

The rest should be self-explanatory.

---

### Post by Mustard on 2006-04-15
This question has been at the back of my mind in this thread...

Why are we making a new partition to store stuff on?

Couldn't the stuff from XP be stored on the already created linux partition in some folder somewhere?

Or is this a case of needing to have a shared FAT partition so that the files can be accessed from the new XP install?

I have to admit to some confusion about this issue. :)

---

### Post by Papa-san on 2006-04-15
Due to cable modem issues, I cannot update...
I'll have to either wait till we get a new cable modem, or come up with a plan "B" using installed XP or ubuntu...

---

### Post by Bleachedbluejeans on 2006-04-15
[QUOTE=Mustard]This question has been at the back of my mind in this thread...

Why are we making a new partition to store stuff on?

Couldn't the stuff from XP be stored on the already created linux partition in some folder somewhere?

Or is this a case of needing to have a shared FAT partition so that the files can be accessed from the new XP install?

I have to admit to some confusion about this issue. :)[/QUOTE]
OK... cable modem reset and working for a minute.
This is why I was trying to ask how was the best method...
I honestly don't know how to do it... seems like the fat32 partition would make sense... Can XP access the ubuntu partition and take the files back? I don't know how any of this stuff works...

---

### Post by aysiu on 2006-04-15
[QUOTE=Bleachedbluejeans]Can XP access the ubuntu partition and take the files back? I don't know how any of this stuff works...[/QUOTE] Sure. [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Mustard on 2006-04-15
Ok, from what I read about the above program, you could boot up in Ubuntu, mount the FAT partition that you need to get the files from, transfer them to some folder on your Ubuntu partition. Then you could reinstall XP on its original partition (installs drivers etc...), then download the above program, mount the Ubuntu parition as an ext2 partition (read FAQ at above website for full explanation on backward compatibility of ext3 filesystems), then transfer all the files from the old XP install to the new XP install from within XP.

Sound like a working plan?

The only real issue after that is going to be XP overwriting Grub when it installs.

The easiest way around this (from my perspective anyway) is to make a backup of the MBR using dd and then after installing XP you could rewrite the MBR using dd from a live CD.  The partimage website has some instructions on this that I have used as a reference many times (in the section on backing up and restoring images, at the bottom of the page there are instructions on making a backup of the MBR and partition tables).  Very basic instructions for this are included in this guide for making a Grub boot floppy disk (making a Grub boot floppy is probably a good idea too)..

[https://wiki.ubuntu.com/GrubHowto/BootFloppy](https://wiki.ubuntu.com/GrubHowto/BootFloppy)

A more detailed explanation (at the very bottom of the page at the URL below)
[http://www.partimage.org/doc/index-3.html#ss3.7](http://www.partimage.org/doc/index-3.html#ss3.7)

Either that or look up some methods in the forum for restoring GRUB.  There are a couple of HOW TO's around.  A selection of links to read are below...

[http://wiki.ubuntu.com/GrubHowto](http://wiki.ubuntu.com/GrubHowto) 
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)
[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)
[http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

Can you tell I've been researching Grub a lot lately? :P  Hehehe.. I've got a grub floppy boot disk, a Super Grub floppy disk, Super Grub CD, System Rescue CD, and various backups of MBR's and partition tables in my home folder at the moment.  I prefer any method that avoids the need for me to manually reinstall Grub, so I prefer making backups of the MBR and restoring the MBR if I have problems.

---

### Post by Papa-san on 2006-04-16
Awesome...thanks guys!

I'll research the grub issue, as one of the major probs with XP is the MBR... I don't want to back it up as is, unless there is an option to back up the ubuntu part of it only.

Ummmm....  What's a 'dd'? lol (I apologize for my ignorance!)

---

### Post by Mustard on 2006-04-16
[QUOTE=Papa-san]Awesome...thanks guys!

I'll research the grub issue, as one of the major probs with XP is the MBR... I don't want to back it up as is, unless there is an option to back up the ubuntu part of it only.

Ummmm....  What's a 'dd'? lol (I apologize for my ignorance!)[/QUOTE]

It should all become clearer as you read the links above. :)

You can use the man command to read manuals on specific commands. The syntax of the man command is

```
man <command>
```

For dd you can do this..

```
man dd
```
Press the 'q' key to exit the menu.

---

### Post by Bleachedbluejeans on 2006-04-16
I have tried to get the Live session to update, and it has locked up on me three times at 43%. I don't know enought about commands to try getting past the error, so I gave up. I am going to try to use XP to upload her files to the server. Then I'll be able to reformat the whole thing. There isn't enough in the ubuntu partition to justify avoiding the re-install... I would love it if I had the confidence in my knowledge of ubuntu to do it thru there. One thing I can say is that I have the confidence in Ubuntu! (Just need to take precautions against the component that usually screws up computers around here... The organic link between the keyboard and the chair...):rolleyes: 

If I can save her stuff to the server, and get things to work in Ubuntu, she might be OK with going 100% Ubuntu... She says she needs to be able to check Ebay, blog, get email, and use turbo-lister for ebay. I can get her going with these things, except for the turbo-lister. I'll research that, and do a test on my laptop to see if I can make it work... Then we can go Gates-less!

---

### Post by hoarythehedgehog2009 on 2006-04-16
not exactly sure what the turbolister is, but if it is a windows program

one word: wine :)

---

### Post by Mustard on 2006-04-16
[QUOTE=hoarythehedgehog2009]not exactly sure what the turbolister is, but if it is a windows program

one word: wine :)[/QUOTE]

Heh..and if you are anything like me, that one word 'wine', leads to another word, 'confusion'. :)

Wine drives me nuts.  Configuring wine to get it to a working state was a nightmare of trial and error.

---

### Post by Papa-san on 2006-04-16
It is a windows based program. E-bay created it, and has no plans to create anything for linux. They might do one for mac, but this doesn't help us, does it?!? lolol (What a surprise!)

I have heard about the nightmares involved with using wine. This is complicated by the fact that the turbo-lister programmers have done a TERRIBLE job putting this one together... Even in an optimal windows system, this one crashes itself or the system at least half of the time...

---

### Post by max_power on 2006-04-16
[QUOTE=Papa-san]:confused: My wife's system is a dual boot now... :D 

I installed ubuntu in a bunch of free space. The win XP install is frogged. (What a surprise!) Does anyone know how I can use the ubuntu to salvage her important documents and files? It is all fat32, so no issue there. (The xP is so bad she needs a boot cd to even run it) my son had tried to use partition magic to transfer her stuff from c:/ to d:/, but it didn't work. I may need to do a couple of things:

1- I need to figure out how to mount the xp partition so I can look at it. 
2- I need to increase the amount of free space on d:/ to handle the files. (Currently have ubuntu on 5 gigs of that 34 gig drive (XP has three gigs already) The c:/ drive is 9.4 gigs, and a lot of that needs to be saved for her.

3- Transferring these files, so I can zip and save to our website for storage.
4- Then, I would like to re-format the xp partition and re-install it.

I don't even know if this can be done. I can't back up her stuff to cd, cause the XP is so messed up, and would require many cd's and lots of the stuff is deletable.

Help or suggestions would be MUCH appreciated![/QUOTE]
\



i would  just get a small live distro (i know dynobolic will work) , boot from the cd and then burn your windows files using Kroast or something like that-

---

