---
title: "How To Make A Root?"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Breezy Badger on 2006-07-05
Hey all,

I should know this, but how do I make a root password.  I never had to during install but now I need it to do many things, like format my HDD.  I did it on 5.10 but I forget how

---

### Post by jayemef on 2006-07-05
Ubuntu uses the sudo system for root administration, so rather than becoming root, you can type
```
$ sudo *commandname*
```
, using your user password when prompted (assuming your user was the first one created during installation).

This is considered more secure than the traditional root method, as a malicious attacker must now know both your username and password rather than just find a password associated with root.

(If you want to actually use the classic root method, see the UbuntuGuide: [http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password]("http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password"))

---

### Post by aysiu on 2006-07-05
You don't really need to:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by T700 on 2006-07-05
The root password is the same password you use to log in when you reboot.  Preface the command with either sudo or gksudo (if it is a graphical application), assuming you are using Gnome.

Paul

*Three answer in the time it took me to type the above!  :-)*

---

### Post by mscman on 2006-07-05
[QUOTE=T700]The root password is the same password you use to log in when you reboot. [/QUOTE]
That statement isn't entirely accurate.  The root password doesn't actually exist when you first install Ubuntu.  The first user created is given sudo access, allowing you to carry out admin commands and essentially giving you root access.  The root password (and account) is null.

Just thought I would throw in my two cents...

---

### Post by T700 on 2006-07-05
[quote=mscman]That statement isn't entirely accurate.  The root password doesn't actually exist when you first install Ubuntu.  The first user created is given sudo access, allowing you to carry out admin commands and essentially giving you root access.  The root password (and account) is null.

Just thought I would throw in my two cents...[/quote]

You are correct, of course.  I spoke too broadly, making no distinction between function and form.  Thanks for the clarification.

Paul

---

### Post by Iowan on 2006-07-05
It IS possible to activate the root account and assign a password, but (as pointed out) it isn't necessary, and I read somewhere that if you re-disable the root account, it can affect the recovery mode (at least on older versions). If you feel you must:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Kilz on 2006-07-05
If its not needed, and I know its not. Then why do people keep telling people how to do it? Why is it in the wiki?

---

### Post by aysiu on 2006-07-05
[QUOTE=Kilz]If its not needed, and I know its not. Then why do people keep telling people how to do it? Why is it in the wiki?[/QUOTE]
Because people keep asking how to enable root.

When someone asks me "How do I enable root?" I usually try to get to the real problem, which is "How do I modify this file I don't have permission to modify?" but other people answer the question directly, not thinking about the end but only the means.

**Further Reading**:
[Why do we indulge the log-in-as-root users?](http://www.ubuntuforums.org/showthread.php?t=139898)

---

### Post by DR_K13 on 2006-07-05
This is true, you never really need to log in as root.  My friends told me that when I first started using Linux.  I didnt listen and found out the hard way.:mad:

---

### Post by Kilz on 2006-07-05
[QUOTE=aysiu]Because people keep asking how to enable root.

When someone asks me "How do I enable root?" I usually try to get to the real problem, which is "How do I modify this file I don't have permission to modify?" but other people answer the question directly, not thinking about the end but only the means.

**Further Reading**:
[Why do we indulge the log-in-as-root users?](http://www.ubuntuforums.org/showthread.php?t=139898)[/QUOTE]
I know its a problem aysiu. But most of the time even if people are aware that sudo is available from the command line. They want the root login because its a gui. For some people its the only reason they want the root login. IMHO I think the root sudo page should put more information on how to run nautilus/konquor in sudo mode. It may stop some people from adding the root account. Right now there are just 2 easy to overlook notes telling how to run graphical applications. I try to point out gksudo nautilus when answering root password posts for that reason.

---

### Post by aysiu on 2006-07-05
Well, that's why I recommend the RootSudo page to veterans from other distributions, but I recommend this page to ex-Windows users who are just confused by the whole permissions thing in general and want to use a graphical way to modify files:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Breezy Badger on 2006-07-09
Ok well here is the problem.  I am using QTparted to try and format a hard drive, but I have to be logged in as the root for any hard drives to even appear....I can't log in as the root without the root password and I don't have it.

Any ideas?

---

### Post by aysiu on 2006-07-09
```
gksudo qtparted
``` if you're in Gnome or ```
kdesu qtparted
``` if you're in KDE. Those commands will launch QTParted with root privileges.

---

### Post by Breezy Badger on 2006-07-09
Hey man thanks that worked...but I am a confused

I right clicked on the hard drive and selected FAT32...it says formatted in FAT 32 but when I restart qtparted again it says its NTFS and the info is still on it like nothing was done to it

---

### Post by aysiu on 2006-07-09
That sounds like a new thread, my friend: "QTParted can't decide whether my partition is FAT32 or NTFS..."

---

### Post by Breezy Badger on 2006-07-09
just noticed this is what it said in the terminal:

```
xxxx@xxxx:~$ gksudo qtparted
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authenti cation protocols specified are supported and host-based authentication failed
Error: Parted can't resize partitions managed by Windows Dynamic Disk.
No Implementation: Support for opening ntfs file systems is not implemented yet.
Error: Parted can't resize partitions managed by Windows Dynamic Disk.
No Implementation: Support for opening ntfs file systems is not implemented yet.
No Implementation: Support for opening ntfs file systems is not implemented yet.
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying  an unclean file system could cause severe corruption.

```

---

### Post by Breezy Badger on 2006-07-09
ok I fixed it...I had to unmount it first...now its formatted....I just have to figure out how to remount it haha

---

