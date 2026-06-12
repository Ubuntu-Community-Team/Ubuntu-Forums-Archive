---
title: "How to allow aptitude write privileges on read-only directory"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Shane10101 on 2006-08-07
Okay, so I'm setting up my second computer in two weeks w/ Ubuntu, & this time I thought I'd try & do some research into properly partitioning & securing the filesystem....The end result is that I listened to someone's advice & set some of my directories (/boot & /usr, specifically) to "read-only", with the understanding that I could temporarily switch them back to read/write whenever I needed to install software or update the kernel.  That's all well & good...but I can't figure out how to do it, and I think that's what's causing aptitude to return the following errors when I try & install the initial updates:

> Preconfiguring packages...

...unable to execute new pre-instalation script: Permission denied...Subprocess pre-installation script returned error exit status 2 

The same message repeats for the post-installation script.

Is this being caused by my setting /boot & /usr to read-only, as I'm guessing?  If so, how can I grant aptitude write permissions??

Thanks!

Shane

---

### Post by moma on 2006-08-07
You need to re-mount the partitions as read/write.

Re-mount /boot partition read/write. 
$ [COLOR="Green"]sudo mount /boot  -o rw,remount[/COLOR]

Or use the device name.
$ [COLOR="Green"]sudo mount /dev/xxx -o rw,remount[/COLOR]
(replace /dev/xxx with correct device name)

Set partition read-only.
$ [COLOR="Green"]sudo mount /boot  -o ro,remount[/COLOR]
or 
$ [COLOR="Green"]sudo mount /dev/xxx -o ro,remount[/COLOR]
(replace /dev/xxx with correct device name)

---

### Post by Shane10101 on 2006-08-07
Thanks, moma!  I'll give that a shot.

Shane

---

