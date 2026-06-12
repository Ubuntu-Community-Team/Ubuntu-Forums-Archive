---
title: "how to access my info"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by adtran1 on 2006-04-04
i am using the live cd on my new notebook & have linux booted up & running, but how do i get to my c drive & access my pictures etc?

---

### Post by trent dillman on 2006-04-04
Look under the Places menu. If not there, Places > Computer > Filesystem > /media/

If you don't see it there, open a terminal (Applications > Accessories > Terminal) and type 'sudo fdisk -l', then post what you get from that here and we'll help!

---

### Post by taurus on 2006-04-04
You need to mount it first before you can access it.  Assuming that your Windows is NTFS and it's on /dev/hda1, click Applications -> Accessories -> Terminal.  Now, type these in at the prompt,
```

sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hda1 /mnt/windows
sudo cd wherever_the_folder_that_has_your_pictures

```

---

### Post by trent dillman on 2006-04-04
Does the Live CD not automount NTFS drives?

Weak.

---

### Post by meborc on 2006-04-04
[QUOTE=taurus]sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hda1 /mnt/windows
sudo cd wherever_the_folder_that_has_your_pictures
[/QUOTE]

the last line should be 
sudo cd [COLOR="DarkRed"]/mnt/windows/[/COLOR]wherever_the_folder_that_has_your_pictures

just so one gets not lost :rolleyes:

---

### Post by taurus on 2006-04-04
[QUOTE=trent dillman]Does the Live CD not automount NTFS drives?[/QUOTE]
Don't know since I don't have Windows whatsoever running on my machines...  Linux and only Linux.

> Weak.
For those who still run/use Windows...

---

### Post by adtran1 on 2006-04-05
i check under media & nothing, but i am hesitant to type any command for fear of screwing up my computer.

isn't there a point & click type menu where you can mount your hard drive to access your info.

i have use the puppy linux & that is how i access my hard drive.

please respond, because i really like to try the live cd linux, but right now it is useless to me, since i can't get to my hard drive.

i have the the nfs memory & not fats](*,)

---

### Post by Sutekh on 2006-04-06
[QUOTE=adtran1]i check under media & nothing, but i am hesitant to type any command for fear of screwing up my computer.

isn't there a point & click type menu where you can mount your hard drive to access your info.

i have use the puppy linux & that is how i access my hard drive.

please respond, because i really like to try the live cd linux, but right now it is useless to me, since i can't get to my hard drive.

i have the the nfs memory & not fats](*,)[/QUOTE]
So we can step you through it, please use the Terminal (Applications -> System Tools menu)

This command will not stuff up your computer, it will list the partitions on your hard discs
```
sudo fdisk -l
```
Post the output and we can work out how to mount the hard drive.

---

### Post by meborc on 2006-04-06
or you can check [https://wiki.ubuntu.com/AutomaticallyMountPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions) ... for info and so ;)

---

### Post by adtran1 on 2006-04-06
hi,
    i found my hard drive info, using the suggested method,

but before i start typing codes, isn't the live cd 5.1 os suppose to be able to let me go into either the media, or mnt file & be able to click on my c drive?

because when i go into either one of those files i see nothing.

is this a bug in the 5.1 os?

because in puppy linux, i can use pmount & all my drives appear & all i have to do is click on the drive i want and get access.

please update me on this, also accoding to what everyone is saying, if i type the commands mention earlier in this tread i should be able to mount my c drive & it will not hurt my present window xp os.

is that true?

i am a newbie so i dont want to screw up my present window os.

thanks in advance for all the help.

---

### Post by Sutekh on 2006-04-06
The 5.10 Live CD doesn't use pmount, its not a bug, it just doesn't have it.

So you'll need to mount the Windows partitions yourself.  Use
```
sudo fdisk -l
```
to find them, and
```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows -t ntfs -o umask=0222
```
To mount it.

The commands won't cause any problems, indeed the mount command I gave only allows read access to the NTFS partition.  So its pretty much indestructible.

---

