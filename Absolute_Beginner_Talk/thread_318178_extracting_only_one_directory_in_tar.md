---
title: "extracting only one directory in tar"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2006-12-13
Hello,
I back up my home directory time to time by using a automatic script. Iwould like to extract only one directory from a big tar.gz file.


I use PINE and I use drop box to download all my emails to my local machine.

But recently I messed up with my mail folder and I lost many important mails.

To sum up, can I extract only a specific directory (e.g. mail) from a tar.gz file (e.g. ubuntu-home-mozkaynak.20061204.tar.gz)?
Thanks in advance for all responses.

---

### Post by seelk on 2006-12-13
To do this you need to have the name and path of the directory you want to extract.  For example, if you have a backup.tgz file that contains:

home/user1
home/user2
home/user3

To extract only the user2 dir you would do:  tar xvpfz backup.tgz home/user2.  I hope that helps.

---

