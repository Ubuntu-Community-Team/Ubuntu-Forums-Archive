---
title: "changing the name of an auto mounted USB device"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2006-01-27
Hi there,

I have an external usb hard drive (1) that shows up on my desktop (and in media) and as "WD USB 2"

I'd like to share the contents of folders on this drive with other machines on my network using NFS. However, I am having problems getting NFS to work though as the name of the drive has spaces in it. 

The drive is not in my fstab, (as it automatically is recognised I saw no need to put it in.) Should it be there?

Is there any way I can rename the drive? I have tried parsing " " marks into the mount syntax on the other machine, but that didnt work. 

Also, this is sort of related.....

I am not if sure if this a bug but if I select a folder (say /crap) on the usb drive and right click on Nautilus to set up a NFS share, the applet defaults to the drive name and not the folder. So in my case I get the abridged drive name ( /WD ) and not ( /crap )

any ideas? thanks in advance :D

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=pompeyjohn]Hi there,

I have an external usb hard drive (1) that shows up on my desktop (and in media) and as "WD USB 2"

I'd like to share the contents of folders on this drive with other machines on my network using NFS. However, I am having problems getting NFS to work though as the name of the drive has spaces in it. 

The drive is not in my fstab, (as it automatically is recognised I saw no need to put it in.) Should it be there?

Is there any way I can rename the drive? I have tried parsing " " marks into the mount syntax on the other machine, but that didnt work. 

Also, this is sort of related.....

I am not if sure if this a bug but if I select a folder (say /crap) on the usb drive and right click on Nautilus to set up a NFS share, the applet defaults to the drive name and not the folder. So in my case I get the abridged drive name ( /WD ) and not ( /crap )

any ideas? thanks in advance :D[/QUOTE]

Basically, I think if you change the name of the drive, it mounts with that name.  If it is a MS-DOS style filesystem, the mtools package will help you.

---

### Post by pompeyjohn on 2006-01-27
[QUOTE=cwaldbieser]Basically, I think if you change the name of the drive, it mounts with that name.  If it is a MS-DOS style filesystem, the mtools package will help you.[/QUOTE]

Cool that would work... I think. I could then give it a simple one word name which hopefully will

a. work with a mount command
b. let me NFS share sub folders on that drive - I am guessing it is the spaces in the drive name that breaks this.

that would be awesome :D 

There are no problems with NFS sharing a folder on a usb drive are they? I cant see why there should be.

I have just downloaded mstools, and I am looking into it - but I am a little lost as to how I can use it to rename the (fat32) drive. Any further advice much appreciated.

For example:

```
# # First SCSI hard disk partition
# drive c: file="/dev/sda1"
```

That has me confused. I can see how you could use it to map a ms drive to a linux point. But this drive already mounts into ubuntu automatically. It is right there under places.

There must be some sort of ID it is giving ubuntu which ubuntu then uses to call it WD USB 2. Which leaves me with 2 options that I can see

1. Find out how the drive sends that info - and change in on the drive, so ubuntu displays the new name. Could be tricky as I guess it is hardcoded.

2. Find out how ubuntu takes that drive name info, and hardcode a rewritten drive name. I would have no idea how to do this.

If there is another way - I would love to hear about it. Frustratingly the rename item in Nautilus' right click menu is greyed out. Oh if only.... sigh.

Perhaps a solution would be to add another layer of abstraction so that the system knows the device as XXX - and the user can rename it to whatever. Then again, perhaps this already happens and I have just not found the way yet!!!! :-D

---

### Post by pompeyjohn on 2006-01-29
Anyone?? I am digging around to try and find an answer to this - it is quite an urgent fix. All help and advice much appreciated.

---

### Post by pompeyjohn on 2006-02-01
somebody.... anybody ?! :)

---

