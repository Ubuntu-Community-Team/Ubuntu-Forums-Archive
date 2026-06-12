---
title: "[SOLVED] Installing Ubuntu without deleting the home partition"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-12-01
I feel mildly retarded for asking this but I suppose I've never done it before.  One of my machines was dual boot and I went in with gParted, deleted resized and grew my /home partition

Now I have my swap, 20gb root and my 160 some gb /home

I'm reinstalling Ubuntu and don't want to lose my /home data but also want it to treat it like it was before just as the /home folder.

Ok, obviously selecting to reformat it is wrong.

But do I want to change it from /media/sda4  to /home  or not?

---

### Post by thelatinist on 2007-12-01
I would just install normally then edit fstab to mount your home partition in /home/.  [This page]("http://www.psychocats.net/ubuntu/separatehome") shows you how to do it (it assumes that you are moving the contents of your current /home/ directory to that partition, so just ignore those bits).  You may have to recreate the user accounts...I've never tried it myself.

---

### Post by siciliancasanova on 2007-12-02
Should be pretty easy, thanks for the link.

---

### Post by svetlin on 2007-12-02
When installing choose to mount the partition as home and you're done.

---

### Post by siciliancasanova on 2007-12-02
and my data will be ok?

---

### Post by siciliancasanova on 2007-12-02
Really if anyone can confirm these because I've been sitting on the live cd for an hour now, that would be great.

Just need to make sure that telling it to mount the drive that has all my data on it as /home is not going to erase any of my data.

---

### Post by siciliancasanova on 2007-12-02
Everything when great, all settings and files are as they were before.

---

