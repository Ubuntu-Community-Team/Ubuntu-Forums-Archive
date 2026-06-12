---
title: "HELP!! Macbook Dead......Need to back up hard drive"
date: 2008-09-22
forum: Apple Hardware Users
---

### Post by muzia22 on 2008-09-22
I used Ubuntu live cd on my dead macbook and it booted....i found i could access my HDD but i could not acces some files which are protected (music movies picture work) under a user account.....

I am completly new to ubuntu....

is there a way to access these files so i can back them up??

PS i do not kno **** about computer codes...so please be basic...


Thanks

---

### Post by ethoxyethaan on 2008-09-22
well if the hard disk is already mounted. you should just add a External Hard drive and copy the files from your Internal hard drive to your external hard drive.

you can both use the Graphical way and the command line way, I guess option 1 is best for you

open ubuntu go to >> accessories >> terminal.

in terminal type, 

```
sudo nautilus
```

drag and drop all the files needed to your external hard drive and unmount the volume when your done.

i hope this helps.

---

### Post by tiresia on 2008-09-22
To back up your Music Folder from your MacOSX Account you must use the 'cp' (copy) command with  'sudo' (it gives you superuser privileges - so that you can access anything on your HD). 
To mount your MacOSX Volume go to Places and just click on your HardDisk (it will be most probably listed as Disk1). If you type```
ls /media
``` you will find your Mac-HD.

The HD where you want to back up your data is also mounted on /media, maybe with the name disk2
If the name of your account on MacOSX is 'muzia22' run

```
sudo cp -r /media/disk1/Users/muzia22/Music /media/disk2
```
With this command you say that you want to Copy the Folder (therefore you have the option '-r') Music of the User 'muzia22' of the 'disk1' to the disk2. Change the names according to your data.

If you have still problems post us what you get from ```
ls -l /media
```

---

### Post by boombox1387 on 2008-09-22
I'm working on the same thing with a Windows computer (using a live CD to save everything that's on the hard drive), and I think most of this thread should probably be relevant for OSX and Windows.

I had a really hard time getting the Windows partition (hda1) to mount.  It kept giving me ntfs errors about hardware problems.  I was about to give up, when I ran gparted.  gparted found the partition and was able to mount a read-only version of it.  I browsed through the Windows file system and made sure everything looked intact, then I tried to copy it to an external drive.  It gave me an error saying that I was not allowed to copy from a read-only drive.

Any thoughts?

---

### Post by muzia22 on 2008-09-22
> **ethoxyethaan said:**
> well if the hard disk is already mounted. you should just add a External Hard drive and copy the files from your Internal hard drive to your external hard drive.

you can both use the Graphical way and the command line way, I guess option 1 is best for you

open ubuntu go to >> accessories >> terminal.

in terminal type, 

```
sudo nautilus
```

drag and drop all the files needed to your external hard drive and unmount the volume when your done.

i hope this helps.

what do u mean by mounted? sorry i dont really know computers that well



i can see the HDD....i can access all the files apart from the ones in user accounts.....they always say i dont have permission to veiw them....

---

### Post by cyberdork33 on 2008-09-22
> **muzia22 said:**
> i can see the HDD....i can access all the files apart from the ones in user accounts.....they always say i dont have permission to veiw them....
Your OS X users are not the same as the Ubuntu user, therefore according to the system, those files do not "belong" to you.

If you use root user permissions, you can access and copy ANY file. Running 'sudo nautilus' will open a file browser that has root permissions. You should be able to use that window to copy files off the hard drive and onto your backup.

---

### Post by muzia22 on 2008-09-22
> **cyberdork33 said:**
> Your OS X users are not the same as the Ubuntu user, therefore according to the system, those files do not "belong" to you.

If you use root user permissions, you can access and copy ANY file. Running 'sudo nautilus' will open a file browser that has root permissions. You should be able to use that window to copy files off the hard drive and onto your backup.


how do i get root user permissions?

---

### Post by tiresia on 2008-09-22
> **muzia22 said:**
> how do i get root user permissions?
Getting root user permissions means that you run a command with 'sudo'.
Therefore you must just run in a Terminal```
sudo nautilus
```

---

### Post by cyberdork33 on 2008-09-22
> **muzia22 said:**
> how do i get root user permissions?

> **cyberdork33 said:**
> Running 'sudo nautilus' will open a file browser that has root permissions. 


...

---

### Post by explorer59 on 2008-09-23
Can you be a little more descriptive about "dead"? You say that the computer will boot the Live CD and you can access the HDD. Did you have an Ubuntu-OSX dual-boot configuration? 

Do you have access to another Mac? If so, try putting your MacBook into Target Disk Mode and connect it to the other Mac.

---

