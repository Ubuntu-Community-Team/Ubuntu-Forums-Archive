---
title: "No write permissions to external hard drive"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by halon on 2007-07-07
Hello: Seems this is a common problem for those using a NTFS formatted HD.  However, I have a Western Digital external FAT32 formatted, all has been well up to today.  Since the unmount option is not functional in 7.04 I simply unplug the drive and this has given no trouble, today, I unplug and now I have no write permissions to the drive and the system only recognizes it as a read only drive.  Tried to set a mount point in /etc/fstab with permissions, no luck. Any help is appreciated in advance.

---

### Post by atria on 2007-07-07
My guess is that the drive was unmounted uncleanly and requires a checkdisk.

You will not be able to mount the disk at all until you run a checkdisk on it (or you can force mount with the mount -f command, but this is NOT recommended)

I don't quite get what you're saying though, what filesystem are you trying to mount? FAT or NTFS? Either way you can boot into windows and run a checkdisk, or you could install the filesystem tools so that disk checking can be done on linux as well.

Good luck

Oh yes, unmount works here. You have to make sure that the disk is not used by any other process. You can also unmount with the umount command in the terminal.

---

### Post by PilotJLR on 2007-07-07
change the mount point owner over to your username... for example, if your username is halon, and the mount point is /media/disk, then:
```

sudo chown halon:halon -R /media/disk

```

---

### Post by halon on 2007-07-08
The drive is mounting and mounts as /media/USB 20GB

here is the print from fdisk -l

Disk /dev/sdb: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2431    19526976    c  W95 FAT32 (LBA)

here is the print from ls -la /media

total 32
drwxr-xr-x  4 root  root  4096 2007-07-08 07:05 .
drwxr-xr-x 21 root  root  4096 2007-06-28 18:18 ..
lrwxrwxrwx  1 root  root     6 2007-06-28 12:22 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2007-06-28 12:22 cdrom0
-rw-r--r--  1 root  root   103 2007-07-08 07:05 .hal-mtab
--wxr-x---  1 root  root     0 2007-04-15 07:56 .hal-mtab-lock
drwx------ 11 halon root 16384 1969-12-31 19:00 USB 20GB

The command sudo chown halon:halon -R /media/USB 20GB gives:
chown: cannot access `/media/USB': No such file or directory

The create folder option is grayed out,  drag and drop says I don't have permission to write to the disk.

Unmount says: Cannot eject volume???

Thanks again in advance

---

### Post by PilotJLR on 2007-07-08
> **halon said:**
> 
The command sudo chown halon:halon -R /media/USB 20GB gives:
chown: cannot access `/media/USB': No such file or directory


Type it this way:
```

sudo chown halon:halon -R /media/USB\ 20GB

```

The backlash "escapes" the space... without it, the command basically stops at "USB", which is why the name isn't found.

---

### Post by BL00dFox on 2007-07-08
I Have an extremely easy solution. Go to your synaptic package manager, search and download: ```
ntfs-3g
``` and install it.

Now access it through Applications >> System Tools

Just check the box saying you can write to external hard drives and your done!

---

### Post by Qwerty_ on 2007-07-08
> **BL00dFox said:**
> I Have an extremely easy solution. Go to your synaptic package manager, search and download: ```
ntfs-3g
``` and install it.

Now access it through Applications >> System Tools

Just check the box saying you can write to external hard drives and your done!

I am having the same problems I tried that last night to no avail.

---

### Post by halon on 2007-07-08
Well, after running ChkDsk on the drive from XP again, plug it in, and I'm set, all permissions are in order and I can write to the drive.  Thank you for the replies. 

Perhaps someone can tell me why the unmount option from the file system says cannot eject volume?? Secondly how is the mount of this drive managed??

---

### Post by Nezing on 2007-07-08
I tried the method,as instructed by BLOOd Fox,and I got a message saying,unable to mount drive.I went back to Synaptic,and uninstalled ntfs-3g,rebooted my pc,and I can see,and use my Seagate external drive (hooray),but still I cannot write to it.Okey,it does not really matter,as it's nearly full anyway,with my media files,and I have a 2gb usb pen drive,which **does** allow me to import-export "stuff" to it.I just wish I had not formatted my Seagate drive to ntfs last year.And no,I'm not going to copy nearly 250 gigs worth of media files to disc,and format the drive again. :lolflag:

Anyway,thanks for trying guys.

---

### Post by PilotJLR on 2007-07-08
Did you try the chown command I posted earlier? Just wondering if that helps regarding the unmount permissions.

NTFS-3g is a wild goose chase in this instance, since fstab reports the partition formatted as FAT32.

---

### Post by halon on 2007-07-08
Yes, I tried the chown command, with no avail. The only thing I can do is click unmount from file system then once it unmounts, quickly unplug before it re-mounts the drive with the "cannot eject drive" message. I'm not a big fan of ntfs -3g at the current moment either.

I have done some searching on the web, and from what I can uncover, this is a bug in 7.04 that will be fixed with the release of Gusty Gibbon.  I will deal with it for now since I only run Ubuntu on one machine.  Thanks for the help.  :guitar:

---

### Post by davisbarrett on 2007-07-11
Oh my God!!!  It's a BUG!!!  I have been sitting here for three days swearing at the universe because my brand-spanking-new Seagate 250G drive just didn't want to do any of this!  By the way Halon, thanks for your example - I didn't get much out of it, but as a noob it was quite helpful on the right syntax required...

OMG, I think I have a friend somewhere with a MicroSHAFT machine...  Perhaps finally he'll be of some use to me after all!!!  ](*,)

---

### Post by davisbarrett on 2007-07-11
Atria!!!  Found the solution on my computer, try it on yours...  In another thread a member called "fish2ways" (though I am entirely curious about the 2nd one) wrote this:

cut-----cut----cut----n----paste   :popcorn:

 fish2ways  fish2ways is offline
First Cup of Ubuntu
	  	
Join Date: Nov 2006
Location: UK
Beans: 1
Ubuntu 7.04 Feisty Fawn User
Re: Ubuntu Feisty USB HDD Bug - Please help
This post could be related to an Ubuntu bug filed at: [https://bugs.launchpad.net/ubuntu/fe...hal/+bug/63090](https://bugs.launchpad.net/ubuntu/fe...hal/+bug/63090)
----------------------------


Hi
I had problems with my external usb HDD's after installing Feisty.

The resolution was that I moved the /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi file. After i did that everything worked as it should.
If you want to try it open a terminal and type

sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /home/your own home folder name

After that switch on your usb drive and see if it mounts as it did under Edgy.

You shouldn't need to edit fstab for usb drives etc. Just let Ubuntu mount them as and when they're connected.
Hope this works for you.

---

### Post by Inxsible on 2007-07-11
> **halon said:**
> The drive is mounting and mounts as /media/USB 20GB
 
here is the print from fdisk -l
 
Disk /dev/sdb: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
Device Boot Start End Blocks Id System
/dev/sdb1 1 2431 19526976 c W95 FAT32 (LBA)
 
here is the print from ls -la /media
 
total 32
drwxr-xr-x 4 root root 4096 2007-07-08 07:05 .
drwxr-xr-x 21 root root 4096 2007-06-28 18:18 ..
lrwxrwxrwx 1 root root 6 2007-06-28 12:22 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-06-28 12:22 cdrom0
-rw-r--r-- 1 root root 103 2007-07-08 07:05 .hal-mtab
--wxr-x--- 1 root root 0 2007-04-15 07:56 .hal-mtab-lock
drwx------ 11 halon root 16384 1969-12-31 19:00 USB 20GB
 
The command sudo chown halon:halon -R /media/USB 20GB gives:
chown: cannot access `/media/USB': No such file or directory
 
The create folder option is grayed out, drag and drop says I don't have permission to write to the disk.
 
Unmount says: Cannot eject volume???
 
Thanks again in advance
I know you have tried a lot already....but I have a solution for you.
 
Since this is an external drive you should use pmount to mount it.
If you do not have pmount installed already
```
sudo aptitude install pmount
```
then you can use it like this:
```
sudo pmount /dev/sdb1 USB20GB
```
pmount will create a folder called USB20GB for you under /media. So make sure you use a folder name which is not already existing. You can use any other name instead of USB20GB. Just make sure it doesnt have any spaces in it, because then you will have to always include quotes around the name to access it. 
 
This will automount the drive always when you connect it.
 
As a side note: I think its always better not to have spaces in folder names.
 
pmount has never failed me...and I have mounted atleast 6 different external drives on my computer :)
Hope that helps !

---

### Post by Inxsible on 2007-07-11
I also see that you are already the owner of the mount point USB 20GB, but your group is root.
 
you can alternatively change the permissions on the mount point
 
```
sudo chmod -R 777 "/media/USB 20GB"
``` the quotes are needed because of the space in the folder name

---

### Post by tgbrowning on 2007-07-14
Regarding the error message -- you may have hit one of those messages that serves several errors and consequently, the message itself is often misleading. If you can query the system for the actual error code, it might be more informative.

Browning>>>t

---

### Post by James.Dedon on 2007-07-14
I think what he is trying to say is that the external drive is not unmounting the way that other drives unmount.  When I try to unmount my Maxtor 120GB it acts like it is unmounting and the drive stops and all, but being that the drive is hard wired for power with it's own switch it automatically remounts itself and gives the message "cannot eject volume".  I don't see it as a problem though.  Just try to eject the drive as you would any other and hit the switch before it remounts.  :neutral:

---

### Post by The Seeker on 2007-07-14
> **halon said:**
> Perhaps someone can tell me why the unmount option from the file system says cannot eject volume?? Secondly how is the mount of this drive managed??

Do you have the fiesty-backports repo uncommented in your sources.list? I ask because I experienced the same problem until I upgraded with said repo enabled; this installed a new version of hal which fixed the problem.

---

### Post by cn9ne on 2007-07-20
Ah-well, pmount works for me. I had the same problem as you guys, until I tried using pmount. 

First, I will umount the autodetected USB drive. Then, I straight away away mount using pmount and it worked!

```
cn9ne@cn8ne:~/fold$ pmount /dev/sdb1 USBHDD

```

P/s: I did sudo the pmount, but it didn't mount the disk. So, I remove sudo.

---

### Post by tombayo on 2007-07-20
I have problems with my USB hard drive aswell, it's a seagate 250gb known as "FreeAgent Drive".
At first when I connected it I could read the files, but not write to them, after replugging the drive, I can't mount it.
So I used pmount. A hard drive showed up, but when I tryed to access the files I got a message saying that I dont have the permission to view these files..
I've also tryed:
```
sudo chmod -R 777 "/media/FreeAgent Drive"
```
But all I got was:
```
chmod: changing permissions of «/media/FreeAgent Drive/Warranty and Customer Support.pdf»: Read-only file system
```

Darn annoying :P
It worked fine under windows, but I dont have access to my windows computer as of now, so I cant run a checkdisk on it, sadly.
I think that pherhaps checkdisk might work, so if anyone have a linux version of a similar program, please give :)

---

### Post by Gary.M on 2007-07-21
For what its worth I did just this...

[http://ubuntuforums.org/showthread.php?p=3059660#post3059660](http://ubuntuforums.org/showthread.php?p=3059660#post3059660)

---

### Post by Neovos on 2007-10-31
Had a similar problem. The chown commands for me changed back to root and graphically it changed back as well. I figured out that it was the default mount options for the ntfs-3g driver. Check it out...

[http://ubuntuforums.org/showthread.php?t=590784](http://ubuntuforums.org/showthread.php?t=590784)

---

### Post by whistlerspa on 2007-12-01
For me it's just temperamental.  

Works on login or first plug in but then seems to disconnect itself after as while and becomes unreadable with Nautilus.  I have to re log in. Occasionally decides it's read only as well.

Works fine under Vista on the same Dual boot box so this must be a Linux / Ubuntu issue I suppose. Very irritating.

---

