---
title: "MyBook - Using &quot;lost+found&quot;...is this correct."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by george1984 on 2007-06-15
Hi. I am definitely a novice. Running Feisty-32 (very nicely).

My new MyBook ext hd is formatted into one primary sda1 only (all linux) (help from forum. for those interested, I think I did...
	sudo umount /dev/sda1
	mkfs /dev/sda1 -t ext3..which reformatted entire drive to ext3.)

It seems to be detected and mounted automatically. An icon appears on the desktop.
Click on icon>File Browser appears containing folder entitled "lost+found". If this folder is opened, folders/files from /home:~ can be copied and pasted; and v.v. I thought this folder was root only; and only for experts.
This "lost+found" appears in /media/disk/lost+found. There seems to be a top level /lost+found which has root access only, and may be different.

MyBook seems to work ok like this. Simplicity itself.

Question:-I am a bit concerned that it is using "lost+found". Does any-one know :Is it meant to do this?

                          Grateful for the forum

                                         Bye

---

### Post by kidders on 2007-06-16
Hi there,

That directory is created by some filesystems (most notably Ext2/3), and should normally be empty, unless your box had to perform some sort of (not too minor) recovery operation.

I would suggest limiting yourself to deleting/copying/moving things out of it, and leaving it "chown root:root" and "chmod 700" ... unless of course you feel like **sudo rm -R ...**-ing it. Afaik that doesn't have any adverse effects.

---

### Post by george1984 on 2007-06-17
Hi. Thanks for that.

It has got me thinking. When setting-up this ext hd my record keeping was not immaculate. I may have done something funny. 

I really can not stand not knowing; or perhaps misleading the forum.

I will copy off the data and then wipe this ext hd, and do the set-up again. Just in case. The second time will be exactly recorded.

I am a bit slow, but I will post what happens.

                                      Bye

---

### Post by kidders on 2007-06-17
What are you concerned about exactly?

---

### Post by Golyadkin on 2007-06-17
Good luck, let us know how it went :)

---

### Post by george1984 on 2007-06-18
Hi again.

What I am concerned about is that I might be doing something  silly. Hence seeking reassurance.

Don't be fooled by the use of commands below. I really am ignorant.

I re-install MyBook by :-

A. Re-Format by doing

	sudo umount /dev/sda1 (Feisty seems to have automatically assigned MyBook to /dev/sda1)
                                   and
	mkfs /dev/sda1 -t ext3

The entire drive is now one partition; sda1 in ext3.

B. The "disk" icon appears automatically.

C. Right click on the icon for information. Mount point is /media/disk.

D. Left click on the icon. "disk - File Browser" appears. It contains one folder,namely"lost+found". This folder has full root restrictions, and is not accessible. 
     Although Feisty has automatically mounted MyBook, it seems to have done so in a way that makes MyBook unuseable.

E. I do   sudo chown -R george /media/disk
	This changes /media/disk/lost+found to allow full user access, and thus MyBook becomes useable. As I only move/copy/delete folders/files in and out, I now understand this is unlikely to cause problems. MyBook works perfectly.
	

	This is exactly how I re-installed MyBook.
	
	
	The question is:- Is this method correct?
                                        Is this how competent Feisty users do it?

                                                            Thanks for the replies

                                                                               Bye

---

### Post by kidders on 2007-06-18
Ahh... now I'm with you.

> **george1984 said:**
> Although Feisty has automatically mounted MyBook, it seems to have done so in a way that makes MyBook unuseable.The default permissions will probably only allow root to write to the device, which is safe and sensible. If you're the only person intending to use the disk, then **sudo chown george /media/disk** should change that by making you the owner of its root directory. The disk should remember that change forever. The "-R" switch recursively rewrites ownership throughout the entire disk, which is unnecessary. It would be advisable to put "lost+found" back the way it was, or remove it altogether.

Anyhow, what you've done is perfectly fine. :-) If you want to share the new disk space with other users on your system, one approach would be to do something like this:[LIST=1]
[*]sudo chown root:root /media/disk
[*]sudo chmod 755 1$
[*]sudo mkdir "George's Stuff" !$
[*]sudo mkdir "Kidders's Stuff" !$
[*]sudo chown george:george "/media/disk/George's Stuff"
[*]sudo chmod 751 !$
[*]sudo chown kidders:kidders "/media/disk/Kidders's Stuff"
[*]sudo chmod 751 !$[/LIST]Effectively, you'd wind up with something that works the way the /home directory does. On the other hand, you might just prefer to leave everything the way it is.

The problem you seem to have been having though, is that Linux normally doesn't let unprivileged users access anything unless it's told to do otherwise. This slightly paranoid approach to security is part of what keeps Linux so safe ... but it *can* get a little irritating!

**Edit:** One additional note ...

Since your new disk is removable, chances are that you'll be plugging it into another computer at some point. In that event, it's important to remember that when you **chown** something, Linux writes the owner's UID onto the disk, not the owner's name. As a result, if you were to change your username in the future, you wouldn't have to wander around your entire computer, **sudo chown**-ing everything in sight.

The down-side of this way of doing things is that UIDs aren't always consistent across every machine. You can find out your UID with:```
$ grep `whoami` /etc/passwd | cut -d: -f3
1000
```So in my case, anything I take ownership of on my own PC is tagged as belonging to user #1000. Anyhow, if you have more than one Linux box, and you'd like to be able to use your disk in them all, I can explain how to avoid running into any difficulty.

---

### Post by george1984 on 2007-06-21
I say Kidders, that was a tutorial. Thanks. No, really Thanks!

The ext hd is now at /media/disk/MyBook , so this is tidied-up.

I will steadily work my way through the tutorial. Plenty to try out - and to think about; learn by doing.

I have only had this ext hd a short while, used for for backing-up; but already it feels indispensable.

                       Thanks again
           
                                   Bye

---

