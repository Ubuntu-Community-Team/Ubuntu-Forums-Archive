---
title: "Repartitioning"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by christek91 on 2006-10-02
Hey guys! I've been using ubuntu for a few days now and am starting to get the hang of it, but I've got a few wrinkles I'd like to smooth out.
First:
  My computer has a sound card. A Sound Blaster Audigy LS. I have a 5.1 surround sound system hooked up to this card. My problem is that Ubuntu plays sound through the fron left and right speakers only, the sound is very loud, and I seem to have no control over the volume. I looked for the card in the device manager and it said that the Device Type and Capabilities were both unknown. Any help on the subject would be appreciated :) 

Secondly:

I have a 250 GB hard drive (or 232.89 GiB to be technical:p ) and when I installed Ubuntu I used the default partition option. The setup created two partitions. The largest of these is 96.19 GiB. I would like to resize this partition (extended 3 partition type) and then fill the space I make by resizing my Windows NTFS partition so that I have more windows space. This is mainly because as much as I enjoy using ubuntu, I still use windows for most of my stuff. Again any help would be appreciated!:) 

--Christek91

---

### Post by Imsati on 2006-10-02
Welcome to the Forums:-)

Regarding volume...

I'm using Kubuntu, and Kmix is my sound recorder/master volume/whatnot program to adjust the master control with. I have mine set to the max ans just manually adjust from there with my speakers. Not sure what the Ubuntu equivilant is, but just look under 'Multimedia' from your drop-down menu.

Regarding partitioning...I'm not sure exactly what your disk partitions look like. You could enter the partition utility and manually resize the XP one, or you could re-install Ubuntu and manually edit during the setup.

If you choose to re-install and do it manually, delete the Ubuntu partitions you have and then resize the XP area. After that, you'll want to make three Ubuntu Partitions (no more than, let's say 50 GB total for all three).

The first is a Linux-Swap (in simplest terms, linux equivalent of Windows virtual Memory). Your Swap should be twice as large as your actual RAM (so 512 mb RAM = 1024 mb Swap drive). Next, dedicate no more than 8-10 GB for a /Root drive, then use the rest for the /Home drive.

By having the three, you can delete/reinstall the Ubuntu OS if anything ever happens and still have your /Home drive intact (no missing personal files).



Of course, if you want to have a separate FAT32 partition so you can store both XP and Ubuntu files on it, just follow the above steps, but reserve more drive space than tha original Ubuntu 50GB I mentioned.

If you just want the XP and Ubuntu stuff separate though, there's a program for Windows that will allow you to access ext2+3 file systems. I don't have the link handy, but if you would like to go that route, let me know and I'll dig for it or someone else can post since I'm going to bed in a few minutes.

Best of luck. Have a great night!

~Jay

---

### Post by Imsati on 2006-10-02
Oh and one more thing before you partition...

It can be strange at first--take your time with it. Also...

[COLOR="Red"]BACKUP BACKUP BACKUP[/COLOR]

the Windows stuff you need to keep.

Just in case...

---

### Post by Sef on 2006-10-02
For repartitioning, I would use [GParted.]("http://gparted.sourceforge.net/livecd.php")

---

### Post by christek91 on 2006-10-02
Thanks guys, I'll try them out tomorrow when I get time. I appreciate the help:)

---

