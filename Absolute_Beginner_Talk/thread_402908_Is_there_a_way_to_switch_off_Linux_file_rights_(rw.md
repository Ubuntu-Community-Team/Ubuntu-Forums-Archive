---
title: "Is there a way to switch off Linux file rights (rwxrwxrwx)?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-04-06
I suppose not, but I'll ask anyway.
You know how Linux marks every file and directory read-write-execute for user, group and superuser?
OK now, how do I switch that off?  It always gets in my way (for example aMule somehow saves some files fully accessible and the others restricted, then I have to do a chmod before I can shift them around on my HDD) and I see zero security benefits.  I mean, it's not like it's an encrypted file system or anything, any ******* with a Live-Linux CD can access them.
So, is there any way that I can get shot of Linux file rights?
BTW, do you agree or disagree with my stance?

---

### Post by mac.ryan on 2007-04-06
> **Blofeld said:**
> OK now, how do I switch that off?

I honestly don't know if this is possible at all. (I would guess not, as - if I am not mistaken - the file permission system is part of the Single POSIX specification). Anyhow: some linux-guru might have _a real answer rather than an guess._

However....

>  BTW, do you agree or disagree with my stance?...I disagree. I find that the file permission system gives a lot of security not really for the computer as a physical machine (unix/linux is not designed to be safe at the console) but for the system when connected to the net, working in multitasking/multiuser, etc...

Basically, the file permission prevents viruses to pester linux, bad packages to corrupt the entire system, malicious software to install itself.... for this reason, I wouldn't "switch off" that feature even if this would be possible... I would rather use a workaround, like for example having a small deamon monitoring and eventually changing owner/permission of files within a certain directory, or even putting the files I need to be "all the time accessible" on a partition that doesn't support file permissions (I believe this is the case for NTFS, but I might be wrong...)

---

### Post by PurplePenguin on 2007-04-06
Disagree.  A person with a Live CD has to break into your home in order to get at your data.  I don't know about your neighbourhood, but in mine, that means that my stuff is pretty safe.

EDIT:  If you really wanted to, I suppose you could give read/write/execute permission to everybody - but please, don't do that.

---

### Post by sessine on 2007-04-06
You can't turn them off, it is an integral part of the filesystem as far as I know.  You can set the default levels though (can't remember exactly what you need to set right now), for example, I use UNIX at work and any files I create allow me read-write-execute permission, group read-execute permissions and world read-execute permissions.  For some work I do I also have a setting that allows group write by default.

I've never used eMule but copying files will usually maintain the same permissions structure.  As for security, if you restrict all your files to only give yourself read-write-execute permissions then even if someone else manages to log into your system they will not even be able to see your files (unless they get into the root account).

---

### Post by zvacet on 2007-04-06
I don´t think that is smart thing to do but if you want to here it is 
[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

