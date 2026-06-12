---
title: "Moving files to a device"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by djshag on 2006-08-24
How do I move files from my hard drive to an SD card?
Tried this:

sudo mv -v /home/djshag/Desktop/linux /dev/sdb2

got:

cannot overwrite non-directory /dec/sdb2 with directory /home/djshag/Desktop/linux 

Thanks in advance!

---

### Post by meng on 2006-08-24
I've not tried this before, but would it not make sense to mount the device first?

---

### Post by ciscosurfer on 2006-08-24
You need to copy and/or move the files to the directory upon which you mounted your SD card.  Check where it's mounted by issuing the 'mount' command within a terminal.

---

### Post by mssever on 2006-08-24
You can't write to the device directly. It has to be mounted first, then you copy files to/from the directory where it's mounted. If you type mount it will tell you where every mounted device is mounted.

---

### Post by djshag on 2006-08-25
Thanks! The advise helped a lot. One problem still...
Keep getting an error message saying device is read only. The SD card has been partitioned. The FAT partition is writable, the linux is not....
mounting media produces:

sdb1 (FAT32 volume) - /dev/sdb1 already mounted or /media/usbdisk busy

sdb2 (ext3 volume) - can't find /dev/sdb2 in /etc/fstab or /etc/mtab


I like Ubuntu very much, but it sure is frustrating... :-/

---

### Post by mssever on 2006-08-25
Is your SD card being mounted at /media/usbdisk? Typing [FONT=Courier New][COLOR=DarkRed]mount[/COLOR][/FONT] will tell you. If so, insert
```
/dev/sdb1       /media/usbdisk     vfat           defaults,users,nls=utf8,umask=007,gid=46,rw   0       1
``` into /etc/fstab and remount. Change this line as appropriate.

---

### Post by djshag on 2006-08-25
Hehe... now i'm getting:

mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Should I give up? What I'm trying to do is put dos & linux files into their respective partitions to run linux on my pda. I have a feeling that something is wrong with the linux partition although it looks ok in QParted.

Wish I'd used this forum before. You've all been very helpful!
Thanks!

---

### Post by djshag on 2006-08-25
Hmmm.... both partitions are showing as primary. Is that a problem?

---

### Post by mssever on 2006-08-25
> **djshag said:**
> mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Usually, this error means that the partition isn't mounted. Make sure that it's mounted before doing anything else. If you're still having problems, please post the output of [FONT=Courier New][COLOR=DarkRed]mount[/COLOR][/FONT] and the contents of /etc/fstab.

---

### Post by djshag on 2006-08-25
mount produced:

> /dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/sdb1 on /media/usbdisk-1 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

contents of fstab (note: I've tried a couple of suggestions and remarked them):

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/sda1 /mnt/fat vfat user,noauto 0 0
#/dev/sdb2 /media/linux ext3 user,noauto,rw,iocharset=utf8,gid=users,umask=0000 0 0
/dev/sdb2       /media/usbdisk     vfat         defaults,users,nls=utf8,umask=007,gid=46,rw   0       1

---

### Post by mssever on 2006-08-26
> **djshag said:**
> mount produced:
```
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
[COLOR=Red]** /dev/sdb1 on /media/usbdisk-1 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)**[/COLOR]
``` 
contents of fstab (note: I've tried a couple of suggestions and remarked them):
```
                              # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/sda1 /mnt/fat vfat user,noauto 0 0
#/dev/sdb2 /media/linux ext3 user,noauto,rw,iocharset=utf8,gid=users,umask=0000   0 0
**[COLOR=Red] /dev/sdb2       /media/usbdisk     vfat         defaults,users,nls=utf8,umask=007,gid=46,rw   0       1[/COLOR]**
```

I've highlighted the relevant lines on both outputs. Mount is telling us that the first (or only) partition on /dev/sdb (/dev/sdb1) is mounted on /media/usbdisk-1. This one should be writable if you copy files to /media/usbdisk-1. Do you have multiple partitions on this device? If so, each one needs to be mounted separately. For each partition (sdb1, sdb2, etc.) other than swap, you should have a mount directory and an entry in /etc/fstab. You might make the directories /media/sdb1, /media/sdb2, etc.

Next, each partition needs to be formatted. Any partition that you plan on putting Linux files on should be formatted with a Linux filesystem, unless you have a good reason not to. And if you're trying to run Linux on your PDA, you definitely **have** to use a Linux filesystem, which means that you'll have to reformat. I'll use ext3 in my instructions, but there are other options, as well.[LIST=1]
[*]Unmount your SD card but *don't remove it*. Try ```
sudo umount /dev/sdb1
``` Make sure that you unmount every sdb partition listed by mount.
[*]Fire up your partition editor. You can probably do what I'm telling you from QParted, but since I've never used it, I'll tell you what I know. Type ```
sudo fdisk /dev/sdb
```
[*]Type p to print the current partition table.
[*]All Linux partitions should say 83 in the Id column and all swap partitions should say 82.
[*]If you need to make any changes, hit t, enter the partition number, then type in the proper id.
[*]When you're finished, type w to save the changes. **Warning: this will destroy all data on the card!**[/LIST]Now, format the partitions. For each of your Linux partitions, type ```
sudo mkfs.ext3 /dev/sdb1
``` Substitute the proper partition number. For each of your swap partitions, type ```
sudo mkswap /dev/sdb2
``` Again, substitute the proper partition number.


Now, add the proper info to /etc/fstab for each non-swap partition. If you've set them up like I've said here, then you'd do something like:
```
/dev/sdb1       /media/sdb1               ext3    defaults,users,noauto 0       1
``` 
Finally, for each non-swap partition, type ```
mount /media/sdb1
``` using the proper mount point that you set up.

Now you should be able to copy files to those mount points, whereupon they wil be written to your code. **Be sure to unmount the partitions on the card before removing it. Otherwise, you might lose data.**

---

### Post by djshag on 2006-08-26
Followed the directions and when trying to move files to disk get a Read-Only filesystem error.

mount =

> /dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/sda2 on /media/linux type ext3 (rw,nosuid,nodev)


fstab=

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/sda1               vfat    defaults,users,noauto 0       1
/dev/sda3       /media/sda3               ext3    defaults,users,noauto 0       1


mtab =

> /dev/hdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-26-386/volatile tmpfs rw 0 0
/dev/sda2 /media/linux ext3 rw,nosuid,nodev 0 0

Normally, a lightbulb would be turning on and I'd be able to figure it out from here, but I feel like 2 yr old trying to learn quantum physics. Perhaps you could suggest a couple of good "learning Linux" with a focus on terminal operations type books. ](*,) 
Thanks again for the help.

---

### Post by mssever on 2006-08-26
Hmm....fstab and mtab look fine. What was the program that gave you the error? And the command you used that resulted in the error?

As far as books go, I don't know any to recommend. I'm sure that there are some, though. When I started out, I did a lot of [FONT=Courier New][COLOR=DarkRed]man whatever[/COLOR][/FONT]. man gives you the manual for a command or a system file. You can also Google HOWTO task where task is what you're trying to accomplish. But it definitely takes time to become proficient with the terminal.

---

### Post by djshag on 2006-08-26
The error was produced when I tried to copy files to the linux partition:

sudo mv -v /home/djshag/Desktop/linux /media/linux

The directory I am trying to move from the desktop to the SD card has an icon of a lock above it. Does that signify "Read-Only"?

---

### Post by bodhi.zazen on 2006-08-26
I am sorry and would like to help.

I can not follow the changes to fstab.

3 posts ago msserver was talking about sdb (sdb1 and sdb2 are in RED)

2 posts ago djshag is posting mount, fstab, and mtab.

Where is sdb (/dev/sdb) ?

Should fstab not have a line like:
```
/dev/sdb1 /media/sdb1 ext3 defaults,users,rw

OR
/dev/sdb2 /media/usbdisk ext3  defaults,users,rw
```

/dev/sda2 is new in mtab. /dev/sda1 and /dev/sda3 are new in fstab. Which is this the partition we are having trouble with ?

I am afraid I am lost.

May I ask what partition are your trying to mount (/dev/what) where (mount point) ?
What are the ownership and permissions of the mount point ?

---

### Post by bodhi.zazen on 2006-08-27
What is the output of 

ls -l /home/djshag/Desktop/ | grep linux

and 

ls -l /media/ | grep linux

(note that is a smalll "L" and not the number 1)

Also is /home/djshag/Desktop/linux a directory or a file?

If it is a directory, and you have the proper permissions, try:

[code}
mskdir /media/linux/linux
cp /home/djshag/Desktop/linux/* /media/linux/linux/
rm -r /home/djshag/Desktop/linux[/code]

Errors at any step (copy or delete ?) ?

---

### Post by djshag on 2006-08-27
Hehe... I hope I can give you all of that info.

I have formatted my SD card with 3 partitions:
- a small FAT partition
- a small linux swap partition
- a large linux ext partition

Right now in /dev I see:

sda, sda1,sda2,sda3,sdb,sdc,sdd

not sure why so many sd*'s for one card

mount shows me that sda2 (the linux ext3 partition) is mounted.

the mount points for the card should be /media/dos (sda1) and /media/linux (sda3)

sda2 is supposed to be the swap file.

QParted shows the drive /dev/sda as read only

Which files or devices do you wish to have the permissions from? Sorry, I think I'm getting quite confused myself here...

---

### Post by djshag on 2006-08-27
ls -l /home/djshag/Desktop/ | grep linux =

> drwxr-xr-x 16 root   root       4096 2005-04-07 08:09 linux
-rw-r--r--  1 djshag djshag 18795695 2005-04-12 12:42 linux.tar.bz2


ls -l /media/ | grep linux =

> drwxr-xr-x 4 djshag djshag 4096 2000-01-01 02:45 linux

/home/djshag/Desktop/linux is a directory and apparently is owned by root. That will make a difference! Although..... I was using sudo to copy or move the files...

---

### Post by bodhi.zazen on 2006-08-27
Let me start with the basics. It looks like your card is /dev/sda with 3 partitioins.

The other sdb, sdc, sdd are all "potential" cards.

GParted shows your card as sda, yes?

And the partition you want to mount and copy to is the ext3 partition, yes?

And that partion is /dev/sdb3, yes?

My understanding is:
/dev/sda1 -> FAT32
/dev/sda2 -> Swap
/dev/sda3 -> ext3

Your desired mount points (fstab) should be;
/dev/sda1 /media/dos
/dev/sda2 Swap
/dev/sda3 /media/linux

**This is different then your current fstab**
> /dev/sda1 /media/sda1 vfat defaults,users,noauto 0 1
/dev/sda3 /media/sda3 ext3 defaults,users,noauto 0 1

---

### Post by djshag on 2006-08-27
I thought it was making sense.... until I realized that I don't know what to put into fstab or /media....

---

### Post by bodhi.zazen on 2006-08-27
> **djshag said:**
> ls -l /home/djshag/Desktop/ | grep linux =




ls -l /media/ | grep linux =



/home/djshag/Desktop/linux is a directory and apparently is owned by root. That will make a difference! Although..... I was using sudo to copy or move the files...

Here you have a permissions problem.

/media/linux is owned by **djshag**
> drwxr-xr-x 4 djshag djshag 4096 2000-01-01 02:45 linux

root does not have write permissions to this file/

Thus when you 
> sudo mv -v /home/djshag/Desktop/linux /media/linux
you have a permissions problem.

Try
```

chown root:djsag /media/linux #Changes ownership of /media/linux
sudo chmod 660 /media/linux #Sets rw permisions on /media/linux
sudo chown -r djshag:djshag /home/djshag/Desktop/linux/ #You should own the files in your home.

sudo umount /media/linux
mount /media/linux

mv -v /home/djshag/Desktop/linux /media/linux
```

---

### Post by djshag on 2006-08-27
Ahh crap!

/media/linux is gone!

Now /media/usbdisk and /media/usbdisk-1 are present.

All I did was change permissions (in GUI not terminal) using Nautilus to allow djshag access to the directory and added "/dev/sda1 /media/dos" and "/linux" lines to fstab


I apologize! I'm a stupid newb and I suck! Thanks for your help!

---

### Post by bodhi.zazen on 2006-08-27
> **djshag said:**
> I thought it was making sense.... until I realized that I don't know what to put into fstab or /media....

format of fstab is:
<device> <mount point> <File type> <options>

Do not worry as much about the "0 0" for just yet.

I think your fstab should have these lines:
```

/dev/sda1 /media/dos    vfat   user,noauto,rw 0 0
/dev/sda2 swap          swap   defaults 0 0
/dev/sda3 /media/linux  ext3   user,noauto,rw 0 0
```

Although it is not ideal to have swap on a removable device, unless the removable device is always present, in which case change the "noauto" to "auto" for dev/sda1 & /dev/sda3.

---

### Post by bodhi.zazen on 2006-08-27
You are changing between /media/linux and /media/usbdisk too much. Use a consistent naming scheme.

When you use /media as your mount point(s),
and change names of the mountpoints in fstab
(from /media/linux to /media/usbdevice)


/media is updated automatically,
which is why you "lost" /media/linux.

I just outlayed /media/dos and /media/linux.

---

### Post by djshag on 2006-08-27
this is now my fstab"

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/dos              vfat    defaults,users,noauto,rw 0       1
/dev/sda2	/media/swap		swap	defaults,users,noauto 0       1
/dev/sda3       /media/linux            ext3    defaults,users,noauto,rw 0      1


I don't think I was changing the /media names :-/

Now what do I need to do to get the /dos, /swap and /linux directories into /media? Do I need to edit the mtab file? 

Once again, the help is much appreciated!

---

### Post by bodhi.zazen on 2006-08-27
```
sudo mkdir /media/dos /media/linux
```

No need for a /media/swap directory

But you do need to change
> /dev/sda2 /media/swap swap defaults,users,noauto 0 1

to

```
/dev/sda2 swap          swap   defaults 0 0
```

In fstab.

Then 
```
mount -a
```

---

### Post by djshag on 2006-08-27
Success! Thanks very much!!! I think I learned at least a little through this process!

---

### Post by bodhi.zazen on 2006-08-27
My pleasure. I was a noobie once to.

Please help others as I have helped you.

---

### Post by djshag on 2006-08-27
As soon as I feel competent enough to advise, I shall! Thanks again!

---

### Post by mssever on 2006-08-27
[FONT=Georgia]*EDIT: didn't notice the next page. However, my notes about labels will simplify your life in the future. I guess the rest is now irrelevant.*[/FONT]

OK...just thought of something. Since you're dealing with removable media, the device name can change (sda, sdb, etc.) depending on what other media is present. So, you need to label your ext3 partition. Find the current device name and do ```
sudo e2label /dev/sda3 LinuxSD
``` (or /dev/sdb3 or whatever it is). Now, change the line in your fstab that begins with /dev/sda3 to 
```
LABEL=LinuxSD    /media/linux            ext3    defaults,users,noauto,rw 0      1
``` This will take care of the changing device names for that partition. I don't know if you can do the same with vfat partitions, and you can't mount swap anyway.

Next, do ```
sudo mkdir -p /media/linux
sudo mount /media/linux
cd /media/linux
touch bogus.file
``` Post any errors you get with these commands. If mount complains about /media/linux already being mounted, do ```
sudo umount /media/linux && sudo mount /media/linux
``` If you can't touch bogus.file, try it with sudo. If you don't get any errors, do an ls and you should see a file named bogus.file. If so, great. You can safely delete it and copy your files to the partition.

---

### Post by bodhi.zazen on 2006-08-27
mssever:

Thank you for the tip Re: Labels.

---

### Post by bodhi.zazen on 2006-08-27
djshag:

You understand the post I made about permissions?

root will always have permission to write/delete a file, I was using this as an example of how permissions can be at fault for your type of problem.

Did you understand the permissions I gave you on /media/dos and /media/linux?

---

### Post by djshag on 2006-08-29
I think I figured all of the permission errors out. Not sure why they were present to begin with. Doesn't really matter at this point, I'm already onto my next problem in a new thread. I'm glad I got this all figured out, but it seems the whole point of it will not happen. Linux does not want to install onto my Toshiba e400 Pocket PC. At least I learned a fair bit about how linux deals with devices.

Thanks to you both!! :D

---

