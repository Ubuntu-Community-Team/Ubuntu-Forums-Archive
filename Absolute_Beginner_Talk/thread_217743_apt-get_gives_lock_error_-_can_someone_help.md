---
title: "apt-get gives lock error - can someone help?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Gig on 2006-07-17
Hi

I have been working with Hoary for a while and run it as a proxy at my home. I have also installed Samba and use it as a Fileserver/ backup for our little network.

Recently I tried to install apache-mysql-php so I can do some programming in php but my system keeps giving me this error:

root@server:/var/lib/dpkg # apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (20 Not a directory)
E: Unable to lock the list directory

It gives me the error on update, upgrade and any install.

I have searched everywhere but no fix seems to help. Can anyone with a bit of experience please advise me as I am stumped and cant make my system an apache server to test scripts, etc.

Thanks

---

### Post by melissawm on 2006-07-17
sure you don't have any other package manager (synaptic, adept etc) running at the same time? i would just delete the lock file and do a ```
sudo apt-get clean
sudo apt-get update
```
and try again...

but i'm not sure you should delete the lock file :P

---

### Post by KittyChunk on 2006-07-19
Also had this problem in Dapper a little while back - got it fixed using the same steps above, worked fine. I would back up the lock file to something else like lock_old though rather than deleting it, just in case :)

---

