---
title: "hey, 3 simple problems"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by twntyonejay on 2008-04-08
I switched over from Vista last month cuz its trash. I love Ubuntu 7.1 but i need to solve some  problems to truly enjoy it,

One: I have a Linksys WMP11 v.4 and my computer sees it but I cant unlock the wireless feature.

Two: I can't watch DVDs with VLC

Three: I just got a 750GB external HDD and I did format it to FAT32 n the OS recognized it but now it says: Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only. Unable to open /dev/scd0 - unrecognised disk label.

Thanks for the help in advance

---

### Post by corney91 on 2008-04-08
> **twntyonejay said:**
> 
Two: I can't watch DVDs with VLC


Installing ubuntu-restricted-extras is probably the solution to this:
```
sudo apt-get install ubuntu-restricted-extras
```

EDIT: I should add, as I've been reminded below, that ubuntu-restricted-extras are all in that 'legally grey' area. 
libdvdcss2 is a package that will be installed with ubuntu-restricted-extras as well as other packages to play, for example, MP3s.

---

### Post by NR1224 on 2008-04-08
cant help with the first and 3rd, but i acn help with dvds. Ubuntu cant included dvd playback due to legal reasons. The package is therefore availible at [www.medibuntu.org](www.medibuntu.org). Check for the libdvdcss2 package. Just remember, this is still a legally grey area

---

### Post by SlappyPappy on 2008-04-08
Check out this thread for #1 problem:

[http://ubuntuforums.org/showthread.php?t=213831](http://ubuntuforums.org/showthread.php?t=213831)

It has some good info.

---

### Post by aeacides on 2008-04-08
Answering to your 3rd question:

Run this command:

**cat /etc/fstab**

And post the result back here.

Maybe you did not choose the right Fat32 format ( must be **0C** )

... and why didn't you format it in NTFS? I think it's well supported now ...
 

Otherwise, Maybe you need to mount your disk as root [...]

Question: Did you ever use your disk on Windows? Maybe you didn't unmount it properly.


Xavier

---

### Post by twntyonejay on 2008-04-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fd5b7349-a784-42fc-b65e-2de374ec82a4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ff9d47f2-8751-4e4d-8145-3e68ca51c989 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I never used it on Windows

---

### Post by bhold on 2008-04-08
> **twntyonejay said:**
> I switched over from Vista last month cuz its trash. I love Ubuntu 7.1 but i need to solve some  problems to truly enjoy it,

One: I have a Linksys WMP11 v.4 and my computer sees it but I cant unlock the wireless feature.

Two: I can't watch DVDs with VLC

Three: I just got a 750GB external HDD and I did format it to FAT32 n the OS recognized it but now it says: Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only. Unable to open /dev/scd0 - unrecognised disk label.

Thanks for the help in advance

About the Linksys wireless - different model number than mine, but this thread shows how I got mine working maybe it will help. To get mine working needed to download the XP driver from realtek and install under ndiswrapper.

[http://ubuntuforums.org/showthread.php?t=650066](http://ubuntuforums.org/showthread.php?t=650066)

---

### Post by philinux on 2008-04-08
One of my favorite colours is gray. :)

---

### Post by twntyonejay on 2008-04-08
wat bout the HDD?

---

### Post by DGortze380 on 2008-04-08
try NTFS on the drive, I had a lot of trouble with my larger drive (500GB) formated as FAT32, where as my 120Gb worked fine.  NTFS support is technically still beta, but I haven't had any trouble with it.

---

### Post by twntyonejay on 2008-04-08
how do i format it to NTFS?

---

### Post by twntyonejay on 2008-04-09
i really need help guys

---

### Post by vishzilla on 2008-04-09
For problem two, refer [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Tatty on 2008-04-09
> **twntyonejay said:**
> how do i format it to NTFS?

Use Gparted.  You can install it with ```
sudo apt-get install gparted
```

But im not sure if the filesystem type is really the problem.

---

### Post by ramjet_1953 on 2008-04-09
To format an external drive, you just need to install [COLOR="Blue"]gparted.[/COLOR]

Open a terminal and copy this command:

[COLOR="Red"]sudo apt-get install gparted[/COLOR]

However, you cannot format, or make any changes to a mounted drive.

Often, it is easier to use the [COLOR="Blue"]gparted Live CD[/COLOR]

You can download the gparted live cd from here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Regards,
Roger :cool:

---

### Post by wawadave on 2008-04-09
OK in fat type drives win98-xpsp1 cannot see more then 147 gigs. 
so linux may allso have same limitation.
got an xp install disk? just about any one of those will format it to ntfs.

Not sure how to do it from linux still a newby.

if no window system is going to need to see the drive then you can format it with ubuntu install disk 
to what ever current file system its using. but disconnect main hard drive so you don,t format wrong drive (did this once lol). I believe under custom  you have options to format and partition drive.
Did on the older linux distros i tried long ago.
 but gparted Live CD sounds like the route to go.

---

### Post by twntyonejay on 2008-04-15
thanks imma try that now

---

