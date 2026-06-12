---
title: "New hardrive"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by souteneur3190 on 2006-03-25
ok i have a new hardrive...its hdb according to device manager, and the disk manger reads it, how do i edit my fstab config?

---

### Post by NeghVar on 2006-03-25
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

That should get you started.

---

### Post by taurus on 2006-03-25
You cannot mount that new harddrive until you create a partition and format it first!  You can use fdisk to create a partition and mke2fs to format it...
```

sudo fdisk /dev/hdb
sudo mke2fs -j /dev/hdb1

```

---

### Post by souteneur3190 on 2006-03-25
malubankudi@ubuntu:~$ sudo fdisk /dev/hdb
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 24792.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): +



whats that?

---

### Post by NeghVar on 2006-03-25
ya its not set up at all, if you were running windows id say to go to your manufacturers site, they usually have a thing u download that will set up the hd so that it can be formatted, I know its probably the stupidest way to sell them but its the way they do it. I'm not sure what the linux equivalent would be.

---

### Post by souteneur3190 on 2006-03-25
how do i make one big partion?

---

### Post by taurus on 2006-03-25
[QUOTE=souteneur3190]malubankudi@ubuntu:~$ sudo fdisk /dev/hdb
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 24792.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): +

whats that?[/QUOTE]
Hit l for list of commands.  If you want to create a partition, use n.  Then p for primary and have it take the whole disk.  Then t to and then number 83--Linux!  Then type w to write and quit.  Then, if you do this at the prompt,
```

sudo fdisk -l /dev/hdb

```
you will see your your /dev/hdb1...

Now, it's time to format it with ext3 filesystem and mount it...
```

sudo mke2fs -j /dev/hdb1
sudo mkdir /media/second
sudo mount -t ext3 /dev/hdb1 /media/second

```

---

### Post by souteneur3190 on 2006-03-25
my goodness, i am having so much trouble with this, anyone wat to direct connect?

---

### Post by souteneur3190 on 2006-03-25
malubankudi@ubuntu:~$ sudo mke2fs -j /dev/hdb1
mke2fs 1.38 (30-Jun-2005)
Could not stat /dev/hdb1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
malubankudi@ubuntu:~$


Thats weired because I DO see it when I type sudo fdisk -l /dev/hdb.  I get this:

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1           24792       24792        8032+  83  Linux

---

### Post by GMachine_24 on 2006-03-25
Hi:

Try this:

Go to System>Administrationg>Disks

Sign in using your password

Check and see if the drive is listed and what its properties are.

Print the results here.

GM

---

### Post by taurus on 2006-03-25
[QUOTE=souteneur3190]malubankudi@ubuntu:~$ sudo mke2fs -j /dev/hdb1
mke2fs 1.38 (30-Jun-2005)
Could not stat /dev/hdb1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
malubankudi@ubuntu:~$


Thats weired because I DO see it when I type sudo fdisk -l /dev/hdb.  I get this:

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1           24792       24792        8032+  83  Linux[/QUOTE]

Maybe you have to reboot first!!!  ;)

---

### Post by souteneur3190 on 2006-03-25
Maxtor 6L200PO
189.92 GIB

Generial Information

Type HD
Device /dev/hdb
speed not avaiaible

partions:

freespace (this is what i see in the partions list)

---

### Post by souteneur3190 on 2006-03-25
rebooting...... see u in 2mins guys.

---

### Post by souteneur3190 on 2006-03-25
ok i see "second" in my computer, but it says i only have 6.4 mb left.

---

### Post by GMachine_24 on 2006-03-25
Have you thought of trying a program such as "QTParted"? It can partition and format a drive for you and you can download it using Synaptic

System>Administration>Synaptic Package Manager

enter your password

"Search" for QTParted

Mark it for installtion - click "apply".

After the program installs, you can find it in 

Applications>System Tools>QtParted

Run the program, highlight your drive and partition it, then format it.

---

### Post by GMachine_24 on 2006-03-25
[QUOTE=souteneur3190]ok i see "second" in my computer, but it says i only have 6.4 mb left.[/QUOTE]


Since you haven't partitioned or formatted your drive, I doubt the "second" that you are seeing is  your hdb drive.

---

### Post by souteneur3190 on 2006-03-25
wut do i do after using qtparted?

---

### Post by souteneur3190 on 2006-03-25
ok problem solved...but how do i get permissions to write and everything?.

---

### Post by GMachine_24 on 2006-03-25
to enable read, write and execute permissions for everyone you can 

sudo chmod 777 /dev/hdb
sudo chmod 777 /dev/hdb1

To be honest, I'm never sure which one it is that works. You might have to reboot for it to take effect.

[I really should know this.]

---

### Post by souteneur3190 on 2006-03-25
lol yah im done with partioning and formating, wut next.

---

### Post by souteneur3190 on 2006-03-25
and as for the fstab config file?

---

### Post by GMachine_24 on 2006-03-25
forget what i wrote here.

---

### Post by GMachine_24 on 2006-03-25
You need to create a "mount point" ... so


sudo mkdir /data1 (or choose another name)

then mount the new partition

sudo mount -t ext3 /dev/hdb1 /data1 (or whatever name you chose)

test for read, write and exe capacities

then in /etc/fstab

**sudo gedit /etc/fstab**

add this line at the bottom

**/dev/hdb1              /data1            ext3    defaults        1        2**

with 'data1' being the name of the mount point your chose

oh yeah - sorry - then "save" the changed fstab file.

you can reboot to test if data1 is mounted on boot

---

### Post by souteneur3190 on 2006-03-25
every time i try to mount it says its already mounted, but i dont see it in my computer.

---

### Post by GMachine_24 on 2006-03-25
You need to give some exact information please, e.g. can you cut and paste the input/output from the terminal (command line) window?

Also, if you click on 

Places>Computer>File System

do you see your mount point/directory  there?

You can also go back to

System>Administration>Disks

to check on the status of the drive/partition etc.

---

### Post by souteneur3190 on 2006-03-25
mount: /dev/hdb1 already mounted or /data1 busy
mount: according to mtab, /dev/hdb1 is already mounted on /data1

---

### Post by GMachine_24 on 2006-03-25
When you check

Places>Computer>File System

do you see the "data1" folder there? Can you open it if it's there?

---

### Post by souteneur3190 on 2006-03-25
yes

---

### Post by souteneur3190 on 2006-03-25
if I reinstall ubuntu... will all this be configured?

---

### Post by GMachine_24 on 2006-03-25
reinstall ubuntu? no. it won't be configured. but it seems you have successfully enabled your hdb drive.

---

### Post by souteneur3190 on 2006-03-25
when i go to disks im even able to system, browse the hardrive, I can even move my movies to the hardrive. i just cant seam to mount it and I dont know what the problem is...can it be jumpers or anything of that nature?

---

### Post by souteneur3190 on 2006-03-25
i found a way to use my hardrive, i went to system devices and then browed my drive.  I made a link called movies and put it on my desktop...this should be ok, until i have the strenth to troubleshoot this again.

---

### Post by GMachine_24 on 2006-03-26
Trust me, your hard drive is mounted. Otherwise you would not be able to read/write to the drive. Either you mounted it with a command line command or you added a line to /etc/fstab which causes the drive to be mounted each time you boot. Or perhaps QTParted does this automatically - I can't remember.

If you added the line mentioned previously to /etc/fstab the drive should be mounted automatically on each subsequent reboot. If you don't believe me, do this:

sudo gedit /etc/fstab

and put a # before the line which specifies your hdb drive to be mounted. Save the fstab file and reboot the computer. Your hdb drive and folders (such as your movies folder) will be inaccessible.

If you do the above you will need to go back into /etc/fstab

sudo gedit /etc/fstab

and remove the # you put before the line which tells Ubuntu to mount your hdb drive. Don't forget to save the file again after removing the # and your drive will be mounted on all subsequent reboots.

[NOTE: I don't advise messing around this much with the fstab file. If your drive mounts and you can access its mount point directory - which you said you can - then I would let well enough alone and just enjoy it.]

---

### Post by souteneur3190 on 2006-03-28
im about to switch back to windows... i just cant seam to get this to work, its driving me crazy.  After I did my little system>disks trick (where i clicked browse on my hardrive and i made a folder, than made a link to on my dekstop) Now I always have to type in the access path and press enable for it to work, this is kind of ridicoulus.  Are my jumper wrong?  I just dont know anymore.

---

### Post by souteneur3190 on 2006-03-28
I will remote desktop with anybody, because i just cant take this anymore.

---

### Post by souteneur3190 on 2006-03-29
Finnaly got it to work, I changed the accss math to media and I made my own folder there.  I edited the fstab myself and tried to make it look like the others.  Thank goodness.

---

