---
title: "partition help"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by asakurax on 2007-07-19
well, here is all the background

i have 40 gb hard drive, which is divided to C D and X partitions

C is where my windows is
D is where my files(music and stuff) are
X is where my Ubuntu is

now, after using Ubuntu for a couple of days, i want to make it my main OS
as in, moving all my needed windows programs(Office and stuff) into C, and merge D and X, so all my music/video files will be usable for Ubuntu

what do i need to do?
dont wanna do anything stupid....

:)

---

### Post by macogw on 2007-07-19
Why not keep your files in the 2nd partition and just use it to store stuff you want to access from both OSes?  What format is that partition?  If it's NTFS, do a Google for ntfs-3g or look it up on ubuntuguide.org or wiki.ubuntu.com and it'll let you mount the partition in Ubuntu so that you can read/write to that partition from it.  Then do ```
sudo gedit /etc/fstab
``` and add it to that file in the same format that the others are done, but make sure you put ntfs-3g in the options for it.

---

### Post by jombeewoof on 2007-07-19
no need to do anything drastic. 
what is the filesystem of D
if it's fat, (which I doubt)
add 
```
/dev/hda2   /files   vfat  defaults  0 0 
```
to /etc/fstab
if it's ntfs just 
```
 sudo apt-get install libntfs-3g0 
```
then your /etc/fstab entry will be
```
/dev/hda2   /files   ntfs-3g defaults 0 0 
```

make sure you create /files and change the ownership of it to you with
```
 sudo chown username:username /files 
```
not /files/ but /files big difference there for what it's worth
then 
```
sudo mount /files 
```
and you'll be all set. and when you reboot into ubuntu it will already be mounted read/write



**ntfs info might be a bit off, I don't use windows anymore so I'm not 100% on ntfs.

---

### Post by Gone fishing on 2007-07-19
I do something similar but have an Ext3 partition (called /home2), which, both Linux and XP can use I mount the drive in Windows using [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html).

just a quick question Automatix has an option for enabling read / write access to NTFS partitions using ntfs-3g (very easy just click the button) does this ever give any problems with NTFS?

---

### Post by asakurax on 2007-07-19
ok, so now i have access to my D partition. thats awesome! (:

now i wonder, when i go into Places - Computer, i dont see the D, only the C partition.
i can go into D via filesystem - media - sda5

does it matter?

---

### Post by jombeewoof on 2007-07-19
if you really want direct access to it, I'm pretty sure in gnome you can add an applet to the panel that had direct access. 1 click access :)

---

### Post by asakurax on 2007-07-19
i mean, its not recognized as a volume

---

### Post by Gone fishing on 2007-07-19
I'm pretty sure that if you get Automatix to set it up for you it will do exactly what you want

Automatix > Miscellaneous >  Automatix read / write NTFS

---

### Post by asakurax on 2007-07-19
zomg, i tried to use the Automatix, and now it doenst recognize it at all
as in, in filesystem - media - sda5, Ubuntu shows nothing
but on XP, everything is there, all my music and stuff

WTF

---

### Post by asakurax on 2007-07-19
bump ? ):

edit: OK, i remounted and now i can access the sda5
but still, it does not recognized as a voulme

also, it seems that i cant create folders in the sda5 folder, but only in sda5\folder

---

### Post by Nevis on 2007-07-19
Did you try using
```
fdisk -l
``` 
to list partitions? If the partition is still available then use
```
sudo mkdir /mnt/ddrive
```
to create a mount point then
```
sudo mount /dev/sda5 /mnt/ddrive
```
to mount it?

---

### Post by asakurax on 2007-07-19
the sda5 is mounted, its just the its not in "computer" directory

---

### Post by Nevis on 2007-07-19
Not totally sure I understand but I think I know what you mean now.  I found this [[COLOR="Blue"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=21508&pp=10&page=5") that might help you out. 

However, I have another suggestion. If the drive is mounted then you can navigate to it through either /mnt/ddrive or /media/ddrive then (assuming you're using Nautilus) assign a bookmark to it from the main menu. It'll then show up on the Places menu.

I hope this helps.

---

### Post by asakurax on 2007-07-19
the thread helped!
thx a lot (:

---

### Post by asakurax on 2007-07-20
i just restarted my ubuntu and the partition is now unmounted
i treid to restart dbus again and no help

?

---

