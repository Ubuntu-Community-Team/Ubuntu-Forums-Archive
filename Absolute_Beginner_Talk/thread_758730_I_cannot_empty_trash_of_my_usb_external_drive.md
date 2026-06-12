---
title: "I cannot empty trash of my usb external drive"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by cseljatib on 2008-04-18
Hi there,
I have a WD250GB usb external unit. It has vfat format.

I am not able to empty its trash, because appear a message that says that the files are in a read-only disk. 

I do not how to change that. I already type in the terminal
sudo chown -R yourusername:yourusername /media/[mountpoint]

then I own everything on that partition (o disk)

Here some outputs that might help

* here it is the output of $mount, (regarding the disk) is
/dev/sdc1 on /media/WD250CSE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

* the output of $ls -ld ~/.Trash
drwx------ 2 christian christian 4096 2008-04-17 12:48 /home/christian/.Trash

* lsattr -d  ~/.Trash
------------------ /home/christian/.Trash

Thank you in advance for your help

---

### Post by kbless7 on 2008-04-18
I don't know if its a permission problem, but this command with help with that part of emptying trash in ubuntu.

```
rm -rf ~/.Trash/*
```

---

### Post by quirks on 2008-04-18
@kbless7: using your command, you would empty your local trash (the one in your profile). But as far as I know, Nautilus creates a .Trash folder on each drive. So the trash cseljatib is trying to empty is probably somewhere here: /media/WD250CSE/.Trash

@cseljatib: can you provide us with the output of the following command:
> ls -l /media/WD250CSE/.Trash

I don't see any problem at the moment.

quirks

---

### Post by cseljatib on 2008-04-18
hey guys,
regarding kuirks, here is the output of $ls -l /media/WD250CSE/.Trash-christian/, please noticed that i could not use $ls -l /media/WD250CSE/.Trash

total 672
drwx------  6 christian root 32768 2008-04-10 11:54 04conference (copy)
drwx------  3 christian root 32768 2008-04-18 00:43 aifbn
drwx------  3 christian root 32768 2008-04-18 00:52 aifbn (copy)
drwx------  2 christian root 32768 2008-04-14 17:18 amsn_received
drwx------  2 christian root 32768 2008-04-14 17:18 amsn_received (copy)
drwx------ 16 christian root 32768 2008-04-18 00:44 articles
drwx------  4 christian root 32768 2008-04-18 00:52 articles (copy)
drwx------  6 christian root 32768 2007-11-06 10:25 auctex-11.84
drwx------  2 christian root 32768 2008-03-26 11:33 bajados_momentaneos
drwx------  2 christian root 32768 2008-03-26 11:33 bajados_momentaneos (copy)
drwx------  2 christian root 32768 2008-03-19 11:50 diameter growth
drwx------  7 christian root 32768 2008-03-26 11:33 dissertation
drwx------  7 christian root 32768 2008-03-26 11:33 dissertation (another copy)
drwx------  7 christian root 32768 2008-03-26 11:33 dissertation (copy)
drwx------  4 christian root 32768 2007-11-06 10:35 ecb
drwx------  3 christian root 32768 2008-04-18 09:42 flyback
drwx------  3 christian root 32768 2008-01-21 11:49 myPChome_backup1
drwx------  2 christian root 32768 2007-10-25 11:57 noUsados
drwx------  3 christian root 32768 2007-11-06 10:39 orgmode
drwx------  2 christian root 32768 2008-04-18 00:43 PDF
drwx------  2 christian root 32768 2008-03-26 11:33 viajeChileMarch2008 (copy)


and what i did as kbless said, it runs, but cannot remove because 'Read-only file system'


PLEASE, help me

c

---

### Post by aysiu on 2008-04-18
You can't *chown* a FAT32 partition. It needs to be mounted with the right permissions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by milton1 on 2008-04-18
Sounds like your usb drive was mounted read-only. You will need to unmount it, then re-mount it as read/write. Then you should gain access to the trash folder.

---

### Post by racoq on 2008-04-18
> **cseljatib said:**
> hey guys,
regarding kuirks, here is the output of $ls -l /media/WD250CSE/.Trash-christian/, please noticed that i could not use $ls -l /media/WD250CSE/.Trash

total 672
drwx------  6 christian root 32768 2008-04-10 11:54 04conference (copy)
drwx------  3 christian root 32768 2008-04-18 00:43 aifbn
drwx------  3 christian root 32768 2008-04-18 00:52 aifbn (copy)
drwx------  2 christian root 32768 2008-04-14 17:18 amsn_received
drwx------  2 christian root 32768 2008-04-14 17:18 amsn_received (copy)
drwx------ 16 christian root 32768 2008-04-18 00:44 articles
drwx------  4 christian root 32768 2008-04-18 00:52 articles (copy)
drwx------  6 christian root 32768 2007-11-06 10:25 auctex-11.84
drwx------  2 christian root 32768 2008-03-26 11:33 bajados_momentaneos
drwx------  2 christian root 32768 2008-03-26 11:33 bajados_momentaneos (copy)
drwx------  2 christian root 32768 2008-03-19 11:50 diameter growth
drwx------  7 christian root 32768 2008-03-26 11:33 dissertation
drwx------  7 christian root 32768 2008-03-26 11:33 dissertation (another copy)
drwx------  7 christian root 32768 2008-03-26 11:33 dissertation (copy)
drwx------  4 christian root 32768 2007-11-06 10:35 ecb
drwx------  3 christian root 32768 2008-04-18 09:42 flyback
drwx------  3 christian root 32768 2008-01-21 11:49 myPChome_backup1
drwx------  2 christian root 32768 2007-10-25 11:57 noUsados
drwx------  3 christian root 32768 2007-11-06 10:39 orgmode
drwx------  2 christian root 32768 2008-04-18 00:43 PDF
drwx------  2 christian root 32768 2008-03-26 11:33 viajeChileMarch2008 (copy)


and what i did as kbless said, it runs, but cannot remove because 'Read-only file system'


PLEASE, help me

c

HI, this is my guess

You could check your pen for a physical switch (a some sort of write protected  switch). The reason is that some pens use a switch to protect the data to read-only access , in order of preventing you to acidently erase information that is critical. You may acidentaly turned it on and that may be preventing you from writing and erasing things to your pen.

If it's not the case, and it's a lack of permission,  then try this in the console

sudo rm -rf /media/WD250CSE/.Trash-christian/

---

### Post by aysiu on 2008-04-18
> **racoq said:**
> 
If it's not the case, and it's a lack of permission,  then try this in the console

sudo rm -rf /media/WD250CSE/.Trash-christian/ If you decide to go this route, be *very* careful when typing. If you accidentally hit the Enter key too early, you can be deleting more than the contents of your trash.

As a matter of fact, it's probably safer to launch a root-privileged file browser and then navigate to the trash and delete it: ```
gksudo nautilus
```

---

### Post by cseljatib on 2008-04-18
how can i do so milton1?

---

### Post by cseljatib on 2008-04-18
the racoq sintax does not work, i already tried. The usb unit does not have any switch

---

### Post by quirks on 2008-04-18
The thing that makes me wonder is that according to the output of mount in his first post, he should have write permissions (note the rw in the filesystem options). I suppose his account has an ID of 1000, so he should be the file owner as well.

> * here it is the output of $mount, (regarding the disk) is
/dev/sdc1 on /media/WD250CSE type vfat (**rw**,nosuid,nodev,shortname=mixed,**uid=1000**,utf8,uma sk=077,usefree)

If you want to unmount a filesystem and mount it again in read-write mode you can use this procedure:
1. Right-click the drive in Nautilus and select unmount.
2. Enter the following command in a terminal.
```
sudo mount -t vfat -o rw /dev/sdc1 /mnt/some_mount_point
```
You will have to create the directory /mnt/some_mount_point before you can do this, if it is not already there.
3. You can then launch Nautilus as root and empty the trash manually as demonstrated by aysiu.

However, as I already said, you should have the proper permissions.

@cseljatib: by the way, can you create any files on the USB stick? Because if so, you should also be able to delete them. Technically there are no different rights required for deleting files than for creating files.

quirks

---

