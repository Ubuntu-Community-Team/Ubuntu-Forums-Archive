---
title: "accessing windows drives"
date: 2005-05-18
forum: Absolute Beginner Talk
---

### Post by Patrissimo on 2005-05-18
i downloaded ubuntu and mepis live cds. with mepis i can access my drives in windows xp, but in ubuntu i can't figure out how to find them. i wonder about this because i want to use ubuntu but i'm not sure i won't have to back up everything to cds and then transfer them. i reckon it's something simple i overlooked.
basically, i want to be able to open something from my xp drives and save it to my ubuntu drive. if i can't do this in the live cd, does it mean i can't do it on the regular install too? i want to do a dual boot.

i probably would have started the regular install already, but i live in  southeast asia and it's not easy to find a linuxfest or linux savvy folks here. i'm reluctant to do it alone as i tried to install a dual boot suse a few months ago and lost all my data. i'm lucky to have an adsl connection tonight. oops, it started to rain, which means the connection will disappear.
gotta go

---

### Post by dave9191 on 2005-05-18
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

That will tell what the commands are for mounting your windows partions in ubuntu. They are not mounted by default unlike with some live cds.

---

### Post by BAshworth on 2005-05-18
Prior to installing Ubuntu, go to Ubuntuguide.org, and print the whole thing out.  It's a good thing to have by your side when setting up Ubuntu from a fresh install.

There is a section there on how to access your Window's drives.  I've never used the live CD myself, so I can't attest as to whether or not you should be able to see your NTFS volumes through it by default.  However, you could always just mount them from the command line.  There are steps in the ubuntuguide for that too.

I used to kill my Windows boot up every time I installed a distro too, until I went into my BIOS, and changed my hard drive access mode from Auto to LBA.  Haven't had even a slight hiccup since.

Good luck.

---

### Post by zaxer on 2005-05-18
One question about mounting.

Imagine I have a win partition with 1 file.

Then I mount it in Ubuntu and I see that 1 file.

Then I add another file to windows partition. Will I see that other file in Ubuntu or do I have to mount again the partition?

---

### Post by dave9191 on 2005-05-18
Mounting is a process of assinging a location in the file system to a physical disk partion. Any drive that you can see in you file system ( / ) or under windows you drive C or D is mounted. You can make any changes to files, add, read or modify them while the drive is mounted. When you are finished with it, you unmount it (happens during shutdown). 

Note that you shouldnt add or modify files on an NTFS partion under linux unless you are using the windows driver for it or you'll mess the entire partion up. 

So if you have a win (say FAT32) partion and you mount it and add a file to it, you will see that file there. If you add the file under windows and you turn linux on, you will see that file if the partion is mounted. You can have linux auto mount windows partions if you want. The file /etc/fstab holds a list of all partions mounted at boot for you.

---

### Post by zaxer on 2005-05-18
[QUOTE=dave9191]
 You can have linux auto mount windows partions if you want. The file /etc/fstab holds a list of all partions mounted at boot for you.[/QUOTE]

Can you explain a little more?


Thanks.

---

### Post by Jussi Kukkonen on 2005-05-18
[QUOTE=zaxer]Can you explain a little more?[/QUOTE]
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows) 
See the part about mounting on bootup. Hope this helps.

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=zaxer]Can you explain a little more?


Thanks.[/QUOTE]


That means taht Window partitions can be loaded at boot. But NTFS drives (what XP uses by default) cannot be written to if you value your data.

---

### Post by michaelharg on 2005-11-07
Hi, im struggling with this, i have followed the guide for hoary and this is what i get:

```
michael@michael:~$ sudo mount -a
mount: /dev/hda1 already mounted or /media/windows busy
mount: according to mtab, /dev/hda1 is mounted on /media/hda1

```

my /etc/fstab file looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
```

I want to mount the drives so i have read only access to them...

Thanks very much

---

### Post by Nrbelex on 2005-11-20
Hi,

I'd also like to access Windows files from Ubuntu - here's my setup:

I've got Ubuntu loaded on an external drive. I have windows on an internal drive. The whole point of the external drive is that I don't want to put my real hard drive in any real risk so if this is too risky, just tell me. The output of "less /etc/fstab" is:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

Thanks!

~ Brett

P.S. - I tried using [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs) but upon typing "sudo mkdir /media/windows", I got the response "mkdir: cannot create directory `/media/windows': File exists"

P.P.S. - Please hurry - My 10 Zeppelin songs from my USB drive are getting old awfully fast!

---

### Post by aysiu on 2005-11-20
Once /media/windows exists, it exist. You don't have to ```
sudo mkdir /media/windows
``` any more because it's already there. Likewise, if you're trying to mount something and it's already mounted, it won't re-mount.

Your best bet is to ```
sudo umount /media/windows
``` Then, edit your /etc/fstab according to these instructions: [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

Finally, once that's done, then ```
sudo mount -a
``` one last time.

---

### Post by Nrbelex on 2005-11-20
I tried to do that and here's what happened:

```
brett@brettslaptopubuntu:~$ sudo umount /media/windows
Password:
umount: /media/windows: not mounted
brett@brettslaptopubuntu:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists

```

Thanks!

~ Brett

---

### Post by dave9191 on 2005-11-20
mkdir is a command for making a directory. You can't make a directory that already exists. Stop trying to type "sudo mkdir /media/windows". It will only work once and you only have to do it once. Just mount the ntfs partion as described in the ubuntu guide without making the directory. So miss that step out. 

Dave

---

### Post by Nrbelex on 2005-11-20
Hahaha - showing exactly why I am in the correct forum...

Thanks!

~ Brett

---

### Post by Nrbelex on 2005-11-20
Ok so I followed the directions (without the first one since appearently I didn't need it) and here's what I got at the end:

```
brett@brettslaptopubuntu:~$ sudo mount -a
mount: special device /dev/hda1 does not exist

```

Just a reminder - I'm running Ubuntu off an external drive.

Thanks!

~ brett

---

### Post by Nrbelex on 2005-11-20
Fixed it - looked in /dev and saw that I had an hdc so I used hdc2 and all is well - thanks!

~ brett

---

### Post by Chayak on 2005-11-20
Maybe we should make a sticky topic about mounting ntfs drives.  I see the same question over and over...

---

