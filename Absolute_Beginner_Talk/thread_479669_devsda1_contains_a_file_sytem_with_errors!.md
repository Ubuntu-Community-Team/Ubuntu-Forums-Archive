---
title: "/dev/sda1 contains a file sytem with errors!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by fonzcorp on 2007-06-20
After two weeks learning and begining with Ubuntu. I ran into my first start up error. When it starts up and Ubuntu needs to check files for booting this is what i get:

Checking files needed to boot...
(it checks everything with [OK] except the root file system.)

*checking root file sytem
/dev/sda1 contains a file sytem with errors, check forced

(It gets up to 100% on that and then proceeds to do a whole mess of something i cannot keep up with. Then at the end its does:)

ta 4096 in
[  253.512000] Buffer I/0 error on device sda1, logical block 10977322
Error reading block 10977322 (Attempt to read block from filesystem resulted in
short read) while doing inode scan.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
              (i.e., without -a or -p options)
fsck died with exit status 4

[fail]
*An automatic file sytem check (fsck) of the root filesytem failed.
A manual fsck must be preformed in maintenance mode with the 
root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After preforming system maintenance, press Control-D
to terminate the maintenance shell and restart the system.
Give root password for maitenance
(or type Control-D to continue):

(i put in my root password)

bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: The: command not found
The program 'apt-get' is currently not installed. You can install it by tping:
apt-get install apt
bash: apt-get: command nto found
bash: dircolors: command not found
bash; The: command not found
The programs 'apt-get' is currently not installed. You can install it by typing:
apt-get install apt
bash: apt-get: command not found
root@Linux-Fonz:~#

(so i then type in 'fsck' in my root)

fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes

(then again it does a whole mess of 'ta ###### in' runs. Some with errors, and some with logical blocks. Then it stops at)

ta 4096 in
[  1672.684000] Buffer I/0 error on device sda1, logical bloack 10977322
Error reading block 10977322 (Attempt to read block from filesystem resulted in
short read) while doing inode scan.

(it asks if i want to ingore it. i choose 'yes'. It then asks if i want to force rewrite. i chose 'yes'. It gives me the same 10977322 error asking if i want to ignore again. i chose 'no' and it aborts 'fsck' sending me back to my root.)

------------------

If someone can help please do. that would be awesome. right now im going to try and put my Ubuntu disk in see.. if i can recover anything or help my system out. ill post if anything new happens with that.

---

### Post by diatribe on 2007-06-20
running fsck on a mounted parition is bad, try booting a livecd and running fsck manually on the drive that way

---

### Post by ukripper on 2007-06-20
Never run fsck on mounted filesystem it can cause instability and sometimes makes system non functional.

---

### Post by Gen2ly on 2007-06-20
In case you haven't tried this before.

In the terminal,  place a new directory and mount it.

> mkdir /mnt/myroot
mount /dev/sda1 /mnt/myroot

> fsck -f /dev/hda11

If it's' an older harddrive you may want to add the -b option to check for bad blocks.

---

### Post by Inxsible on 2007-06-20
Additionally you can plug in your LiveCD and then run ```
fsck /dev/sda1
``` from the terminal.

---

### Post by fonzcorp on 2007-06-20
not sure excacty how to do this. i placed my live cd in. but do i run Ubuntu from my partition or the CD?

i ran from CD trying 'fsck' in a terminal. but its taking too long for anything to happen.

---

### Post by Happy_Man on 2007-06-20
uh, uh, uh, wow. Is that the partition Ubuntu is on? If so, I fear a reinstall may be your only choice. I have no idea *what* you did, but from what it says, your partition is complaining. A lot. Hopefully, you have a separate /home partition. If not, make one while you're reinstalling. Those things are one of the major benefits of running Linux.

Perhaps fsck takes a while.... I've never had to try it.

---

### Post by fonzcorp on 2007-06-20
i have no idea what i did either. last boot that worked, i installed an automatix2 update. if anything did i fear that did.

im try a couple things. Dirk and INX...neither worked because mounting a dir cant since its a read only file system. and fsck /dev/sda1...only does the same thing in finding errors and asking to ignore ect.

be back later tonight guys thanx.

---

### Post by fusionisthefuture on 2007-07-16
hi

i have basically this exact same error, but i did absolutely nothing to deserve it, i assure you.  what could possibly cause it to think apt-get is somehow uninstalled?  im running feisty on my dual boot machine, and i hardly ever boot into it on this one, because its my gaming machine, and i just tried to tonight, and it said all the exact same stuff the OP's said.  literally the only thing ive done to this computer is uninstall the gnome network manager, but its worked fine every time after that until now.  i can try to run a live cd, and fun fsck in its terminal, but i really dont see how this will help, becuase something IS broken, and there is NO reason it should be.  it was fine when i powered it down last time, and now its bad, and this is a brand new hard drive.  
any ideas?
thanks,
-arne

---

### Post by ukripper on 2007-07-17
> **fusionisthefuture said:**
> hi

i have basically this exact same error, but i did absolutely nothing to deserve it, i assure you.  what could possibly cause it to think apt-get is somehow uninstalled?  im running feisty on my dual boot machine, and i hardly ever boot into it on this one, because its my gaming machine, and i just tried to tonight, and it said all the exact same stuff the OP's said.  literally the only thing ive done to this computer is uninstall the gnome network manager, but its worked fine every time after that until now.  i can try to run a live cd, and fun fsck in its terminal, but i really dont see how this will help, becuase something IS broken, and there is NO reason it should be.  it was fine when i powered it down last time, and now its bad, and this is a brand new hard drive.  
any ideas?
thanks,
-arne

If you are using same partition for your dual boot win and ubuntu, probably some of data from your win might have overlapped your ubuntu filesystem and consequently corrupting your intact file system. That is why it is always recommended to keep two different OS on different partitions especially win,  as windows gets too  fragmented.

---

