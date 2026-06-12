---
title: "formatting second hard drive"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by sdbkr on 2007-05-27
hi i'm new to linux. i 've installed 7.04 on the main hard drive and have a second drive which i want to use as a back up. just read how to format a second hard drive if you have ubuntu 6 but i can't find instructions for  feisty 7.04. is it the same procedure? i.e. go to synaptic package manager and install gparted ? there is a pop up box which says it will affect other packages.

---

### Post by forestpixie on 2007-05-27
synaptic is just telling you what it needs to run i believe

---

### Post by sdbkr on 2007-05-27
ok thanks. i just want to use it to back stuff up. should i choose ext 3 ?

---

### Post by ugm6hr on 2007-05-27
If you're not going to share files with any other OS - then ext3 is probably the most appropriate.
After using GParted, I think you still have to "format" the partition - since GParted only creates the filesystem (I believe).

It's something like:

mkfs.ext3 -c /*dev/hdb1*

Just substitute the drive location (if it's wrong - likely hdb1 or sdb1) in Terminal

---

### Post by sdbkr on 2007-05-27
hi thanks for that i tried what you suggested and got 

mke2fs 1.40-WIP (14-Nov-2006)
/dev/hdb is entire device, not just one partition!
Proceed anyway? (y,n) 

so i chose y and got 
mkfs.ext3: Permission denied while trying to determine filesystem size

actually i think i already formatted it with gparted ? but for some reason it doesnt show up now in the /media file so i don't know how to mount it

---

### Post by ugm6hr on 2007-05-27
My mistake - got the command slightly wrong.  Plus, you'll probably have to start it with sudo:

sudo mkfs.ext3 -c /dev/hdb1

You may have to reboot after that - it should hopefully appear then.

---

### Post by sdbkr on 2007-05-27
thanks i did that and got 

mke2fs 1.40-WIP (14-Nov-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
2490368 inodes, 4980142 blocks
249007 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
152 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000

but still can't find where its gone to ! also can't figure out how to change the permissions on cd drives and floppy drives. i looked at posts from other people with same problem but still can't get them to change - any ideas ?

---

### Post by ugm6hr on 2007-05-27
Tried rebooting?

Changing permissions uses the chown command - don't know it well enough to quote here.  Will check.  But I think you can do it with graphical interface (as root):

gksudo nautilus

Find the media you want - then right-click and somewhere in properties it should give ownership / read& write options.

EDIT: Just realised drives don't appear until they are mounted in /media - that's why it's not there.  In Xubuntu, all media auto appears on the desktop - mounted or not...  Someone else with Ubuntu might need to step in here.

EDIT: This is all rubbish - see entry below.

---

### Post by ugm6hr on 2007-05-28
This should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Just substitute "/dev/hda5" with "/dev/hdb1" and "marie:marie" with "*yourusername:yourusername*"

Then it should appear in nautilus as /storage (or if you want it somewhere else - just sustitute "/storage" with "/*whatever_directory_i_want*" 

Sorry for messing it up a bit :o

---

