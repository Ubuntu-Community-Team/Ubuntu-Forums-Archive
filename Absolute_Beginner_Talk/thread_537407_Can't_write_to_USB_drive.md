---
title: "Can't write to USB drive"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by mattgw on 2007-08-28
I have a SanDisk Cruzer and was able to put files on it a week ago, but am unable to now.  The volume is now being mounted as read only.  It is FAT.  I have searched and been unable to find a solution.

Any help would be appreciated.  Complete Ubuntu noob here.

---

### Post by uclalinux on 2007-08-29
you can try to change the write and read permissions when the usb drive is in, type the following into the terminal

sudo chmod 777 /media/"device name"

or

 you can unmount then remounting it to a new folder with different read and write permissions 
see [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)  , will have lots of answers for you
 

 or 

you could try to reformat the usb thumb drive, just take to files off of it and try to reformat it, use the gparted (get gparted using synaptic package manager)

 or

 using the terminal and following this [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4) that web page dose it for a hard drive, but you do the same thjing,  just make sure u know the path to the usb stick 
You can find it using "df -h" command

---

### Post by vanadium on 2007-08-29
I find it very strange that you have such a behaviour, especially with a fat drive. For the sake of having a clue, can you follow the instructions I give here and post the output here? I will be very specific as this is the beginner's forum. First make sure the USB is not plugged.

1. Open a command line (Applications, Accessories, Terminal)
2. Type
```

ls -l /media

```
Post the outcome here.
3. Plug in your USB
Wait a few seconds, then reissue the same command, Post the outcome here.

This is what I have, inserting my Sandisk Cruzer.

```

:~$ ls -l /media
total 4
lrwxrwxrwx 1 root root    6 2007-04-06 21:34 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-04-06 21:34 cdrom0
:~$ ls -l /media
total 20
lrwxrwxrwx 1 root  root     6 2007-04-06 21:34 cdrom -> cdrom0
drwxr-xr-x 2 root  root  4096 2007-04-06 21:34 cdrom0
drwx------ 7 vanadium root 16384 1970-01-01 01:00 USB
ft

```

The second time I issued the command, Ubuntu automatically created the mount point for my USB. A moint point is an empty directory, and you see it listed in the third entry. The name is USB, thus the mount point is /media/USB. Automatically, I have been set as the user of the device, and the permissions show that I can do all (read, write, execute: rwx) while the group and others have no rights at all.

My further suggestions will follow after you put your output here.

---

### Post by mattgw on 2007-08-29
Output the first time:

total 8
lrwxrwxrwx 1 root root    6 2007-07-13 07:23 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-07-13 07:23 cdrom0
drwxr-xr-x 2 root root 4096 2007-08-28 21:32 sda


Second:

total 24
lrwxrwxrwx 1 root root     6 2007-07-13 07:23 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2007-07-13 07:23 cdrom0
drwx------ 3 matt root 16384 1969-12-31 19:00 disk
drwxr-xr-x 2 root root  4096 2007-08-28 21:32 sda

I am still unable to write or edit files on the flash drive.  I haven't tried any of the instructions from the first post, though.

Also, could you explain what the commands mean - I am getting very good at copy-pasting commands into the terminal, but am only just beginning to figure out what they really do.  Command line doesn't frighten me, but I don't understand it yet.

---

### Post by mattgw on 2007-08-29
From what Vanadium said, and what my output was, it appears that I have "read write execute" privileges, but I still can't copy files to, or delete files from, the flash drive.

Tried the chmod command as well - no dice.

When attempting to delete a file in the terminal it gives the following (with x.x being the file):
> rm: cannot remove `x.x': Read-only file system

Any help is appreciated.

---

### Post by vanadium on 2007-08-29
There is not much more I can add. Your output shows that your USB is being mounted in a regular way, and that indeed you as user have all rights. Is your disk really fat32 formatted? Please post the output of the command "mount". The line containing "disk" will do (you can type"mount | grep disk". Chances are we'll discover your stick is ntfs formatted.

The command "ls -l /media" shows a directory listing of your /media directory. The -l option requiests a "long" listing, i.e. a listing that includes some details such as permissions and size of the files and directories.

---

### Post by redfox1160 on 2007-08-29
my flash drive doesnt even show up

---

### Post by mattgw on 2007-08-29
output of the mount command:
```

/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
```

---

### Post by vanadium on 2007-08-30
Unfortunately, there is nothing I can add. The behaviour you report is exactly the same as on my system, yet I can write (I explicitly tried to make sure), and you can't. I hope this is not a new bug creeping up in Feisty. There are many threads popping up with USB drive related issues, for example here [http://ubuntuforums.org/showthread.php?t=439037](http://ubuntuforums.org/showthread.php?t=439037)

---

### Post by mattgw on 2007-08-30
To add a wrinkle to it, if I try to write to it (or delete a file) right as it is mounting, it will let me.  Then a second later everything (including the files I just dropped on it) are locked.

As long as I don't attempt to delete a file, I can write as much to it as I want, but only have a few second window to delete a file.  Then, after I try and am told it is write-protected, it locks the whole drive down.

---

### Post by notwen on 2007-08-30
Have you tried changing permissions for the USB drive in Nautilus launched by root?

> gksudo nautius

I've had this happen on multiple occasions and I have to go in and change the permissions ever so often, perhaps when it is not ejected properly from a windows machine?  It's always fixable by changing the permissions for me, wish I knew what might be causing it, although it doesn't happen too often, but often enough for me not to be surprised by it anymore.  Good luck w/ your situation. =]

---

### Post by por100pre1 on 2007-08-30
This may sound dumb but, have you checked if the drive is full with a hidden trash folder? :-k

---

### Post by mattgw on 2007-08-30
> **notwen said:**
> Have you tried changing permissions for the USB drive in Nautilus launched by root?

Doing the gksudo commmand, and then trying to delete a file (using rm in the terminal) I was able to delete one file, but then when I tried the second it said it was read-only (although the permissions still showed "rwx" - is there something that would delete the given permissions and then remount with new ones?)

No hidden trash folder.

I hadn't done it before, but just looked at the permissions under preferences in the file browser and it says it is all read only and won't let me change them.  It appears that the "ls -l" command and the GUI file browser show two different permissions.

---

### Post by vanadium on 2007-08-30
fat does not support permissions. The permissions for the whole disc are these of the mount point. There is something else I am thinking of. Do check the file system: perhaps there is an error in the file system causing this behaviour. In Windows, this used to be chkdsk. In Linux there is dosfsck (or fsck.msdos). The command is 

dosfsck /dev/sdb1

Post the output here, if any. How full is the usb? (df | grep sdb1)?

---

### Post by mattgw on 2007-08-30
```
dosfsck /dev/sdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
**list of files on disk**
Reclaimed 526 unused clusters (8617984 bytes).
Leaving file system unchanged.
/dev/sdb1: 34 files, 1/62283 clusters
```

and

```
df | grep sdb1
/dev/sdb1               996528      8432    988096   1% /media/disk
```


Is there a way, in linux, to just reformat the disk and start over?  If so I could just reformat it in FAT and try from there.

---

### Post by vanadium on 2007-08-31
It is quite clear that your disk is 1) full and 2) damaged.

OPTION 1: Repair

* restore the file system running "dosfsck -a /dev/sdb1"

The -a option will automatically repair the errors to make the filesystem consistent again. Lost clusters will be converted to files and keep taking space. Perhaps also space will be freed. After running the disk check, run "df -h /dev/sdb1" again to check the free space. Chances are it will already be more than 1% (I added the -h swicht, means "human readable) to have sizes displayed in kB, MB). After that, clean up the drive, deleting what isn't necessary.

OPTION 2. Reformat altogether

sudo umount /dev/sdb1
sudo mkfs -t vfat /dev/sda1

Warning: You are probably aware that reformatting destroys all data on the disk !

---

### Post by mattgw on 2007-08-31
Many thanks Vanadium.  Repaired and the disk works fine now.

Any ideas on what could have corrupted the disk?  (I only used it once, to put the files on it that I was attempting to delete/replace)

What does "dosfsck" do? (besides work wonders on a USB drive)

---

### Post by vanadium on 2007-09-01
Nice that we found the solution! Would you please add "[SOLVED]" to the title of your thread?

A disk can be corrupted by removing it before the writing has finished (or by a power shutdown). You had "lost clusters", clusters that are marked in the file system as occupied, but there is no entry in the directory that points to them. Although from the directory it appears that there is plenty of free space (only 1% used), the system can't find free clusters anymore while trying to write a file.

dosfsck does check the file system and if errors (inconsistencies) exist, repairs them

---

### Post by mattgw on 2007-09-01
Done, and many thanks.

Of course, now my LCD screen on my laptop went out, and I am playing the waiting game with Best Buy as they repair it (under warranty).

---

### Post by MrWookie on 2007-09-05
So, I'm having a very similar problem to this.  I'm running Ubuntu 7.04.  I can mount my USB flash drive, but I can't write to it.  I get a permission denied error.  I can't chown it, and chmod does nothing.  dosfsck returns no errors.  I formatted it with mkfs -t vfat, but it still doesn't work.  I'd be tempted to throw the thing out if it wasn't for the fact that it works fine on my windows laptop.

---

