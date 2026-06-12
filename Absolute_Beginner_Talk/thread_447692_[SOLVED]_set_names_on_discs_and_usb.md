---
title: "[SOLVED] set names on discs and usb"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-05-18
Hi, I've got my system setup thus;
Feisty on Hard disk sda
2nd Feisty (not usable after 'desktop effects') used as storage only, on hard disc sdb
ext hdd for mobile storage (I can take movies and music and pics to class, - I teach.)
ext hdd for backup
flash mp3
flash (general purpose).
Currently, whichever is the first mounted gets the name; disk, then disk1, 2, etc.
I want to be able to set the name of each so that it always mounts with that name, so I can see which but also because I want sdb to always mount as the music/video/etc storage disc that other apps get their data from, eg. amarok, gnutella.
So I guess I really want an automatic mount setup. 
Session startup doesn't do it, at least it hasn't for me, I assume because it needs sudo.
I don't run xp or anything like that.
Right clicking the icon won't allow renaming.
I've tried changing the name thru terminal some time ago without success.
I read somewhere ages ago that the live cd would read 2 main discs as 2 partitions, but it doesn't. I guess i misunderstood.
I can't see anything here that refers to this particularly.
Thanks.

---

### Post by spin2cool on 2007-05-18
This should answer your question:
 [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by HereInOz on 2007-05-18
I am not really understanding you, but when you mount a hard disk or partition in *nix, it is mounted as part of the file system, so you would mount sdb in a directory in your file system, the same as sda is mounted as root, or, if you like, "/"

Thus if you set up a mount statement in /etc/fstab to mount your disks on boot up, then they should always be mounted in the same directory, and thus the path to them should always be the same.

Or have I misunderstood totally (my apologies if I have)

---

### Post by carloslosgrande on 2007-05-19
Hey Spin2cool, thanks man, that looks just the ticket. I'll try it and post back.:guitar:
HereinOz, thanks too, I'm sorry my post isn't clear. It was clear in my head but I do have trouble making my meaning clear at times as I not really sure of the right way to state my desires in computer speak.

---

### Post by carloslosgrande on 2007-05-19
Update, this howto worked great, simple, direct and effective. 2 discs under ext3 are now renamed and 2 more under vfat also. There is however one more vfat flash disc that won't change because of this; > ozymandias@ramses:~$ sudo mlabel -i /dev/sdc1 -s ::
Password:
Total number of sectors not a multiple of sectors per track!
Add mtools_skip_check=1 to your .mtoolsrc file to skip this test
and I can't find this [COLOR="Red"].mtoolsrc[/COLOR] file. [COLOR="Red"]whereis .mtoolsrc[/COLOR] just gives me [COLOR="Red"]mtoolsrc:[/COLOR]
But, that said it doesn't really matter for this particular disc as its the only one that didn't work and I don't use it for apps.
So thanks Spin2cool and thanks to the people setting up these howtos and docs
happy:guitar:

---

### Post by zba78 on 2007-07-13
I had the same error message. Just create the file .mtoolsrc in your home directory and add the line mtools_skip_check=1 to it.

A quick way to do this is to open a terminal and type ```
echo  mtools_skip_check=1 >> .mtoolsrc
```

---

