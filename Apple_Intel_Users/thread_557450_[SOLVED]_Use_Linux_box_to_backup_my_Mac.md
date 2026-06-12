---
title: "[SOLVED] Use Linux box to backup my Mac?"
date: 2007-09-22
forum: Apple Intel Users
---

### Post by Mode_Locrian on 2007-09-22
First off, I'm sorry if there already some threads floating around on this--I searched (a lot) and didn't come up with anything (but maybe I just suck at searching).  Anyway, here's my situation:

I've got a desktop machine running Ubuntu Fiesty with 3 hard drives in it.  I'd like to use one of those hard drives (not the one on which Ubuntu is installed) to backup my MacBook's hard drive--ideally by just storing an image there.  Now, I figured that the best way to do this would just be to format this drive in HFS+ and then use some cloning program (like SuperDuper, maybe) on my Mac to clone the drive over the network (Samba).  However, I'm stuck here because I cannot figure out a way to format the drive in HFS+ -- the option is "greyed out" in gparted.  Any ideas?  I would really appreciate some help.

---

### Post by cyberdork33 on 2007-09-22
> **Mode_Locrian said:**
> First off, I'm sorry if there already some threads floating around on this--I searched (a lot) and didn't come up with anything (but maybe I just suck at searching).  Anyway, here's my situation:

I've got a desktop machine running Ubuntu Fiesty with 3 hard drives in it.  I'd like to use one of those hard drives (not the one on which Ubuntu is installed) to backup my MacBook's hard drive--ideally by just storing an image there.  Now, I figured that the best way to do this would just be to format this drive in HFS+ and then use some cloning program (like SuperDuper, maybe) on my Mac to clone the drive over the network (Samba).  However, I'm stuck here because I cannot figure out a way to format the drive in HFS+ -- the option is "greyed out" in gparted.  Any ideas?  I would really appreciate some help.
There is pretty much nothing that can create HFS+ except OSX. If you plan to access it over the network, it doesn't matter what filesystem it is as long as the server hosting it can access it. (When you copy a file to a samba share, your mac is not doing the writing to disk, the server system is.) You really have quite a few options unless you are trying to make a complete, bootable backup (like with Carbon Copy Cloner) and you just want to backup your user files (music, pictures, etc) then you can use rsync which should scan and do an incremental backups.

---

### Post by alephsmith on 2007-09-22
If you were to create a disk image on the target filesystem and back up to that image rather than the vanilla smb share you wouldn't need to worry about the target filesystem.

I am also thinking of doing the same thing so please post back here with your experience.

---

### Post by Mode_Locrian on 2007-09-25
Good point, alephsmith--I hadn't even thought of that.  Well, anyway, I took your suggestion and set up an ext3 partition on one of the drives in my ubuntu box, shared it via samba, and then put a big fat disk image (big enough to image my entire MacBook hard drive) on it with OSX Disk Utility.  Then, using Carbon Copy Cloner (a pretty nice donationware app) I set up a schedule to backup to that image every time it gets mounted .  So far, it appears to be working great.  All of my files etc. are properly backed up and I'm *assuming* that the image of the disk is ok so I could completely restore my OSX install if I needed to (of course I'm too scared to test it needlessly).

Anyway, your suggestion seems to be working great, long story short.

---

### Post by cyberdork33 on 2007-09-25
Can you mark as solved?

---

### Post by alephsmith on 2007-09-26
CCC and SuperDuper both seem to fail mid-backup to my external USB, maybe I will have better luck if I perform my backup over ethernet to my feisty box in the same manner.

Can I ask a couple of questions:
Are you using a sparse image file?
Have you tried doing a 'smart' backup (not sure of the name in CCC)?
have you been able to boot off the disk image?

---

### Post by Mode_Locrian on 2007-09-26
I marked the thread as solved.

As to your questions, aleph:

Yes, I am using a sparse image file.
I'm not sure what you mean by "smart" backup--do you just mean an rsync-like operation where only files that are changed get copied over?  If that's what you mean, then yes, that's what I'm doing (I believe this is the default for CCC).
I haven't attempted to boot off of the disk image yet, so I don't know.  I'm not sure how to boot OSX off of an image that's on a drive shared on the network (as opposed to physically connected to the machine).  I would like to test this soon, but I've been too busy to spend any time figuring out how it might work.

---

