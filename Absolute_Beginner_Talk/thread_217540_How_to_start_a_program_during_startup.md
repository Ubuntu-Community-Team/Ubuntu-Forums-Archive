---
title: "How to start a program during startup?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by sri1025 on 2006-07-17
Hi All,

I am an absolute beginner of Linux. I have a Java application which I want to start as a service or it will be okay even if I can somehow start it at the time of booting.

I have a shell script to launch my Java program, but I don't have a clue about the service thing. If someone can point me to the right direction, it will be very useful.

I was googling and I found that we can create some symbolic link to the script which we want to start and drop that link on to some system folder and it picks up at the time of start-up. But I don't know exactly what to do.

And by the way, I would like to use that same technique across all the linux flavors and not just on Ubuntu.

Thank you! :)

---

### Post by sri1025 on 2006-07-17
If someone knows, please tell me. I am really struggling with this.

Thanks in advance!

---

### Post by reacocard on 2006-07-17
to start for a user at login: System -> Preferences -> Sessions
to start for system at boot: add it to your /etc/init.d/bootmisc.sh file, just before the line with : exit 0

---

### Post by steve.horsley on 2006-07-17
> **reacocard said:**
> to start for a user at login: System -> Preferences -> Sessions
to start for system at boot: add it to your /etc/init.d/bootmisc.sh file, just before the line with : exit 0

The normal way to do this would be to put the starter script in /etc/init.d, and then symlink it from /etc/rc2.d (Ubuntu uses runlevel 2). 

This may help:
[http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=67](http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=67)

---

