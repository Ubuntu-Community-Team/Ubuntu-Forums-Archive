---
title: "Firefox / mplayer plugin problem"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-10-29
My problem is that I CAN get the mplayer plugin to work in Firefox 1.5.0.7 BUT NOT Firefox 2. Does anyone know how I can fix this problem?

Thanks :)

---

### Post by spamzilla on 2006-10-29
Anyone?

---

### Post by Cooler22 on 2006-10-29
Hi, please help me, how to install FireFox 2.0. I downloaded .gz file, unziped to .tar file and when typing in correct directory "./configure" nothing happend. What are the next steps when I have unzipped files in "firefox" directory?

---

### Post by spamzilla on 2006-10-29
[http://ubuntuforums.org/newthread.php?do=newthread&f=73](http://ubuntuforums.org/newthread.php?do=newthread&f=73)

---

### Post by mahy on 2006-10-29
> **Cooler22 said:**
> Hi, please help me, how to install FireFox 2.0. I downloaded .gz file, unziped to .tar file and when typing in correct directory "./configure" nothing happend. What are the next steps when I have unzipped files in "firefox" directory?

You don't have to run ./configure because it is NOT a source archive. Just unpack it somewhere (sudo tar xzvf something.tar.gz -C /desired/directory) and run the file named firefox in that directory.

---

### Post by mahy on 2006-10-29
> **spamzilla said:**
> My problem is that I CAN get the mplayer plugin to work in Firefox 1.5.0.7 BUT NOT Firefox 2. Does anyone know how I can fix this problem?

Thanks :)

I guess it is because you downloaded Firefox 2 from Mozilla.com and then just unpacked it somewhere. This new firefox naturally knows nothing about mplayer plugin. A likely solution would involve symlinking some directories, which is easier than it sounds, but i don't know which directories to link. :( I'll try to find out though.

---

### Post by spamzilla on 2006-10-29
> **mahy said:**
> I guess it is because you downloaded Firefox 2 from Mozilla.com and then just unpacked it somewhere. This new firefox naturally knows nothing about mplayer plugin. A likely solution would involve symlinking some directories, which is easier than it sounds, but i don't know which directories to link. :( I'll try to find out though.

Ok thanks :)

---

### Post by spamzilla on 2006-10-29
> **mahy said:**
> I guess it is because you downloaded Firefox 2 from Mozilla.com and then just unpacked it somewhere. This new firefox naturally knows nothing about mplayer plugin. A likely solution would involve symlinking some directories, which is easier than it sounds, but i don't know which directories to link. :( I'll try to find out though.

Does anyone have the answer to this problem?

---

### Post by mahy on 2006-10-29
You have to find out where the new Firefox stores it's plugins; it'll be somewhere in <something>/lib/plugins, where <something> stands for the directory where you unpacked the firefox to. Instead of symlinking, go to /usr/lib/mozilla/plugins and copy everything from there into the new plugins directory. Hope it works.

---

### Post by spamzilla on 2006-10-29
Awesome! Thanks worked, thanks mate :)

---

### Post by mahy on 2006-10-29
> **spamzilla said:**
> Awesome! Thanks worked, thanks mate :)

:D you're welcome

EDIT: if you're interested in symlinking the directories (so that after mplayer plugin update you wouldn't have to copy it again), here's a short intro into (sym)linking:

Goal: I wanna directory /usr/src/linux point into directory /usr/src/linux-2.6.18.1

Solution:

sudo ln -s /usr/src/linux-2.6.18.1 /usr/src/linux

hope it helps!

---

