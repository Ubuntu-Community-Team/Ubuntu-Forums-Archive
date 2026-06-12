---
title: "running DVDs"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by ineffabilliken on 2008-03-13
I have a lot of questions that I think will end up all running into each other, but I'll just lay them out one at a time and see what happens. So here's the first:

I just installed ubuntu on my laptop, and it's working great so far. But how do I open a dvd? I was hoping that a default program would just pop up when I put a disc in the drive, but that didn't happen, so I downloaded gxine. Then things got stupid. The gxine wizard didn't see the DVD drive and told me to point to it somehow (I don't remember the exact message, and I don't want to try running it again because I'm worried it will mess things up (see below)). Then, when I closed that window, ubuntu logged me out and started up again with a blank desktop (even the "preload" thingy was gone--what is that by the way? Oops, that's another question).

---

### Post by billgoldberg on 2008-03-13
Follow these instructions and then install vlc.

[http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/](http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/)

(stating the obvious here but the terminal is located at "applications -> accessories")

Open vlc and press "file -> open disc" and then ok to view dvd's.

You could install libdvdcss2 instead of vlc that would enable totem movie player to play dvd's but vlc handles dvd's that much better.

---

### Post by OffAxis on 2008-03-13
to watch a dvd you need to have the proper codecs installed. There's instructions and packages here:
[http://www.medibuntu.org](http://www.medibuntu.org)

---

### Post by ineffabilliken on 2008-03-13
Thanks for the tips, but I'm still having problems. I installed vlc, but when I tell it to open a dvd disc, nothing happens.

I also tried installing libdvdcss2 according to the instructions on medibuntu, but I got the following message:

[INDENT]amos@ubuntu:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate[/INDENT]

---

### Post by jan quark on 2008-03-13
try this
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh
```

and open the dvd with gxine

---

### Post by billgoldberg on 2008-03-13
> **ineffabilliken said:**
> Thanks for the tips, but I'm still having problems. I installed vlc, but when I tell it to open a dvd disc, nothing happens.

I also tried installing libdvdcss2 according to the instructions on medibuntu, but I got the following message:

[INDENT]amos@ubuntu:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate[/INDENT]

Did you install the medibuntu repository before installing vlc?

Did you update your system after adding the medibuntu repo?

You need to update or it won't work.

```
sudo apt-get update

```

Or use the reload button in synaptic.

---

### Post by ineffabilliken on 2008-03-13
I ran the update, and libdvdcss2 is installed, but vlc still does nothing and the gxine wizard still doesn't see the dvd drive. Here's the message:
[INDENT]
FAILED- could not access dvdrom: /dev/dvd

Either create a symbolic link /dev/dvd pointing to your cdrom device or set your cdrom device in the preferences dialog.[/INDENT]

---

### Post by ineffabilliken on 2008-03-13
I also tried Jan Quark's suggestion. No luck there either.  A quick investigation of the filesystem, by the way, reveals that there is in fact no directory /dev/dvd. 

So how do I create a symbolic link pointing to my cdrom device?

---

### Post by mc4man on 2008-03-13
I'd be surprised if you didn't have symlinks - look in places>computer>filesystem>dev - they'll have little arrows - if there ck. properties to see link target
Vlc should work - open it in the  terminal, under file tab click open disk and post output from terminal

---

### Post by Nythain on 2008-03-13
how many cd/dvd rom drives do you have??? is the dvd drive it... probably because i think you said you're on a laptop...

either way, try telling vlc or gxine that your dvd drive is /dev/scd0 instead of /dev/dvd... you should have an scd0 hopefully... if not you could always type
cat /etc/fstab
in a terminal and paste its contents here, we can try to figure it out one way or another

---

### Post by ineffabilliken on 2008-03-13
Yes, the cdrom and DVD drive are the same.

Here's the output I get in the terminal when running vlc:

[INDENT]amos@ubuntu:~$ vlc
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat 
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000291] dvdread demuxer error: DVDRead cannot open source: 
[00000289] main input error: no suitable access module for `dvd://'
[00000280] main playlist: nothing to play[/INDENT]

And here is the output for fstab:
[INDENT]
amos@ubuntu:~$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults          0   0
/media/host/wubi/disks/system.virtual.disk      /               ext3        loop,sync         0   1
/media/host/wubi/disks/home.virtual.disk      /home           ext3        loop,sync         0   2
/media/host/wubi/disks/swap.virtual.disk      none            swap        sw                0   0[/INDENT]

I tried looking for symlinks, but I don't see anything that points to a cdrom.

---

### Post by mc4man on 2008-03-14
Sorry I don't know much about wubi installs and from the threads I glanced at I'm not too sure I would.
If you don't get a resolution here you may want to move thread to [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)
There doesn't seem to any posts relating to your issue - possibly you have a borked or incomplete install

---

