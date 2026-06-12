---
title: "How would I mount a separate home partition"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by buttheadxa on 2008-04-17
How would I mount a separate home partition?

---

### Post by indytim on 2008-04-17
1.  Search the forums.
2.  [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

IndyTim

---

### Post by Crafty Kisses on 2008-04-17
If you already made the partition, you need to mount e.g:
```
/dev/hda1 and /dev/hda7
```
You'd have to go into Terminal and mount them:
```
sudo mkdir /old
sudo mount -t ext3 /dev/hda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/hda7 /new
```
Then you have to go back to the /home directory on the older partition to move it to the newer one:
```
cd /old/home
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home
```
Then you have to specify to use the new Linux partition as /home:
```
sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab
```
Say hello to the text-editor, don't be afraid of it, just add this line:
```
/dev/hda7 /home ext3 nodev,nosuid 0 2
```
Then you need to save:
```
Cntrl+X
```
Then confirm:
```
Y
```
Then you should be set. :)

---

### Post by buttheadxa on 2008-04-17
Codename, your a life saver, how did you get so good with linux?

---

### Post by oedha on 2008-04-17
[http://psychocats.net/ubuntu](http://psychocats.net/ubuntu)
[http://help.ubuntu.com/community](http://help.ubuntu.com/community)

---

### Post by Crafty Kisses on 2008-04-17
> **buttheadxa said:**
> Codename, your a life saver, how did you get so good with linux?
It just takes time, once you start using it for awhile, you'll start understanding things better, but I'm glad I could help you.

You may want to mark the thread solved, so other people can benefit from this thread, thanks!

---

