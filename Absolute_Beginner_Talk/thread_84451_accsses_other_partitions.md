---
title: "accsses other partitions"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2005-10-31
I just install Ubuntu on my PC . Dual boot with Win Server 2k3. (During
installation ubuntu didn’t recognize win2k3 and referred to it as win
XP).
My hard drive is like this :

C primary partition – windows server 2003 (25GB)
D logical partition  - files (20GB)
E ubuntu linux(20GB)
I also left 3 GB for swap place and a little unpartitioned space

Im using a dell dimension 2400 with a 1GB ram /pentium 4
This is my first experience of linux and everything went quite well
I realize that linux name partitions differently and I have HDA1 and HDA
5  on  my desktop which are probably my C drive and E drive but when I
click on them it says ‘you do not have permission to view these files’ .
I’m the only user and have admin rights.
I would like to access my files on drive D
So my question is :how do I view other partitions with linux?
thanks

---

### Post by seshomaru samma on 2005-10-31
actually , i just found what i wanted so never mind...:) 
system>administration>disks>partitions (if other beginers are wondering..)

---

### Post by linbetwin on 2005-10-31
It won't work from System > Administration > Disks. In my experience, you won't have permission to view files. If you get it to work from there, tell me how you did it.

---

### Post by Hallavej on 2005-10-31
[QUOTE=linbetwin]It won't work from System > Administration > Disks. In my experience, you won't have permission to view files. If you get it to work from there, tell me how you did it.[/QUOTE]
If  your windows partions is in /dev/hda1 and you want to mount in in eg. /media/windows do:
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
Note. You can view but not write to that partition.
If you want it mounted when starting ubuntu then ad:
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
to /etc/fstab

---

### Post by seshomaru samma on 2005-11-01
[QUOTE=linbetwin]It won't work from System > Administration > Disks. In my experience, you won't have permission to view files. If you get it to work from there, tell me how you did it.[/QUOTE]

You are right. I have spoken too fast. It does let me view the files but i cannot change them or move them or use them in any way.Interestingly from the windows side -the linux partition doesnt exist.

---

### Post by Eelke81 on 2005-11-01
> If your windows partions is in /dev/hda1 and you want to mount in in eg. /media/windows do:
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
Note. You can view but not write to that partition.
If you want it mounted when starting ubuntu then ad:
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
to /etc/fstab

I have the same problem as seshomaru, I tried the solution posted by Hallavej, but it didn't work. When I type the command in the console I get this error message:

**mount: mountpoint /media/windows/ doesn't exist** (translated, original message is in Dutch)

I also tried to figure out in which file the rights for accessing partitions is stored in /etc/ but couldn't find anything. Perhaps somebody knows where I can find it, so I can change the file in a way that you don't have to be root to access the windows partition.

---

### Post by Hallavej on 2005-11-01
[QUOTE=Eelke81]I have the same problem as seshomaru, I tried the solution posted by Hallavej, but it didn't work. When I type the command in the console I get this error message:

**mount: mountpoint /media/windows/ doesn't exist** (translated, original message is in Dutch)

I also tried to figure out in which file the rights for accessing partitions is stored in /etc/ but couldn't find anything. Perhaps somebody knows where I can find it, so I can change the file in a way that you don't have to be root to access the windows partition.[/QUOTE]

You have to mount to an existing folder. If you want to mount it in /media/windows then make the folder first:
sudo mkdir /media/windows
and then try the mount command again.

---

### Post by Nomad_01 on 2005-11-01
Windows doesn't know how to make sense of ext3 partitions (like what your linux install is on.) Linux can read NTFS but not write to it. So you can view what's going on with your windows partitions from linux but not really do anything. 

If you want to share files between Windows and Linux (i.e. Music, Video), then you'll need to make another partition that is FAT32. Both windows and linux can read, write, and execute from a FAT32 part.

Once you have that set up you can follow the mounting stuff Hallavej posted but apply it to your new FAT32 partition.

---

