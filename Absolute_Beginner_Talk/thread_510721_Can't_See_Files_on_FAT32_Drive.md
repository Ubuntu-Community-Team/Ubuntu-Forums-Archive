---
title: "Can't See Files on FAT32 Drive"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by raywood on 2007-07-26
I have a dual-boot system.  Along with a couple of NTFS partitions, I have a FAT32 partition.  Ubuntu sees the sole working folder (i.e., not counting Recycle Bin etc.) on that FAT32 partition.  That folder is named Current.  But Ubuntu does not see any of the contents of Current, even though there are a number of files in it.

---

### Post by Foxmike on 2007-07-27
What folder is named current?  Is this: /media/Current ?  If it is the case, you do not see the content of the folder because it is not mounted.  Mounting a partition attach it to the root arborescence.

---

### Post by raywood on 2007-07-27
Thanks for your response.

First, I installed WinXP on drive C.  Using PartitionMagic, I also created an NTFS drive D for certain Windows-related files, as well as FAT32 drive E for a workspace to be shared between Windows and Ubuntu.  On drive E, I created a folder called Current.  In Ubuntu, I am able to see that folder, but not its contents.  Drive E does not appear on the list of other partitions (e.g., drive F, CD-ROM, flash drive) that I see when I use Ubuntu's default file browser to see what's available.

I am puzzled that Ubuntu seems to see drive E, insofar as it can see the Current folder; but it does not seem to see the contents of Current, nor anything else on drive E.  Drive E has no other working folders, for my purposes, but it does have the Recycle folder and Windows' System Volume Information folder.

---

### Post by Foxmike on 2007-07-27
OK.  To make things clear, Linux doesn't work with "drives" as Windows does.  It has a main arborescence starting from root (/) up in directories.  To access another partition, that partition's arborescence has to be hooked to the main (root's) arborescence, on a "mounting point".  For an example: I currently have 2 partitions to hold my files.  1 is the root and the other holds all the "home" directories.  My "home" partition is attached to the root one under /home.  What it means, is that when my "home" partition is not "mounted", i.e. not attached to the main arborescence, the /home directory still exists but it is read empty.  When the "home" partition is mounted, ie attached to the root arborescence, I see appear under the /home directory some subdirectories.  Going from a partition to another is completly transparent under Linux (or any other unix-like system).
 
Now, maybe your "current" partition is seen, but not mounted to the root arborescence, so it is unavailable for reading/writing.
 
To help you solve it out, can you post the output the terminal gives you when you tipe-in those 3 commands (you can just copy/paste the commands into a terminal and copy/paste the output it gives back here):
```
df
```
to list the mounted partition
```
cat /etc/fstab
```
to list what partitions wil be auto-mounted
and
```
ls /dev | grep "[h-s]d[a-d][1-12]"
```
to see what partitions are available to the system.

---

### Post by vanadium on 2007-07-27
You should probably post more detailed info for people to  be able to see what might be wrong. fat32 partitions should not be an issue.

Can you post the output of the following teminal commands here (open a terminal, paste the command, highlight output, right-click copy, paste here)

```

 sudo fdisk -l

```

This will list all the drives and partitions that your Ubuntu sees.

```

mount

```

This will list all partitions that are effectively mounted, so that their contents are accessible. Your partition should appear in both outputs.

If it does, then post the output of

```

ls ahl <name_of_the_moint_point_of_your_drive> <name_of_the_moint_point_of_your_drive>/Current

```

This will list *a*ll files (including hidden ones) in a *l*ong listing of the root of your drive, and of your Current folder on it. <name_of_the_moint_point_of_your_drive> is the path to the directory where your partition is mounted. Normally, this is done under /media. The second item in the output of the second command will provide you that path.

---

### Post by raywood on 2007-08-08
I think they must have fixed this in an update, or something.  I have not yet had a chance to implement the foregoing suggestions, yet I can see everything now.

---

