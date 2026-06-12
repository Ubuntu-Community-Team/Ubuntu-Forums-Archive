---
title: "&quot;basic&quot; drag &amp; drop question"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by tomaasj on 2007-07-15
Hi,

stumbled onto a problem which forced me to startup Vista.  Attached an external hardrive and moved folders onto it for backup.  I was not able to do so since I am not permitted.  In the file browser the external harddrive has also a lock on it.  How to to solve so I can simply drag and drop onto my external harddisk ?  I do not want to go back to Vista to do these things !

I am new to Linux, and/but progressing somehow...

Tomaasj

---

### Post by rax_m on 2007-07-15
I think there could be a number of things that might cause this ( I don't think I know all of them ):

1. What filesystem does your external hdd have ? If it's NTFS then you might need to install the ntfs-3g drivers in order to write to it. 
2. If it has a unix filesystem e.g. Ext3 then perhaps you need to create a folder that your user has permission to write to. 

I guess one easy way to check is to copy from the command line using: ```
 sudo cp <filename> /media/<hdname>/<filename> 
``` You need to do the above from a terminal. Alos the values in <.> need to be replaced by something specific for your system. It will ask you for your password and if that still fails then you probably need to enable write access to the drive. 

Feel free to ask more questions if I've confused you ;)

---

### Post by tomaasj on 2007-07-15
Hi,

I found out in the terminal that the external harddrive has a NTFS file system.  How do I load the drivers you mentioned ?  I have never done this before.

Tomaasj

---

### Post by Outrunner on 2007-07-15
```
sudo aptitude install ntfs-3g ntfs-config
```

To start ntfs-config

```
gksudo ntfs-config
```

Should be fairly straightforward after that.

---

### Post by tomaasj on 2007-07-15
Great,

it works,  thanks !

One more question: I noticed I cannot eject the external harddrive.  An alert says that it is writing data to it and cannot eject the volume.  Any suggestions maybe ?

gr. Tomaasj

---

### Post by Outrunner on 2007-07-15
That happened to me a few times, too, both in Windows and Ubuntu. If I remember correctly, you'll have to wait it out(might take a few minutes). I DO NOT suggest to you remove the drive before it says it is safe to remove, you might regret it later.

---

### Post by tomaasj on 2007-07-15
> **Outrunner said:**
> That happened to me a few times, too, both in Windows and Ubuntu. If I remember correctly, you'll have to wait it out(might take a few minutes). I DO NOT suggest to you remove the drive before it says it is safe to remove, you might regret it later.


OK, Thanks for advice etc. !

---

