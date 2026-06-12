---
title: "Lost access to external hdd"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by SteveHoffmanUK on 2006-07-21
I have an 80GB external hard disk attached via USB connection. Have been doing my backup security dumps to it and writing other files to it as well with no problems.

Today I boot Ubuntu 6.06 and can't access it and get this message from Nautilus:
```
Unable to mount the selected volume.
```

Then click on "Show more details" and get this:

```
error: directory /media/fhd-2pro is not empty
error: could not execute pmount
```

Anyone know what might cause this to happen?

More importantly, what do I have to do to correct the problem?

---

### Post by trent dillman on 2006-07-21
type 'mount' in a terminal, and see what that says. Also try rebooting with the drive plugged.

---

### Post by mssever on 2006-07-21
Check /media/fhd-2pro to see if it does have something in it.
```
ls -A /media/fhd-2pro
```
If there is anything in it, move it somewhere else and try mounting again. It may be that you thought that you were writing to the drive sometime when in fact it wasn't mounted.

---

### Post by Saphira on 2006-07-21
I found this, hope it helps. I'll keep looking...

 Question  Re: Will not mount NTFS drive
I too am having this problem.

On a newly installed 6.06 all my windows partitions are not accessible with the error:-

Unable to mount the selected volume.
error: device /dev/sda2 is not removable
error: could not execute pmount


(This did work on 5.10 which I had on for about a day before realising there was 6.06)

I have tried mounting from the command line using:-
"sudo mount /dev/sdb1 /mnt/data_drive"

Which works, but then the mount point is only accessable from the command line when using "sudo su".

Is their a way to mount the partition in a way so that I can browse and use the partition with the file browser gui?

Regards,
Daniel Ellis.
Last edited by danellisuk : 1 Week Ago at 08:32 AM.
Reply With Quote

---

### Post by SteveHoffmanUK on 2006-07-21
Mssever: thanks for the suggestions. Taking them in reverse order, I show these terminal responses:

```
steve@steve-desktop:~$ ls -A /media/fhd-2pro
ls: /media/fhd-2pro: No such file or directory
```

```
steve@steve-desktop:~$ mount fhd-2pro
mount: can't find fhd-2pro in /etc/fstab or /etc/mtab
```

So then I thought I should see what is in these two directories, but Nautilus doesn't show any such directories (I thought everyone has an fstab?). Then I tried the terminal:

```
steve@steve-desktop:~$ cd /etc/fstab
bash: cd: /etc/fstab: Not a directory
```

...which seems to confirm Nautilus, if I got the command right.

What's going on?

Finally, I have already rebooted with it plugged in -- no change:(

---

### Post by mssever on 2006-07-21
Your problem with fstab is that /etc/fstab is a file, not a directory, so you can't cd to it. But you can view it or edit it:
```
#view fstab
less /etc/fstab

#edit fstab
sudo vi /etc/fstab # substitute your favorite editor for vi
```

That said, I don't think fstab will be helpful to you. Ubuntu's automounter doesn't use it.

I've recently been having difficulty accessing my USB HD, and what made it work for me was cycling the power on the drive, which apparently caused the sytem to re-detect it. I don't know what causes these problems...mine cropped up after a power outage (but I was surge-protected).

Oh, if the above doesn't work for you, do an [FONT="Courier New"]ls /media[/FONT] and see if it's possible that Ubuntu renamed your disk. I can't see how that could happen, but it's worth a try, anyway.

---

### Post by mssever on 2006-07-21
I've done a little more checking and found that USB drives are by default handled by pmount. Typing [FONT="Courier New"]man pmount[/FONT] will give you documentation.

If you want to bypass pmount, you can add the drive to /etc/fstab like any other partition. Then you should be able to acces it like normal. I haven't tried it, but I think that adding the disk to /etc/fstab will have the side effect of disabling automounting the disk whenever you plug it in, so you'll probably have to manually mount and unmount it.

One other thing: if you use /etc/fstab, it would be best if you refer to the partition by label, rather than name, in case the USB system assign a different name at some time. If your disk is formatted as ext2/3, you can use [FONT="Courier New"]e2label /path/to/device[/FONT] (likely /dev/sda1) to find the label. But it's probably fhd2-pro.
```
#Sample fstab line--change to match your specifics
LABEL=fhd2-pro  /media/fhd2-pro  ext3    defaults  0  2
```

---

### Post by SteveHoffmanUK on 2006-07-21
Mssever: thanks again for your help.

Your comment about power rang all sorts of bells, because we had a power failure while I was online, although I can't remember whether I had successfully accessed it after that. I was not surge protected but am now.

Anyway, I tried powering down the device, rebooting with it unplugged, then plugging it back in and rebooting, but it hasn't corrected the problem. Before I edit fstab, I believe and hope that it's fat32, not ext3. How can I verify that? I want to be able to write to it from WinXP in a virtual machine (though haven't got that far yet!).

Can you suggest a fstab line to add for a fat file format?

---

### Post by mssever on 2006-07-21
If you've accessed it with Windows, then it's either fat32 or ntfs. The default for most drives is fat32. If that's the case, replace ext3 in /etc/fstab eith vfat. If it's NTFS, then use ntfs. But be warned: writing to NTFS partitions in Linux is unsafe. Also, you might have to replace the LABEL=... portion with the actual device name (probably /dev/sda1).

In Windows, if you look at the drie properties, it'll tell you the format. In Ubuntu, you can go to System > Administration > Disks > Partitions to see the format. But if Ubuntu isn't seeing your drive, then it might not show you the format. You can set the filesystem type to auto (instead of vfat, ext3, etc.) and Ubuntu will try to guess the type. If it's a fat32 FS, it might guess fat16 (limiting you to 8.3 filenames), but then you would know that it really is fat32/vfat.

As another option, you could reformat your drive as ext3 (which is a superior filesystem and supports Unix/Linux permissions) and install a program--I forget the name--that enables Windows to use ext2 filesystems. Ext3 is fully backwards-compatible with ext2.

---

### Post by SteveHoffmanUK on 2006-07-22
mssever:

Thanks again for helping me through this.

OK. I plugged my external hdd into my wiefe's XP system (1) to determine the format and (2) to make sure it hadn't been fried by a power failure when running unprotected.

XP says it's FAT32 and all the files are there, so I am confident that we're not talking about a hardware problem. 

I followed your instructions. As you surmised, it wasn't in my fstab, so I then edited fstab as you suggested, and it now shows:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
LABEL=fhd2-pro  /media/fhd2-pro  vfat    defaults  0  2
/etc/fstab (END)
```

Then I went to Nautilus and asked it to mount the volume, but I still get the same error message:
```
Unable to mount the selected volume
error: directory /media/fhd-2pro is not empty
error: could not execute pmount
```

It appears that adding it to fstab hasn't bypassed pmount; well, maybe I am assuming too much. Let's just say that it doesn't seem to have solved my problem, but you may spot something I did wrong in this.

---

### Post by mssever on 2006-07-22
First, does the directory /media/fhd2-pro exist? Is it empty? That's the prerequisite here.

Next, I'm asuming that the line /etf/fstab (END) isn't actually in your fstab. If it is, delete it or comment it out (prefix it with #). Also, I neglected to mention another change you need to make to your fstab since we're dealing with a vfat drive. Change "defaults" to "defaults,users" (with no space after the comma). This will allow normal users (you) to access the files on the partition.

Now, let's try mounting from the command line until we get it working that way. The commands to use are (everything after the # is a comment and can be omitted):
```
mount /media/fhd2-pro # to mount
umount /media/fhd2-pro # to unmount
```

If this doesn't work, change the LABEL=... part to /dev/sda1.

If you can mount and unmount from the command line but not from Nautilus, then you can make a button to manually mount/unmount it.
Try something like this:
```
#!/bin/bash

DRIVE=/media/fhd2-pro
MOUNTED=`mount | grep $DRIVE`

if [ -z "$MOUNTED" ]; then
        mount $DRIVE
else
        umount $DRIVE
fi

```
Paste this into a file and save it. Then do [FONT="Courier New"]chmod 755 /path/to/the/file[/FONT]. Now, right click on the panel and choose "Add to panel..." Click "Custom Application Launcher" and Give it a name (Mount USB HD or something). In the command field, type the full path to the file you just created. Check the "Run in terminal" box and hit OK. Now you have a button that will mount the drive if it isn't mounted and vice versa.

If you wany to be able to pull the plug on your drive without unmounting it, you can add "sync" to the options in /etc/fstab. Doing so will degrade performance, however.

---

### Post by SteveHoffmanUK on 2006-07-22
mssever wrote:
> First, does the directory /media/fhd2-pro exist? Is it empty? That's the prerequisite here.
Yes, but, interestingly, Nautilus shows it with a red flag, and under its Properties, says its "unreadable". Permissions are dimmed out. Sorry to rely on Nautilus, but am not a terminal whizz (although getting to be more so every day).

> Next, I'm asuming that the line /etf/fstab (END) isn't actually in your fstab. If it is, delete it or comment it out (prefix it with #).

No it isn't there. Sorry, I must have copied that from my edit program.

> Also, I neglected to mention another change you need to make to your fstab since we're dealing with a vfat drive. Change "defaults" to "defaults,users" (with no space after the comma). This will allow normal users (you) to access the files on the partition.

OK, did that. Here is what fstab looks like now:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
LABEL=fhd2-pro  /media/fhd2-pro  vfat    defaults,users  0  2

```

> Now, let's try mounting from the command line until we get it working that way. The commands to use are (everything after the # is a comment and can be omitted):

OK, here goes ...
```
steve@steve-desktop:~$ mount /media/fhd2-pro
mount: mount point /media/fhd2-pro does not exist
steve@steve-desktop:~$
```

I suspect this has something to do with the first thing we discovered -- that /media/fhd2-pro is "unreadable", but you know more than I about these things. Thanks for your continuing to follow this and help. I'm sure we'll get there in the end!

---

### Post by mssever on 2006-07-22
OK. I'm guessing about the permisions here. If you paste the result of ```
ls -l /media
``` it will tell me what the situation is for sure. I'm sorry that I don't know Nautilus well enough to help you in that way. When I first learned Linux, Nautilus wasn't a realistic option so I was forced to learn the command line. Now, I usually find it to be the fastest way to accomplish a task. Of course, it takes quite a bit of time to become proficient with the command line.

Without knowing the permissions of /media/fhd-2pro, here are some things that I'm guessing might help. Try them in order, trying to mount after each one.
```
sudo mkdir -p /media/fhd-2pro # We're making sure that the directory is really there and that Nautilus
               # isn't using stale data

sudo chmod 755 /media/fhd-2pro # We're making sure that the permissions are set to a reasonable value.
               # Mounting a disk overrides these permissions, but still, it's worth checking

sudo chown steve /media/fhd2-pro # Assuming that steve is your username... We're making you the owner of
               # the directory. Don't do this unless necessary.
```

---

### Post by SteveHoffmanUK on 2006-07-22
OK, here's what we get from the first entry:
```
steve@steve-desktop:~$ ls -l /media
total 16
lrwxrwxrwx 1 root root    6 2006-07-12 08:20 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-07-12 08:20 cdrom0
drwxr-xr-x 2 root root 4096 2006-07-22 22:44 fhd-2pro
drwx------ 3 root root 4096 2006-07-21 09:02 FHD-2PRO
drwxr-xr-x 2 root root 4096 2006-07-19 10:56 floppy
steve@steve-desktop:~$
```

```
sudo mkdir -p /media/fhd-2pro # We're making sure that the directory is really there and that Nautilus
               # isn't using stale data
```
Tried mount, but same error message as before

```
sudo chmod 755 /media/fhd-2pro # We're making sure that the permissions are set to a reasonable value.
               # Mounting a disk overrides these permissions, but still, it's worth checking
```
Tried mount, but same error message as before

```
sudo chown steve /media/fhd2-pro # Assuming that steve is your username... We're making you the owner of
               # the directory. Don't do this unless necessary.
```
Tried mount, but same error message as before

Does this shed any more light?
Again, thanks for pursuing this for me.

---

### Post by mssever on 2006-07-22
> **SteveHoffmanUK said:**
> OK, here's what we get from the first entry:
```
[FONT="Courier New"]steve@steve-desktop:~$ ls -l /media
total 16
lrwxrwxrwx 1 root root    6 2006-07-12 08:20 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-07-12 08:20 cdrom0
drwxr-xr-x 2 root root 4096 2006-07-22 22:44 fhd-2pro
[COLOR="Red"]drwx------ 3 root root 4096 2006-07-21 09:02 FHD-2PRO[/COLOR]
drwxr-xr-x 2 root root 4096 2006-07-19 10:56 floppy
steve@steve-desktop:~$[/FONT]
```

The capitalized entry (highlighted) is interesting. As you may know, Linux is case-sensitive, so /media/fhd2-pro and /media/FHD2-PRO are two different directories. Try changing everything to refer to the capitalized version, including the label in fstab. You might want to make incremental changes here, testing between them. Of course, your mount command would need to change, as well.

There's also a remote possibility that there could be a collision between directory names that differ only in case due to case-insensitivity in the FAT32 filesystem. You can test for it by renaming or deleting one or the other of the directories.

Another remote possibility is that something has gone wrong with your computer's USB hardware. If you plug in another USB drive, does it work? A USB flash drive should work fine, and most digital cameras are USB flash drives. (You can actually store arbitrary data on them by mounting them as drives.)

As I write this, I'm growing increasingly skeptical of my answer, because it doesn't seem to address your error message. However, right now I can't think of anything else to try.

---

### Post by SteveHoffmanUK on 2006-07-22
I tried changing everything to the capitalised version, including the LABEL, the fstab and media entries, but mount still didn't work. Also changed everything to lower case, but still no luck.

I have a newly-purchased stick memory plugged into the same USB controller, and it doesn't work either, although Nautilus "sees" it OK. Hmm, maybe significant.

I then tried your suggestion and plugged in my digital camera into one of the rear USB ports (replacing the stick memory) and it was immediately recognised; also tried it in one of the front ports, same thing happened.

Then I removed the camera, put the memory stick back in and, more or less on a whim, in Nautilus right-clicked the FHD-2PRO icon, then 'Mount this volume', and it mounted! I can now read its contents and they look fine.

/etc/fstab looks like this:
```
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
LABEL=fhd2-pro  /media/fhd2-pro  vfat    defaults,users  0  2
```

and /media looks like this:
```
steve@steve-desktop:~$ ls -l /media
total 44
lrwxrwxrwx 1 root  root      6 2006-07-12 08:20 cdrom -> cdrom0
drwxr-xr-x 2 root  root   4096 2006-07-12 08:20 cdrom0
drwxr-xr-x 2 root  root   4096 2006-07-22 22:44 fhd-2pro
drwx------ 7 steve steve 32768 1970-01-01 01:00 FHD-2PRO
drwxr-xr-x 2 root  root   4096 2006-07-19 10:56 floppy

```

Go figure, as they say.

I doubt that this will make any more sense to you than it does for me, but you may see something in it.

So I now have my hdd back, without understanding exactly how I did it. I am very grateful for your guidance and support.

Now I have to get the stick memory working, but that's for another day.:)

---

### Post by mssever on 2006-07-22
I wonder if you've got a bad USB port or controller. Maybe it got fried in connection with your power outage? It's possible that it could only be partially bad, which could give us these strange problems. At any rate, I'm glad you got it working. Don't touch anything! :)

---

