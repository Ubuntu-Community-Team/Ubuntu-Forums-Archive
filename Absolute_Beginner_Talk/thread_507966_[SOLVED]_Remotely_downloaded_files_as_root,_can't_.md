---
title: "[SOLVED] Remotely downloaded files as root, can't find them"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by saera05 on 2007-07-23
Hi,

I'm sure this probably has a simple answer, but after googling I haven't found anything that has helped/worked. 

I had been using irssi to download files from irc channels. At first everything was fine, downloaded the files to my home directory. Unfortunately, some file servers require you to open up ports such as 59, and you need to run irssi as root do to this. I did, and everything worked fine, and the files seemed to download. However, when I go to look in my home directory, I don't see the files. (just for reference, I'm doing all this remotely via ssh).

My guess is that the files are owned by root and so aren't showing up, although I'm not sure this guess is correct. I tried "sudo ls -a",  and they didn't show up doing this either. 

If anyone has any suggestions on how to access the files I've downloaded, I'd appreciate it.

---

### Post by geek_Man on 2007-07-23
They're probably in /root not /home/saera05.

---

### Post by Jon@bayleys.org.uk on 2007-07-23
h

---

### Post by saera05 on 2007-07-23
That's where they were. Thanks so much! I knew it would probably be something simple that I was just missing.

---

### Post by geek_Man on 2007-07-23
Cool.

---

