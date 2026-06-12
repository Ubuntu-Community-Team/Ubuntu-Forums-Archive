---
title: "BSD vs Linux"
date: 2007-01-03
forum: BSD
---

### Post by ice60 on 2007-01-03
i installed FreeBSD the other day and was wondering what the differences between Linux and Free/BSD are, i know what some differences are, but i also know there must be some things i haven't found out about yet.

i've only read the first 3 pages from the link below so far; from what i've read it seems well written. i have read the last page too :rolleyes: - [*11. Responses*](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux11.php), and afew linux users seem abit upset by some afew things that were said.

i just wanted to post and ask what others think about BSD vs Linux (in general rather then just this essay) and if you read the essay if you agree with it? :) 
[http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php)

---

### Post by enopepsoo on 2007-01-03
I think that the main difference is the licensing.  The BSD license does not require people to make their code changes public if they are rereleased.  This means that you can take BSD licensed code, change it and sell it as closed source software.

I think Mac OS X did that somehow.

---

### Post by ice60 on 2007-01-03
> **enopepsoo said:**
> I think that the main difference is the licensing.  The BSD license does not require people to make their code changes public if they are rereleased.  This means that you can take BSD licensed code, change it and sell it as closed source software.

I think Mac OS X did that somehow.
yeap, there was also alot written about MS taking the BSD network stack for NT based systems. i don't know if that's really true though.

but, i was hoping to find out some things based on the actual differences between the too OS's, not really about the licences. although that is something i hadn't thought about and is a very big part of each OS.

you know? things like BSD's programs are all written for BSD - like mv, cp, ls, top etc. and Linux is a mix of all different programs :)

---

### Post by RAV TUX on 2007-01-04
moving to the BSD forum

---

### Post by Sunnz on 2007-01-04
A bit old, but still holds some truth: [http://people.freebsd.org/~murray/bsd_flier.html](http://people.freebsd.org/~murray/bsd_flier.html)

Other than that, it is the mainly development model as stated in the article you posted. They got a rigid engineering release cycle, and the distinction between a base system and ports.

Other than that, it depends on the flavour os *BSD, e.g. OpenBSD have a strict code review and makes sure the code is clean; NetBSD have multiple of abstraction of their code to make it run efficiently on more architecture than any other OS.

---

### Post by mips on 2007-01-04
i've seen that essay a few times and do agree with it.

I'm currently installing openbsd on my laptop as a trial, curious to see if i can use it as a functional desktop os. I must admit it is harder than linux for probably because i'm not familiar with it.

will keep ya posted on the progress. So far I did a net type install, have to fix Grub so i can dualboot xp/bsd. i'll continue from there.

---

### Post by ice60 on 2007-01-12
thanks for the replies :)

i haven't spent any time with my freebsd install yet, other then doing the install and getting all the updates. but, i'm definately going to learn as much as i can, then hopefully install open bsd too.

in the past, before i even used linux, if someone mentioned BSD to me the thing i'd think about is a super secure OS (probably thinking of openBSD). and it seems, just from the little time i spent at freenode #freebsd, BSD users do spend more time thinking about security, and that's something that appeals to me.

most of my windows/XP time was spent on security forums and i found learning about securing an OS really is a great way to learn about how that OS works - it teaches you about networking, system processes/files, how things interact, what should be running, troubleshooting, fixing etc, etc. so i hope if i get to grips with freebsd i'll be able to run openbsd, and then learn more about unix :cool:

---

### Post by Sef on 2007-01-13
> I think Mac OS X did that somehow.

Yes, they did.   OSX is based in part on FreeBSD's Darwin.

---

### Post by Sunnz on 2007-01-13
Actually, Darwin have used FreeBSD codes, but again they have open sourced Darwin which contributes back to FreeBSD itself.

Actually, lots of FreeBSD developers are also Darwin developers, and vice versa.

However, Darwin has its own kernel: XNU, also open source. It is built on top of the Mach microkernel. GNU/Hurd is like that too, being built on top of Mach, although Hurd developers (if any) may use L4 instead.

And then, Mac OSX is what built on top of Darwin.

---

### Post by SunnyRabbiera on 2007-01-13
BSD is getting there, I use it at work quite a bit.
But for the desktop Linux is quite a bit better to me, but I swear by my BSD server at work

---

### Post by Bealer on 2007-02-08
> **Sunnz said:**
> However, Darwin has its own kernel: XNU, also open source. It is built on top of the Mach microkernel.

XNU is a hybrid kernel. It's mainly built upon a modified version of Mach 3.0, but also contains BSD components within the kernel.

---

### Post by Sunnz on 2007-02-08
That's right, you caught me there... though I thought it was easier to just say it builds on top of Mach...

But hell, a diagram probably worth a thousand words - see attached.

---

### Post by yatesco on 2007-02-08
My biggest problem is that OracleXE and vmware don't work on BSD.

---

### Post by Bealer on 2007-02-08
> **Sunnz said:**
> That's right, you caught me there... though I thought it was easier to just say it builds on top of Mach...

But hell, a diagram probably worth a thousand words - see attached.

Ah cool. Nice diagram.

Would you say Mac's aren't inherently Unix based then? (Given that most of it's low level architecture is based on Mach)

Just discussing it with a mate. Apple seem to market it as a Unix based system, yet it's mainly based on Mach which was built as a replacement to the Unix kernel.I guess it's effectively "Unix-like" rather than based on Unix.

---

### Post by Sunnz on 2007-02-08
> **Bealer said:**
> Ah cool. Nice diagram.

Would you say Mac's aren't inherently Unix based then? (Given that most of it's low level architecture is based on Mach)

Just discussing it with a mate. Apple seem to market it as a Unix based system, yet it's mainly based on Mach which was built as a replacement to the Unix kernel.I guess it's effectively "Unix-like" rather than based on Unix.
Ha nice question, but nah, UNIX isn't just a kernel...

I know this could be confusing, since Linux itself is really just a kernel, but most people mistakenly refers Linux as the whole operating system, so when it comes to technical discussions like this, it is understandable the we sometimes mistaken UNIX as just a kernel.

As far I understand of, being UNIX isn't about using a particular kernel, but to implement the *UNIX specification*, such that if you have written a program in C on a UNIX system, it should be able to re-compiled easily on other UNIX systems - since they'll be implemented the same *interface*. Note interface here refers to programming interface, not user interface such as command line. Though I think the UNIX specification does require certain CLI commands to be available to the user, like "ls" and "cp", again, this does not require a particular kernel or what not.

Did you know that FreeBSD, OpenBSD and NetBSD aren't distros of BSDs in the sense that Ubuntu is a distro of Linux? They all have their own kernel - you can't just re-compile an OpenBSD kernel on FreeBSD and expect it to work. And these are all **real** UNIX, their code-base are derived the UNIX released by AT&T. Whereas Linux was written from scratch without know any UNIX codes, hence it is called a 'UNIX-clone'.

BTW, Apple is getting their latest version of OS X, Leopard, to be verified by the Open Groups, the guys who defines the UNIX Specification, it is gotta to be more 100% UNIX than anything else out there!!! Except for Solaris.

---

### Post by Bealer on 2007-02-09
Ah yeah. Just been doing some more reading about what UNIX is, and how the term UNIX is allowed (or not so) to be used (in terms of a trademark).

For example FreeBSD is based on 4.4BSD which was (I believe) is a modified version of the original UNIX operating system.

UNIX was at one point though, registered as a trademark, so other operating system's couldn't legally call themselves a UNIX operating system without conforming to the Single UNIX Specification, and also paying a fee for the privilege. 

So many operating systems are called "UNIX-like" as they either don't follow the Single UNIX Specification, or haven't paid for the rights to use the UNIX trademark.

Hence, Darwin (which is made up of the XNU kernel) is currently defined as being UNIX-like (even though Apple state otherwise, I believe there were/are legal battles about it). However, as you mentioned it looks like Apple are trying to become compliant with the Single UNIX Specification for their up and coming Leopard release.

---

### Post by Sunnz on 2007-02-09
The trademark now belongs to the Open Group, and you have to like pay large sum o money to have your OS to be verified by those guys. Sun's Solaris has done so, and perhaps the iPod has made enough money for Apple to do it too.

When it comes to xBSD's history, well, perhaps I'll upload another diagram:

[IMG]http://i54.photobucket.com/albums/g87/dblahdx/Unix-history.png[/IMG]

Well yea, the modern BSDes are all based on 386BSD, which if you haven't guessed yet, runs on 386 machines. They are pretty direct UNIX descendants, however they are all free software and simply doesn't aim to pay the Open Group to have their system to be verified. They do however, follow the Single UNIX Specification very closely.

UPDATE: Have found an article with very interesting BSD and Linux history: [http://www.freebsd.org/doc/en_US.ISO8859-1/articles/bsdl-gpl/article.html](http://www.freebsd.org/doc/en_US.ISO8859-1/articles/bsdl-gpl/article.html)
Though the main story is the argue BSD licence vs. GPL, the historical stuff is still interesting.

---

### Post by handy on 2007-02-12
@Sunnz: Thanks for the great picture, saves lots of words doesn't it?

I use PC-BSD, it's my main OS these days, my uses are simple; internet, doc's, pdf's, DVD's... the standard routine is very easy to deal with on PC-BSD.  Some don't like the .pbi install method, others love it.  You don't have to use .pbi's, all the FreeBSD ports are simply available.  The Forum & community is nice, very small compared to Ubuntu.

The only thing I am using Ubuntu for is to run Guild Wars...  The BSD's are even more limited than Linux as far as games are concerned at this stage.  This will of course change with time.

Over all I have found PC-BSD to be quicker & easier to install, & a simpler, cleaner & tidier OS than the Linux's.  I still love Ubuntu & the community, but if something is easier I will go that way these days.

---

