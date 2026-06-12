---
title: "Ubuntu too easy to use?"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by amac777 on 2006-11-08
My friend's wife is a windows system admin but she's got zero linux experience. She's been transferred to a linux based project and wanted to get some experience at home doing basic linux configuration so I recommended ubuntu as a good disto to play around with since that's what I use at home. She tried out the dapper live cd and it configured her internet and worked flawlessly running from cd. 

The result after playing with the live cd: She didn't install it because there was "nothing left for her to do". Said she needs to find a distro that doesn't work so well out of the box so she can fix it.

Thought someone else might get a kick out that.

---

### Post by nereid on 2006-11-08
Give her a try at [Linux From Scratch](http://linuxfromscratch.org) :D

---

### Post by mithras86 on 2006-11-08
You can try Gentoo. There you need to compile every package on your own to install it. Then you can create an ebuild (sort of Gentoo package). 

Gentoo is a distro that forces you to learn how a pc exactly works. It costs some time, but then you know much more than using a out-of-the-box working Ubuntu ;)

---

### Post by LLRNR on 2006-11-08
Hi amac777. I'm a new Linux user myself (Ubuntu is the only distro I tried so far). I'm studying CS at the University and I have experience in C/C++ and x86 assembly programming on MS based systems. My goal is to slowly migrate to Linux from MS and still be a professional person ; I think that Ubuntu is a good place to start from with such a goal in your mind, because it indeed seems to be self-configured, as your friend pointed out, but... you can do a lot of things with it. 

The good thing about Ubuntu is that it covers all sorts of needs - I bet that if I'd manage to convince my dad (who is a French literature professof at the university) to try it out, it would perfectly suit his needs, since he only wants a good text editor (OpenOffice is ok with that), good messaging/chat clients and media players, lol. But this is also a great distro for me, since there are a lot of good things just waiting to be unveiled.

For a professional person, there are a whole damn lot of things to configure by yourself and, since your friend is a system administrator, yes, it would be challenging indeed to try Linux out - anyways, it's known to be a very secure OS and in general, Linux systems were designed with the aim to be very secure, very stable... you know the story. Linux is said to be the best solution for servers (btw you could tell your friend that google uses Linux servers, for instance - I didn't know that myself until recently). Think about permissions and all sorts of things. Think about the UNIX/Linux filesystems, about the way that information on the files is stored in inodes and things like that, think about the 9 bits in each file's inode that represent the permissions on that file (to the user, to the user's group and for others) and so on.

IMHO, Ubuntu is a good place to start with since it already comes self-configured for basic needs, so you don't have to spend time decrypting everything, and by having this advantage you can move on to learning some advanced stuff.

Good luck to your friend!

LLRNR

---

### Post by bluenova on 2006-11-08
Lol, If she wants to do it all herself, rather than have the O/S do it for her, then [Gentoo](http://www.gentoo.org/) or [Linuxfromscratch](http://www.linuxfromscratch.org/) is the way to go, but it's really not for newbies.

---

### Post by sKuarecircle on 2006-11-08
I don't think I have EVER heard of someone looking for a more difficult Linux o/s. EVER!!

---

### Post by Kateikyoushi on 2006-11-08
She has different needs than an average Joe, I do not think spending a weekend with compiling LFS would help her reding manuals and config files would have more benefit. If she wants to see how the system builds up go for gentoo stage 1 install rather than lfs.

---

### Post by nereid on 2006-11-09
Gentoo stage 1 is no different from LFS. Just use stage 3 and your ready to go. 

Recently I stumbled over [GoboLinux](http://gobolinux.org).  A distribution akin to Gentoo but with a very ordered filesystem. Maybe she want's to give it a try.

---

### Post by livinginx on 2006-11-09
I tried Gentoo.  Not near as basic of a setup.  If you want to difficult, try some old school redhat or something from 98/99 :-P  That may be fun.

---

### Post by 3rdalbum on 2006-11-09
Slackware or Debian would probably be good candidates. Lots of setup required, but no compilation of the base system.

---

### Post by Blutack on 2006-11-09
Ask her really really nicely to recompile the generic kernel with bootsplash.org support, package it in a deb and then post it somewhere... :-)

---

### Post by justin whitaker on 2006-11-09
Tell her to go check out GoboLinux. There is always something broken in that distro that needs some serious command line -fu. :rolleyes:

---

### Post by Blutack on 2006-11-09
Lets be honest, as a windows sysadmin she is never going to find anything hard to fix in comparison under linux...mmm, regedit.

---

### Post by DeadEyes on 2006-11-09
Perhaps, just maybe, it might make sense for her to load the same distro as the one she'll be using in work, No?

---

### Post by Blutack on 2006-11-09
The principles are pretty much identical.  I learnt on a scratched mandrake cd I found in a book in the local library.  From there its just scaling up.

---

### Post by bsussman on 2006-11-09
It may be futile to try to make up hard stuff - hypothetical issues never mimic the real world.

Maybe she needs to start looking at some of the questions that get posted here - in some of the more specific forums.

Or, tell her to do everything in a terminal window - no more gui - and add/change users/sudo privs, ftp setup, X config, log analysis, apache maintenance, etc, etc, etc.

---

### Post by seuaniu on 2006-11-09
Ubuntu is fine for her.  If she wants to learn linux, the quickest way to do it is Applications --> Accessories --> Terminal.

Not being a troll here.  If you want to get proficient on any *nix, you're gonna have to get used to a terminal.  Period.  Servers don't have nice GUIs to use.

One of the neat things about Linux (at least to me) is that there isn't any "server" version or "desktop" version when you get down to it.  If she wants to learn how to admin the different servers that you can install, its the same command as if you were getting a new game:

```
apt-get install apache
```

That easy.  In 10 minutes, she'll have a fully functioning webserver at her disposal.  Same goes for email servers, dns, firewalls, collaberation servers like horde or hula, ftp, sftp, active directory domain controllers, anything you want.

When I was first learning, I only had one computer, and thats how I did it.
I couldn't get X configured because I had this old vesa 1MB video card, so I was stuck at the terminal.  I had already nuked my win95 install.  I basically had no choice but to learn how to get it done.  I figure I learned at about 10x speed because I had no choice (MS fdisk couldn't delete the partition because it didn't recognize what type it was - go figure).

---

