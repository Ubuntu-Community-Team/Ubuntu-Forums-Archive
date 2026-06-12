---
title: "deleting everything from a hard disk"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-11-15
I replaced my hard disk. I'm going to connect the old one using a IDE to USB converter (that's the device, I think) and transfer my data to the new one. After that, I want to delete all data on the old hard disk - I don't mean just formatting it. I mean making sure the data can't be recovered in any way. (I need to do this because I'm probably going to give the hard disk away to someone.)
I have no clue how to do it. Could someone tell me the easiest way to do this?
Thanks.

---

### Post by Inxsible on 2007-11-15
Have a look at [DBAN]("http://dban.sourceforge.net/")

---

### Post by Benedolt on 2007-11-15
Or try this guide: [http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html](http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html)

---

### Post by az on 2007-11-15
sudo badblocks /dev/sda -w -s -p 5

Where the device is sda.

---

### Post by Hospadar on 2007-11-15
I use dban to wipe hard drives and have had good success with it.  It's very easy to use and does the job.

---

