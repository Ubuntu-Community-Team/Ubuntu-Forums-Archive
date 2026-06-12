---
title: "Best stable media partition filesystem for Linux/OSX dual boot"
date: 2011-01-24
forum: Apple Hardware Users
---

### Post by theromanone on 2011-01-24
Hi there, dual booting linux and Snow Leopard.. I am re-formatting my media partition (which I keep separate from the linux and osx files so as to keep them safe if I want to reinstall/upgrade the operating systems or mess something up), and was wondering as to the best filesystem I should pick? I would do ext4, but from what I understand osx cannot read/write to it natively or in a stable fashion.

Any suggestions? Thanks!

---

### Post by nevius on 2011-01-24
> **theromanone said:**
> Hi there, dual booting linux and Snow Leopard.. I am re-formatting my media partition (which I keep separate from the linux and osx files so as to keep them safe if I want to reinstall/upgrade the operating systems or mess something up), and was wondering as to the best filesystem I should pick? I would do ext4, but from what I understand osx cannot read/write to it natively or in a stable fashion.

Any suggestions? Thanks!

As long as none of your files are larger than 4GB, go with FAT32.

---

### Post by theromanone on 2011-01-24
Most of my movies and even tv shows are HD and are from 4 to 10GB... thats the thing. I had ntfs left over from 3 years ago from when I originally replaced windows with linux, but didn't want to not be able to read my music in windows if I didn't like linux. What happened was the ntfs partition never had windows installed on it at all, just files, I just want something new since it doesn't seem partition friendly as I like to experiment with new distros often.

---

### Post by srs5694 on 2011-01-24
I'd go with HFS+ (aka "Mac OS Extended," IIRC). Linux has good read/write support for it, and of course it's Mac-native. There are a couple of caveats, though:


[list]
[*]You'll have to create and use the filesystem *without a journal*. This won't degrade performance or stability, but it will cause long filesystem check times in the event of a power outage or other uncontrolled shutdown.
[*]Because HFS+ supports Unix-style ownership and permissions, you'll need to set permissive permissions or, better, coordinate your username/UID mappings between OS X and Linux. You can change your Linux UID values with the "usermod" command. I'm not sure offhand how to do it in OS X. Either way, you may need to go in and clean up file ownership after the fact. Alternatively, you could create a new account in one OS or the other, set its UID value appropriately, and begin using that account as your regular account.
[/list]

---

### Post by theromanone on 2011-01-24
Figured I might as well do something that windows 7 can read/write as well... since that will likely be installed on the side at some point..
Ntfs sounds like the best one so far, since I'll be using linux 90% of the time and I've never had a problem with files written to ntfs. 

How bad is this instability with hfs+? Am I going to lose some files or corrupt a few documents when I randomly reboot the computer, or shutdown improperly?

The media partition will be used as a server of sorts on the same hard drive, with all three OS's reading/writing to and from it.

---

### Post by srs5694 on 2011-01-25
For triple-boot OSX/Linux/Windows, NTFS may be the best bet, but you'll probably want NTFS read/write drivers in OS X. There's a version of NTFS-3g for OS X that should do the job, and also a commercial product (I don't recall the name offhand, though). I didn't suggest it before because you mentioned only OS X and Linux, and NTFS is a poor choice for those two alone. The problem is that there's no disk check utility for NTFS in either OS, so when (note "when", not "if") the system shuts down improperly, you'll be left with NTFS in an inconsistent state and you won't be able to do anything with it until it's checked in Windows. This is obviously a problem if you have no Windows installation! With Windows installed, though, you can reboot to Windows and fix the problem.

I don't recall ever seeing any reports of problems with HFS+ under Linux, aside from an inability to write to journaled disks and permissions issues if usernames and UIDs aren't mapped consistently in the two OSes. I mentioned problems with uncontrolled shutdowns because these things do happen because of power failures and system crashes that are unrelated to the filesystem. It's just that the lack of a journal (to get read/write support in Linux) causes longer filesystem check times when you reboot. (I believe you'd need to do the check in OS X, too.)

---

