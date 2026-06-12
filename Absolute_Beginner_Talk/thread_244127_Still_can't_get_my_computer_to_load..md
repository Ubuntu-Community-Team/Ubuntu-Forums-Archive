---
title: "Still can't get my computer to load."
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by buyj3llo on 2006-08-26
okay, this all started with the xserver thing. I had gotten the fix from the main page and was about to put it in. But then when I started up the PC, instead of showing the little blue screen and sending me to command promt, it said something like "system check forced". It then proceeded to scroll through screen after screen of apparently random numbers. This goes on for like 40 minutes, then it pops up with and error along the lines of:```
UNEXPECTED INCONSISTENCY; Run fsck MANUALLY (i.e.,, without -a or -p options)
```
Note that it also says "root file system is currently mounted read-only". 

But after that it drops me off into command prompt again so I figured everything was okay. But then when I try to put in the xserver fix, it doesn't work. It starts off like it's doing something, but then it messes up at 82% done. It gives me this:```
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file couldnot be parsed or opened
```

I think it has something to do with that "read-only" stuff. But I'm just a noob. Can anybody help me?

---

### Post by Cynical on 2006-08-26
You're right. First of all your filesystem is screwed up. Thats why its asking you to run fsck. I would boot the computer using a livecd and follow with the fsck.

What type of filesystem are you using? (ext3, reiserfs, etc)

---

### Post by buyj3llo on 2006-08-26
okay, you gotta remember that I'm a complete noob. I don't even know what filesystem, fsck, or "mount the root partition" is.

But I do remember seeing ext3 somewhere. So I guess thats the one I have.

---

### Post by Skia_42 on 2006-08-26
First, lets find out what filesystem you have, when you put in the following command in the terminal it displays what filesystems are usually mounted on your computer.
> cat /etc/fstab
There should be a filesystem that has a root mount point that is simply "/", this is your main harddrive. It is probably ext3 but check to make sure. My hard drive looks like this:
> 
/dev/hda3    /    ext3   defaults,errors=remount-ro  0         1

You cannot ren fsck on a booted partition so boot up with your install cd (or live cd) and boot up in rescue mode. Then type fsck in the terminal.

---

### Post by buyj3llo on 2006-08-26
I put in that cat thing, and it says:
```
/dev/hda1/ext3 defaults,errors=remount-ro 0 1
```

I've still got the old bootdisk laying around, but how do I get into the terminal from the boot disk?

---

### Post by buyj3llo on 2006-08-26
okay, I put the install cd in and it has the installation options and "boot:". I can type after the boot part. what do I do now?

---

### Post by buyj3llo on 2006-08-26
You know what. Forget this crap, I'm just gonna re-intall and hope I don't get another **** update that murders my computer.:mad:

---

