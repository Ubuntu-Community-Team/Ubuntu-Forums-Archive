---
title: "EDGY shuts down so fast!!"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-12-01
I just remembered being told that Ubuntu EDGY shuts down sooo fast they had to cut the logoff sound and make it shorter to go with the speed!!!!...just wanted to mention it!!
:D

---

### Post by Bachstelze on 2006-12-01
Not as fast as FreeBSD yet, though :D

---

### Post by Arisna on 2006-12-01
On my hardware, FreeBSD won't shut down at all.  I have to hold down the power button for a couple seconds to make it power off once everything has stopped.

---

### Post by Mazen on 2006-12-01
Allright there u have it:D install EDGY:D

---

### Post by DarkN00b on 2006-12-01
It does shut down really quickly though. 

One thing I have noticed is the startup speed compared to Dapper. With Dapper, I had startup speeds of about 42 seconds. Since I installed Edgy, my startup speed has steadily decreased. It *started* at 42 secs this time and has since dropped to 29 secs over the last 2 weeks. Thank goodness for Bootchart :D.

---

### Post by Mazen on 2006-12-01
> **DarkN00b said:**
> It does shut down really quickly though. 

One thing I have noticed is the startup speed compared to Dapper. With Dapper, I had startup speeds of about 42 seconds. Since I installed Edgy, my startup speed has steadily decreased. It *started* at 42 secs this time and has since dropped to 29 secs over the last 2 weeks. Thank goodness for Bootchart :D.

Ehm...what's bootchart??
lol

---

### Post by DarkN00b on 2006-12-01
It is a program the tells you how fast your machine starts up, and what it is doing during startup. Connect to the internet and at the command line, type:

```
sudo aptitude install bootchart
```


Then restart your computer and go to /var/log/bootchart and you will see a PNG there. Open the picture and you will see a chart of your boot process -- a "bootchart". It creates a new bootchart every time you start up your machine. I love it. You do need to delete them every now and then as they eat up space pretty quickly. Just open a terminal and 

```

cd /var/log/bootchart
sudo rm *.png

```

to get rid of them.

There's a thread where everyone was posting theirs [here]("http://ubuntuforums.org/showthread.php?t=241604&highlight=bootchart").

Let's hope this shows up correctly:
[IMG]http://img.photobucket.com/albums/v191/DarkN00b/Bootcharts/edgy-20061201-2.jpg[/IMG]

---

### Post by Mazen on 2006-12-02
My Ubuntu took 1:13 mins to boot!!...kina slow ey!!!
any suggestions on boot speedups??

---

