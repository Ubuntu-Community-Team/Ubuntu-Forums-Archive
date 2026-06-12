---
title: "Mounting Ex2 partition as Home?"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-03-07
I have 2 HD's:

HD1  Windows XP + Ext2 Partition
HD2 Ubuntu

I have just created the Ext2 partiton on HD1 as it has more space.

How do i now mount it so that it's visible in Ubuntu and how do i make it my home directory?

The partition is hda5

---

### Post by el3ktro on 2006-03-07
Look into the file /etc/fstab. If you already had an extra home partition, then you simply have to change the device to hda5. If you don't have one yet, then create a new line for your home partition, the syntax should be obvious. Don't forgot t copy your user data over to the new partition first! Then do a restart (you can also manually remount the partitions, but doing a restart is probably simpler for now), and you're done

Tom

---

### Post by _simon_ on 2006-03-07
sorry i don't understand.

i added this:

/dev/hda5      /home/simon        ext2             defaults      0    0

And it buggered up - i had to use the failsafe terminal and remove it.

---

### Post by el3ktro on 2006-03-07
This fstab line is correct. Did you copy your files over?

Well a better idea would be to mount /dev/hda5 to /home, NOT to /home/simon.


Tom

---

### Post by _simon_ on 2006-03-07
I tried mounting the partiton as /media/P1 so i could copy stuff accross.

it won't let me copy the files... it has root permission only.


How do i change this?

---

### Post by _simon_ on 2006-03-07
not sure what i have done now or how i get around it but...

(gedit:9529): Gtk-WARNING **: cannot open display:
simon@ubuntu:~$ sudo gedit /etc/fstab
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


Been back through the failsafe terminal and removed that line from fstab again as it wouldn't let me do anything.

---

### Post by _simon_ on 2006-03-07
i'm confused!!!!

mounted the partition as:

/dev/hda5 /media/P1 defaults 0 0 

It wouldn't let me do anything unless i was root. I managed to change this using chmod.

I just tried to copy the contents of home to the partition and was told there wasn't enough space.

Partition is 15Gig

I checked and it claims Home takes 46Gig
My drive has 30Gig free

How is this possible when my linux drive is only 40gig!?

---

### Post by _simon_ on 2006-03-07
i am such a twat... worked it out.

I have my Xp drive mounted in home so it's taking that into account.

---

### Post by el3ktro on 2006-03-07
Hi,
okay I'll try to help you.

First of all, you should do EVERYTHING as root, and you should NOT be logged in as user "simon". So first enable the root account:

sudo passwd

This asks for your password first, and then you have to enter a new password for root twice. Now log out, and then log in back as user "root".

First, mount your NEW home partition to /media/P1, just as you did it, good idea. Then create a new directory "simon" on this NEW partition, do this with

mkdir /media/P1/simon

Then change the permissions of this new directory, because it has to belong to the user "simon":

chown simon:simon /media/P1/simon

Now this directory belongs to the user simon.
Now copy all files from your OLD home directory /home/simon over to your NEW home directory /media/P1/simon. The best thing is to do this with cp -a, so all file perms/timestamps etc. are preserved.

Now your fstab line must read:

/dev/hda5 /home ext2 defaults 0 0

IF your OLD home dr is on a seperate partition, then umount it first:

umount /home

(skip this if your OLD home is NOT on a separate partition. Then now mount your NEW home directory:

mount /dev/hda5

If you now do ls -l /home you should see a directory "simon" which belongs to "simon:simon" and you should see your files in it.

Now log out as root and log in as simon again and you should be done!


Tom

---

### Post by Mustard on 2006-03-07
Just as an aside, root login via the gdm login screen is disabled by default.  So 'logging out and logging in again as root' would not work unless gdm root login is enabled.  An easier way might be to use ctrl + alt + f1 to get to a terminal and login to root that way.

If you really must login in via the gdm login screen, you would need to go to System>>Adminstration>>Login Screen Setup, then go to the 'Security' tab, and tick the box labelled 'Allow root login with GDM'.  This is not a method that is highly recommended, as it's disabled in Ubuntu for various reasons relating to security and safe usage of the system.

---

### Post by _simon_ on 2006-03-07
not having much luck.

I followed your instructions step-by-step and logged in as root using ctrl alt f1

the contents of home is now located at media/p1/simon

but ubuntu doesn't seem to see this as the home directory - i have lost all my settings and clicking on the Places -> Home Folder brings up a home folder with just desktop in

I think the partition IS now home and i just need to copy the files back? - copied files back but no joy.

This is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/WinXP    ntfs    nls=utf8,umask=0222        0       0
/dev/hda5	/home		ext2	defaults	0	0

```

---

### Post by _simon_ on 2006-03-07
home folder seems ok now but still lost all my settings.

can't find a way to restore them so putting them back manually....

EDIT: found my settings! for some reason they didn't all copy back across to home!

thanks a lot for your help.

---

