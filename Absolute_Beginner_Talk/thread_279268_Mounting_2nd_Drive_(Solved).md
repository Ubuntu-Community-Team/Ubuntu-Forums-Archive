---
title: "Mounting 2nd Drive (Solved)"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Voyageur on 2006-10-17
I have just got a second drive which I reformatted to Ext3 and is hdc1.
This is mounted on /media/Drive2 as below:

Filesystem            Size Used Avail Use% Mounted on
/dev/hda1              18G   16G  1.5G  92% /
varrun                125M  128K  125M   1% /var/run
varlock               125M  4.0K  125M   1% /var/lock
udev                  125M  108K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   19M  107M  15% /lib/modules/2.6.15-27-386/volatile
/dev/hdc1              28G  129M   26G   1% /media/Drive2

What I want is this drive to be available as a drive on my desktop.

Any suggestions?

---

### Post by bulldog on 2006-10-17
You can try in gconf-editor apps-nautilus-desktop and look at volumes visible.

ALT-F2  gconf-editor.

---

### Post by Voyageur on 2006-10-17
This is set to true.

I'm not sure if there is a problem with the mounting.

FSTAB reads:
/dev/hdc1    /media/Drive2  etc3  defaults,errors=remount-ro 0 0

---

### Post by bulldog on 2006-10-17
Is it seen in your /media folder and accesable?

---

### Post by Voyageur on 2006-10-17
Drive2 is in my media folder and is accesable.
It has a Lost+Found flder in it

---

### Post by bulldog on 2006-10-17
Well maybe you can make a Icon yourself on your desktop.

Right click the desktop and choose new starter and fill in the form,choose an Icon and maybe it works that way,haven't try it myself though.

---

### Post by aysiu on 2006-10-17
Maybe you should change this: ```
/dev/hdc1 /media/Drive2 etc3 defaults,errors=remount-ro 0 0
``` to this ```
/dev/hdc1 /media/Drive2 ext3 defaults 0 0
```

---

### Post by Voyageur on 2006-10-17
Looks like a more fundamental issue.
When I copy a file into media/Drive2 it doesn't go onto my second hard drive. It's still adding to my 1st drive.?!?

---

### Post by Voyageur on 2006-10-17
Great news - I have a drive mounting on the desktop called Drive2

However, when i try to copy into it I get the error

Error while copying to "/media/Drive2".
You do not have permissions to write to this folder.

This is where I get lost - if I created the drive then surely I have full read/write access?

---

### Post by starsky on 2006-10-17
> **Voyageur said:**
> I have just got a second drive which I reformatted to Ext3 and is hdc1.
This is mounted on /media/Drive2 as below:

[.....]

What I want is this drive to be available as a drive on my desktop.

Any suggestions?

Hi,
Try
 sudo mount -ro -t ext3 /dev/hdc1 /media/Drive2 (this will go in your command-line). This will mount /dev/hdc1 as read only on your mount point "/media/Drive2". After successful mount, anything in your /media directory will appear on your desktop. 

if you want this to happend automagically when the computer boots, then "sudo gedit /etc/fstab" (Alt+F2),
and add this entry in your last line (without the line beginning with "#", which is a comment.).

# <file system> <mount point>   <type>  <options> <dump>  <pass>
/dev/hdc1 /media/Drive2 ext3  defaults,errors=remount-ro 0  1

if you want in depth, knowledge then start with man mount.

But I am sure this should suffice just for mounting ext3 partition.

Hope it helps.

---

### Post by starsky on 2006-10-17
> **Voyageur said:**
> Great news - I have a drive mounting on the desktop called Drive2

However, when i try to copy into it I get the error

Error while copying to "/media/Drive2".
You do not have permissions to write to this folder.

This is where I get lost - if I created the drive then surely I have full read/write access?

Hi,
Not necessarily. :D  if you mount it with read-only, then it won't be writable, you must do "mount -rw -t ext3 /dev/hdc1 /media/Drive2".

Hope it helps.

---

### Post by Voyageur on 2006-10-17
I did a sudo chown and everything is fixed

Thanks to you all

---

