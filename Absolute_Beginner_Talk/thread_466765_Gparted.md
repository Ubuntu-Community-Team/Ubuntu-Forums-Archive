---
title: "Gparted"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Noyminibin on 2007-06-07
I have a second hard drive that i want to wipe and use to keep files on, it still has some old windows files on how do i wipe it with Gparted. I want to make sure i know what im doing before i go ahead and end up ballsing it up

---

### Post by Inxsible on 2007-06-07
Put in your GParted LiveCD or simply use the GParted available on the Ubuntu LiveCD. Select the drive you want to format, select the file system and hit ok.

If its an external drive, make sure it connected of course :)

all done !

---

### Post by buuntuu! on 2007-06-07
best is to download the last version of gparted [here]("http://gparted.sourceforge.net/index.php") and read the documentation. it's quite easy, have fun

---

### Post by Noyminibin on 2007-06-07
I tride to wipe it and i get the following error

The following operation could not be applied to disk:

Create Primary Partition #1 (ext3, 149.01 GiB) on /dev/sdb

See the details for more information

Can some one give me total noob directions on how to wipe it so that it is totally clean so i can then start to drag siles on to it like videos and stuff

---

### Post by darren1270 on 2007-06-07
You can download killdisk at [http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm) create the .iso and boot from it...It will let you choose what you want to delete... the free version will support only one pass but worked for me!

Good Luck
Darren

---

### Post by Noyminibin on 2007-06-07
i wiped the hard drive now all i have is a lost and found folder in it for some reason but then i go to drag something in to it it comes up 


Error while copying to "/media/disk".
You do not have permissions to write to this folder.

---

### Post by Songwind on 2007-06-07
By default, you only have write permissions to your home directory.

You can add read, write, execute permissions for all users on that disk by issuing this command:

```

sudo chmod -R a+rwx /media/disk

```

That tells the system to add those permissions to /media/disk and all subdirectories.  I don't advise doing this to your whole filesystem - sometimes it's a good thing you can't accidentally overwrite files in the system directories. :)

---

