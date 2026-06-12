---
title: "only root can mount /dev/sda1 on /media/sda1"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Kuraboy on 2006-08-25
Hi!

I just had a fresh new install of Ubuntu 6. And I had my external drive plugged in while I installed the os. 

after the install when I try to access the drive I get the message:

only root can mount /dev/sda1 on /media/sda1

why? It auto-mounted of it's on before. And this is a fresh install, I havnt changed any setting.

thnx in advance.

---

### Post by bodhi.zazen on 2006-08-25
Edit /etc/fstab and modify or add the line:
```
/dev/sda1 /media/sda1 auto user,noauto,rw,sync 0 0
```

use the options user,auto,rw,sync if you want to mount the USB drive automatically at boot.

To edit /etc/fstab
In a terminal:
```
sudo nano /etc/fstab
```
To exit nano: Type Ctrl-X, Y to save, N to exit without saving.

---

### Post by Kuraboy on 2006-08-25
hi, thnx for the fast reply.

the line in /etc/fstab is :

/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0    1

so should I delete it and add the line you provided, or edit it in someway.

thnx again ^_^

---

### Post by sultanoswing on 2006-08-25
> **Kuraboy said:**
> 

so should I delete it and add the line you provided, or edit it in someway.


Yes (asuming it's a vfat drive still!). The reason you can no longer mount it is because of the 'gid' tag, and since you've reinstalled, the gid has changed.

---

### Post by Kuraboy on 2006-08-26
Hi thnx for your help. 

my external drive is working.

I tryed to change the status of an ex3 drive (Ubuntu isn't installed on it) in fstab but it didn't work, when I open nautilus I couldnt create any files.

so then I opened nautilus in sudo mode and change the permission graphicly.
[I]
so dosnt nautilus read the fstab file? [/I]

another thing I noticed is that when I try to change the status of the external drive in nautilus it dosnt let me change anything, I mark a box and nautilus unmark it. why?

thnx

---

### Post by bodhi.zazen on 2006-08-26
I think now you are having a permissions problem which is different.
In a terminal:
Unmount your usb and ext3 drives.
```
sudo umount /media/sda1
sudo umount /location/ext3_mount_point
```

? mount point of ext3 drive, but use same general technique.
This sets the permissions of the mount point.
```
sudo chown root:user /media/sda1
sudo chmod 770 /media/sda1
```
owner remains root.

now mount your usb drive as a user
```
mount /media/sda1
```
Note: No sudo.

Should now be good to go.
Same steps with your ext3 drive.
If you share your ext3 drive across OS; use sudo chmod 777 .....

---

### Post by kopilo on 2006-09-01
Similar issue, except my hard-disk is internal, I followed these steps but I'm still unable to mount as user.

---

### Post by bodhi.zazen on 2006-09-01
> **kopilo said:**
> Similar issue, except my hard-disk is internal, I followed these steps but I'm still unable to mount as user.

What mount command are you using and what error message are you getting?

Steps:
1. Make mount point.
2. Set permissions.
3. Edit fstab.

Mount should look something like:
sudo mount /dev/hdb1 /media/hdb1

Use what name you like for "/media/hdb1"

If you can mount with the sudo command, edit /etc/fstab and you can either auto mount at boot or mount as a user.

---

### Post by baron_samedi on 2006-09-07
I have a related (but a bit different) problem: my box will mount my usb stick (/dev/sda1) okay, but I cannot umount it as user. Besides, it looks like the stick is not reading the /etc/fstab file when mounting.

Any idea?

---

### Post by bodhi.zazen on 2006-09-07
> **baron_samedi said:**
> I have a related (but a bit different) problem: my box will mount my usb stick (/dev/sda1) okay, but I cannot umount it as user. Besides, it looks like the stick is not reading the /etc/fstab file when mounting.

Any idea?
Either:

1. the drive is still in use. Are you accessing any files on the drive with nautilus, an editor, playing a MP3, is nautilus open to the usb drive?

Or

2. fstab is incorrect. 

If #2:
[list][*]you can unmount with sudo.
[*]edit/post fstab.[/list]

---

### Post by baron_samedi on 2006-09-07
I have no window opened on the usb stick and no program / player running on it that I am aware of. Yes I can umount it as root, but that is just, er... not cool. ;-) I want to click on the icon and go "umount".

A new funny thing I've found is that this is happening with just one of my usb sticks: a Packard Bell MP3 player. The other one (a regular stick), and the SD card from my camera work okay.

---

### Post by bodhi.zazen on 2006-09-07
> **baron_samedi said:**
> I have no window opened on the usb stick and no program / player running on it that I am aware of. Yes I can umount it as root, but that is just, er... not cool. ;-) I want to click on the icon and go "umount".

A new funny thing I've found is that this is happening with just one of my usb sticks: a Packard Bell MP3 player. The other one (a regular stick), and the SD card from my camera work okay.

With the problematic usb, check that it is recognized as /dev/sda1 and not /dev/sdb1 or something else.

For example, I have an external drive that is always recognized as "/dev/sda4", even when it is the only usb device attached. Why the 4? who knows (it has only a single partition). Any guess as to how long it took me how to configure fstab (Hint: It was some time ago and I was a newbie at at the time)?

---

### Post by baron_samedi on 2006-09-07
> **bodhi.zazen said:**
> With the problematic usb, check that it is recognized as /dev/sda1 and not /dev/sdb1 or something else.

Okay, lets see: the original line I had in my /etc/fstab was:

```

/dev/sda        /home/samedi/stick   vfat    rw,user,noauto  0       0
```

Whith just this line, my "good" stick mounts itself okay on /media/sda (which I can't find anywhere) but also on /home/samedi/stick (which is where I want it). Also, it unmounts okay as user.

However, my problematic stick (plugged in the same usb port) mounts itself on /media/sda1, but not on /home/samedi/stick. It wont't umount as user, but it will go away typing

```

# umount /dev/sda1
```

So I added a second line to the /etc/fstab, to make it look like this:

```

/dev/sda        /home/samedi/stick   vfat    rw,user,noauto  0       0
/dev/sda1     /home/samedi/stick   auto    rw,user,noauto  0       0
```

And then it is even worse, because my problematic usb opens up an **empty** window on /media/sda1, doesn't show up in /home/samedi/stick either, and besides, a dialog comes out with the message:

[B]mount: wrong fs type, bad option, bad superblock on /dev/sda,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so[/B]

!!!???

> **bodhi.zazen said:**
> For example, I have an external drive that is always recognized as "/dev/sda4", even when it is the only usb device attached. Why the 4? who knows (it has only a single partition). Any guess as to how long it took me how to configure fstab (Hint: It was some time ago and I was a newbie at at the time)?

Wouldn't dare to guess... it took me weeks to even figure out that /etc/fstab existed at all.

---

### Post by bodhi.zazen on 2006-09-07
It is times like these I wish I were smarter. #-o 
Thank you for your continued posts.

I think the problem is in a few tweaks:

First unmount all usb drives.
```
sudo umount /home/samedi/stick /media/sda1
```

Try:
```

/dev/sda        /home/samedi/stick_a   vfat    rw,user,noauto  0       0
/dev/sda1     /home/samedi/stick_a1   auto    rw,user,noauto  0       0
```

Or:
```

/dev/sda        /home/samedi/stick   auto    rw,user,noauto  0       0
/dev/sda1     /home/samedi/stick   auto    rw,user,noauto  0       0
```

Delete /media/sda1 [color=red]UNMOUNT YOUR MEDIA FIRST OR YOU MAY DELETE DATA[/color]:
```
sudo rm -r /media/sda1
sudo rm -r /media/sda
```

Now re-mount/re-try your USB devices. [-o< 

If this does not work there is a way of assigning a label to the usb devices, I do not recall it off the top of my head and would need to research.....

---

### Post by baron_samedi on 2006-09-08
> **bodhi.zazen said:**
> It is times like these I wish I were smarter. #-o 
Thank you for your continued posts.

You are helping me and you thank me for posting? you are cute... 

And you are smart, too :wink:: the first option you wrote worked alright:

```

/dev/sda        /home/samedi/stick_a   vfat    rw,user,noauto  0       0
/dev/sda1     /home/samedi/stick_a1   auto    rw,user,noauto  0       0
```

So that is it. Thanks, dude. (I'll give a go now to try and mount my PDA: if I don't get to do it i might open a new thread).

Cheers.

---

