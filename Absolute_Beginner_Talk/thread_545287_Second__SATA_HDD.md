---
title: "Second  SATA HDD"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by dac10 on 2007-09-07
i have two SATA hard drives, one 40gb raptor with Kubuntu on, but the second 250gb maxtor one was formated in NTFS and id like to use it for storage only. 

so how do i format it in whichever file system Linux uses? and where do i find it, as in theres no 'my computer'.

thanks,

---

### Post by expatCM on 2007-09-07
Boot your system from the Live CD.

Then open the Gnome Partition Manager and then select the drive and take it from there.......

---

### Post by dac10 on 2007-09-07
dont i have a partition manager on kubuntu? its just that it would take ages to download the live CD. how can i access partition manager?

---

### Post by carloslosgrande on 2007-09-07
[FONT="Comic Sans MS"]For what its worth, try downloading GParted. It doesn't take very long, not like the ubuntu CD.
Its really useful and is more powerful than the built-in (live CD) partition editor. I've used my copy many times.
Ubuntu uses ext3 format.[/FONT]

---

### Post by dac10 on 2007-09-07
where can i find the new storage space?

---

### Post by dac10 on 2007-09-08
ive now got the hdd mounted on a folder in my home directory and its got a "lost+found" folder inside which is locked and it wont let me create new folders or send files to it. however it does indicate the correct storage space.

how do i create a usuable folder inside it?

---

### Post by dondad on 2007-09-08
> **dac10 said:**
> ive now got the hdd mounted on a folder in my home directory and its got a "lost+found" folder inside which is locked and it wont let me create new folders or send files to it. however it does indicate the correct storage space.

how do i create a usuable folder inside it?

One way is to do an alt-f2 to bring up the run dialog box. Type gksudo nautilus and then run. (I am assuming you are running gnome and not kde) This will bring up the file manager with root access.  Find the drive , right click on it, and go to the permissions tab. Set the permissions to set yourself as the owner, and with read/write access. Close that instance of nautilus so you don't get into trouble with it, then you should be able to access the drive.

---

### Post by dac10 on 2007-09-10
im using KDE. i can find the filesystem but under the permissions tab it only has options for enabling/disabling the drive. nothing about read/write access?

---

### Post by dondad on 2007-09-10
> **dac10 said:**
> im using KDE. i can find the filesystem but under the permissions tab it only has options for enabling/disabling the drive. nothing about read/write access?

Not familiar with KDE, but are you running it with sudo or gksudo(graphical)? You will have to be root to change the permissions.

---

### Post by Drake2k on 2007-09-20
I'm using Ubuntu:Feisty.  Gnome.  I'm having the exact same problem and followed everything right up to the ALT-F2 and running gksudo nautilus.  It comes up, then you say to look for the disk.  I can't find it.  I'm not exactly sure where to look.   The Gparted says they are /dev/sda and /dev/sdb.  Ok so I looked there and found something.  I gave myself ownership of it but still no dice.

When I reboot the system and click Places then Computer, It shows them  as 

37.3 GB Volume
37.3 GB Volume (2)    They're exactly the same

When I double click it asks for my password and then mounts them.  It places icons on my desktop as Disk  and Disk-1.

If I double click them I can see the locked Lost & Found and can not make directories or copy files.


I'm missing something....but what?

---

### Post by Drake2k on 2007-09-25
bump

---

### Post by carloslosgrande on 2007-09-25
[FONT="Comic Sans MS"]Hi, first, its better to start your own post than to tack onto someone elses. You get more responses that way.
second, have you tried getting [COLOR="Magenta"]'storage device manager'[/COLOR] from[COLOR="Red"] add/remove[/COLOR] in [COLOR="#ff0000"]applications[/COLOR]? Its a gui for setting up your discs.[/FONT]

---

### Post by Drake2k on 2007-09-29
Update:

I ended up booting into windows and repartitioning the sata drives (after turning off the raid).  I made them both FAT32 and each one has 2 20g partitions.

I'm having a slight issue with them however which you can read here if you're intersted in lending a hand.

[http://ubuntuforums.org/showthread.php?t=560922]("http://ubuntuforums.org/showthread.php?t=560922")

---

