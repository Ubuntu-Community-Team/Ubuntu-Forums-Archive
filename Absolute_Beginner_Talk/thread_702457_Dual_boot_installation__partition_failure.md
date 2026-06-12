---
title: "Dual boot installation : partition failure"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by idy on 2008-02-20
Hello,

I have Windows XP installed on my laptop. I have just defragmented it and run a chkdsk /f (after following the recommended steps in various Ubuntu help guides on installing Ubuntu while retaining Windows).

Trying to install Ubuntu from the latest live CD, I get the following warning when trying to partition the disk in Gparted (with the live CD boot) :
```
unable to detect filesystem! possible reasns are:
-the filesystem is damaged
-the filesystem is unknown to Gparted
-there is no filesystem available (unformatted)
```
Trying afterwards to install directly without going to Gparted, I cannot resize the initial partition, therefore I cancelled the installation.

The hard disk is on NTFS.

Any help on what I could try to install Ubuntu while keeping Windows & data would be much appreciated !

Thx !

---

### Post by oedha on 2008-02-20
what if you boot with ubuntu live cd and manage the partition there ?

---

### Post by pkacianu on 2008-02-20
If you have few data for backup, I think it's better backup those data, full format the entire disk, create a Windows partition (50-70% of your total disk space) and install Ubuntu in the free space.

Another options is install Ubuntu in a virtual machine.

[ ] s,

---

### Post by mkoehler on 2008-02-20
Well, before you try that, I would recommend getting the gparted live cd.  Chances are that you'll attain similar results to what you found using gparted on the live cd, but it's worth a shot.

---

### Post by idy on 2008-02-20
@oedha : sorry if I was not clear, but I tried to manage the partition from the live CD.

@pkacianu : well my hard disk is 75% full - thanks for the tip. Would running Ubuntu in a VM actually slow it down quite a lot ? Is it possible to have the same functionnalities and install Linux applications in that case ?

Thx !

---

### Post by idy on 2008-02-20
@mkoehler : ok, will try that, thanks for suggesting - as I said, I tried using gParted and directly the partition step during the installation process but either I got the warning in the first place (and therefore did not want to do anything) or had the options to either install on the full disk or go to the manual partitioning - without being proposed to resize my disk and use the freed space.

Thx.

---

### Post by oedha on 2008-02-20
which gparted....gparted live can be found - [http://gparted.sourceforge.net]("http://gparted.sourceforce.net")

if  you boot from live cd......open terminal :=> sudo gparted or qparted
or you just install ubuntu and pay full attention on step 4 of 7
this is partition step....choose manual....and manage there :)

---

### Post by Duck2006 on 2008-02-20
This may help.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by idy on 2008-02-20
@oedha : thanks for the link (btw, mispelled : [http://gparted.sourceforge.net](http://gparted.sourceforge.net)), will have to try that as well.

@oedha and @Duck2006 : the thing is I do not see the 3 options as you may see in the following screenshot ([http://img379.imageshack.us/my.php?image=feistydual06rw5.png](http://img379.imageshack.us/my.php?image=feistydual06rw5.png)) [IMG]http://img379.imageshack.us/my.php?image=feistydual06rw5.png[/IMG] : I just have manual or use full disk, not the guided resizing option. In manual, I cannot either resize the partition, size is not displayed, and I do not have the size dropdown list in editing the initial partition.

Thanks a lot for being so prompt in replying - any further ideas ?

---

### Post by oedha on 2008-02-20
o..oo......can you boot to windows ?
then restart it properly.....try the gparted or live cd back

---

### Post by idy on 2008-02-20
I did not partition yet anything (my issue) and therefore did not install anything yet.

I can boot to windows prorperly. I tried inserting the ubuntu live CD twice after a full shut-down, but same issue. Did not try yet with gparted live cd though.

Thx !

---

### Post by Duck2006 on 2008-02-20
Did you defragmenter your drive in XP first?
You should do it two or three times be for you install ubuntu.

---

### Post by idy on 2008-02-20
As I was mentioning in my first post, I have fully defragmented the disk. Actually did it twice.
Thx for suggesting anyway.

---

### Post by idy on 2008-02-21
I went back looking at the defragmentation results and have been wondering whether xhat I saw could be issue : the free space is not completely contiguous i.e. the white spaces appear in several places.

But running the defragmenter again does not improve anything. Do you know of any other free Windows defrag tool which would allow to have two contiguous blocks, one with the data, the other free ? Or is it not related ?

In parallel, I tried installing Ubuntu using wubi on the net, but got an error other people encountered when rebooting : initramfs at the command line, which again seems to the same issue I am facing with my disk (which I cannot format - not my personal computer if you see what I mean !).

Thx again for your help !

---

### Post by Duck2006 on 2008-02-21
Did you run a check disk on the disk from within windoze?

---

### Post by idy on 2008-02-21
Yes, I did : chkdsk /f which in fact asked me to reboot to complete.

Thx for suggesting.

---

### Post by jcanini on 2008-02-21
You could try a windows app to shrink the xp partition then install ubuntu in the free space.
Sorry cant think of anything specific as I haven't done this in some time. Anyone?

Also when resizing Its not a bad idea to back up your original partition on to an external hard drive, or something like that, in case of software problems or a blackout e.t.c which could damage your Windows partition.

For backup I have previously used Clonezilla --  [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/) -- . is a live cd that worked well for me.

All the best.

---

### Post by idy on 2008-02-23
Thx jcanini.

I used O&O defrag which helped consolidate the free space. And then tried to install Wubi again, but got exactly the same error when rebooting and choosing Ubuntu :
No RAID disks
and then further below, access to the command line iwth
initramfs >

So I uninstalled Wubi and defragmented again, and now not really knowing what to do

---

