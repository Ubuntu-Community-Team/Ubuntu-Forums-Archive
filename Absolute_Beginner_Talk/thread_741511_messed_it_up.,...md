---
title: "messed it up.,.."
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by manicmailman on 2008-03-31
k new problem... my media drive is NTFS... after reading the comments i figured it was ok to get the NTFS drivers (which were already installed) and mount the drive...

when i double-clicked the drive... it mounted it onto my desktop... i figured i would put it into my home folder... i then figured this could be done in the option called 'mount point'... so i typed in /home/[user].... and proceeded to unmount then mount the drive for the settings to take effect... not so... i shoulda just dragged the damn thing... because now it wont open... giving me this message: "mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)"

unfortunately the button "do what you did before then" doesnt exist....

damnit... any suggestions? (besides the obvious "turn and walk away from linux")... but i dont want to do that... so your stuck with my dumbass problems...

---

### Post by maybeway36 on 2008-03-31
You could try editing the fstab:
```
gksu gedit /etc/fstab
```

---

### Post by manicmailman on 2008-03-31
> **maybeway36 said:**
> You could try editing the fstab:
```
gksu gedit /etc/fstab
```

im actually looking at the fstab in gedit now... but i dont know how to edit it... ?

i know the computer knows that i have that drive because its listed in the file browser although unmounted... if i can find it and know its name im sure a simple command can fix the mounting problem..

---

### Post by superprash2003 on 2008-03-31
first unmount the drive..the create the folder in the /home/[user] directory..
then type sudo mount /dev/hdb /home/[user]/folder 

where /dev/hdb is your ntfs drive

---

### Post by maybeway36 on 2008-03-31
Copy and paste the fstab here, that might help.

---

### Post by Duck2006 on 2008-03-31
This is a how to to do what you want to do.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by manicmailman on 2008-03-31
k... i got it to mount on the desktop again...

but im having trouble unmounting/remounting the drive... when i do fdisk in terminal its listed as sda1 (2 is linux) but it wont unmount (as per the link posted)... do i have to call it "Media" in the termina to unmount itl? because thats what its listed as in /media... then mount it as sda1 or media?

---

### Post by Duck2006 on 2008-03-31
In the terminal type

sudo fdisk -l

and

cat /etc/fstab

and post the outputs hear

---

### Post by manicmailman on 2008-03-31
Disk /dev/sda: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x000ac027



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1               1       44619   358402086    7  HPFS/NTFS

/dev/sda2   *       44620       60138   124656367+  83  Linux

/dev/sda3           60139       60801     5325547+   5  Extended

/dev/sda5           60139       60801     5325516   82  Linux swap / Solaris



# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda2

UUID=2f845c9a-dcd3-4cf2-978d-3b836cbef6e3 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda5

UUID=0ac98531-64a0-4fe3-bcc8-428dee5d6e67 none            swap    sw              0       0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Duck2006 on 2008-03-31
Witch drive do you want to mount?

---

### Post by manicmailman on 2008-03-31
sda1

---

### Post by Duck2006 on 2008-03-31
Did you make the mount point?

sudo mkdir /media/(what ever you want it called)

and it will show up on the desktop when it is mounted ect.

---

### Post by manicmailman on 2008-03-31
sorry but i think im wasting your time... my problem is simple i think.... and thats why its dumb..

my hd (sda1, media) shows up on the desktop when mounted... when i go into properties it says the mount point is "/media/Media" the capital Media being the drive (accidental it was around before ubuntu)... anyway... i figured i would mount it in my home folder... say... in music or something of the sort... so i changed the mount point to "/home/[user]/Music... or just /home/[user]... or anything in there, but it gives me an error everytime... so do i just have to live with it on the desktop or can it be moved?

---

### Post by Duck2006 on 2008-03-31
Ok umout the drive.
make the new mount point
edit your fstab
and then remount the drive
And you should have the job done.
You could try
sudo mkdir /home/username/what you want to call it

---

