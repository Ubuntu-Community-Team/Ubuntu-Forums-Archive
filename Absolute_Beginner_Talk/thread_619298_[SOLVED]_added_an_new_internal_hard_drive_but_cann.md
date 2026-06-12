---
title: "[SOLVED] added an new internal hard drive but cannot use it"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by rexxxlo on 2007-11-21
ok so i added a a160 gig drive yesterday and i m having troubles 

here was how i did it 
it was an ntfs drive so i moved all of the data off of it then used gparted to delete the ntfs prtition
then used gparted to create a partition of the whole drive ext3 format witch was a successful operation

i have followed this [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) tutorial but i am confused n what these commands mean and what to do from this point.......

So now I'll create a mount point for that partition:
sudo mkdir /storage

Then I'll edit my /etc/fstab file:
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab

Once in there, I should add in this line:
/dev/hda5 /storage ext3 defaults 0 0

Then I can save (Control-X), confirm (Y), and exit (Enter).

Since we've made changes to the /etc/fstab file, we need to have Ubuntu acknowledge those changes:
sudo mount -a

Now I need to give it the proper permissions. Let's just assume, for this example, that my username is marie.
sudo chown -R marie:marie /storage
sudo chmod -R 755 /storage

Now the partition is mounted in the /storage folder and is ready for use!

---

### Post by twiceasworn on 2007-11-21
Ok, What is happening exactly that is causing it not to work?  Are you getting an error of some sorts?

---

### Post by Inxsible on 2007-11-21
So have you used those commands yet?

and it still doesnt work for you? I am sorry I don't exactly get where you are stuck. are you getting errors?

---

### Post by rexxxlo on 2007-11-21
well actually i cant find it to tell you what is happening 

gparted tells me that i have  dev/sdb1 is formatted to ext3 and is un mounted

it also will not highlight the option to mount the drive 

i have had this problem before but i am not sure what to do to use this drive or where /how to mount it

---

### Post by Inxsible on 2007-11-21
If your drive is named **sdb1 **and you put in **hda5** in the fstab, it wont work. Make sure you put the same drive name

---

### Post by PurposeOfReason on 2007-11-21
Post the output of 

sudo fdisk -l

---

### Post by rexxxlo on 2007-11-21
> **Inxsible said:**
> So have you used those commands yet?

and it still doesnt work for you? I am sorry I don't exactly get where you are stuck. are you getting errors?

no i haven't used these commands i don't want to mess anything up by using the wrong commands  im still very shaky with the terminal

here are the results of that command 

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fc52fc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38184   306712948+  83  Linux
/dev/sda2           38185       38913     5855692+   5  Extended
/dev/sda5           38185       38913     5855661   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed31ed31

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cb9708e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30515   245111706    7  HPFS/NTFS

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29561760

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       35753   287185941   83  Linux
/dev/sdd2           35754       36481     5847660    5  Extended
/dev/sdd5           35754       36481     5847628+  82  Linux swap / Solaris

Disk /dev/sde: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe93a112c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       48640   390700768+   7  HPFS/NTFS


---

### Post by PurposeOfReason on 2007-11-21
How many hard drives do you have and what is the size of the one you just added? This is saying you have four. .

---

### Post by Inxsible on 2007-11-21
> **PurposeOfReason said:**
> How many hard drives do you have and what is the size of the one you just added? This is saying you have four. .5 actually.

sda - 320 GB - is all EXT3 with Ubuntu installed on it

sdb - 160 GB - EXT3

sdc - 251 GB - NTFS with a Windows installation

sdd - 300 GB - is EXT3 again with probably another installation

sde - 400 GB is NTFS with a boot flag - Windows installation


Am I correct? So which is the new drive that you just added? and you have 4 different OS'es on your machine?

---

### Post by rexxxlo on 2007-11-21
i have   5 

a 300 gig seagate with the os on it 
a 160 gig wd that is the one i just formatted
a 320 gig wd with the firs attempt of ubuntu on it haven't decided what to do with it exactly just yet
a 250 gig ntfs (storage) until i figure out how to reformat and partition correctly
and an external 400 gig ntfs 


the 160 gig is the drive i am working on    /dev/sdb1  i believe?

---

### Post by PurposeOfReason on 2007-11-21
> **Inxsible said:**
> 5 actually.

sda is all linux with Ubuntu installed on it

sdb

sdc

sdd

sde is NTFS
Dang, I counted wrong.  OP, add this to your fstab, not what you did before.

/dev/sdb1 /storage ext3 defaults 0 0

Then run:

sudo chown -R YOURUSERNAME:YOURUSERNAME /storage
sudo chmod -R 755 /storage

---

### Post by Inxsible on 2007-11-21
so then simply use the commands that you had in your first post and replace hda5 with sdb1. If you want to change the mount point, you can change that too from /storage to whatever you want, for instance /media/storage or /media/movies or whatever you see fit. Just make sure you change it all through the commands.

---

### Post by rexxxlo on 2007-11-21
> **PurposeOfReason said:**
> Dang, I counted wrong.  OP, add this to your fstab, not what you did before.

/dev/sdb1 /storage ext3 defaults 0 0

Then run:

sudo chown -R YOURUSERNAME:YOURUSERNAME /storage
sudo chmod -R 755 /storage

k this is where i get lost ? how do i add that to fstab and where do i do it ? 

im sorry i totally new to this terminal stuff and feel really stupid.....is there a plae where i can learn  what al of the commands mean and what they do ?

---

### Post by rexxxlo on 2007-11-21
> **Inxsible said:**
> so then simply use the commands that you had in your first post and replace hda5 with sdb1. If you want to change the mount point, you can change that too from /storage to whatever you want, for instance /media/storage or /media/movies or whatever you see fit. Just make sure you change it all through the commands.

the stuff in my first post were form psychocats and his tutorial it wasnt my exact words per say  


[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

this is what is confusing me 

i see that people know what to replace in a command and what not to 
i dont know what the command is saying so i cant know what to replace

---

### Post by PurposeOfReason on 2007-11-21
> **rexxxlo said:**
> k this is where i get lost ? how do i add that to fstab and where do i do it ? 

im sorry i totally new to this terminal stuff and feel really stupid.....is there a plae where i can learn  what al of the commands mean and what they do ?
Just do a google search for 'linux terminal commands'.

In the terminal type ```
sudo gedit /etc/fstab
```. What that means is 
sudo - super user do. It give you root privileges 
gedit - use the text editor gedit. You can use many like nano, vim, leafpad. Gedit is default with ubuntu so stick with it, it's really great.
/etc/fstab. That is the location of the fstab file.

---

### Post by PurposeOfReason on 2007-11-21
> **rexxxlo said:**
> the stuff in my first post were form psychocats and his tutorial it wasnt my exact words per say  


[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

this is what is confusing me 

i see that people know what to replace in a command and what not to 
i dont know what the command is saying so i cant know what to replace
Okay, I'll explain their thing bit by bit. Then it's off to school so I hope this helps.

**sudo fdisk -l** Posts the output of all the storage devices it finds.
**sudo mkdir /storage** This makes a new directory located at /storage.
**sudo cp /etc/fstab /etc/fstab_backup** This copies your /etc/fstab folder to /etc/fstab_backup. This is incase the poop hits the fan, you can replace the broken one with this one you saved.
**/dev/hda5 /storage ext3 defaults 0 0** This is what you add to the /etc/fstab. It goes in the order: mountpoint (which you should change to the one you're using, where to mount it (the directory you created), how it is formatted (extension three), and then what parameters to use.
**sudo mount -a** Puts the new changes into effect by rereading the file.
[b]sudo chown -R marie:marie /storage[b] Change marie to your user name. This will let you have access to the directory '/storage'.
**sudo chmod -R 755 /storage** Let's you write to the directory '/storage'.

---

### Post by Inxsible on 2007-11-21
to summarize :
open a terminal and type in```
gksudo gedit /etc/fstab
``` Then add the following line to the file```
/dev/sdb1 /storage ext3 defaults 0 2
``` Save and close the file.

Now back in the terminal```
sudo mkdir /storage
``````
sudo mount -a
```That should do it

If you want to change the location of the mount point, i.e. from /storage to say /media/storage or whatever, do it, but make sure you change it appropriately in all places.

Since you created the folder, you should have the appropriate permissions on the mount point already

---

### Post by rexxxlo on 2007-11-21
ok now that i created the file in storage and i can see it there is 1 folder lost+found and if i right click it tells me there are 139 gig free sounds about right so far 

but if i try to create a file or move data there it will not let me paste in to that folder

looks like i have some serious reading to do

---

### Post by Inxsible on 2007-11-21
> **rexxxlo said:**
> ok that created the file in storage and in that fil there is 1 folder lost+found and if i right click it tells me there are 139 gig free sounds about right so far 

but i i try to create a file or move data there it will not let me paste  in to that folder

looks like i have some serious reading to doOk, I guess you need to change permissions
```
sudo chown -R <your-username>:<your-username> <path to mount point>
```So assuming that you mounted to /storage and that your username is rexxxlo, it would be```
sudo chown -R rexxxlo:rexxxlo /storage
```

---

### Post by rexxxlo on 2007-11-21
lolo@lolo-desktop:~$ sudo chown -R <lolo>:lolo /storage
bash: lolo: No such file or directory
lolo@lolo-desktop:~$ sudo chown -R <lolo>:<lolo><storage>
bash: syntax error near unexpected token `<'
lolo@lolo-desktop:~$ sudo chown -R <lolo>:<lolo> <storage>
bash: syntax error near unexpected token `<'
lolo@lolo-desktop:~$

---

### Post by Inxsible on 2007-11-21
> **rexxxlo said:**
> lolo@lolo-desktop:~$ sudo chown -R <lolo>:lolo /storage
bash: lolo: No such file or directory
lolo@lolo-desktop:~$ sudo chown -R <lolo>:<lolo><storage>
bash: syntax error near unexpected token `<'
lolo@lolo-desktop:~$ sudo chown -R <lolo>:<lolo> <storage>
bash: syntax error near unexpected token `<'
lolo@lolo-desktop:~$
you dont need the <> signs in the command, please check the example I gave you again.

---

### Post by rexxxlo on 2007-11-21
well it works now don't i feel dumb duhhhh   

thank you for your extreme patience and understanding

it is transferring the files now

---

### Post by Inxsible on 2007-11-21
> **rexxxlo said:**
> well it works now dnt i feel dumb duhhhh   

thank you for your extreme patience and understanding

it is transferring the files now
Sweet !!!

Mark your thread solved :D

---

### Post by geirha on 2007-11-21
One final thing, you should change the line in fstab to read
```
/dev/sdb1 /storage ext3 defaults 0 **2**
```

The difference beeing the 2 which I've highlighted in bold font. The last number tells ubuntu whether it should attempt to do a filesystem check during startup (if that time is due). 0 means don't ever do a filesystem check, 1 means first priority, only the partition mounted as / should have this. 2 means second priority, which all other ext3 should have. (NTFS and FAT partitions should always have 0 though, leave filesystem checking of those types of filesystems to windows)

You really want to have your ext3 filesystems checked regularily.

---

### Post by Inxsible on 2007-11-21
> **geirha said:**
> One final thing, you should change the line in fstab to read
```
/dev/sdb1 /storage ext3 defaults 0 **2**
```The difference beeing the 2 which I've highlighted in bold font. The last number tells ubuntu whether it should attempt to do a filesystem check during startup (if that time is due). 0 means don't ever do a filesystem check, 1 means first priority, only the partition mounted as / should have this. 2 means second priority, which all other ext3 should have. (NTFS and FAT partitions should always have 0 though, leave filesystem checking of those types of filesystems to windows)

You really want to have your ext3 filesystems checked regularily.You are right. Glad you caught that. I will change it in my instructions too. :D

---

### Post by rexxxlo on 2007-11-21
oki will but now this leads me to another question that i will start another thread for 

thanks all who helped 

ubuntu is getting easier everyday

---

### Post by blop on 2007-11-23
thank you all contributors this helped me mount a freshly installed hard disk with an ext3 partition....

---

### Post by rexxxlo on 2007-11-24
ok when i create a file why can i not use it ? or not copy files to that folder or create folders in that folder i created ?sudo fdisk -l

i have been trying to create files and folders i succeede on creating them with the 

sudo mkdir /media/movies 

but i cant use the folder?

why is this ???

---

### Post by geirha on 2007-11-24
Firstly, by default, a fresh ext3 filesystem will only be readable and writable by root.

Secondly, when creating a directory with sudo mkdir, you create it as root, and it will only be readable and writable by root. You need to change ownership of the directory. The easiest way of doing this is by running nautilus as root: ```
sudo nautilus
``` browse to the file(s) and/or folder(s) you want to have access to, right click -> properties -> permissions, and set your user as the owner.

---

### Post by rexxxlo on 2007-11-24
wow that was helpful 

in the huge world of Linux i couldn't find anything about that anywhere

---

### Post by rexxxlo on 2007-11-24
can i mount 2 drives to this location?

i just tried and now i cant seethe files that i just put there

---

### Post by geirha on 2007-11-24
You can mount two filesystems to the same folder, yes. No files will be lost, but you will only see the files of the last filesystem mounted.

---

### Post by rexxxlo on 2007-11-24
ok so every drive should be mounted to a different place if i want to use the files?

---

### Post by geirha on 2007-11-24
Yes, typically you create a directory in /media/ for each partition you want to mount, and then add the proper lines in /etc/fstab

---

### Post by rexxxlo on 2007-11-24
ok in the confusion i think i have made a mistake in the 
etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=60f74535-e82e-416a-baed-939a117ef4de /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c29bcbc1-2102-4298-af29-2a934f9e8141 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/sde1 /media/sde1 ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
/dev/hda5 /home/movies ext3 defaults 0 2
/dev/sdd1 /home/movies ext3 defaults 0 2
/dev/sdc1 /home/movies2 ext3 defaults 0 2


and this is the fdisk -l output  
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed31ed31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fc52fc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38184   306712948+  83  Linux
/dev/sdb2           38185       38913     5855692+   5  Extended
/dev/sdb5           38185       38913     5855661   82  Linux swap / Solaris

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cb9708e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30515   245111706   83  Linux

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29561760

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36481   293033601   83  Linux

Disk /dev/sde: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe93a112c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       48640   390700768+   7  HPFS/NTFS
lolo@lolo:~$ gksudo gedit /etc/fstab




it seems to me that this is a problem

/dev/hda5 /home/movies ext3 defaults 0 2

does that look right? i don't think it should be there

and the last time i rebooted i got an error about a file system being corruptedand to run fsck(i think that is what it was called) manually

---

### Post by geirha on 2007-11-24
just removing the /dev/hda5 should hopefully fix it. /dev/hda is apparently one of your cdroms, so /dev/hda5 can definitively not be a legal partition.

fsck is short for file system check. Remove the hda5-line in your fstab, boot, and if the fsck message comes again, write it down and post it here.

Everything else looks good.

---

### Post by rexxxlo on 2007-11-25
ok i get it its ll working pretty good now

that sudo nautilus thing helped didn't know about that yet

thank you for clarifying that for me

---

