---
title: "Graduating from Wubi to the real thing"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by erictlee on 2007-05-31
Having enjoyed Wubi for 10 days now, I want to do a proper partitioning of the disk and install the 'real' Ubunu 7.04.  How can I do this and retain all the files and settings I've set up already?  Thanks.

Eric

---

### Post by steve.horsley on 2007-05-31
You should look for a guide for installing Ubuntu. [www.psychocats.net](www.psychocats.net) might be a good starting point.

You can save your home directory to restore after the install. I would use this command:
**tar cfz myhome.tar.gz .**
which will make a tar file of your entire home directory. Save this elsewhere (write to CD or DVD perhaps?) and restore it to your new home with this command:
**tar xfz myhome.tar.gz**

I think it best to install the OS from scratch, which will mean reinstalling any other apps you installed afterwards though.

---

