---
title: "Using additional drives"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by DakotaBlue on 2007-11-06
I am doing a clean install on an old PC.  It has three hard drives, all have been wiped clean.  This is my first exposure to Linux (or any UNIX for that matter).

I installed ubuntu 7.10 without any noticeable problems.  It takes a long time to boot, but that may be my old PC or some fine-tuning; either way, it is not today's problem.

I am an expert with Windows XP Professional, including managing a small business network system (using workgroups, not domains) with NAS, etc.  I am a computer professional in my day job, but not an IT professional.  I mention that only to say I am a) not completely technically naive, but b) Windows handicapped and not at all experienced with Unix systems.  I'm sure there is an incredibly simple solution to my problem.

I have successfully partitioned the two additional drives and formatted them exp3.  When ubuntu boots, it mounts the drives, and they are visible in the Places -> Computer window, but I can do absolutely nothing with or to them.  The system tells me I can't store a file on them because I don't have the privilege.  It tells me the drives are owned by root and I can't change their names or other properties.

Everything I have done successfully with the system has been with the GUIs.  I reformatted the drives (to force root to let go of them) and then tried to manually establish a mount point and manually mount them, but was unsuccessful, probably because I was in cut and paste mode with the terminal and don't really understand the command language.  I'm sure UNIX's arcane command language becomes second nature after awhile, but right now they are a seemingly random collection of 2 or more letters.

How do I add additional blank drives to the system so they are accessible and usable by ordinary (not root) users?

---

### Post by hyper_ch on 2007-11-06
Well, if you format drives and mount them first, they are normally owned by root and you nromally don't have write access to it. So all you have to do is either change ownership to you or give write access to it.

You have to understand how the linux permissions work then you'll understand more clearly.

However for giving you simple advice I assume two things:

(1) Your username that you use to login is called "user"
(2) One of your drive location, when mounted, it /media/sdb1

In order to change ownership just run this command:

```

sudo chown -R user.user /media/sdb1

```

sudo --> do as super user ;) (I guess you know that already)
chown --> change ownership
-R --> make it recursive
user.user --> the new owner of those files/folder and the new group the files and folders belong to
/media/sdb1 --> where that partition is mounted

---

### Post by Arthur Archnix on 2007-11-06
I think there's a typo. It should be a colon, not a period, no? At least, according to the chown man page I looked at.
> sudo chown -R user:user /media/mount_point

---

### Post by hyper_ch on 2007-11-06
you can use either dot or semi-colon.

---

### Post by Arthur Archnix on 2007-11-06
I see. Just ran through it all testing. My bad.

---

### Post by hyper_ch on 2007-11-06
well, I use both... sometimes the dot, sometimes the semi-colon ;)

but I agree, there should be only one way... semi-colon would be better (IMHO) so usernames can also contain dots...

---

### Post by DakotaBlue on 2007-11-07
Krimonitly, this board zooms along!  This thread was already down to page 20 (on my browser setup)!  Yikes!

Anyway, thanks for the help.  I was able to successfully change the ownership, but now I have other problems.  Except for the ownership changes, I'm using the GUI tools, not Terminal.

My change to Permissions does not seem to stick.  I can change the permissions, but when I go back and check, they have reverted to default.

The GUI utilities seem to be confused as to who owns the drives (going by the information they display.)

I was wrong about the drives being auto-mounted. I do have to mount them manually.  Any way to fix this?

They are named "xx.x GB Volume - disk" or "xx.x GB Volume - disk-1" and their mount points are /media/disk or /media/disk-1.  I am unable to change the disk names. It refuses to let me.

Does anyone have a good "Linux Concepts and How to Sys Admin a Linux System for Brain-washed Windows Dummies" reference?

Editorial comment on my experience so far?  Nice looking system, but anyone who claims Linux is ready for prime-time home use or even business use without professional IT staff is forgetting how difficult this system appears to the non-geek.  And, I'm even a geek and it is difficult.  I can't even do the basics of getting a g-d hard drive installed and usable.

---

### Post by hyper_ch on 2007-11-07
I gave you the according commands above... all you need to know is what your username is and where the drives are mounted to...

regarding forum moving fast: Go to your user control panel in the forum, somewhere there you can set subscription settings. I recommend to auto-subscribe to every thread you participate and have immediate email notification.

---

