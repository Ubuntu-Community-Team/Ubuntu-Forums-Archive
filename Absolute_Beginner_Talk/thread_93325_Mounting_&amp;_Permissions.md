---
title: "Mounting &amp; Permissions"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by somody on 2005-11-21
Yay!  I finally got my Ubuntu up and running (previous versions didn't support my graphics card).

I followed steps to mount my WINDOWS partition and my DOCUMENTS partition (both NTFS), and I set their mount location to my Desktop.

Now I have a few problems:

1.  My DOCUMENTS partition isn't "startable" for some reason, though my WINDOWS one is (I might add the DOCUMENTS one is on a completely fully partitioned seperate 6GB drive :))

2.  When I open my WINDOWS folder, it says "I don't have necessary permissions" and puts a red "X" in the bottom left of the icon on the Desktop.  I tried logging in as "root" from the Login Screen, but it says I can't log in with root from there.

What should I do?

---

### Post by somody on 2005-11-21
[COLOR="Red"]This is urgent...BUMP![/COLOR]

---

### Post by blastus on 2005-11-21
If /dev/hda1 is your NTFS partition, add this line to /etc/fstab...
```
/dev/hda1  /media/hda1  ntfs  noauto,users,exec,ro,umask=0222 0  0
```
To mount it:
```
sudo mount /media/hda1
```
To unmount it:
```
sudo umount /media/hda1
```
To find out if it is mounted:
```
mount -l
```

---

### Post by somody on 2005-11-21
How do I add to the fstab?  When I open in text editor, it says 'read only'!

---

### Post by aysiu on 2005-11-21
Follow these directions:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

I hope you realize, though, that NTFS is strictly read-only. Do not modify the NTFS files or add files or delete them.

---

### Post by somody on 2005-11-21
Why?  Is there anyway to make them editable like in Windows?

---

### Post by LuxoDave on 2005-11-21
[QUOTE=somody]Why?  Is there anyway to make them editable like in Windows?[/QUOTE]


If you want to move files back and forth between windows and linux you need to make a FAT32 partition on your hard drive. You can use qtparted to do this. Then you can use the link aysiu provided above, it worked for me.

---

### Post by somody on 2005-11-22
Thanks...I'm sure this will work, but everytime I try to do anything (even dragging something to the trash, or backing up /etc/fstab), it says that I don't have permission...how can I fix this?

---

### Post by aysiu on 2005-11-22
Okay. 

1. Give up on whatever you were trying to do before. It's not working, clearly.

2. Follow the instructions I linked to before. If you don't know what your Windows partition is called (the instructions assume it's /dev/hda1), type this command in a terminal ```
sudo fdisk -l
``` If you don't know what this "terminal" is that you type commands into, go to Applications > Accessories > Terminal.

3. Once you change the /etc/fstab file, the changes won't take place immediately. You either have to reboot the computer (I highly recommend this method--though, it takes longer, of course) or type this command in ```
sudo mount -a
```

---

### Post by somody on 2005-11-22
I don't know if you understood, but I know how to do this already.

The problem is as follows now:

1.  I can't edit /etc/fstab because it says that I have insufficient privileges.
2.  How can I convert my NTFS partition to FAT32 partition without losing data, or having to temporarily move data (I have no more room :()?

---

### Post by LuxoDave on 2005-11-22
[QUOTE=somody]I don't know if you understood, but I know how to do this already.

The problem is as follows now:

1.  I can't edit /etc/fstab because it says that I have insufficient privileges.
2.  How can I convert my NTFS partition to FAT32 partition without losing data, or having to temporarily move data (I have no more room :()?[/QUOTE]


1. sudo gedit /etc/fstab

2. You will have to back up any data someplace. Maybe burn to cd? But you can shrink the NTFS part of the hard drive (after doing a defrag) with out losing any info. with QTParted or another drive partition tool.

---

### Post by joshuaxls on 2005-11-22
To edit /etc/fstab so that you can write to it, open a terminal and type:

```
sudo gedit /etc/fstab
```

As for turning NTFS to FAT32, I know that PartitionMagic can do it. I'm not sure that there's an easy (or free) way, however.

---

### Post by somody on 2005-11-22
Thank guys!  In QTParted, when I right-click the partition to resize, "Resize Partition" is grayed out :(.

---

### Post by aysiu on 2005-11-22
[QUOTE=somody]Thank guys!  In QTParted, when I right-click the partition to resize, "Resize Partition" is grayed out :(.[/QUOTE] You have to make sure the partitions you're resizing are not mounted.

---

### Post by somody on 2005-11-22
OK, tried that, still grayed...

---

### Post by somody on 2005-11-22
Bump...

---

### Post by somody on 2005-11-22
Bump.  This is extremely urgent!  I have homework :p!

---

### Post by narcolept on 2005-11-22
You have unmounted the partitions by typing 

```
sudo umount /dev/devicename
```

and then restarted QTParted?

---

### Post by somody on 2005-11-22
Yup!

---

### Post by somody on 2005-11-23
Sorry for DP, but, does anybody know what I should do?

---

### Post by blastus on 2005-11-23
[quote=somody]How can I convert my NTFS partition to FAT32 partition without losing data, or having to temporarily move data (I have no more room )?[/quote]

Do what I do, buy a second hard drive. That way you can easily backup everything on the other drive and re-partition the first drive (and re-install everything from scratch again) without the hassle of burning off everything to CD/DVD. It's not a good idea to convert file systems or re-partition your hard drive without backing everything up--otherwise you are just waiting for a disaster to happen. 

This is one reason why having a second drive is extremely handy. A second drive is also useful for instantly backing up whatever you are working on--with the idea that eventually you'll burn off the important stuff to CD/DVD. In this way I always have a backup of everything important and I don't have to burn a CD/DVD every other day--having a second drive is well worth the cost.

I would not use FAT32 for anything except for temporarily moving data between Windows and Linux in both directions. NTFS is more efficient, more robust, and more reliable than FAT32 so if you are using Windows you should use NTFS. Most of us use NTFS for Windows but have a separate FAT32 partition that we use just for temporarily moving data between Windows and Linux.

If I were you, I'd buy a second hard drive and create a FAT32 partition on it since you have no more space on your first drive. Later when things settle down for you and you have more time, you can rebuild your system and reorganize your partitions the way you really want. And you can use your second drive to help you repartition the first drive and vice-versa.

---

### Post by Danielle on 2005-11-23
if it's really desparate you can use UBCD4WIN it's a live windows cd you can mount the drive and do what ever you want. it also comes with lots and lots of programs.
[www.ubcd4win.com/](www.ubcd4win.com/)

BTW i think you'll need a WinXP CD for it to work and it's fairly difficult to setup the .iso, you have to do it yourself - manually.

---

### Post by somody on 2005-11-23
I have one 40GB drive (partitioned to Linux, Windows, and Swap) and one 6GB drive with documents on it.

If I resize the 6GB partition to 5GB or so, or even resize Linux or the Swap a bit, I can just have a FAT32 "buffer transition" like partition...

Is that right?

---

### Post by somody on 2005-11-23
Sorry for DP but I am a genius!

I CAN USE MY 6GB IPOD AS A TRANSITION SPACE!

I am so smart...I am so smart...s-m-r-t...s-m-r-t...

---

