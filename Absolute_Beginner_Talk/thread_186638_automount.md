---
title: "automount"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by millsy on 2006-06-02
Hi - question from a real noob.  I'm having trouble with automounting drives and CDs.  Basically ...

1. If I plug in a usb drive formatted with FAT in windows, it shows up in nautilus but goes not mount giving an error :

```
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount
```

2. If i put a CD rom in the drive (I've got a laptop CD rom drive in my ubuntu box), nothing happens until I double click the CD icon in nautilus, then it mounts and an icon appears on the desktop

3.  Audio CD's do not automount at all and therefore don't play automatically.  I realise that you can't mount Audio CD's but the 'Removable drives and media' applet thing says that they should play automatically.  I also assume this is why I can't use Soundjuicer.  I CAN play CD's through the CD player applet however and using Grip.

4. I have to manually mount a removable hard drive which is formatted on a Linksys NSLU2 (in ext3 format).  It does not automount.

I've tried fiddling with the bios to make sure this it says 'plug and play os installed' - no help
I've added the autofs package - no help
I've checked that my user is in the plugdev group - no help
I've looked at fstab - don't really understand it!
I've made sure that the 'Hal' user has permission on removable drives and CDs - no help.

I hope that this is easy to sort out - I LOVE ubuntu but this is quite annoying, especially the inability to rip CD's as I've set my ubuntu box up as a mediaserver!

Looking forward to your replies.   Mark

---

### Post by ProjectGod on 2006-06-02
i think you'll have to manually enter your mount points into the /etc/fstab file... :)

---

### Post by catlett on 2006-06-02
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) This gives a good explanation of /etc/fstab. Something isn't right though, I apologise for posting and not knowing the answer, a usb drive and external hard drives should be detected automatically and mounted. Check the guide and hopefully someone with more /etc/fstab and/or automounting will reply.

---

### Post by millsy on 2006-06-02
Thanks for your quick response.  This is my fstab file contents

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

What do you suggest I change?

---

### Post by ProjectGod on 2006-06-02
have you tried this url? [http://ubuntuguide.org](http://ubuntuguide.org) 

hope this helps. :)

---

### Post by millsy on 2006-06-02
yes - doesn't really help

---

### Post by catlett on 2006-06-02
bump

---

### Post by millsy on 2006-06-09
Thanks for all you who helped me.  Two points ...

1.  What does 'bump' mean?
2. I tried booting off the liveCD and automount worked so I reinstalled Ubuntu and it's sweet.  Must have been a botch on initial install.

Thanks again.

Mark

---

### Post by u.b.u.n.t.u on 2006-06-09
[QUOTE=millsy]Thanks for all you who helped me.  Two points ...

1.  What does 'bump' mean?
2. I tried booting off the liveCD and automount worked so I reinstalled Ubuntu and it's sweet.  Must have been a botch on initial install.

Thanks again.

Mark[/QUOTE]

"bump" is text slang for "bumping up a post" so it is visible again, eg at the top of all posts. Someone "bumps" a post when they want to discuss it again. A more subtle method is just to post something, thereby bringing up the post again.

---

### Post by skale on 2006-07-05
I know It's an old thread, but you have to change the noauto to auto on the /dev/hdd  line. 
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,auto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
Then you can mount it with 
> sudo mount -a
and play it in rhythmbox or whatever. 

What you are doing is changing the default option so it mounts automatically, rather than going through all the mount -t blah-blah yackey asdfg stuff, or something like that. I figured it out today, and am mighty proud of myself!

---

### Post by Sammi on 2006-07-18
Too late he already reinstalled.

I feel for all the new people to Ubuntu, who have to reinstall every time they encounter silly little problems like this. Mostly because I been there and tried it a few times too often hehe :rolleyes:

---

