---
title: "DVD-RAM Writer with dapper"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Ubunteras on 2006-10-08
Hi,

i´m trying to get my DVD-RAM Writer to work properly. I want to be able to write fat32 or udf media. What i have to do? At the moment i can´t write on fat32 media. What kind of entry i need in fstab? I ´ve installed pktcdvd but i don´t understand how to use it.

Thanks

---

### Post by thephantomlinguist on 2006-10-24
I'm going to take a stab at this. I just figured it out myself, but I went down so many dead-end paths that I can't remember exactly how I got it to work. Hopefully, what I've posted below will be of some help.

First, I assume that what you're wanting is to be able to use the packet-writing capability of your device and media. That being said...

You'll need to make sure that you have udftools installed
```
sudo apt-get install udftools
```

You'll have to edit /etc/default/udftools to include your device.
```
sudo vim /etc/default/udftools
```

Uncomment the second line (begins with DEVICES) and then put your device(s) in the list for packet writing. For me, it looks like this:

```
# Drives to register for packet writing:
DEVICES="/dev/hdb"

...
```

Now, you'll need to reconfigure the udftools package.
```
sudo dpkg-reconfigure udftools
```

Tell it to Create device files.

You should notice that it created a device. On my system it's /dev/pktcdvd/0. This is important, because now you get to edit your fstab.
```
sudo vim /etc/fstab
```
Add the following line (edit to your needs):
```
/dev/pktcdvd/0  /media/cdrom1  udf,iso9660  rw,user,noauto,notatime,dev  0  0
```

Now create a folder under /media to accommodate the new entry in fstab.
```
sudo mkdir /media/cdrom1
```

Then, to get it to really work, you have to change the ownership of the new mount point.
```
sudo chown -R [username] /media/cdrom1
sudo chgrp -R [username=group] /media/cdrom1
```
The -R probably isn't really needed, but I threw it in there for good measure.

If your system is like mine, when you pop in a DVD-RAM disk, it'll mount it under /media/dvdrecorder. I haven't figured out how to change that yet (I'll get around to it eventually), but here's the quick fix:

Create a script called DVD-RAM.remount (or whatever is easy) and put the following in it (again, edit to your needs):
```
#!/bin/bash
sudo umount /media/dvdrecorder
sudo mount /dev/pktcdvd/0 /media/cdrom1
```

Make it executable (you can right-click it and make it executable under the permissions tab).

Wow, that was a lot, but it should do the trick. Let me know if anything's fuzzy and I try to clear it up.

Hope this helps!

---

### Post by Ubunteras on 2006-10-31
I'm gonna give this a try.  
I found out that the native format of DVD-RAM is UDF. So I would not advise anyone to use FAT32 with DVD-RAM. I've used FAT32 only because i had some problems with InCD and UDF.   When i find some time I'll format all my DVD-RAMs in UDF.

Thank you for answering my questions!

---

