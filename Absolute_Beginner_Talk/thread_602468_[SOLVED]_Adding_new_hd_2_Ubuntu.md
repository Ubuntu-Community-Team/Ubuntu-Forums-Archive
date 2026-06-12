---
title: "[SOLVED] Adding new hd 2 Ubuntu"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by PogMoThoin on 2007-11-04
Hi,

I've got several Sata hd's in my pc, 5 to be exact. They are as follows:

36Gb raptor: Vista
36Gb Raptor: Ubuntu
120Gb Seagate: Vista Documents ntfs
120Gb Seagate: Unpartioned space, was raided with other 120gb but now its split
160Gb Seagate: Music & videos ntfs, can mount in ubuntu when needed

I'd like to do 2 things,
1: I'd like to have my music & video hd mount automatically when i log on 2 ubuntu as i use it all the time & have 2 mount everytime. I'm constantly listenin 2 music.
2: I'd like to mount the other 120Gb Seagate & use it for Ubuntu documents, It doesnt need 2 be visible or usable by Vista.

Any help would be great.

Thanks in advance.

Pog

---

### Post by ggaaron on 2007-11-04
Doesn't ubuntu mount everything automatically? I think that somewhere is such an option. You can always edit /etc/fstab and add your discs, but it can be frustrating for someone who likes to configure everything from a gui.

---

### Post by PogMoThoin on 2007-11-04
No, Ubuntu doesnt mount it automatically, the music & video hd is ntfs & must be mounted each time & the other unused hd is not showing up, I'd not have a problem configuring it from terminal if some1 would take me thru it. Cansome1 here take me through editing /etc/fstab?

---

### Post by oisuxx on 2007-11-04
im sure you probably did this....but when i put my sata in it was previously laded in windows. i had to load windows back up then remove it from the system....

i just started using ubuntu 3 days ago...sorry if this is a dumb reply.

---

### Post by PogMoThoin on 2007-11-04
No, it was a raided hd, but now the raid is split & it shows up as unpartioned space (raw) in Vista disk manager. Vista is not using this hd. I want 2 use it for ubuntu.

---

### Post by ggaaron on 2007-11-04
Sure, I can help.

First run gparted - it will present you some discs/partitions etc. The point is to know how your discs are named (/dev/something), then you can post a list:
I want my /dev/something1 to be mounted /somewhere and it is ext3/ntfs. I'll make you text to paste to fstab=)

If you don't plug your discs out it will be ok, if you do, then of course there is an option, but I don't remember how to get a partition's UUID=/

---

### Post by ggaaron on 2007-11-04
I'll need this too:
ls /dev/disk/by-uuid/ -l

---

### Post by PogMoThoin on 2007-11-04
Ok, the 120Gb unpartioned hd is named /dev/sdd & the 160Gb music & video hd is named /dev/sde1

---

### Post by PogMoThoin on 2007-11-04
This is what i get:

> colm@l33t-str33t-PC:~$ ls /dev/disk/by-uuid/ -l
total 0
lrwxrwxrwx 1 root root 10 2007-11-04 11:40 446ABB616ABB4F04 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-11-04 11:40 72E0B284E0B24E5B -> ../../sde1
lrwxrwxrwx 1 root root 10 2007-11-04 11:40 78CCC363CCC31A70 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-11-04 11:40 a3a19bd5-788b-4494-9fde-ac199b2c1a3e -> ../../sdc1
lrwxrwxrwx 1 root root 10 2007-11-04 11:40 cd1e5256-9b6e-4775-b22f-ff1ba0d15039 -> ../../sdc5


---

### Post by ggaaron on 2007-11-04
You can partition the unpartitioned drive with gparted.

Is this partition ntfs? then:
UUID=72E0B284E0B24E5B   /media/music    ntfs-3g     auto,users,locale=en_EN.utf8,uid=1000,gid=1000      0 0

ext3 drives are more simple
UUID=<uuid> /media/mountpoint auto auto,user 0 1

---

### Post by ggaaron on 2007-11-04
I've forgot. I think that you must have directories in which you want drives to be mounted.

sudo mkdir -p /media/music
chown username.username /media/music
mount -a

I'm not sure weather ntfs will give you writing rights... If it complains then use the second line again after mounting the drive.

---

### Post by PogMoThoin on 2007-11-04
Ok, have partioned unpartioned hd "/dev/sdd" to ext3, but this is where i get stuck, What do i do next to mount it.

Also yes that would be the music & video hd, Its ntfs & was named media. So therefore would my directory be called /media/media?

---

### Post by ggaaron on 2007-11-04
1st option:
sudo mount /dev/sdd1 /somewhere

2nd option:
check uuid again
add a line like in above posts for ext3, change mountpoint to where you want to see your disc
sudo mout -a

---

### Post by PogMoThoin on 2007-11-04
this bit i do not understand:
> ext3 drives are more simple
UUID=<uuid> /media/mountpoint auto auto,user 0 1

Sorry for being noobish :)

---

### Post by ggaaron on 2007-11-04
> **PogMoThoin said:**
> So therefore would my directory be called /media/media?

No, it will be named as you wish, it's just a folder name that you can specify, for example it can be /home/mydiscs/musicdisc, but commonly discs are mounted in /media or /mnt.

---

### Post by PogMoThoin on 2007-11-04
Right, ran in2 a problem, used this command

sudo mount /dev/sdd1 /media

now when i go2 filesystem, media all i see is a folder called "lost and found". How do i undo this

Also i cannot open the music & video hd, it keeps telling me it could not find it

---

### Post by ggaaron on 2007-11-04
You can't undo=D It is an obligatory folder for ext3 system. Ignore it=)

UUID=<uuid> /media/mountpoint auto auto,user 0 1 

Add this line to your fstab
change UUID to the right uuid, run the uuid checking command again and get the uid from line with /dev/sdd1 on the end
/media/mountpoint is of your choice but better do a folder in /media, rather than mount it to media like just before, you have more than one disc to mount=)
If you want to unmount something just run sudo umount /dev/sdd1 (or any other disc)

---

### Post by PogMoThoin on 2007-11-04
ok, unmounted /dev/sdd1 & all went back 2 normal.

then created directory like this:
> sudo mkdir -p /media/music
chown username.username /media/music
mount -a

but i get this:
> colm@l33t-str33t-PC:~$ sudo mkdir -p /media/music
colm@l33t-str33t-PC:~$ chown colm.colm /media/music
chown: changing ownership of `/media/music': Operation not permitted
colm@l33t-str33t-PC:~$ mount -a
mount: only root can do that
colm@l33t-str33t-PC:~$ 


Where am i going wrong? Maybe i should take this 1 hd at a time, For the time being lets forget bout /dev/sde1........my music & video hd & just get the blank hd mounted.

---

### Post by PogMoThoin on 2007-11-04
ok, I've managed to mount the blank hd in /media/documents. How do i create a shortcut in my home folder 2 it?

Also need to set music & video hd to mount automatically, gonna have a go @ this now. Have a folder created in media called /media/musicandvideo for it

---

### Post by PogMoThoin on 2007-11-04
All done.

Btw, got a folder in my /media folder i wanna delete as i made them by mistake
/media/music. How do i delete it?

Also how do i create shortcuts 2 my /media/musicandvideo and /media/documents folder in my home folder?


Thanks very much ggaaron. you've been a great help & I've learned loads =D>

Cheers,
Pog

---

### Post by PogMoThoin on 2007-11-04
Right after a reboot, Both hd's show up but have to be mounted manually and the disk i partioned is not named, Help,

---

### Post by PogMoThoin on 2007-11-04
Actually when i mount them they're mounted in my /media folder & named /disk & /media, they not mounted in /media/documents & /media/musicandvideo. Can any1 help me?

---

### Post by PogMoThoin on 2007-11-04
Right,

I have them mounting where i want them by using this
> colm@l33t-str33t-PC:~$ sudo mount /dev/sdd1 /media/documents
[sudo] password for colm:
colm@l33t-str33t-PC:~$ sudo mount /dev/sde1 /media/musicandvideo
colm@l33t-str33t-PC:~$ sudo mount -a

Any1 know how i get them 2 mount permanently as i have to use this everytime

---

### Post by PogMoThoin on 2007-11-04
Right,
after a bit of googling & re-reading this thread i've managed to edit my /etc/fstab and also managed to delete the unwanted directories. Didn't realise i had to log in as root to save the /etc/fstab file & it wouldn't save. All is good.

Thanks once again

Pog

---

### Post by ggaaron on 2007-11-04
Sorry. I've been out for some time.

This is what fstab is for - for mounting drives every time you boot, and yes, for most actions you need root access.

For shortucts make a symlink:
ln -s original-dir your-home-dir's-shortut

If everything works, then I'm happy=)

---

