---
title: "how to install firefox 2 as a tar.gz file?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by shiloz on 2007-09-04
hi i have downloaded the firefox-2.0.0.6.tar.gz to my desktop and i tryed to install it using this command (tar -xvzf firefox-2.0.0.6.tar.gz) this is the error messages i found:

tar: firefox-2.0.0.6.tar.gz: cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

i am currently using Ubuntu and edubuntu operating systems, i will appreciate any help. God bless

---

### Post by nowshining on 2007-09-04
to install the main build from firefox themselves do this
 
download


 _[http://sourceforge.net/project/platformdownload.php?group_id=202789](http://sourceforge.net/project/platformdownload.php?group_id=202789)_
 
then 
 
wait for the next instructions

---

### Post by meborc on 2007-09-04
what you need is to read this - [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

scroll down to installing from source :) it is not that easy... you better stick to programs available from apt (synaptic)

---

### Post by nowshining on 2007-09-04
ubuntuzilla is a shell script to auto compile it and install it :)

---

### Post by Majorix on 2007-09-04
Why not use the repos? Firefox latest version is almost always there. To install it do:
```
sudo apt-get install firefox
```

---

