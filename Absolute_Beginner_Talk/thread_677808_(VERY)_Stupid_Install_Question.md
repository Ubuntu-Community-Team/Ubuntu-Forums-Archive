---
title: "(VERY) Stupid Install Question"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by durdensbuddy on 2008-01-25
Is it possible to install Ubuntu Gutsy (64) without a root user?

I don't know really what I'm doing, but I had allowed my LiveCD to install onto about a 65 gig partition.  Then I wanted to reinstall to fix problems and resize.  Now I have a 100 gig Ubuntu partition.  I can cd /root and receive no errors. 

This question came to mind because during my second install a few times an error came up stating that I had not chosen a root mount or something similiar.  I finally was able to get past that by choosing from a drop down men " / " as a load/mount position (lingo escapes me, sorry).  And on my desktop now I have my windows partion and backup partition as icons.  Attempted to unmount these but would not allow me to.  

Does this make sense?

---

### Post by ynef on 2008-01-25
I think this is all due to a misunderstanding -- the root of the file system is "/", whereas the root user's home directory is "/root". Had you not made it install into a partition called "/", then I can definitely understand why the installer complained!

The reason your backup partition and windows partition are showing up on the desktop is because they were found on the hard drive, and have been mounted for your convenience. If you don't want them to show up there, you can always mount them yourself somewhere else by editing /etc/fstab (google will find you good guides for this).

Apart from the icons showing up, are you experiencing any problem with the install at all?

---

### Post by durdensbuddy on 2008-01-25
None, whatsoever.  Was just curious and trying to figure out what was happening.  In fact, I think this install is working better for me than the last one, although that might just be having a few threads and leads as to where to look this time around.  

Thanks for the quick reply

---

### Post by quinnten83 on 2008-01-25
yeah, root is the root of all
Here it gets explained better than I could
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by sumguy231 on 2008-01-25
As was said before, the device icons for your partitions are there for your convenience. You can turn them off in the desktop settings, but your devices aren't actually mounted to your desktop.

---

### Post by durdensbuddy on 2008-01-25
This should then make it a bit easier for me to share between partitions if I'm understanding things, correct?  I'm still going to need samba and get that configured, but in your opinions will this let me access files/folders from my windows side and to send linux created/d/led files to windows?

---

### Post by nodegamra on 2008-01-25
Nope! :)
If you already have access to your partitions you are set.
From what i can read you partitions are mounted and ready to go.
Can you read from those?
SAMBA is to share files with windows computers on you network.

---

