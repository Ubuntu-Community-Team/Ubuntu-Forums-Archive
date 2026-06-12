---
title: "USB Drive File System Issue"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by junkMonkey on 2007-12-28
Ok, 
Lets assume for a minute that I'm a complete n00b. I'm using Gutsy (7.10) and I'm trying to save some files to a Datastor USB external hard drive. The problem is:
[LIST=1]
[*]I save the files by using a copy/paste command using the graphical interface. 
[*]I look and see that the files are present in the External Drive's navigator window.
[*]I unmount the drive and then re-mount.
[*]I look for the files and they are gone.
[/LIST]
Am I missing something? Did I forget to do something before I unmounted the drive? Or is this a bug that I should report on Bugzilla?

The Laptop I'm using is a Sony Vaio CR220E.

Advanced Thanksance!

---

### Post by blueridgedog on 2007-12-28
Try to duplicate your problem, but before unmounting run:

```
sudo sync
```

Also, try the command from a terminal, on a command line, manually and see if there is a difference.

These bits of info my help.

---

### Post by dstew on 2007-12-28
Maybe permissions changed when you re-mounted. How did you remount? What command did you use?

---

### Post by junkMonkey on 2007-12-28
I did everything from the GUI desktop. 
I suppose I should be a dilligent nerd and just use the command line as suggested above. (Which I'll do once I get home tonight!)
I think the sync command stands a good chance of solving the problem.

I've looked at the permissions and I should be good to go. Further, the disk's file system is FAT not NTFS (why I formatted this thing as FAT I'll never know).

---

### Post by blueridgedog on 2007-12-28
I wasn't implying that people should use the command line, but that in this case it would be a good point of information to help solve the problem.  

However, that said, I find that I can move/manage files faster from the command prompt.

---

### Post by Mad_Dawg on 2007-12-28
What I do is plug in the USB drive before I turn on the computer.  Then I leave it there until the computer is turned off before I unplug it.  Never had a problem.

---

### Post by junkMonkey on 2008-01-01
OK,
So, here's what's happening:
When I plug in the usb drive, Ubuntu automatically mounts it. 
I've tried the sync command and that didn't work. 
I ran the other experiment, shutting down before I removed the drive and that actually DID work. I re-booted and the file was where I expecte it on the USB drive.

So, the process for shutting the system down saves the file information and the GUI is not doing something the same when I use the unmount command (by right clicking and selecting 'unmount')

And for the record, I didn't take offense at the command line suggestions. The were well received and were useful in getting to the root (no pun intended) of what might be the problem by removing the GUI from the equation. Didn't mean to sound sarcastic, it was more of a d'Oh! on my part. 

I'm RTFMing the man page on mount/umount to figure out how to get this system to work the way I expect/want it to. 

Thanks again for your help!

---

