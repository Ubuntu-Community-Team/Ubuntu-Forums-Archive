---
title: "Copying files from OSX with open permisions"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by neptune39 on 2006-09-05
Hi

I'm trying to move my music libary onto my Ubuntu Server and having trouble with permisions, history as a windows user im afraid. What is the best way to copy files from my OSX user to the server and have open permisions?

Thanks

---

### Post by neptune39 on 2006-09-07
Been trying to sort this out, one solution was to copy the files from a windows PC which created the files with my user as the owner.

I also worked out how to use the chown and chmod commands:
I want /home/public/iTunes to be owned by the linux user and everyone to have read write permisions. Heres the commands i use:

sudo chown luke /home/public/iTunes/*

sudo chmod 777/home/public/iTunes/*

Couple of questions;

Is this a resonable way to go about this, is there a better way I suspect it might be frowned upon by some more experienced users?

How do I get these commands to run say every 30 mins? I know about the cron but not abut how to use it or create the scripts. Any help on what to do or a link to the info would be much appreciated.

Cheers

---

