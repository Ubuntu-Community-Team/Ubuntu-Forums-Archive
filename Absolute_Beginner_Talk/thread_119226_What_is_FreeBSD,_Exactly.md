---
title: "What is FreeBSD, Exactly?"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by Rev. Nathan on 2006-01-19
Not sure if this is the right place, but I must say Ubuntu has really been a welcoming way into the world of Linux. I do something from the HOW-TO at least three times a week, always question what I'm typing into the terminal, and am in touch with software, distributions, communities, etc. I made Ubuntu a stepping stone; whatever Distro I find more advanced with better features I would move onto when I was ready.

Only problem? I don't want to move on. Ubuntu is very up-to-date. Not to mention .deb files, apt-get, plenty of software... not to mention the community! I've gotten just about all of my questions answered right here, or on the IRC, and have even been able to contribute. Lurking, say, gentoo's forums, I'm seeing a lot of S.O.L. situations, and a lot of "RTFM!"-type posts.

But BSD intrigues me. What is it, and why do people say it is superior to Linux? Does it offer the same programs and command line? Who is it fit for? Can I run Linux programs on it and vice-versa? Are Linux and BSD in competition with one another, even though both are free? Are there and clear advantages in BSD, and why people so strongly perfer it?

---

### Post by paulmilliken on 2006-01-19
This is an informative link that may answer some of your questions:
[http://en.wikipedia.org/wiki/FreeBSD](http://en.wikipedia.org/wiki/FreeBSD)

---

### Post by fuscia on 2006-01-19
here's a link to an article that contrasts bsd to linux - [http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php)

---

### Post by Galoot on 2006-01-19
[QUOTE=fuscia]here's a link to an article that contrasts bsd to linux - [http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php)[/QUOTE]*Thank you* for this link!

---

### Post by fuscia on 2006-01-19
[QUOTE=Galoot]*Thank you* for this link![/QUOTE]

my pleasure. i found it to be most generous in both its depth and its objectivity.

---

### Post by Sef on 2006-01-19
Think I will try it on my laptop that I use as a test computer 'cause it is so old and falling apart slowly.  Luckily the insides are good.

---

### Post by az on 2006-01-19
[http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux9.php](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux9.php)

A few caveats to the "myths" section of that article.

"BSD doesn't support common hardware."

If we are talking about a wireless card for which someone has written a linux kernel module to make it work, then, no, it will not work in BSD yet.  Someone will have to write a BSD driver for it.  The same goes for webcams, some printers, etc....

Linux has more doodad support because it has more people who use doodads hacking the code.

"But Linux is more popular."
See above.


"BSD is hard to use, more advanced, more complicated, less user-friendly."

Ubuntu is user-friendly.  Ubuntu uses HAL which uses Udev which is a kernel thing to abstract you from the hardware.  When BSD can use udev, then ubuntu will be able to run on it.


Also,

The BSDs do not make as much of a strong statement about software freedom as does Ubuntu.

---

### Post by ertrules22 on 2007-08-05
I would agree with some previous comments made.  I run FreeBSD on an old Dell Inspiron with only 128 MB of RAM.  I am somewhat happy with it.  Although it is difficult to install, and you have to make sure you read everything in the handbook, and installation, and it takes a very, very long time, it is very lightweight.  It runs GNOME or KDE, but you have to begin in a command line interface, and edit a text file before it will boot into GNOME on startup (which I still have not been succesfull doing by the way).  The commands in the command line are very different, and basically when you want to install a new package (which all necessary and extra packages are included on CD 2 of the set) you have to completely restart the computer and go in and add the package off the CD at startup and it takes a long time to add packages to your computer.  It is a perfect choice for slower and older computers, as it runs just as fast as Ubuntu on my old laptop.  If you have a computer that is able to run Ubuntu, I would run Ubuntu though.  The only reason I chose FreeBSD is because of it's lightweightness.
:)

---

