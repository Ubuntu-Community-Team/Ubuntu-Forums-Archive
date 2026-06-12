---
title: "USB Label can be listed but the not found by mount command"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by jadedjay on 2006-11-04
Can anybody help me with this as I am lost for ideas ?

I followed this excellent "How to fstab" [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
in order to mount my USB drives based on their label.

All the commands/instructions seemed to work fine until the final mount command which returned.
"mount: special device LABEL=AUDIO does not exist."

My first approach was:
$ ls /dev/disk/by-label
AUDIO  GENERAL  HDREC  U  VISUAL
Then edit my /etc/fstab to include

LABEL=AUDIO /media/audio vfat defaults,uid=1000,gid=1000,auto,rw,nouser 0 0
LABEL=VISUAL /media/visual vfat defaults,uid=1000,gid=1000,auto,rw,nouser 0 0

Then
$ sudo mount LABEL=AUDIO
mount: special device LABEL=AUDIO does not exist.
didnt work so I tried
$ sudo mount -a
mount: special device LABEL=AUDIO does not exist.
mount: special device LABEL=VISUAL does not exist.
which seems strange when I can list the device by its label.

So I tried using the mtools solution (following the "how to")

$sudo aptitude install mtools
$cp /etc/mtools.conf ~/.mtoolsrc

Mount the usb drive.
$sudo mount /dev/sda1 /media/audio

Edit ~/.mtoolsrc:
drive i: file="/dev/sda1"

$ mcd i:
$ mlabel -s i:
 Volume label is AUDIO
$ sudo umount /media/audio
$ sudo mount LABEL=AUDIO
mount: special device LABEL=AUDIO does not exist

So now I am a little confused. Both methods of listing the LABEL return the correct LABEL, but I am unable to Mount the device based on the LABEL.
Any ideas???  ](*,)

---

### Post by jadedjay on 2006-11-15
Any ideas on this one?
I could try mounting the devices by their UNIQUE ID however they are USB External drives from the same company and have the same ID.
I would really like to mount them via the LABLE as their device definition (/dev/sd?1) keeps changing.](*,)

---

### Post by bodhi.zazen on 2006-11-15
Try this fstab line:> LABEL=AUDIO /media/audio vfat uid=1000,gid=1000,noauto,umask000 0 0

You can also try by UUID

ls /dev/disk/by-uuid

Then mount UUID=xxxxx /media/audio

fstab: > UUID=xxxxx /media/audio vfat uid=1000,gid=1000,noauto,umask000 0 0

where xxxx is the uuid if your usb device

Example:

bodhi@Arch:~$sudo mount UUID=8093-8F05 /media/mobile/

---

### Post by jadedjay on 2006-11-15
> **bodhi.zazen said:**
> Try this fstab line:

You can also try by UUID

ls /dev/disk/by-uuid

Then mount UUID=xxxxx /media/audio

fstab: 

where xxxx is the uuid if your usb device

Example:

bodhi@Arch:~$sudo mount UUID=8093-8F05 /media/mobile/
Thanks. I think there is a typo in the first quote

LABEL=AUDIO /media/audio vfat uid=1000,gid=1000,noauto,umask**=**000 0 0

I added this to my fstab and then at the prompt ran
sudo mount -a
but the tested USB drive wasnt mounted

I have just now noticed that if I do
sudo mount -L AUDIO /media/audio
it works fine 

Does this give you any other ideas on how just set my fstab so that the drives are mounted when Kubuntu boots?   
Or am I misunderstanding how the mount command works?

---

### Post by bodhi.zazen on 2006-11-15
Interesting....

If you want the usb devices to automount at boot add auto the options in fstab...


LABEL=AUDIO /media/audio vfat uid=1000,gid=1000,**auto**,umask=000 0 0

Also try mounting without sudo

mount -L AUDIO


or **mount /media/audio**   <-- This may be your best bet :p


or mount -L AUDIO /media/audio


Sorry about the typo :redface:

---

### Post by jadedjay on 2006-11-22
Thanks those suggestions helped a bit.

I actually ended up re-installing Dapper and found that my USB external drives are automatically mounted and mapped under /media/LABEL_NAME. 
So at the moment they are working like that with the line in /etc/fstab.

However Im not really sure why they are working like that now, and not in my previous install of Dapper.  I must have changed some default setting.  

Its working so dont touch it, I guess.

---

