---
title: "Dapper can't mount 2nd hdb1"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-09-17
vBulletin Message

    Sorry - no matches. Please try some different terms. 

I have added a second harddisk to Ubuntu. It is formated in Linux/Ubuntu. Places/Computer shows the 2nd disk as: "33.6GB Volume". Attempting to open the volume returned:

[COLOR="DarkOrange"]error: device /dev/hdb1 is not removable

error: could not execute pmount[/COLOR]

It is my former boot disk. I only want to move /home to the new drive.

What command(s) are necessary?

---

### Post by Jose Catre-Vandis on 2006-09-17
Dapper seems to struggle to properly deal with an added second drive. You will need to manually edit your fstab to get it going properly.

First off, in a terminal, do the following:
```
sudo fdisk -l
```
this will show you the exact location and name of your second drive, in your case, most probably /dev/hdb1. OK now you have that:
```
 sudo mkdir /mnt/Drive2
```
(where Drive2 is the name you want for the second drive, whatever you want)
then
```
sudo gedit /etc/fstab
```
Add the line:
```
/dev/hdb1 /mnt/Drive2	ext3	defaults	0	2
```
(assumes your second drive is ext3)
now:
```
sudo mount -a
```
and you should have your new drive mounted, and you can get on with moving /home :D

---

### Post by Mark_in_Hollywood on 2006-09-17
Thanks, first.

Did as you had posted by "cutting and pasting" your instructions into a terminal, one line at a time.

Something went wrong. The drive is no longer listed.

Here is the Gedit of fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**/dev/hdb1 /mnt/drive2	ext3	defaults	0	2**

The 40gig drive (primary slave) has on it, an installation of Dapper that was working except for the modem. I suppose it's a ext3, but I don't know. A little more help, please.

---

### Post by bodhi.zazen on 2006-09-17
could be as simple as syntax. The instructions list "Drive2" with a capital D.

your fstab lists the mount point with drive2 or small d.

try changing your fstab to:
```
/dev/hdb1 /mnt/Drive2	ext3	defaults	0	2
```

you may want to change defaults to user which will allow users (rather then root) to mount the partition.

---

### Post by Mark_in_Hollywood on 2006-09-18
Thanks. Yet, I purposefully changed the "D" to a "d", because I already had a serious problem using a capital letter for the /home/Mark on a previous installation; that is: during the installation.

mark@lexington:~$ sudo /dev/hdb1 /mnt/Drive2ext3defaults02
Password:
sudo: /dev/hdb1: command not found

and

mark@lexington:~$ ls /dev/hd*
/dev/hda   /dev/hda2  /dev/hdb   /dev/hdb2  /dev/hdb5  /dev/hdd
/dev/hda1  /dev/hda5  /dev/hdb1  /dev/hdb3  /dev/hdc

How do I change who can mount a device other than root and does that mean that unless user=root the 2nd drive cannot be accessed?

suggestions welcome!

---

### Post by bodhi.zazen on 2006-09-18
First, you have the format a little off.

The command is```
mount <device> <mount point>
```

Thus it should read:```
sudo mount /dev/hdb1 /mnt/Drive2
```

Second, you access via the mount point and NOT the device.

Thus ```
ls /mnt/Drive2
``` and [color=red]not ls /dev/hdb1.[/color]

Last, to allow users to auto mount, edit fstab:
```
/dev/hdb1 /mnt/Drive2	ext3	user	0	0
```

Do not know why you had the "2", but I think it should be "0".

---

### Post by Mark_in_Hollywood on 2006-09-19
Did all as you suggested. At first, sudo mkdir  /dev/hdb1 /mnt/Drive2
returned a "permissions" error. So I cd /mnt and ran the line again. Success!

Then followed:

mark@lexington:/mnt$ ls /mnt/Drive2

bin    dev   initrd      lost+found  opt   sbin  tmp  vmlinuz
boot   etc   initrd.img  media       proc  srv   usr
cdrom  home  lib         mnt         root  sys   var


Added the line to fstab and then sudo mount -a

the second hard disk drive is not appearing in Place/Computer although one of the partitions is appearing 2.9GB Volume, by name. It, was like the former, which was the name 33.6GB Volume. Opening that 2.9GB Volume returned:

Unable to mount the selected volume.
error: device /dev/hdb3 is not removable

error: could not execute pmount

Any ideas appreciated.

---

### Post by Irony on 2006-09-19
First make the directory;

[PHP]sudo mkdir /mnt/Drive2[/PHP]

then mount it;
[PHP]
sudo mount /dev/hdb1 /mnt/Drive2[/PHP]

You should then see it in folder /mnt/Drive2, this assumes you've formatted as ext3.

Note if you have several partitions on the second drive you will have to repeat the procedure for each partition.

---

### Post by Jose Catre-Vandis on 2006-09-19
Please try doing exactly as I posted in the first place and it will work, for hdb1. if you want to mount specific partitions on the second drive, then you will need to change the names accordingly. Always remember to create a directory to mount to before you try the mount command.

To create a directory you only need this syntax:
```
sudo mkdir /mnt/mydirectory
```
to mount a directory your fstab only needs this syntax:
```
/dev/hdb1 /mnt/mydirectory ext3 defaults 0 2
```

Please follow the syntaxes indicated from me or bohdi.zazen as this will help to get things working for you

---

### Post by Mark_in_Hollywood on 2006-09-19
José

I did as your first response said. I did it by "cutting and pasting". I now note some small discrepencies from expected. And post them, quoting you (red letters) first, below:

[COLOR="Red"]First off, in a terminal, do the following:

sudo fdisk -l 

this will show you the exact location and name of your second drive, in your case, most probably /dev/hdb1. OK now you have that:[/COLOR]

returned:

mark@lexington:/$ sudo fdisk -l

Disk /dev/hda: 10.2 GB, 10202050560 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1185     9518481   83  Linux
/dev/hda2            1186        1240      441787+   5  Extended
/dev/hda5            1186        1240      441756   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4390    35262643+  83  Linux
/dev/hdb2            4773        4865      747022+   5  Extended
/dev/hdb3            4391        4772     3068415   83  Linux
/dev/hdb5            4773        4865      746991   82  Linux swap / Solaris

Partition table entries are not in disk order

[COLOR="Blue"]Please note that /dev/hdb1 is not what was returned, it was only /dev/**hdb**[/COLOR]

As the next command of your is to [COLOR="Red"]sudo mkdir /mnt/Drive2[/COLOR], this cannot be repeated, I paste the output of

mark@lexington:/$ **ls /mnt/Drive2**
bin    dev   initrd      lost+found  opt   sbin  tmp  vmlinuz
boot   etc   initrd.img  media       proc  srv   usr
cdrom  home  lib         mnt         root  sys   var

mkdir would not work, returning a permission denied until I cd/mnt and then issued mkdir.

Next:

[COLOR="Red"]sudo gedit /etc/fstab[/COLOR]

returned

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

to which was added

[COLOR="Red"]/dev/hdb1 /mnt/Drive2	ext3	defaults	0	2[/COLOR]

making:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

[B]## line below added to read 40gig drive by mp 9/17/06

/dev/hdb1 /mnt/Drive2	ext3	defaults	0	2[/B]

and I note that the line reads: [COLOR="DarkOrange"]/dev/hdb1[/COLOR], and not [COLOR="DarkOrange"]hdb[/COLOR]

[COLOR="Red"]assumes your second drive is ext3[/COLOR]

**as the drive being mounted is a former boot drive and was installed less than a week ago, maybe it has hda formatting on it?**

Lastly:

[COLOR="Red"]sudo mount -a[/COLOR]

which returned me to the prompt:

mark@lexington:/$

Looking into Places/Computer shows that there is a 2.9GB Volume, clicking on it returns 

Unable to mount the selected volume

error: device /dev/hdb3 is not removable

error: could not execute pmount

This is all I can give. I've done what I have seen, but admit I'm only human and even though "cut and paste" should work. I've done what I could to both understand and apply your excellent thoughts but as of yet, I don't have command of this problem.

Have you any more ideas?

---

### Post by crokett on 2006-09-19
> **Mark_in_Hollywood said:**
> José
/dev/hdb1 /mnt/Drive2	ext3	defaults	0	2[/B]


Well here you are attempting to mount /dev/hdb1.  This is the first partition on your 2nd hard disk, hdb

[QUOTE=Mark_in_Hollywood]

Looking into Places/Computer shows that there is a 2.9GB Volume, clicking on it returns 

Unable to mount the selected volume

error: device /dev/hdb3 is not removable

error: could not execute pmount
[/QUOTE]

This is telling you that the third partition could not be mounted.  Is this a typo or is that the actual error message? 

You can also try the mount command manually before adding to fstab:

sudo mount /dev/hdb1 /mnt/Drive2 and see if you can mount it

---

### Post by xpod on 2006-09-19
Cheers folks....worked for me with the wee hd i just stuck in our Kubunto.
Terminal spat a few errors back at me using "kate" for the editing but it still all seemed to work ok as it`s all mounted with the solitary "lost & found" file in it.
Just to move the "home" over now..
Ive had a bit of experience trying that before so should be okay.

Something "right" first time for a change:D 
Good luck pal,hope you get sorted ok

---

### Post by Mark_in_Hollywood on 2006-09-19
[QUOTE=crokett;1519087]Well here you are attempting to mount /dev/hdb1.  This is the first partition on your 2nd hard disk, hdb

This is telling you that the third partition could not be mounted.  Is this a typo or is that the actual error message? 

[COLOR="Red"]This is the "actaul error message". That is to say: it is the message received from Places/Computer and scrolling the mouse cursor over the icon named 2.9GB Volume and clicking on that icon.[/COLOR]

You can also try the mount command manually before adding to fstab:

mark@lexington:~$ sudo mount /dev/hdb1 /mnt/Drive2
mount: /dev/hdb1 already mounted or /mnt/Drive2 busy
mount: according to mtab, /dev/hdb1 is already mounted on /mnt/Drive2

but, (and now I'm SOOO confused), the disk is installed, wired up and powered up. I don't know if it's mounted or unmounted, so your idea about "manually [mount] before adding to fstab:" is confounding in it's inexplicablity. Am I to unmount by removing the line from the fstab or what?

Repeat: I'm a newbie with less than 6 months with Ubuntu and Linux.

---

### Post by xpod on 2006-09-19
> 6 months with Ubuntu and Linux.
THATS all ive had of pc`s in total.4 months of m.e\xp and 2ish of Ubu\kub 
Dont give up:D ..

---

### Post by Jukey on 2006-09-19
wow...

well, you're lucky. you didn't get sucked in to badly by windows XP in those 4 months. i've been using windows daily for the past 5 years. Swithing to linux is a big feat after you've been in windows for so long and everybody you know is running windows


and i believe this is the website for you, Mark:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by bodhi.zazen on 2006-09-19
> **Mark_in_Hollywood said:**
> [QUOTE=crokett;1519087]Well here you are attempting to mount /dev/hdb1.  This is the first partition on your 2nd hard disk, hdb

This is telling you that the third partition could not be mounted.  Is this a typo or is that the actual error message? 

[COLOR="Red"]This is the "actaul error message". That is to say: it is the message received from Places/Computer and scrolling the mouse cursor over the icon named 2.9GB Volume and clicking on that icon.[/COLOR]

You can also try the mount command manually before adding to fstab:

mark@lexington:~$ sudo mount /dev/hdb1 /mnt/Drive2
mount: /dev/hdb1 already mounted or /mnt/Drive2 busy
mount: according to mtab, /dev/hdb1 is already mounted on /mnt/Drive2

but, (and now I'm SOOO confused), the disk is installed, wired up and powered up. I don't know if it's mounted or unmounted, so your idea about "manually [mount] before adding to fstab:" is confounding in it's inexplicablity. Am I to unmount by removing the line from the fstab or what?

Repeat: I'm a newbie with less than 6 months with Ubuntu and Linux.

Not to be offensive, but the above output clearly states the partition is mounted.

Try ```
ls /mnt/Drive2
```

Also try reading a little.

---

### Post by Mark_in_Hollywood on 2006-09-19
Per:

ls /mnt/Drive2

returns:

mark@lexington:~$ sudo ls /mnt/Drive2
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz


so, if it is mounted, why can't it be opened/browsed? Or please give me the command line commands, such as ls /hdb/???

As for reading a little, I've looked at:

man mount (very technical and no clear examples)

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
(excellent if you are using windows and linux, not helpful here)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

the above mostly deals again with using windows, which I do not have any of. (thank you very much). 

The Ubuntu WIKI/Manual has nothing significant. I know that this isn't a "unique" problem, but please, a little more help.

---

### Post by crokett on 2006-09-19
> **Mark_in_Hollywood said:**
> 
but, (and now I'm SOOO confused), the disk is installed, wired up and powered up. I don't know if it's mounted or unmounted, so your idea about "manually [mount] before adding to fstab:" is confounding in it's inexplicablity. Am I to unmount by removing the line from the fstab or what?


/etc/fstab is for Linux to know what to mount where when it boots.  Adding a filesystem to fstab does not mount it until you either mount manually or reboot. 


Google or man pages the mount and umount commands.

```
mount
``` will tell you what is mounted to what mount point
```
sudo umount /dev/sdb1
``` will unmount /dev/sdb1 

```
ls -l /mnt/Disk2
``` will list the contents assuming something with a valid filesystem is mounted there.

After the filesystems are mounted you still may not have rights to access them.

Google or man pages chown and chgrp and do some reading on Linux permissions in general

---

### Post by xpod on 2006-09-19
> well, you're lucky. you didn't get sucked in to badly by windows XP in those 4 months.

They were both pretty messed up and the xp especially was badly infected with many other probs.I spent 4 months learning all about viruses,spyware,dehyjacking,Dodgy dll`s and the obligatory BSOD`s..

Hence the reason i discovered FF,TB then pretty soon after that ISO`s and Ubunto 

And here i am....It`s hard and frustraiting and i still dont know my alsa`s from my oss or my gnome from my nano???

It`s great fun finding out though!!!!

Keep at it!!!Dont give up on a good thing(FREE TOOOOOOO!!!):D

---

### Post by Jose Catre-Vandis on 2006-09-19
> **Mark_in_Hollywood said:**
> Per:

ls /mnt/Drive2

returns:

mark@lexington:~$ sudo ls /mnt/Drive2
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz


so, if it is mounted, why can't it be opened/browsed? Or please give me the command line commands, such as ls /hdb/???

As for reading a little, I've looked at:

man mount (very technical and no clear examples)

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
(excellent if you are using windows and linux, not helpful here)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

the above mostly deals again with using windows, which I do not have any of. (thank you very much). 

The Ubuntu WIKI/Manual has nothing significant. I know that this isn't a "unique" problem, but please, a little more help.

So it looks like hdb1 is mounted given the output of ls /mnt/Drive2. In a terminal, type:
```
nautilus /mnt/Drive2
```

What do you get?  ( I hope you are on ubuntu and not kubuntu ;) )

---

### Post by bodhi.zazen on 2006-09-19
LOL  :lol:

Make that ```
gksudo nautilus /mnt/Drive2
```

Read.... read.... read...

Permissions perhaps?

To answer your next question:

Add```
/dev/hdb1 /mnt/Drive2 ext3 auto,user 0 0
```To fstab.
:lol:(sudo gedit /etc/fstab):lol:


Then```
sudo umount /mnt/Drive2
mount /mnt/Drive2
nautilus /mnt/Drive2
```

to display the contents of /mnt/Drive2.

---

### Post by Mark_in_Hollywood on 2006-09-20
SUCCESS!


I added another line to the /etc/fstab. I renamed the hdb1 to hdb3 on that line. For some strange reason, I can now read/write to 2.9GB Volume. That is all I needed to get this mess cleaned up.

thank you one-and-all.

---

### Post by Jose Catre-Vandis on 2006-09-21
All's Well That End's Well :lol:

---

