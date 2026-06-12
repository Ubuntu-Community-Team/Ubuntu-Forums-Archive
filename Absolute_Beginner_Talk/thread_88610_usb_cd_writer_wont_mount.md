---
title: "usb cd writer wont mount"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by dronug on 2005-11-10
hi
  im runnung ubuntu hoary hedgehog and i have a usb  hp cd writer cd4e series.
it shows up in device manager and in places-> computer it shows up to.  but when ever i put a cd in and try to mount it i get a message saying unable to mount selected volume could not determine filesystem type and none was specefied.

and it doesnt show up in gnomebacker or graveman. 
if anyone has any ideas plz post.

---

### Post by Lambert on 2005-11-10
Not sure how you're trying to mount but open a terminal and try this.

```
sudo mount -t iso9660 /dev/scd0 /mnt/usbcdrom
``` 
scd0 might not be the correct device, you will have to find out what that is.

You might try the command 

```
scsi_info 
or
lshw -C bus
``` 

and see if that tells you

If this doesn't help search using key words of [COLOR=Sienna]mount -t iso9660 /dev/scd0

[COLOR=Black]What's happening is it needs to know what file type, that's what the -t iso9660 is telling it. That's usually what a cdrom file system is.[/COLOR]
[/COLOR]

---

