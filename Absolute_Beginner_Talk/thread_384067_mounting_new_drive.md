---
title: "mounting new drive"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by jasonsexton on 2007-03-14
I have added a new SATA drive to my Edgy 64bit system.  I formatted drive using gparted and ext3 filesystem.  what do I need to do to acces this drive so I can copy files to it for storage?
here is what comes up when I sudo fdisk -I

sexton@SummerHome:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19130   153661693+  83  Linux
/dev/sda2           19131       19457     2626627+   5  Extended
/dev/sda5           19131       19457     2626596   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux
sexton@SummerHome:~$

---

### Post by charles.g.moore on 2007-03-14
As long as you can see it you mount it try 'man mount'
If you want it to automount upon startup check 'man fstab'

Good luck

---

### Post by brettg on 2007-03-14
OK, I am **assuming** that the 320gb drive is the new drive, if not you need to modify thes instructions accordingly.
What you need to do is the following;

Create a mount point. You would normally do this in /media but you don't have to. I have a    drive mounted as /store for instance. I will use this as an example;

   sudo mkdir /store

From here you can mount the drive manually but I'm guessing you want it to mount automagically at boot so . . . 

edit your fstab

   sudo gedit /etc/fstab

add a line to the end like so;

   /dev/hdb1    /store   ext3   defaults   0 0 

type;

   sudo mount -all 

or reboot and you are done.

Good luck

---

### Post by jasonsexton on 2007-03-14
ok so where you have store, can I use any name for example "music"?

---

### Post by maniacmusician on 2007-03-14
> **jasonsexton said:**
> ok so where you have store, can I use any name for example "music"?
kind of but not quite. You don't want to use /store because you shouldn't really be mounting a drive at root (/). put it in /media/music instead.

You of course also have to create that directory, for which you would do "sudo mkdir /media/music"

---

### Post by jasonsexton on 2007-03-14
I will give that a whirl
thank you

---

### Post by jasonsexton on 2007-03-14
now I can't get a terminal window
help????

---

### Post by maniacmusician on 2007-03-14
you need to be more verbose with your errors. What do you mean you can't get a terminal window? please be more descriptive and give us any errors if you're getting them.

---

### Post by jasonsexton on 2007-03-14
I apologize
I'm really having a hard time with this stuff

if I try to open terminal nothing happens
if I try to go to my home directory nothing happens

---

### Post by jasonsexton on 2007-03-14
I have been running ubuntu for a few months now and I have had to re-install a couple times
it seems like every time I try something from terminal I screw something up

I have been very cautious about changing anything from the "basic" ubuntu install because of this

---

### Post by Mr. C. on 2007-03-14
> **maniacmusician said:**
> kind of but not quite. You don't want to use /store because you shouldn't really be mounting a drive at root (/). put it in /media/music instead.

You of course also have to create that directory, for which you would do "sudo mkdir /media/music"

Just for the sake of understanding, there is nothing wrong with mounting a hard device such as a disk in the root directory.  Mounting a network share is a no-no.  It is common to mount separate file systems on /home, /var, and even /usr.

---

### Post by maniacmusician on 2007-03-14
hmm that's weird. I would say launch the terminal from the terminal but obviously you can't do that :D For now, you can do any terminal work you need to do using a virtual console and you can figure out your terminal issues later.

Press Ctrl + Alt + F1 to get to a virtual console. Press Ctrl + Alt + F7 to get back to your graphical screen.

---

### Post by Mr. C. on 2007-03-14
Here's some info that might help you format and mount your disk.  Review Week 4 "Filesystems, Disks and Partitions" coursework, lab, and homework at:

[http://cis68c1.mikecappella.com/calendar.php](http://cis68c1.mikecappella.com/calendar.php)

MrC

---

### Post by maniacmusician on 2007-03-14
> **Mr. C. said:**
> Just for the sake of understanding, there is nothing wrong with mounting a hard device such as a disk in the root directory.  Mounting a network share is a no-no.  It is common to mount separate file systems on /home, /var, and even /usr.
true, but he's not mounting a system folder there. It's a storage/music hard drive and thus belongs in /media for the sake of keeping a sane setup :)

> **jasonsexton said:**
> I have been running ubuntu for a few months now and I have had to re-install a couple times
it seems like every time I try something from terminal I screw something up

I have been very cautious about changing anything from the "basic" ubuntu install because of this
Understandably, you're frustrated; but stick with it, you'll get the hang of it sooner or later. Don't get into the "reinstall if something screws up" mentality. Things are usually fixable.

---

### Post by maniacmusician on 2007-03-14
> **Mr. C. said:**
> Here's some info that might help you format and mount your disk.  Review Week 4 "Filesystems, Disks and Partitions" coursework, lab, and homework at:

[http://cis68c1.mikecappella.com/calendar.php](http://cis68c1.mikecappella.com/calendar.php)

MrC
Is that your site? I have to say, I saw you post that in another thread and I thought it looked pretty impressive. I have it bookmarked to look at later.

---

### Post by jasonsexton on 2007-03-14
thank you my friends
I am going to read some more at this point
I appreciate all the advice

---

### Post by Mr. C. on 2007-03-14
> **maniacmusician said:**
> true, but he's not mounting a system folder there. It's a storage/music hard drive and thus belongs in /media for the sake of keeping a sane setup

That is an arbitrary distinction, but not the point.  Its best to teach people the rules for how the system actually works, and distinguish those from folklore, voodoo, and someone's common practice.

MrC

---

### Post by maniacmusician on 2007-03-14
> **Mr. C. said:**
> That is an arbitrary distinction, but not the point.  Its best to teach people the rules for how the system actually works, and distinguish those from folklore, voodoo, and someone's common practice.

MrC
Yup, you are correct :) I always stress that we need better education for new users, so I really should have practiced that in this case :)

---

### Post by Mr. C. on 2007-03-14
> **maniacmusician said:**
> Is that your site? I have to say, I saw you post that in another thread and I thought it looked pretty impressive. I have it bookmarked to look at later.

Yes, and thank you.  Its one of several I created for some courses I taught a couple of years back, at a local college.  Students found the material very helpful, and the labs helped them learn the fundamentals through hands on practice.  Here are all the sites I still have up:

[http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)
[http://cis68b1.mikecappella.com/](http://cis68b1.mikecappella.com/)
[http://cis68c1.mikecappella.com/](http://cis68c1.mikecappella.com/)
[http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

Have a look around, and feel free to download the materials for your personal use.

MrC

---

### Post by maniacmusician on 2007-03-14
> **Mr. C. said:**
> Yes, and thank you.  Its one of several I created for some courses I taught a couple of years back, at a local college.  Students found the material very helpful, and the labs helped them learn the fundamentals through hands on practice.  Here are all the sites I still have up:

[http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)
[http://cis68b1.mikecappella.com/](http://cis68b1.mikecappella.com/)
[http://cis68c1.mikecappella.com/](http://cis68c1.mikecappella.com/)
[http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

Have a look around, and feel free to download the materials for your personal use.

MrC
[speechless]

Damn.

I think I will. That is a treasure chest full of stuff. Some way over my head, but good stuff to learn.

---

### Post by Mr. C. on 2007-03-14
> **maniacmusician said:**
> [speechless]

I'm speechless every time I see that J.C. mugshot !  :-)

---

### Post by maniacmusician on 2007-03-14
> **Mr. C. said:**
> I'm speechless every time I see that J.C. mugshot !  :-)
haha, get used to it :) it's going nowhere

[fights the urge to edit your post and change the J to a K]

---

