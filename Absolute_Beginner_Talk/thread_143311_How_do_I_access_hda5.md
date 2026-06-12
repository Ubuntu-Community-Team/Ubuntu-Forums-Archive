---
title: "How do I access hda5"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by don cole on 2006-03-12
It shows up on my desktop but when I drag anything too it ,it says no permision granted. Under properties it says it's owner is 'root'.
My user name is 'don'.
I tried to change the owner name to 'don'. But it said I couldn't do that.

Any help please,

Don Cole

---

### Post by knalle on 2006-03-12
hda5 sounds like its a ntfs partition or a vfat partition without access rights set in the mount command in **/etc/fstab**, try **man mount** and read about mountoptions for ntfs and vfat

---

### Post by don cole on 2006-03-12
Thank you knalle,

You're absolutely right hda5 is a vfat partition.

when I /etc/fstab, I get acess denied.

When I lookup fstab with the fine files feature. 

hda5 is in there as a vfat type.

Now what do I do. 

I have a problem I can't go on line with ubuntu, so I have to keep booting back and forth to windows to test things.


Don Cole

---

### Post by kittycatsexycat on 2006-03-12
why not try just opening it with root and changing the permissions then...

open the terminal and type...

sudo su
enter your password then type

nautilus

this give you your filesystem in a window... find that harddrive through that window and change permissions....

carefull though your in root....

sorry if that doesnt help...:KS

---

### Post by knalle on 2006-03-12
[QUOTE=don cole]Thank you knalle,

You're absolutely right hda5 is a vfat partition.

when I /etc/fstab, I get acess denied.

When I lookup fstab with the fine files feature. 

hda5 is in there as a vfat type.

Now what do I do. 

I have a problem I can't go on line with ubuntu, so I have to keep booting back and forth to windows to test things.

Don Cole[/QUOTE]

first find your UID and GID;

```
id don
``` i get this: uid=1000(karl) gid=1000(karl)

then do ```
sudo emacs /etc/fstab
``` (or use any other editor than emacs) and edit the hda5 entry to contain this after the **defaults** text.

```
uid=1000,gid=1000,umask=002
```

replace 1000 with your UID and GID

use umount to ```
sudo umount /dev/hda5
``` and ```
sudo mount -a
``` to reload fstab

Happy Hacking

---

### Post by xmastree on 2006-03-12
For the easy way, put this line in your /etc/fstab file:
```
/dev/hda5	/your/mount/point	vfat	umask=000	0	0
```
Then do the sudo mount -a thing.

---

### Post by knalle on 2006-03-12
but can't everybody read and write to it then?

---

### Post by xmastree on 2006-03-12
Yep, is that a problem? I guess it depends on Don's requirements.

---

### Post by don cole on 2006-03-12
Thanks everyone for the responses,

I don't care who read and writes to my drive as long as I can.

I'm going to try xmastree's easy way. I'll get back to you. I'm sure I'll have problems.
But I have to do something else right now.

Don Cole

---

### Post by don cole on 2006-03-13
The first link you sent me to and results.
Q: How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write?
Assumed that /dev/hda1 is the location of Windows partition (FAT) --ok Ill go along with that (I know I'm looking at hda5 but it really dosen't matter)
Local mount folder: /media/windows-- I don't know (how would I know?).


sudo mkdir /media/windows--that works 
sudo cp /etc/fstab /etc/fstab_backup--I don't have permission to do that.
sudo gedit /etc/fstab--that seems to work 

I re-booted and a still can't drag to that drive.

---

### Post by xmastree on 2006-03-13
[QUOTE=don cole]
Local mount folder: /media/windows-- I don't know (how would I know?).[/quote]It's your call. That's one of the nicer things about linux compared to windows. If you install a new disk, **you** decide where it goes.

> sudo mkdir /media/windows--that works
That's the mount point created, but you can make that anything you like.

Before editing the fstab, try to mount it manually;
First, unmount it, if it's already mounted:
```
sudo umount /dev/hda5
```Then, mount it like this:```
sudo mount /dev/hda5 /media/windows -t vfat -o umask=000
```
That mounts it at /media/windows (the one you made earlier) -t, type, is vfat. -o, options, umask=000 is basically the same as setting all permissions to 777 to allow all access.

That ought to work.

If it does, then put this in your fstab, and remove any other references to hda5:```
/dev/hda5	/media/windows	vfat	umask=000	0	0
```And you should be good to go.

---

