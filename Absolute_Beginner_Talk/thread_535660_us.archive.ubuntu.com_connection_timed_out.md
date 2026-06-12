---
title: "us.archive.ubuntu.com: connection timed out"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by yfpjaya on 2007-08-26
I have been trying to connect to us.archive.ubuntu.com since past few weeks. I have tried different mirrors and I am wondering if the server is temporarily down, perhaps? 
But when I ping us.archive.ubuntu.com, it pings without any problem.
I am not able to update the software or install many software as a result.
Anybody facing this problem? Thanks!

---

### Post by Majorix on 2007-08-26
Try the main mirror or let the software sources program find the best server for you. The local server is not always the best and might be down at times.

---

### Post by yfpjaya on 2007-08-26
But this problem has been persistent and when I give 'apt-get update'..its going to go to us.archive.ubuntu.com anyway, right?

---

### Post by bobplano on 2007-08-26
> **yfpjaya said:**
> But this problem has been persistent and when I give 'apt-get update'..its going to go to us.archive.ubuntu.com anyway, right?

not necessarily. you need to check your /etc/apt/sources.list. you can change the servers so they use the main one, just get rid of the *.us.*

---

### Post by Majorix on 2007-08-26
"System > Admin > Software Sources" if you are using Gnome. That program can change all the servers with a single click and it can search the fastest server for you automatically. Gotta love it.

Good luck.

---

### Post by yfpjaya on 2007-08-26
I have tried 'deleting .us. from the sources.lst file, and also,
I tried the gui option, and true to the post, it did find 'some server' for me..I am not aware of the criteria with which it decided, but now when I try updating, it gives a whole bunch of errors and says that it has failed to download a lot of index files..

---

### Post by Majorix on 2007-08-26
If you use the internet while its trying to find a server it might fail. Because it pings like 150 sites and their ftp/http one after the other.

If nothing works just select the main server. That one is usually fast too if not the fastest.

---

### Post by yfpjaya on 2007-08-26
Yep, I tried that..same problem..looks like I have to try my luck on some other day/time...:confused:

---

