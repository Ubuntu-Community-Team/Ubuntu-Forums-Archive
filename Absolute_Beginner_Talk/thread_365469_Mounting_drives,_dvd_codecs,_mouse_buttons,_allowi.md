---
title: "Mounting drives, dvd codecs, mouse buttons, allowing permission"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Yellowbelly on 2007-02-19
Sorry for the long post but I have some little things I need to figure out:

I want to see the other drives because they have my music, movies, and so on. When I installed ubuntu, I didn't mount it on any other partition because I wasn't sure what it did so I just just mounted/installed it only on the partitions I designated for Ubuntu. So when I start up ubuntu, I can't see the other drives in the Computer thing. I'd like to mount these drives, or just be able to see them and use them. They are just 2 fat32 partitions on separate drives. One being on another partition of the same drive that ubuntu's on and the other on HDb1 or something like that. Any quick and painless ways of doing this?

I just tried to put in a dvd and the system recognized it but could not read it, i'm assuming because i don't have the codecs. I downloaded automatix2 and got the stuff that I thought I needed but apparently I didn't get all of it. Which codec do I need and If I can't get it in automatix, where/how do I get it?

I have a logitech mx500 mouse and would like to use the side buttons as internet back/foward buttons in firefox and stuff and maybe changed to faster scrolling. I read that you change a line in a .conf file to add numbers 5and 6 so the system can recognize it. I tried this but the system files are locked. How do I unlock the system files temporarily so I can change them? Or better yet, are there drivers I can download for my mouse? Also, I have a similar problem trying to add new fonts that are windows based but I can't do it because I don't have permission to write anything on there.

Also, another question: when I change themes, some have these unsightly lines like break lines separating the taskbar menu from the internet buttons from the quick link butotns. Can I get rid of these?

---

### Post by petri on 2007-02-19
> **Yellowbelly said:**
> ... I want to see the other drives because they have my music, movies, and so on. When I installed ubuntu, I didn't mount it on any other partition because I wasn't sure what it did so I just just mounted/installed it only on the partitions I designated for Ubuntu. So when I start up ubuntu, I can't see the other drives in the Computer thing. I'd like to mount these drives, or just be able to see them and use them. They are just 2 fat32 partitions on separate drives. One being on another partition of the same drive that ubuntu's on and the other on HDb1 or something like that. Any quick and painless ways of doing this? ... Yes and no. Do you have Edgy or Dapper?

> **Yellowbelly said:**
> ... I just tried to put in a dvd and the system recognized it but could not read it, i'm assuming because i don't have the codecs. I downloaded automatix2 and got the stuff that I thought I needed but apparently I didn't get all of it. Which codec do I need and If I can't get it in automatix, where/how do I get it? ...  Well my Totem, the filmplayer didn't work untill I installed **totem-xine** with Synaptic (it uninstalls totem-gstreamer). They say also that player VLC is even better.

> **Yellowbelly said:**
> ...
I have a logitech mx500 mouse and would like to use the side buttons as internet back/foward buttons in firefox and stuff and maybe changed to faster scrolling. I read that you change a line in a .conf file to add numbers 5and 6 so the system can recognize it. I tried this but the system files are locked. How do I unlock the system files temporarily so I can change them? Or better yet, are there drivers I can download for my mouse? Also, I have a similar problem trying to add new fonts that are windows based but I can't do it because I don't have permission to write anything on there.
...
This guide is for gentoo but it works for all of us ;) [http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations](http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations)

> **Yellowbelly said:**
> ...
Also, another question: when I change themes, some have these unsightly lines like break lines separating the taskbar menu from the internet buttons from the quick link butotns. Can I get rid of these? ...Could it be the themes? Or do you have the right viedodrivers installed (or modules :D )?

---

### Post by Yellowbelly on 2007-02-19
I have Edgy.



Sweet, thanks. I'll get that.



I can't change that file because the permission isn't allowed or something.



I guess it could be the themes but the pictures of that I downloaded didn't have them and I just updated/downloaded my video drivers.

---

### Post by petri on 2007-02-20
> **Yellowbelly said:**
> ...
I can't change that file because the permission isn't allowed or something.
...

You have to have **sudo-rights** to change the important files and for that you have to use **sudo** command. If you are using a program with graphical user interface, GUI, you have to use **gksudo** like this ```
gksudo gedit /etc/X11/xorg.conf
``` in terminal. You will get an warning which is totally harmless and it is a reported bug with very low level so developers haven't fixed it yet.

---

### Post by Yellowbelly on 2007-02-20
I've tried this and the thing comes up but the file is completely blank. Maybe I don't have the code right.

Also does anybody know the code to mount my drives hdb1 or hdb5 and hdd1? I don't know what mount point is best so can someone pick something out for me? I'm totally clueless when it comes to making up new code and mounting.

---

### Post by rccharles on 2007-02-20
> **Yellowbelly said:**
> I've tried this and the thing comes up but the file is completely blank. Maybe I don't have the code right.

Also does anybody know the code to mount my drives hdb1 or hdb5 and hdd1? I don't know what mount point is best so can someone pick something out for me? I'm totally clueless when it comes to making up new code and mounting.

See this entry on mounting windows:
 [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Robert

---

### Post by Yellowbelly on 2007-02-20
> **rccharles said:**
> See this entry on mounting windows:
 [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Robert

That kinda helps but its a really different situation that I have. I just have 2 other partitions (hdb1 or hdb5 - it kinda gave me 2 that are the same; and hdd1) that I need that I cannot access because Linux doesn't see the ones that I didn't originally mount when I installed ubuntu at the time because I didn't know much about it. Now I THINK i have to mount the drives and I read something about mounting to a /vsr or /usr point mount or something. edit: both partitions are fat32 so it shouldn't be that hard, I just can't find the specific code or what I really need to do.

---

### Post by petri on 2007-02-21
> **Yellowbelly said:**
> I've tried this and the thing comes up but the file is completely blank. Maybe I don't have the code right.

Also does anybody know the code to mount my drives hdb1 or hdb5 and hdd1? I don't know what mount point is best so can someone pick something out for me? I'm totally clueless when it comes to making up new code and mounting.

It's always best to copy and paste commands you get. ;)

Copy - highlight the text with left mousebutton
Paste - click once the scrollwheel/middlebutton (on two buttons mouse - both buttons simultaneously)

Mounting in Edgy might be trickier because Edgy has that UUID on harddrives. I don't have Edgy so I'm not the right person to talk about it. About mounting in general, you can mount hd:s where ever you want but the best/most used might be the /mnt catalogue or even media. When I use LiveCD I usually mount the hd:s to the desktop.



EDIT: I was wrong about UUID :D here's a thread where you should find how to mount yours: [http://ubuntuforums.org/showthread.php?t=366036&highlight=mount+edgy](http://ubuntuforums.org/showthread.php?t=366036&highlight=mount+edgy) and rccharles link to aysiu/psychocats page should work for you. Or do you need specific instructions for you computer only?

---

### Post by Yellowbelly on 2007-02-21
Oh snap. I just find new stuff all the time. I didn't know all the drives were in /dev. I thought they were in Computer kinda like Windows hahaha.

---

### Post by Maestro23 on 2007-02-21
> **Yellowbelly said:**
> Oh snap. I just find new stuff all the time. I didn't know all the drives were in /dev. I thought they were in Computer kinda like Windows hahaha.

You must unlearn what you learned in Windows.:guitar:

---

### Post by Yellowbelly on 2007-02-21
Ok here's my /dev folder and those highlighted are the partitions/drives that I need to mount or get or whatever. I tried the other methods but they didn't really work; it couldn't find something or I don't have permission to do it and so on. 

Sorry for the really bad picture but I forgot that image shack doesn't do linux filesystems or at least that I know of so i had to upload it here and this is the biggest I could get. May have to zoom in some. The highlighted partitions are hdb1, hdb5 (which hdb5 is under hdb1, kinda weird like one is an extension of the other), and hdd1. All are fat32.

Oh and I'd prefer specific instructions since I'm an idiot at this and don't really know what's going on.

---

### Post by Yellowbelly on 2007-02-22
ok, I tried every piece of code there was about mounting drives but it's not really working all too well for various reasons. Things can't be found, wrong names, no permission, etc. Is there any way to do this through the gui or is it all code? Can someone tell me exactly which code I need or what to do?

---

### Post by petri on 2007-02-22
_Paste_ in your terminal the command ```
sudo fdisk -l
``` and then paste the result here.

---

### Post by Yellowbelly on 2007-02-22
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        5005    40194630    f  W95 Ext'd (LBA)
/dev/hdb5               2        5005    40194598+   b  W95 FAT32

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       11869    95337711    b  W95 FAT32
/dev/hdd2           11870       18804    55705387+  83  Linux
/dev/hdd3           18805       19457     5245222+  82  Linux swap / Solaris

---

### Post by rccharles on 2007-02-22
> **Yellowbelly said:**
> 

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        5005    40194630    f  W95 Ext'd (LBA)
/dev/hdb5               2        5005    40194598+   b  W95 FAT32



I'll type up the access for /dev/hdb5

applications > accessories > terminal

verify that the partition isn't mounted
sudo mount

# if mounted...
sudo umount /dev/hdb5

sudo mkdir /media/diskb5

sudo nano /etc/fstab

# you will need to add this line...

/dev/hdb5    /media/diskb5     vfat    iocharset=utf8,umask=000 0 0

# to save
control-o
#
press enter

control-x

sudo mount -a

# you will get a warning message.  I suppose you should ignore it

cd /media/diskb5
ls


........

This should do it.  Report back any problems and the commands you issued.

These command should help you sort through 
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)


Robert

---

### Post by Yellowbelly on 2007-02-23
I did this but I don't think it worked. I checked the /dev folder and it still said it was unmounted. There was a Diskb5 foldber in /media though, nothing in it and it said there was 46gb of free space which is the size of my ubuntu partition, not my hdb5 which is about 3gb of free space and around 38gb capacity.

I made sure it wasn't mounted first so I didn't bother with the sudo unmount command.

I wrote:

sudo mount

sudo mkdir /media/diskb5

sudo nano /etc/fstab

I added this line to the bottom of all the text:
/dev/hdb5 /media/diskb5 vfat iocharset=utf8,umask=000 0 0

I pressed ctrl o

pressed enter

pressed control x

sudo mount -a

cd /media/diskb5 (i put this in pushed enter, didn't know what it did)
ls (put this in and same as above)

I probably jacked something up along here. I checked out that link and it makes a lot more since now, but I don't know what those numbers mean and that locharset stuff

---

### Post by rccharles on 2007-02-23
> **Yellowbelly said:**
> I did this but I don't think it worked. I checked the /dev folder and it still said it was unmounted. There was a Diskb5 foldber in /media though, nothing in it and it said there was 46gb of free space which is the size of my ubuntu partition, not my hdb5 which is about 3gb of free space and around 38gb capacity.



Let's get some diagnostic information.  Do:

#the script command will save all output to the file seedata.
script seedata

cat /etc/fstab

sudo fdisk -l

sudo mount

sudo mount -a

sudo mount

cd /media/diskb5
pwd
ls

# this will end the script
exit
 
less seedata

# to verify you have the info.

I hope you can somehow copy seedata here.

....

The mount command makes the file directory available on the disk.  Do this partitions work in windows?

Robert

---

### Post by Yellowbelly on 2007-02-23
Script started on Fri 23 Feb 2007 10:49:40 PM CST
ESC]0;bripod@bripod-desktop: ~^Gbripod@bripod-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd2
UUID=423598ec-a428-4b96-a59c-be1150b8a979 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hdd3
UUID=26e9f3a3-a21b-4941-88ab-498af184cd4a none            swap    sw            
  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb5 /media/diskb5 vfat locharset=utf8,unmask=000 0 0
ESC]0;bripod@bripod-desktop: ~^Gbripod@bripod-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
seedata

---

### Post by Yellowbelly on 2007-02-23
Is that what you wanted? There was a bunch of stuff that came up that I probably could have gotten but that's the seed data at the end.

Yes the partition (i guess) works in windows. I just see D:/, i don't know exactly what partition it is though. There's hdb1 and hdb5 but they seem to be the same thing- same size and everything in gparted it had the arrow pointing down when it lists all the drives and partitions:

   v   hdb1
            L> hdb5

---

### Post by rccharles on 2007-02-24
> **Yellowbelly said:**
> 

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
seedata

Is this all of the output from
sudo fdisk -l

?

I do not see the disk hdb.  Earlier, you posted results from fdisk -l and you included hdb.  What has changed? Perhaps, it is just a posting error.

I edited in some more commands after I first posted the article.  Could you try again?

I do not have access to a Windows system.  Perhaps someone else would comment.

---

### Post by rccharles on 2007-02-24
> **rccharles said:**
>  Perhaps, it is just a posting error.

I suggested you use less seedata to display the data. Maybe this was a mistake.

I need to see all the data.  

Could you try:
gedit seedata

I believe under edit you will see select all. 


or cat seedata

Robert

---

### Post by Yellowbelly on 2007-02-25
Here's sudo fdisk -l:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        5005    40194630    f  W95 Ext'd (LBA)
/dev/hdb5               2        5005    40194598+   b  W95 FAT32

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       11869    95337711    b  W95 FAT32
/dev/hdd2           11870       18804    55705387+  83  Linux
/dev/hdd3           18805       19457     5245222+  82  Linux swap / Solaris

---

### Post by Yellowbelly on 2007-02-25
gedit seedata:


Script started on Fri 23 Feb 2007 10:49:40 PM CST
]0;bripod@bripod-desktop: ~bripod@bripod-desktop:~$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/hdd2

UUID=423598ec-a428-4b96-a59c-be1150b8a979 /               ext3    defaults,errors=remount-ro 0       1

# /dev/hdd3

UUID=26e9f3a3-a21b-4941-88ab-498af184cd4a none            swap    sw              0       0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/           /media/floppy0  auto    rw,user,noauto  0       0

/dev/hdb5 /media/diskb5 vfat locharset=utf8,unmask=000 0 0

]0;bripod@bripod-desktop: ~bripod@bripod-desktop:~$ sudo fdisk -l

Password:



Disk /dev/hda: 40.0 GB, 40020664320 bytes

255 heads, 63 sectors/track, 4865 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS



Disk /dev/hdb: 41.1 GB, 41174138880 bytes

255 heads, 63 sectors/track, 5005 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/hdb1               2        5005    40194630    f  W95 Ext'd (LBA)

/dev/hdb5               2        5005    40194598+   b  W95 FAT32



Disk /dev/hdd: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/hdd1               1       11869    95337711    b  W95 FAT32

/dev/hdd2           11870       18804    55705387+  83  Linux

/dev/hdd3           18805       19457     5245222+  82  Linux swap / Solaris

]0;bripod@bripod-desktop: ~bripod@bripod-desktop:~$ sudo mount

/dev/hdd2 on / type ext3 (rw,errors=remount-ro)

proc on /proc type proc (rw,noexec,nosuid,nodev)

/sys on /sys type sysfs (rw,noexec,nosuid,nodev)

varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)

varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)

procbususb on /proc/bus/usb type usbfs (rw)

udev on /dev type tmpfs (rw,mode=0755)

devshm on /dev/shm type tmpfs (rw)

devpts on /dev/pts type devpts (rw,gid=5,mode=620)

lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)

binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

]0;bripod@bripod-desktop: ~bripod@bripod-desktop:~$ sudo mount -a

mount: wrong fs type, bad option, bad superblock on /dev/hdb5,

       missing codepage or other error

       In some cases useful info is found in syslog - try

       dmesg | tail  or so



]0;bripod@bripod-desktop: ~bripod@bripod-desktop:~$ cd /media/diskb5

]0;bripod@bripod-desktop: /media/diskb5bripod@bripod-desktop:/media/diskb5$ pwd

/media/diskb5

]0;bripod@bripod-desktop: /media/diskb5bripod@bripod-desktop:/media/diskb5$ ls

[00m[m]0;bripod@bripod-desktop: /media/diskb5bripod@bripod-desktop:/media/diskb5$ les[K[K[Kexit


Script done on Fri 23 Feb 2007 10:51:13 PM CST

---

### Post by Yellowbelly on 2007-02-25
ok, i put cat seedata thinking it was different but i think it's the same thing so the gedit one is still up. I can get this one if needed.

---

### Post by rccharles on 2007-02-25
> **Yellowbelly said:**
> 

/dev/hdb5 /media/diskb5 vfat locharset=utf8,unmask=000 0 0



Oh...

The option is iocharset.  

Try:
/dev/hdb5 /media/diskb5 vfat iocharset=utf8,unmask=000 0 0

Here is an example copied from:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0


> 
   Device Boot      Start         End      Blocks   Id  System

/dev/hdb1               2        5005    40194630    f  W95 Ext'd (LBA)

/dev/hdb5               2        5005    40194598+   b  W95 FAT32


This looks good to me.

> 
sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb5,

       missing codepage or other error

       In some cases useful info is found in syslog - try

       dmesg | tail  or so


The mount command failed for some reason.  These or'd error messages should be banned.

Robert

---

### Post by Yellowbelly on 2007-02-25
> **rccharles said:**
> Oh...

The option is iocharset.  

Try:
/dev/hdb5 /media/diskb5 vfat iocharset=utf8,unmask=000 0 0

Here is an example copied from:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0



So do I put "/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0" in the fstab thing? isn't the one above the same one I put in?

---

### Post by rccharles on 2007-02-26
> **Yellowbelly said:**
> So do I put "/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0" in the fstab thing? isn't the one above the same one I put in?

No on both questions.

You misspelled the option iocharset.  For the first letter, you put an l when you need an i.  These two letters are a little harder to read in italic.

Robert

---

### Post by Yellowbelly on 2007-02-26
darnet. I wished I got this command a little earlier. Like an idiot, i decided to try beryl by  some persuasion from my roommates and I think it screwed me over so I reinstalled. Weird thing is, I had 2 or 3 version of ubuntu on GRUB with recovery's and all that and now I only have 1 which has the number 10 after it instead of 386 or 11 or whatever and my xp thing. Is that bad?

Anyway I got a clean install with my 2 partitions in /media with all my stuff. But there's locks on some of it? Dunno what that means. I can still go into it and stuff.

---

