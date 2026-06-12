---
title: "Partitioning"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by Berticus on 2005-09-15
I'm not sure if this is the right place to post this...I'm somewhat new to Linux.  I've been able to do some stuff on init 3.  I currently have Fedora Core 4 installed on a hard drive.  I kinda know what a partition is.  Well, to my understanding it's a "wall."  Basically it divides the hard drive up so you can run multiple operating systems or have different filesystems on 1 hard drive.  Did I get at least that part right?

So I was wondering, if I partition my hard drive, will I be able to access the filesystem of Fedora?  How about the programs?  Or to sum it all up, will everything basically carry over so that I don't need to re-install all of my programs, and re-set up everything like accounts and all that.

---

### Post by Kapre on 2005-09-15
[QUOTE=Berticus]I'm not sure if this is the right place to post this...I'm somewhat new to Linux.  I've been able to do some stuff on init 3.  I currently have Fedora Core 4 installed on a hard drive.  I kinda know what a partition is.  Well, to my understanding it's a "wall."  Basically it divides the hard drive up so you can run multiple operating systems or have different filesystems on 1 hard drive.  Did I get at least that part right?

So I was wondering, if I partition my hard drive, will I be able to access the filesystem of Fedora?  How about the programs?  Or to sum it all up, will everything basically carry over so that I don't need to re-install all of my programs, and re-set up everything like accounts and all that.[/QUOTE]

You got the patitioning part correct. But you have to keep in mind that Fedora and Ubuntu are built or separate platforms. Fedora is RPM based and Ubuntu is Debian based. You can access your Fedora Core file system when you're on Ubuntu (or any other distro) but carrying over your programs I will say you cannot.

K

---

### Post by Berticus on 2005-09-15
Well, I have apt-get enabled on Fedora, will those programs carry over?

Is there not a way for Fedora and Ubuntu to share my home folder?

---

### Post by rj686 on 2005-09-15
[QUOTE=Berticus]Well, I have apt-get enabled on Fedora, will those programs carry over?

Is there not a way for Fedora and Ubuntu to share my home folder?[/QUOTE]
 apt-get on Fedora isn't true debian its just kind of a mask to help with dependencies

---

### Post by Berticus on 2005-09-15
aight, that means I've got a lot of installing and configurations to do...

So let me go back to my other questions, is there a way for them to share some things?  Like the home folder?  Instead of having a separate one for Fedora, and then another one for Ubuntu.  I guess it would be difficult, or likely totally impossible, for them to share databases?

---

### Post by SilentCacophony on 2005-09-15
It's technically possible to share the /home between two distros, so I hear, but they would tend to make a mess of it with different configuration files in most cases, I'd bet. I don't think I'd try it.

---

### Post by Berticus on 2005-09-15
Okay, well I guess I'll just separate them completely...  I can't really separate from FC4 cuz that was kinda my first Linux experience, and it's like your first car.  You can't really separate from it...  I really started almost 2 years ago with RH8, but didn't work on it a lot.  Then I jumped to FC4 a few months ago and really started going.

I've started up the disk twice and got to the partition part.  However, I'm completely confused about how to do it all.  When I installed FC4, I never thought I'd install multiple OS on the same HD.  I've never partitioned a hard drive, and I barely know what it is (as you saw, or rather read).  I've searched a little bit...  so far didn't find anything useful...

The last thing I would do is format Ubuntu over FC4, and re-install FC4.  It's probably the easiest since FC's installation process is very graphical, and doing the partition looks very easy (tell it to keep all partitions intact).

So someone wanna point me in the right direction?

---

### Post by Kapre on 2005-09-15
Berticus - since you've got FC4 going for you and you really want to try Ubuntu. Try looking at the install how to [THIS](https://wiki.ubuntu.com/Installation/I386) and it will guide you to the rest of the install (partitioning your existing disk also).

Please make sure to use GRUB from Ubuntu as the one to handle your boot sequence (I find it more easy than LILO).

K

---

### Post by Berticus on 2005-09-16
I partitioned the hd, but now it seems as though I can't get back onto Fedora :(

How do I manage partitions in here?

------------------------------------------**Edited**------------------------------------------
I know I still have it cuz when partitioning, I split the hd directly in half for each OS.  I went to the filesystem, and it's showing the correct amount it should have.

---

