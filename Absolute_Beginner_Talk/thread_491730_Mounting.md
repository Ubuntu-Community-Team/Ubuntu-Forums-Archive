---
title: "Mounting"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-07-04
I use Ubuntu Studios and I'm not able to mount my ipod (5th G). It says That I am not privileged to do that.
 help.

---

### Post by KIAaze on 2007-07-04
How are you trying to mount it?

Usually to mount (by command-line) you use the following commands:
1)Determine the device name (ex: /dev/sdax):
```
sudo fdisk -l

```
2)Create the directory where it will be mounted
```
sudo mkdir /mnt/ipod
```
3)Mount the device:
```
sudo mount /dev/sdax /mnt/ipod
```
[B]edit:
Note that /dev/sdax is put here only as an example!!
You have to use the device name listed as HFS (supposing that the filesystem on your Ipod) in the list obtained from the previous command.
If you are not sure which device name to use post the output of "sudo fdisk -l" here.[/B]

To unmount:
```
sudo umount /mnt/ipod

```

---

### Post by CapitanYochua on 2007-07-04
after mounting I tried to transfer a .mp3 song and I got an "Error Transferring track" and it said it could not open file... I am using Rhythmbox Music for this. Using a different program help?

---

### Post by CapitanYochua on 2007-07-04
gtkpod didn't really work any better in this case.

---

### Post by alienexplorers on 2007-07-04
Did you start Ryhthmbox with gksudo.  This may give you the permission to transfer the mp3 files.

---

### Post by CapitanYochua on 2007-07-04
no...
So I would type in gksudo in the terminal and run "Ryhthmbox Music Player" as "root"?

---

### Post by alienexplorers on 2007-07-04
Yea.  Give it a try.  Can't hurt anything.

---

### Post by CapitanYochua on 2007-07-04
Nothing Happened...

---

### Post by CapitanYochua on 2007-07-04
Oh! When I did the sudo fdisk -l. My ipod was an /dev/sde2 rather than any sda. Any importance to that?

---

### Post by KIAaze on 2007-07-05
I don't know if it matters or not that it's sde.
I also don't have any experience at all with Ipods or any Apple hardware.

But I suppose your Ipod works like an HD probably formatted in HFS (Apple's filesystem).
[LIST=1]
[*]When you do "sudo fdisk -l", is it marked as being HFS?
[*]Could you please post the complete output of "sudo fdisk -l"?

[*]After mounting it, can you read from it?
Try ```
ls /mnt/ipod
``` to test this.

[*]After mounting it, can you write to it?
Try ```
touch /mnt/ipod/foobar
``` for example.
If that doesn't work try ```
sudo touch /mnt/ipod/foobar
```.
The "touch" command creates empty files.
To remove the created file afterwards, just use ```
rm /mnt/ipod/foobar
```
[/LIST]

[LIST]
[*]If you can't read from it->You might not have the necessary driver to read HFS
[*]If you can read from it but not write to it as user->check the folder permissions:
```
ls -ld /mnt/ipod/
```
To change them, you can use "chmod", "chgrp" and "chown" (or through the GUI: right-click->properties->permissions).
Info about file permissions:
[http://www.freeos.com/articles/3127/]("http://www.freeos.com/articles/3127/")
[*]If you can read from it but not write to it even as root->It might be mounted as read-only or you don't have a driver capable of writing to it
The "mount" command usually mounts as read/write by default, but to be sure, you could try using "mount -w" instead.
[/LIST]

If you can write to it with sudo, then running rythmbox with gksudo will probably work.
But I wouldn't recommend it as a permanent solution.

Some info about linux device naming and partition maps I found while searching for why it's sde and not sda:
[http://www.t2-project.org/handbook/html/t2.partition.apple.html]("http://www.t2-project.org/handbook/html/t2.partition.apple.html")
[http://publib.boulder.ibm.com/infocenter/dsichelp/ds8000ic/index.jsp?topic=/com.ibm.storage.ssic.help.doc/f2c_linuxdevnaming_2hsag8.html]("http://publib.boulder.ibm.com/infocenter/dsichelp/ds8000ic/index.jsp?topic=/com.ibm.storage.ssic.help.doc/f2c_linuxdevnaming_2hsag8.html")
[http://www.debian.org/releases/slink/m68k/mac-fdisk.txt]("http://www.debian.org/releases/slink/m68k/mac-fdisk.txt")

I haven't read through them completely, but maybe you'll find something useful there.

---

### Post by Outrunner on 2007-07-05
Obiviously, if the iPod is /dev/sde2 then you have to mount /dev/sde2 not /dev/sda. Actualy, I'm pretty sure /dev/sda was used just as an example

---

### Post by KIAaze on 2007-07-05
Yep, it was an example.
I edited my first post to make it more obvious. ^^'

But since the OP managed to determine that his device was /dev/sde2, I supposed he figured that out.

---

### Post by CapitanYochua on 2007-07-06
> **KIAaze said:**
> I don't know if it matters or not that it's sde.
I also don't have any experience at all with Ipods or any Apple hardware.

But I suppose your Ipod works like an HD probably formatted in HFS (Apple's filesystem).
[LIST=1]
[*]When you do "sudo fdisk -l", is it marked as being HFS?
[*]Could you please post the complete output of "sudo fdisk -l"?

[*]After mounting it, can you read from it?
Try ```
ls /mnt/ipod
``` to test this.

[*]After mounting it, can you write to it?
Try ```
touch /mnt/ipod/foobar
``` for example.
If that doesn't work try ```
sudo touch /mnt/ipod/foobar
```.
The "touch" command creates empty files.
To remove the created file afterwards, just use ```
rm /mnt/ipod/foobar
```
[/LIST]

[LIST]
[*]If you can't read from it->You might not have the necessary driver to read HFS
[*]If you can read from it but not write to it as user->check the folder permissions:
```
ls -ld /mnt/ipod/
```
To change them, you can use "chmod", "chgrp" and "chown" (or through the GUI: right-click->properties->permissions).
Info about file permissions:
[http://www.freeos.com/articles/3127/]("http://www.freeos.com/articles/3127/")
[*]If you can read from it but not write to it even as root->It might be mounted as read-only or you don't have a driver capable of writing to it
The "mount" command usually mounts as read/write by default, but to be sure, you could try using "mount -w" instead.
[/LIST]

If you can write to it with sudo, then running rythmbox with gksudo will probably work.
But I wouldn't recommend it as a permanent solution.

Some info about linux device naming and partition maps I found while searching for why it's sde and not sda:
[http://www.t2-project.org/handbook/html/t2.partition.apple.html]("http://www.t2-project.org/handbook/html/t2.partition.apple.html")
[http://publib.boulder.ibm.com/infocenter/dsichelp/ds8000ic/index.jsp?topic=/com.ibm.storage.ssic.help.doc/f2c_linuxdevnaming_2hsag8.html]("http://publib.boulder.ibm.com/infocenter/dsichelp/ds8000ic/index.jsp?topic=/com.ibm.storage.ssic.help.doc/f2c_linuxdevnaming_2hsag8.html")
[http://www.debian.org/releases/slink/m68k/mac-fdisk.txt]("http://www.debian.org/releases/slink/m68k/mac-fdisk.txt")

I haven't read through them completely, but maybe you'll find something useful there.

 Okay. Sorry for the late reply (I was out of town). Anyways. I was able to read it. But  only could  write it with the sudo (as root) and removed the written file with sudo as well.  I did gksudo rhythmbox music player, but it didn't detect my ipod like my own rhythmbox would. I was able to refer to various Ubuntu books while I was gone and most said that it is a simple plug, click and drag deal with feisty fawn.  Just in case, I will mention that I am using Ubuntu Studio. I was easily able to manage my ipod with my previous computer (which had feisty fawn). Oh, for all the data above I mounted it by doing.... sudo mount /dev/sde2 /mnt/ipod -o user. 
 Here is the pastebin of the fdisk -l:
[http://paste.ubuntu-nl.org/28905/plain/](http://paste.ubuntu-nl.org/28905/plain/)

 I haven't read all the links yet or looked into the chmod to change permissions and the such. I'll keep you updated.

---

### Post by macogw on 2007-07-07
Try it with Amarok.  In my experience, Rhythmbox doesn't know how to set up the database that the iPod needs to be able to sort by id3 tag, but Amarok works fine for it.  After you mount the iPod, can you do "gksu nautilus" and then in the Nautilus window that comes up right-click the iPod and give yourself permission to use it then try it through Amarok?

---

