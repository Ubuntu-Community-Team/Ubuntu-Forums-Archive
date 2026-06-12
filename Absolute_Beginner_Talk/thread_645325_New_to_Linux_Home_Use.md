---
title: "New to Linux Home Use"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by JamesBowen on 2007-12-19
Hey there, guys!  I've just erased windows xp x64 (yeah, I know, probably a bad idea right away, but i don't do things in halves) from my system and loaded ubuntu 7.10.  I've been using feisty at work for programming / sshing / etc the last several months, so I'm familiar with the general principles behind using linux.  Now, as I haven't explored these forums yet (Yeah, I know, it's bad etiquette to do this -- I swear, I'll try to be cooler than that as a general rule in the future), but I wanted to launch in with a couple of questions and see if anyone could point me in the right direction.

First off, one of the big things I do at home is play games.  Furthermore, I told an ardent windows user a few hours ago that I could get wine running directx9 games in under a week.  He said that if I do, he will switch to linux.  For the sake of evangelism, help me here.  :P  Anyway, the big thing is, I'm running into trouble running anything but note pad in wine -- and I'm wondering if there's some sort of auto configuration script or such that I'm lacking.  Secondly, I had a 175-gig ntfs partition on my box that was dedicated to files -- all of my media/etc is on there, and I was wondering how, exactly, I could get at it.  Most of the tutorials for accessing ntfs that I've seen have always left crucial steps out.  If someone could point me in the right direction for either of those things (wine configuration of using old ntfs partitions), please let me know.  I'll give you hugs, n' such.

Anyway, other than that rather inconsiderate request, I'd just like to say hi...and it's good to finally join the community! :D

---

### Post by GavinZac on 2007-12-19
hi james!

[www.winehq.org](www.winehq.org) is your best bet for wine games.

ntfs partitions should work "out-of-the-box" on gutsy

---

### Post by JamesBowen on 2007-12-20
> **GavinZac said:**
> hi james!

[www.winehq.org](www.winehq.org) is your best bet for wine games.

ntfs partitions should work "out-of-the-box" on gutsy

Thanks for the linkage on the wine thing.

About the ntfs partitions working out of the box on gutsy...that's all well and good...but what exactly do I do to access them?  I'm guessing that since it's a seperate partition it's going to involve mounting some device somewhere, but, well, most of the stuff I do involves make files or using sshfs, this end of things is all a bit esoteric and new to me.  Still, it's relieving to know it'll work.  Didn't wanna lose all my stuff. ^^  Thanks for your help so far, and if anyone wants to give me a run down on how to access ntfs partitions/drives, I'd much appreciate it.

---

### Post by LaRoza on 2007-12-20
For the NTFS partition, if you installed with the partition in existance, Ubuntu will have added the partition to fstab (don't worry if you don't get that).

Basically, to use it, you double click it in Computer or chose it in Places.

No work needed.

(Places is the menu on the top panel)

---

### Post by Presto123 on 2007-12-20
Lol, love your comment on "I don't do things in halves." Definitely made me chuckle.

---

### Post by jordanmthomas on 2007-12-20
Any NTFS partitions you have on your disks will automatically be mounted at /media/devsdxy
where x is the disk number
and y is the partition number

To access it, you'll just have to go to places --> partition of your choice

Should you want to mount one by hand in the off chance it doesn't automatically get mounted, I'll try to explain mounting as simply as possible.

You can mount any partition whenever you feel like it using the mount command.  This can be annoying if you have a partition you'd always like mounted, so there is a file called /etc/fstab that lists where to mount certain partitions / filesystems (a filesystem can be more than a partition, but that's getting a little more advanced)

You can mount things wherever you want.  C: D: E: and such are a foreign concept to linux.  Say you have a partition on some drive that is dedicated to music.  It would make sense to find your music in your home folder, right?  So, you could mount it at /home/JamesBowen/music and when you're using it, it will just look like a folder in your home directory called music (very neat in my opinion)

To see what partitions you have, you can run this:
```
sudo fdisk -l
```
You'll get something like this albeit not the exact same.
[PHP]Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b78d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4173    33519591   83  Linux
/dev/sda2            4174        4273      803250   83  Linux
/dev/sda3   *        4274        7295    24274215    7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe93a112c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   83  Linux
[/PHP]

This shows that I have 2 disks, /dev/sda and /dev/sdb
/dev/sda3 is an NTFS partition (I have a Windows installed there, so sue me.  :mad: ) and it's the third partition on that disk.

So, if I wanted to mount it at /media/windows I would type this:
```
sudo mount -t ntfs-3g /dev/sda3 /media/windows
```
Here, the -t ntfs-3g flag tells mount that I am mounting an ntfs partition (well, really that it should use the read / write version of ntfs)
/dev/sda3 is the device (partition) I wish to mount
/media/windows is where I'd like to mount it (note:  this directory must already exist)

Anyway, I can go on and on here, but I think I'd be wasting my time.  This should be enough to get you going and to let you know what to look up should you need more help (I think the answer you were looking for is way up at the top of the post anyway  :) ).

Let us know if you need any more help; people are here just for that reason.


edit
...and beaten because I took so freakin' long to type that

---

### Post by LaRoza on 2007-12-20
If the partition has a label, it will be mounted under /media/<label>

---

### Post by jordanmthomas on 2007-12-20
> **LaRoza said:**
> If the partition has a label, it will be mounted under /media/<label>

Ah, yes...forgot to mention that.  (probably because my stuff never gets automounted in Arch and I just do it myself)

---

### Post by JamesBowen on 2007-12-20
LaRoza, Jordan, you guys pretty much rock.  Thanks.  Yeah, right after you said 'It should be mounted already', I looked at my desktop and realized it was in the top-left corner with my old volume's name...d'oh!

Thanks for the more detailed information, jordan, it was pretty informative, as my only experience in fstab was when I tried to mount about 6 remote servers using sshfs using fstab at boot...hahh...never did get those ssh keys working.

Anyway, I now have all my old data which will help enormously in, well, everything.  Thanks a million!

---

### Post by jordanmthomas on 2007-12-20
Well, you can also put things in /etc/fstab that DO NOT automatically mount, so don't think you're limited by that.  It's just a place to define how to mount each device.

Anyway, glad it helped.

---

