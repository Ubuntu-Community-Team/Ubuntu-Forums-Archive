---
title: "[SOLVED] Saving data, permissions &amp;amp; ext. drive"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-04-20
I have, this moment installed an external usb drive of 40gig size. (formatted as ext3 by GParted)

My /home on my 320gig is just under that 40gig. In GParted, I had to in a LiveCD session, do sudo su

to get gparted to work.

I want to change the entire usb disk's ownership to user: mark

then I want to copy all of /home from the 320gig to the 40gig.

I would like help doing this from the command line.

---

### Post by sisco311 on 2008-04-20
Change the owner with the chown command:

```
sudo chown -R <your_username>\: <mount-point-of the-partition>
```for example:
```
sudo chown -R mark\: /media/disk
```Copy the files with the cp command:
```
cp -rv /home/mark /media/disk/mark
```

---

### Post by Mark_in_Hollywood on 2008-04-20
Please know that I'm in a LiveCD session.

sudo chown -R mark /media/usbdrive

returned 

chown `mark' : invalid user

---

### Post by Mark_in_Hollywood on 2008-04-20
I

sudo adduser mark

and was then able to 

sudo chown -R mark

thanks.

---

