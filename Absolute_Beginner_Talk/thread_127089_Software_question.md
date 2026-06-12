---
title: "Software question"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by z|x on 2006-02-08
Just wanted to know if an application/software made for other linux systems like SUSE, Mandrake... will work for Ubuntu??? If so, is it the same for drivers too??

---

### Post by matthewv on 2006-02-08
It should, however, due to a different package management system and directory structure on ubuntu and suse and mandriva, etc. it may not be very easy to get working. Both mandriva and suse use the rpm package format, and to install rpms you'll need to use the command line tool alien (run "sudo apt-get alien" (without quotes) from commandline, and then run from command line "sudo alien <packagename.rpm>" , replacing <packagename.rpm> witht the package you want to install)

---

### Post by z|x on 2006-02-08
k

Another question, Now I have windows and ubuntu installed on 2 diffrent partitions. and there are another 2 partitions that have my stuff. Is there anyway that i can access those 2 partitions from Ubuntu??

---

### Post by Jimmey on 2006-02-08
Yeha, through a process called mounting.

You have to find the address of the partition you want to mount using the command 

>  sudo fdisk -l 

That should provide a list of partitions, and they're filesystems. Then, once you've figured out which partition ( format dev/hdaX, where X is the number of the partition ), you can then enter the mount command into the terminal.

First, you need to make a directory to mount the files to:

>  sudo mkdir /nameOfTheNewFile 

Then, you need to mount the partition to that folder, the general format of which is as follows: 

>  sudo mount -t <filesystemType> /dev/hdaX /nameOfTheFolderYouCreated

And example of this in action is: 
>  sudo mount -t ntfs /dev/hda2 /windows
Sorry to make it long winded, but I hope it helps :)

---

### Post by bartbes on 2006-02-08
[quote=Jimmey]and they're filesystems[/quote] sorry that I have to correct it, but my instict (as a bilangual student) says that it is wrong it's: their.

You can also mount the filesystems in fstab to mount them on startup, there's a nice 'guide' ion how to do this on ubuntuguide.org. [the guide](http://ubuntuguide.org/#automountntfs) (for windows partitions)
for linux partitions do something like this: ```
/dev/<drive>       <mount point>               ext3    defaults 0       0 
``` (if it's ext2 change ext3 in ext2 the same for other sorts of file systems)

---

### Post by az on 2006-02-08
[QUOTE=z|x]Just wanted to know if an application/software made for other linux systems like SUSE, Mandrake... will work for Ubuntu??? If so, is it the same for drivers too??[/QUOTE]

It probably will not.  It will work if you get the source code and compile it on your ubuntu box.

A precompiled binary (a package) made for another distro will have different dependancies and probably have different configurations which may make your system do funny things.  Stay away from packages that were compiled for other distributions.

If you want something that is not already available to you from the ubuntu archives, get the source and compile it yourself.  That will just about always work.  If it can't work (because it's improperly made, too old, uses unavailable libraries...) , a precompiled package would not work either.

---

### Post by z|x on 2006-02-08
Ok, I'll try the partitioning part. 

The worst thing is that I can't go on the internet thru ubuntu because I use a dial-up connection.

azz, I do not know head or tail about programming/compiling for Ubuntu Linux or any other Linux distros. So is there any place where I can request for them?? Also, I checked the page for downloading drivers for my Nvidia graphics card and there it has drivers for Linux IA32, Linux IA64, Linux AMD64/EM64T, FreeBSD x86, Solaris x64/x86. I guess the Linux IA32 will suite my config. But will it work with Ubuntu?? Nothing is mentioned about which distro it has been made for.

---

### Post by z|x on 2006-02-08
[QUOTE=Jimmey]Yeha, through a process called mounting.

You have to find the address of the partition you want to mount using the command 



That should provide a list of partitions, and they're filesystems. Then, once you've figured out which partition ( format dev/hdaX, where X is the number of the partition ), you can then enter the mount command into the terminal.

First, you need to make a directory to mount the files to:



Then, you need to mount the partition to that folder, the general format of which is as follows: 



And example of this in action is: 

Sorry to make it long winded, but I hope it helps :)[/QUOTE]
I tried that method but it doesnt work. When I go to the folder that was made, it is always empty.

---

### Post by z|x on 2006-02-09
Another problem I found out is that I cant even use my floppy drive In ubuntu. I get the error message saying that this device is unmountable.

---

