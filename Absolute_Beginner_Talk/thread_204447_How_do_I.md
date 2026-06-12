---
title: "How do I?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by wych77 on 2006-06-27
I just installed Ubuntu and now running all the updates and upgrading to Dapper.  I am curious as how to look for the remaining amount of space on my hd.  In windows I just click on the drive and it tells me.  Is there something similar in Ubuntu?

---

### Post by croak77 on 2006-06-27
[QUOTE=wych77]I just installed Ubuntu and now running all the updates and upgrading to Dapper.  I am curious as how to look for the remaining amount of space on my hd.  In windows I just click on the drive and it tells me.  Is there something similar in Ubuntu?[/QUOTE]
 
Open a terminal and enter;
```
df -h
```

---

### Post by wych77 on 2006-06-27
Thanks, I also saw the size at the bottom of the file window in the left hand corner. :)

---

### Post by aysiu on 2006-06-27
You can just right-click on the empty space and select **Properties**.

---

### Post by wych77 on 2006-06-27
Thanks again :)

---

### Post by barbarian on 2006-06-27
nice GUI program for hd monitoring, btw:

*sudo apt-get install filelight*

[http://methylblue.com/filelight/](http://methylblue.com/filelight/)

---

### Post by matrooswolf on 2006-06-27
Try **boabab** also (I think it is installed by default) (in applications/accessories I think, but I'm on a dutch ubuntu, so that is my translation).

It gives a nice overview of your harddisk, (or any folder you want), and shows you where all the space has gone to (in a graph or as percentage ...).
Very usefull

---

### Post by 3rdalbum on 2006-06-27
System > Administration > Disks

Click on the hard disk icon, then click on each partition int he right pane and it tells you how much space is left in it.

---

