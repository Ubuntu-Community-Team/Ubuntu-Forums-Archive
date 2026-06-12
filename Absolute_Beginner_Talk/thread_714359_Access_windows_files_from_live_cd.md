---
title: "Access windows files from live cd"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Skivache on 2008-03-03
A friend of mine is having trouble with windows (won't boot) and needs to use the Ubuntu Live CD to recover his files.  There is an HP-PAVILLION folder listed in Computer, but he recieves a "cannot mount volume" error when trying to open it.

If that is not the hard drive, can someone please tell me how to access the hard drive of a windows machine from the Live CD?  If it is, how can the files be accessed?

---

### Post by santiagoward2000 on 2008-03-03
> **Skivache said:**
> A friend of mine is having trouble with windows (won't boot) and needs to use the Ubuntu Live CD to recover his files.  There is an HP-PAVILLION folder listed in Computer, but he recieves a "cannot mount volume" error when trying to open it.

If that is not the hard drive, can someone please tell me how to access the hard drive of a windows machine from the Live CD?  If it is, how can the files be accessed?

Hi!
Try opening a console and type:
```
gksudo nautilus
```
and see if you can mount it then.
Good luck!

---

### Post by Skivache on 2008-03-03
> **santiagoward2000 said:**
> Hi!
Try opening a console and type:
```
gksudo nautilus
```
and see if you can mount it then.
Good luck!

What will that command do, and how will he be able to use the drive then?

If I am correct, gksudo has to do with graphic interfaces...

---

### Post by Rolcol on 2008-03-03
The reason it won't mount, I think, is because the hard drive locked itself from an improper shutdown.

---

### Post by santiagoward2000 on 2008-03-03
> **Skivache said:**
> What will that command do, and how will he be able to use the drive then?

If I am correct, gksudo has to do with graphic interfaces...

The command will open Nautilus (the file manager) with root privileges. That means you can delete or modify things you can't with normal privileges. It's not exactly about graphic interfaces. The command that does that on command line applications is **sudo**, while **gksudo** is for applications with graphical interface.
Cheers!

---

### Post by glennric on 2008-03-03
Post the output of 
```
sudo fdisk -l
```
Is the HP-PAVILLION thing a folder or partition?  How are you seeing it?

---

### Post by mikewhatever on 2008-03-03
> **Rolcol said:**
> The reason it won't mount, I think, is because the hard drive locked itself from an improper shutdown.

+1. Partitions often would not mount after an improper shut down. I really doubt gksudo nautilus would do anything to repair that, since the two seem unrelated.
Skivache, perhaps your friend should use photorec or testdisk instead of Ubuntu live.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by glennric on 2008-03-03
You can still mount NTFS volumes after improper shutdowns if needed.  If you attempt to mount a NTFS volume that is improperly shut down it will tell you the command you need.  I don't think that is the problem here.

---

### Post by Skivache on 2008-03-03
2 more related questions:
I ran the command on my Ubuntu partition and it required the root password, what would be the password on the live cd?
Then, where would he access the files on the hard drive, in the HP-PAVILLION folder or the /dav/hda1 folder?

As for the output from the sudo fdisk -l command, he said it lists:
/dev/hda1
/dev/hda2
both are NTFS

---

### Post by glennric on 2008-03-03
On the live cd there is no password needed to run sudo commands.  You still need to put sudo in front of a command to get root access, but there is no password requested.  
To mount the NTFS partitions you will have to first load the fuse module with
```
sudo modprobe fuse
```
Then you will have to create a directory somewhere to mount the partitions for example
```
mkdir ~/hda1 ~/hda2
```
Then type 
```
sudo mount -t ntfs /dev/hda? ~/hda?
```

I still am not sure what you are talking about with the HP-PAVILLION thing?  If it is a folder you wouldn't need to mount it.  Only partitions need to be mounted and those are the things that show up when you do the fdisk thing.

---

### Post by Skivache on 2008-03-03
> **glennric said:**
> On the live cd there is no password needed to run sudo commands.  You still need to put sudo in front of a command to get root access, but there is no password requested.  
To mount the NTFS partitions you will have to first load the fuse module with
```
sudo modprobe fuse
```
Then you will have to create a directory somewhere to mount the partitions for example
```
mkdir ~/hda1 ~/hda2
```
Then type 
```
sudo mount -t ntfs /dev/hda? ~/hda?
```

I still am not sure what you are talking about with the HP-PAVILLION thing?  If it is a folder you wouldn't need to mount it.  Only partitions need to be mounted and those are the things that show up when you do the fdisk thing.

The HP-PAVILLION is listed under Computer.
Could you please explain more about creating a directory for the partitions.
In this command:
```
sudo mount -t ntfs /dev/hda? ~/hda?
```
Should the ? be replaced with a 1 or 2 or left as a question mark?

---

### Post by glennric on 2008-03-03
Yeah, sorry.   I meant to comment on that.  Replace the question mark with 1 and then 2 (two seperate commands) to mount both partitions.

---

### Post by glennric on 2008-03-03
Ok, then HP-PAVILLION is a mounted partition.  It is one of the /dev/hda?'s.  You can access it by typing
"gksu nautilus computer:///"

---

### Post by Skivache on 2008-03-03
Where would this create a directory in?
```
hen you will have to create a directory somewhere to mount the partitions for example
Code:

mkdir ~/hda1 ~/hda2


```

---

### Post by glennric on 2008-03-03
It will create the directory in the live cd users home directory.  To go there type "cd"

---

