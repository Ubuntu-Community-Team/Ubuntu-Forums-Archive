---
title: "how to make USB drive read/writable"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by tambidude on 2007-10-07
Ubuntu 7.04
I have an external HDD connected to my laptop via USB 2.0 port.
It is auto detected and mounted on /media/SimpleDrive. The 
trouble is that it is set to 555 mode. How to set it to 777 mode.
running sudo chmod 777 /media/SimpleDrive fails

chmod: changing permissions of `SimpleDrive': Read-only file system

also where to put it so as to automatically chmod everytime the system
boots.

---

### Post by AlexenderReez on 2007-10-07
i guess that harddisk use ntfs partition right?..hm...

follow the link below about to install ntfs-config .... you will able to read/write afterwards....

---

### Post by philinux on 2007-10-07
sudo chown -R yourusername /media/simpledrive

that should set up all the correct permissions

only works if ext format

---

### Post by tambidude on 2007-10-07
"follow the link below about to install ntfs-config .... you will able to read/write afterwards...."

The USB drive is standard USB drive. On my Windows laptop it shows as E:

sorry I did not see any link on how to make it r/w.


"sudo chown -R yourusername /media/simpledrive"

This I already tried and it does not work.

thanks.

---

### Post by philinux on 2007-10-07
When you say dont work do you get eny errors. 

In nautilus can you browse the disk in list view andlook at the owner and permissions?

---

### Post by AlexenderReez on 2007-10-07
> **tambidude said:**
> "follow the link below about to install ntfs-config .... you will able to read/write afterwards...."

The USB drive is standard USB drive. On my Windows laptop it shows as E:

sorry I did not see any link on how to make it r/w.


"sudo chown -R yourusername /media/simpledrive"

This I already tried and it does not work.

thanks.

sorry...follow this..

> [http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by tambidude on 2007-10-07
Hi all, it works now. 

thanks all.

---

