---
title: "Is it possible to change partition sizes?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by camz on 2007-03-23
hey, the noob is back again with another question.

is it possible to change the partition sizes without reinstalling anything (like, can i do it all via the terminal), so that i can give some of the windows memory to ubuntu. I never use windows and yet it has 12 gb all to itself... can i give this back so i have more space in ubuntu?

---

### Post by floke on 2007-03-23
You have to use gparted and you can't resize  mounted partition. Best to do this from the LiveCD or Gparted CD. Also, you can't resize right to left, which is a pain is Windows is to the left of Ubuntu. Best solution in this case is to resize Windows down and use the spare space (now between shrunk Windows and Ubuntu) as a separate home partition.

See here for a HOWTO:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by camz on 2007-03-23
Oh well so when I get my new HD and I reinstall XP and Ubuntu (hopefully Feisty!), can I give XP like only 1GB more than it's total size and leave the rest for Ubuntu?

---

### Post by camz on 2007-03-23
oh and while im here could someone tell me how to get rid of the orange update button next to te sound button and time cos i don't like it :P

---

### Post by joethenoob on 2007-03-23
You might get something from this thread:

[http://ubuntuforums.org/showthread.php?t=389793&highlight=resize+partition]("http://ubuntuforums.org/showthread.php?t=389793&highlight=resize+partition")

I hate resizing partitions. There is always a possibility that something will go wrong and you'll lose everything.

In my opinion, just back your stuff up and reinstall both from scratch. It's the only way to be sure your boot system doesn't get jacked. Its a drag, but probably the safest way.

---

### Post by camz on 2007-03-23
Ok it's alright I am not in dire need of space it's just Windows is taking up more than it needs I'll wait for my new HD then redo it all.

---

### Post by camz on 2007-03-23
So, can I get rid of the orange button?

---

### Post by floke on 2007-03-23
> **camz said:**
> Oh well so when I get my new HD and I reinstall XP and Ubuntu (hopefully Feisty!), can I give XP like only 1GB more than it's total size and leave the rest for Ubuntu?

Yep - but the home partition is definitely a good idea. My table currently looks like this:

1) Feisty
2) Edgy
3) Feisty Home
4) Edgy Home (+ swap)

This way I always have a dual boot ready in case ubuntu gets borked; its easy to update/reinstall etc. since I don't touch the home directories and so don't have to backup all my stuff; and I can always keep upto date with the latest and greatest ubuntu release- so when Feisty+1 comes out i install it over edgy; when +2 comes out I install it over Feisty etc.

> **camz said:**
> oh and while im here could someone tell me how to get rid of the orange update button next to te sound button and time cos i don't like it :P

Deselect update notifier from the startup options (in system/preferences/ sessions) - but remember to keep checking manually for updates though!

---

### Post by camz on 2007-03-23
I will :D

---

### Post by zvacet on 2007-03-23
Best way to get rid of orange button is to update,because updates are there for reason.

---

