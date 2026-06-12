---
title: "Some silly, silly questions"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by melody on 2006-07-13
Hi, I'm one of those kids who have used Windows for all their life, but now I'm sort of forced to switch - XP crashed and I've been wanting to try out Ubuntu for a long time already... so I have a few questions. Sorry if they've been answered a billion times already but I'm on a Live CD now, 640x480 screen resolution so actually looking for something is very uncomfortable. -.- I looked through other support sections but didn't really find an answer to my questions... I'm rather advanced when it comes to working with Windows, but Linux and switching between those two? I'm a complete new to that. Anyhow, here's what I want to know - can I have both Ubuntu and XP on my computer, so I could possibly switch between them if needed? Also, if I want to keep my existing files... can I still keep my programs, like for example Photoshop etc? And will they work? 

As some wise man said... the fool is the one who doesn't ask questions >__< help please?

---

### Post by Sonic Alpha on 2006-07-13
You can keep both, should you wish, we call this a "dual boot" system.  That's how I have my PC set up.

Ubuntu should install "grub", which lets you choose which operating system you wish to use shortly after you power up the computer.

It's better to install XP first (and leave space for Ubuntu), and then install Ubuntu.

There are a number of guides around on how to do this :)

---

### Post by tribaal on 2006-07-13
Yes, you can run both on your computer.

Either you dual boot (you get to decide at boot-time which OS will be used), or you can even make both run concurrently on the same machine with the help of virtualization software ([VMware]("http://www.vmware.com/") being the most famous).
If you wish to have the less problems, I suggest you start by dual-booting.
To do that, the eaisest way is to install windows first (leaving enoughdisk space for Ubuntu to use), and then install ubuntu.

On the programs:

Well you will only be able to run windows programs (the ones you already own) on windows, or to some extent by using [wine]("http://www.winehq.com/"), which work s like an [emulator]("http://en.wikipedia.org/wiki/Emulator") (although it's not one, technically).

Most windows software have a [linux counterpart]("http://ubuntuforums.org/showthread.php?t=33183").

Hope this helps.

- trib'

---

### Post by Radioactive Fellow on 2006-07-13
As Sonic Alpha said you can dual boot XP/Ubuntu. You are not going to lose any information stored on your Windows partition and will be able to use all your Windows software installed without any trouble.

Welcome to the Community and to Ubuntu.

---

### Post by MaximB on 2006-07-13
before you install ubuntu know that ubuntu **can't** write into NTFS drivers
it can only read/copy from them
so you should make fat32 or ext3 partition to share between ubuntu and winxp.

---

### Post by stig on 2006-07-13
As an alternative to setting up dual boot from your existing hard disk you could install a second hard disk, especially if you need some extra disk space. Then install Ubuntu on the new disk.

Hard disks are very cheap now if you buy a modest sized one, and not that difficult to install (I did it and yet I know very little about PCs!)

Don't spend too much time trying to run Win-based software - have a look at all the great Linux software that's out there - and it's very easy to install and uninstall on Ubuntu if you restrict yourself to the thousands of applications in the repository.

---

### Post by Radioactive Fellow on 2006-07-13
> before you install ubuntu know that ubuntu can't write into NTFS drivers it can only read/copy from them

It can be done, its experimental and not recommended tough. You can read about it here.

[http://www.ubuntuforums.org/showthread.php?t=142481&highlight=writing+ntfs]("http://www.ubuntuforums.org/showthread.php?t=142481&highlight=writing+ntfs")

---

