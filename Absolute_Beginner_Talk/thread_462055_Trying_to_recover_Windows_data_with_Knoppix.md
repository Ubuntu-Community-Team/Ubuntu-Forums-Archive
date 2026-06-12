---
title: "Trying to recover Windows data with Knoppix"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by AlanDavidson on 2007-06-02
I'm trying to use Knoppix to recover data from a neighbour's laptop. The problem is more Unix than Knoppix, so I thought I might get help on this forum. My Unix knowledge is only basic.

hda1 is visible in Knoppix. hda2 and hda5 cannot be accessed. The error message is:

mount:i could not determine filesystem type and none was specified.

I typed:
cat /etc/fstab

I got (among other things):

# Added by KNOPPIX
/dev/hda1  /media/hda1   ntfs   noauto, users,exec,umask=000,uid=knoppix,gid=knoppix  0  0
# Added by KNOPPIX
/dev/hda2  /media/hda2   auto   noauto, users,exec  0  0

I typed:

sudo  mount  -t  ntfs  -o  uid=knoppix,gid=knoppix   /dev/hda2    /media/hda2

I got the message:

NTFS signature is missing.

I would be grateful for any advice.

(By the way, does Ubuntu have data recovery tools for Windows, similar to Knoppix?)

---

### Post by Inxsible on 2007-06-02
I dont know if Knoppix does it differently, but in ubuntu the devices are listed before the options.
So your command would be
```
sudo mount -t ntfs-3g /dev/hda2 /media/hda2 -o uid=knoppix,gid=knoppix
```

[COLOR="Red"]the options I use are[/COLOR]
```
sudo mount -t ntfs-3g /dev/hda2 /media/hda2 -o iocharset=utf8,umask=000
```

Also, did you try the file system as ntfs-3g. You would need to install those, i think

Hope that helps !!

---

### Post by crispy_420 on 2007-06-02
Sounds like that partition is trashed down to the file system. I think this happened to a coworkers laptop and I was able to recover via Berry Linux. It is a live distro based on Fedora. But no simple/cheap tool may work if the formatting of the partition is trashed.

Have looked into Bart PE? The live windows disc. Lot of tools in there for these sorts of problems.

---

### Post by AlanDavidson on 2007-06-02
I first tried swapping the bits, as you suggested:

sudo   mount   -t   ntfs   /dev/hda2   /media/hda2   -o   uid=knoppix,gid=knoppix

I'm no expert, but the message seemed "less negative":
---------------------------
Error opening partition device: Is a directory
Failed to start volume: Is a directory
Failed to mount '/media/hda2': Is a directory
----------------------------

I then tried your suggestion using "ntfs-3g", and got exactly the same error messages.

Am I getting closer?

---

