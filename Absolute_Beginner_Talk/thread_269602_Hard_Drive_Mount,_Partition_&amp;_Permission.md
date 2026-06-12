---
title: "Hard Drive Mount, Partition &amp; Permission"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by NewRubberSoul on 2006-10-02
So one of my roommates was getting rid of this old computer and I managed to swipe the 20Gb hard drive out of it and install it as a slave drive into my system.  I already had ubuntu installed when I put it in and the computer didn't have a problem recognizing it when I booted up.

I used Gnome Partition Editor to partion the entire drive and then used the ubuntu "Disks" function to enable it and make it mount in /media/Second Drive. Now when I open the media folder, I see the folder "second drive", but I don't see the CD/DVD drives that used to be there.  Instead, there's a folder called "lost+found" that I can't access.

Is this a problem, or is this normal?  Thanks in advance for the advice!

---

### Post by NewRubberSoul on 2006-10-02
Forgot to mention, but when I open the lost+found folder I get this message:

> You do not have the permissions necessary to view the contents of "lost+found".

---

### Post by Marsolin on 2006-10-02
I'm not sure what the problem is, but it doesn't sound normal. It's possible the drives are being mounted with root permissions only.

---

### Post by uk_sphinx on 2006-10-02
my dad threw a computer out once and someone swiped the harddisk out of it.
the guy got a program and undeleted a load of files in the free space.
swiped my dads credit card numbers.
didnt find out for 2 weeks and run a bill of £1.5k

---

### Post by pyman on 2006-10-02
Look at the file using root priv. with sudo gedit /etc/fstab and make sure that the drives are all there with proper chmod.
something like /dev/hda1 /media/partitionname  ntfs   nls=utf8,umask=0222 0       0

and you can remount all of your patitions with 
suod mount -a

---

### Post by NewRubberSoul on 2006-10-02
This is my fstab redout:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Note that my second hard drive is /dev/hdb  but I don't see it in here.  And I wouldn't know what to write if I were to put it there...

---

### Post by keheikev on 2006-10-02
I would pull the old drive out. 
```
sudo gedit fstab
```
Just print the contents of the new set up. Now install it and redit fstab so that it doesnt have any reference to the old drive in it.
Do you want that drive in ext3 or fat32 to mount at boot up or would you like to mount it manually so that everyone can read/write to it. In the former case it is wise to use the terminal its best to create the mount points in the /mnt directory which is more for fixed disks any way. I think your sytem as the graphical disk utilities arent that good yet in ubuntu.
HTH
Kiheikev

---

### Post by cotcot on 2006-10-02
As keheikev wrote the partitioners in Ubuntu are not that good. 
First of all : have you set the jumper on the slave hard drive in the slave position ? I assume yes.
Does sudo ```
fdisk -l
``` in terminal show you this drive (probably as hdb) ?
If yes continue (if no : then it looks like a hardware problem).
Partition and format it with the Gparted LiveCD. The Gparted CD has a graphical interface. Reboot en remove the Gparted CD. In ubuntu adapt you fstab with sudo ```
gedit /etc/fstab
``` 
And a line or lines according to your new partitions. Here is a link explaining fstab [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

Then about the lost+find. You need root permissions to access it. In terminal sudo > chmod 755 /path-to-the-lost+find/lost+find will give you access.

---

### Post by herrdoktor330 on 2006-10-02
While we're on the topic of Hard Drive mounting:

I've had this issue installing Ubuntu on my system without doing sloppy "one HD at a time installations". Allow me to explain:

I have a PCI IDE 133 card, 4 hard drives, and a DVD burner. I recently did an installation where I have 1 hard drive running off the main primary IDE bus as a master, the DVD drive running off the secondary IDE bus as master and a smaller hard drive running as a slave on the secondary. Then I have the other 2 hard drives running as master off the PCI card.

the problem I have is that after I install ubuntu, I get GRUB error 15. It doesn't matter if I install off of the 1st master hard drive off the PCI card (registering as hda1) or off the mobo's IDE (hde1). The only way I've had a successful install is to install with PCI card inserted with no HDs attached and install with only one HD to add the rest on after the install has been completed.

What am I doing wrong when I install?

And what are the DUMP and PASS values in the fstab file do?

Thanks for the info so far. I've learned alot already (but not nearly enough).

---

