---
title: "[SOLVED] I broke my Kubuntu but can't get to both pieces :)"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by therandman on 2007-06-30
Okay, I tried to follow a tweaking guide I found somewhere to speed up my broadband, boot-up, etc. and something didn't go quite right.  Now my Kubuntu boots up to a non-GUI login, and after about 15 second it goes back to the Kubuntu loading screen and just locks up.  I am able to login but I will have to run commands quickly.  I'm not exactly sure what I did to break it, so it will be difficult to reverse what I did.

I guess I have two options, either try to fix it or just get my home directory backed up.  As far as the second option, I was going to make a seperate /home partition, but didn't quite make it that far.  I can't really figure out how to use the LiveCD to access my /home directory so I can just move the files to a usb drive.  Any ideas?

Thanks in advance!

---

### Post by Outrunner on 2007-06-30
I think you might not need to reinstall. When you get to the text login, just press CTRL-ALT-F2 to get to another console. Login and then type

```
sudo dpkg-reconfigure xserver-xorg
```

Press the spacebar to put a tick (the asterisk - * ) in a checkbox and Enter to accept settings. For things that you do't know, you can just leave the default answers

After this type ```
startx
``` If it doesn't work, come back and we'll see what else we can try

---

### Post by Nekiruhs on 2007-06-30
Pop in the live cd. Boot up. 
1) Get to the terminal.
2) Remember the name for your partition with Kubuntu on it. (Something like sda, hda, sda1, hda1, sdb, hdb, sdb1, hdb1, with or without a number or letter)
3) Mount that partition by doing ```
sudo mkdir /media/old && sudo mount -t ext3 PartitionName /media/backup
```
4) Tarball and gzip your homefolder with ```
cd /media/old/home/USERNAME/ && tar -cvvz home .tar /media/old/home/USERNAME
```
5) Copy that compressed tarball to a flash drive and reinstall

---

### Post by edoviak on 2007-06-30
Here's how you can use a live CD to transfer your files to a USB disk.

Start by inserting an Ubuntu live CD. Once it has loaded, open the console and become root by typing:
[B]
$ sudo su
[/B]
Next you have to find the name of the partition on which you installed Kubuntu. To do that, type:  
[B]
# fdisk -l
[/B]
You should get some output that looks like this:
```

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         765     6144831    c  W95 FAT32 (LBA)
/dev/hda2            2015        2432     3357585    f  W95 Ext'd (LBA)
/dev/hda3            1407        2014     4883760   83  Linux
/dev/hda4             766        1406     5148832+  83  Linux
/dev/hda5            2076        2432     2867571    c  W95 FAT32 (LBA)
/dev/hda6            2016        2075      481918+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
In your case, you should have only one Linux partition. I have a separate home partition, which is on either hda3 or hda4. Let's assume that it's on hda4 however.

Next you need to create a directory to which you'll mount your Linux partition and then mount it. To do that, type:
[B]
# mkdir /media/harddisk
# mount /dev/hda4 /media/harddisk
[/B]

Next insert your USB disk. (It should mount itself automatically, but if it doesn't just follow steps similar to the ones above).

Now open up a root file manager. With an Ubuntu Live CD, you would type **# nautilus** With an Kubuntu Live CD, you would type **# konqueror**. Then go into the file manager and open up the **/media/harddisk** folder to find the file system on the harddisk. Copy the files that you need to your USB disk (which should be mounted at **/media/disk**).

Once you're done, close the file manager, safely remove the USB disk (by right-clicking on the desktop icon), go back to the console and unmount your harddisk by typing the command:
[B]
# umount /dev/hda4
[/B]
Note: there's only one "n" in "umount." If for some reason, your USB disk did not mount automatically, you could safely remove it by unmounting the pendrive (for example: **# umount /dev/sda1**).

Your files should be backed up and you should be ready to reinstall Kubuntu.

Good luck!
- Eric

---

### Post by therandman on 2007-06-30
Thanks Outrunner, Nekiruhs, and Edoviak.  I ended up going with the last suggestion.

Got all the way to the point of opening up the root file manager, and using 

```
# konqueror
```

gives me this error:

```
root@ubuntu:/home/ubuntu# konqueror
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

konqueror: cannot connect to X server :0.0

```

---

### Post by therandman on 2007-06-30
Okay, what would be the console commands to move the entire home directory to my USB drive?  cp doesn't seem to work for moving a folder.

---

### Post by edoviak on 2007-06-30
I'd start with Nekiruhs' suggestion that you tarball and gzip your home folder. That will reduce the file size (so you can save more to your USB disk and so that you can spend less time moving it to your USB disk). 

I use Kubuntu, so I tried typing **# konqueror** (at the root prompt) and I was quite surprised when I got the same error message. I was able to open a root file manager by typing **$ sudo konqueror** however. 

So try "sudo'ing Konqueror" and if that doesn't work, then try copying to your USB disk by typing:
[B]
# cp /media/harddisk/home/therandman/home.tar.gz /media/disk
[/B]
Note that I've assumed that your harddisk is mounted at **/media/harddisk**.

Hope this helps! Good luck!
- Eric

ps: I imagine that you have a USB disk that is large enough to hold all of your data. If not, then go out and buy a USB external hard disk.

---

### Post by therandman on 2007-07-01
Somehow my home folder magically appeared on my USB harddrive.  Not sure how I did it, but my problems are solved.  Thanks for everyone's help!

---

