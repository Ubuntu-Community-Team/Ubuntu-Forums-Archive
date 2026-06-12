---
title: "Q's - ac3, writable ntfs and root?"
date: 2005-05-13
forum: Absolute Beginner Talk
---

### Post by Malicine on 2005-05-13
Hi,
Just started playing with ubuntu and have some small questions: :? 
1. How can i make a mounted ntfs drive writable?
2. Is there a plugin for totum or similar that plays  ac3 embeded .avi (I use ac3 filter in win)
3.How can I enter 'root'?, Qparted will not let me edit partitions.

Thanks, this forum has been a great guide so far.

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=Malicine]
1. How can i make a mounted ntfs drive writable?
[/QUOTE]

Ok. This might disappoint you a little, but I'll be honest. You can write to an NTFS drive, but only if you do not value the data on it.

I quote from here:

[http://linux-ntfs.sourceforge.net/info/ntfs.html#2.6](http://linux-ntfs.sourceforge.net/info/ntfs.html#2.6)

> Can the Driver write to an NTFS volume, too?

Not really, but if you only need to copy files from Linux to Windows on a dual-boot machine, see "How to write to NTFS" below for a possible way to work around the lack of write support. For write support in Linux, read on.

There are two drivers, currently. The original driver, in 2.4 has some write code in it, but it is extremely dangerous to use it. The possibility of destroying your filesystem is very high.

The new driver, introduced in 2.5.11, has some write code, but it's very limited. The driver can overwrite existing files, but it cannot change the length, add new or delete existing files.

Adding write support will take a long time. NTFS is built like a database. Any changes you make, necessitate making changes in many places, for consistency. Make a mistake and the filesystem will be damaged, make too many mistakes and the filesystem will be destroyed.  

One thing you can do is use fat32 instead, which both Linux and Windows can write and read with ease. Its how most people (who respect their data) deal with the situation.

> 3.How can I enter 'root'?, Qparted will not let me edit partitions. 

open up the root terminal in Applications-system tools. Give the user password. Start qparted by typing 

qtparted

But I personally advise that you install gparted instead....

---

### Post by Malicine on 2005-05-13
Thanks,
yea I have installed qparted but when i go applications>system tools>QParted
It will not let me edit anything. Is there a way to log on as root in ubuntu?

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=Malicine]Thanks,
yea I have installed qparted but when i go applications>system tools>QParted
It will not let me edit anything. Is there a way to log on as root in ubuntu?[/QUOTE]

No, by default Ubuntu has no root acount. What you need to do is open the program from the run dialog box with the word gksudo before it

like:

gksudo gparted

or 

gksudo qtparted

---

### Post by Malicine on 2005-05-13
/slaps head

Of course, i'll try that now.
Thankyou.




no, didn't work.

---

### Post by Kurai on 2005-05-13
Yeah I have the same problem it asks for a password when you use gksudo, right?

---

### Post by gil-galad on 2005-05-13
[QUOTE=Malicine]
2. Is there a plugin for totum or similar that plays  ac3 embeded .avi (I use ac3 filter in win)
.[/QUOTE]

I think totem will play ac3s right out of the box.  If not, install totem-xine which adds more codecs.  I know totem-xine will play ac3s.

---

