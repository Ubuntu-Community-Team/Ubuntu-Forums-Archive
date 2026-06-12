---
title: "unable to access NTFS share over netatalk"
date: 2008-09-14
forum: Apple Hardware Users
---

### Post by Apocrathia on 2008-09-14
I have been in a transitional phase of moving my windows server over to linux, so I have a couple of ntfs shares setup that I would like to keep intact until I am able to move them onto a larger drive and centralize everything.
I have setup my AppleVolumes.default for the shares and they broadcase and show up fine in leopard finder, however whenever I go to access them I get an error that they couldnt be accessed because the original item couldnt be found. I ended up just sharing my /media/ folder and it works fine and I am able to get into everything, but if I do /media/drv1 which was my network drive, it wont read at all. weird. here is the bottom of my configuration file. I have commented out a few lines just to keep things working but have the lines of code intact until I need them.
```

/home/ian/"Time Machine"/ "Time Machine" cnidscheme:cdb options:usedots,upriv
/media/ "Network Share" cnidscheme:cdb options:usedots,upriv
# /media/drv0/"Documents and Settings"/Ian/"My Documents"/ "My Documents" cnidscheme:cdb options:usedots,upriv
# /media/drv0/"Documents and Settings"/"All Users"/Documents/ "Documents" cnidscheme:cdb options:usedots,upriv

```
any ideas? I am planning on getting a 1tb drive, formatting it fat32 and moving everything onto it and organizing everything from there. but if it cant read ntfs, will fat32 even work??? I would like to be able to take the drive to another computer and still be able to access all of my data if need be. so fat32 would just be the easiest format to use.

---

### Post by cyberdork33 on 2008-09-15
I can't really help with your netatalk config, but for FAT32, your limitation will be 4GB filesize, so not DVD-size image files or anything...

---

### Post by Apocrathia on 2008-09-18
S**t, I forgot about the 4gb filesize limit. FAT32 is out the window then...
I'm really starting to get confused on how to get this system working the way I need it to. Any suggestions on what filesystem to use? I'm kinda sketchy about using etx3 for some reason.
I want this system to pretty much act as a drobo on steroids. I've got everything configured on the service-side. but if I don't have a stable filesystem then I dont know what to do. Can OS X read ext3?

---

### Post by cyberdork33 on 2008-09-18
> **Apocrathia said:**
> I'm really starting to get confused on how to get this system working the way I need it to. Any suggestions on what filesystem to use? I'm kinda sketchy about using etx3 for some reason.
I want this system to pretty much act as a drobo on steroids. I've got everything configured on the service-side. but if I don't have a stable filesystem then I dont know what to do. Can OS X read ext3?
It doesn't matter unless you put the drive that the filesystem is on into your mac...

The server actually reads the files from the filesystem and exports them over a network format that is readable by other systems. You mac has no idea what the real filesystem is, it only cares about the exported format.

This is why you can use whatever filesystem you want in Linux or windows or OS X, and setup a samba share, and any system that has samba drivers installed can see the files...

---

### Post by Apocrathia on 2008-09-19
I know that the receiving system won't care or even know what the server's file system is. It will see AFP, SMB, whatever. I am thinking of in the event of a drive failure or anything like that and I have to attempt to retrieve data off the drive from another computer that is not Linux based.

I am trying to figure if ext3 would be a safe filesystem to use in that sense.

---

### Post by cyberdork33 on 2008-09-19
> **Apocrathia said:**
> I know that the receiving system won't care or even know what the server's file system is. It will see AFP, SMB, whatever. I am thinking of in the event of a drive failure or anything like that and I have to attempt to retrieve data off the drive from another computer that is not Linux based.

I am trying to figure if ext3 would be a safe filesystem to use in that sense.
Well, for the most part the ext3 drivers outside of linux are quite poor. On the other hand, it is quite simple nowadays to boot a liveCD on a machine with the hard drive attached, and retrieve whatever data you need.

Using a non-native file system will just slow your network shares down though...

---

### Post by Apocrathia on 2008-09-25
true about the livecd. But I am wanting to setup a software raid w/ parity. Essentially a software drobo (still looking for a solution to that one). I don't know, the chance of failure in a raid5 or so is pretty low. but the livecd idea is definitely a good one. I can at least compile a damn small linux cd with whatever raid software I end up using.

---

