---
title: "Pc-bsd"
date: 2012-10-05
forum: Any Other OS
---

### Post by Welly Wu on 2012-10-05
I visited [http://www.pcbsd.org](http://www.pcbsd.org) and I downloaded PC-BSD 9.1 RC2 Live DVD ISO file. I created a VM Ware Workstation 9.0.0 64 bit 20 GB guest virtual machine and I am installing it now. I am interested in BSD UNIX and PC-BSD seems to be the easiest and most user friendly version just like Ubuntu is the easiest and most user friendly version of Debian. It's taking a long time to install, but I am doing a complete installation with K Desktop Environment. I expec to play around with PC-BSD 9.1 RC2 this weekend to test it out. I like the AppCafe, PBI, and Warden features and I think that they are intriguing.

I will update this thread with more detailed impressions and observations about PC-BSD.

---

### Post by jerrrys on 2012-10-05
Its the most secure OS around

 [http://www.google.com/search?q=bsd+security&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=bsd+security&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by Welly Wu on 2012-10-05
BSD security is legendary. I think that I am going to try out PC-BSD 9.1 RC2 later tonight to see if I can get more progress made in customizing it and improving its performance.

Ubuntu security is also pretty darn good. It's almost right up there with BSD after a lot of hardening and customization. The two are very similar in terms of security. Both are safe to use compared to Windows and OS X.

---

### Post by mips on 2012-10-06
> **jerrrys said:**
> Its the most secure OS around


I don't think it is but I could be wrong.

---

### Post by GeForce 9500GT on 2012-10-06
> [QUOTE]Its the most secure OS around
I don't think it is but I could be wrong.[/QUOTE]


Well...i think it's correct to say that PC-BSD is a very secure OS. Unlike Linux Free-BSD, PC-BSD, Open-BSD runs the Unix kernel which is the basis of the Linux kernel.

---

### Post by IRobinson on 2012-10-09
> **GeForce 9500GT said:**
> Well...i think it's correct to say that PC-BSD is a very secure OS. Unlike Linux Free-BSD, PC-BSD, Open-BSD runs the Unix kernel which is the basis of the Linux kernel.

It is correct that PC-BSD is a very secure operating system.   PC-BSD is a graphical user interface on top of FreeBSD emphasizing a user-friendly desktop system.  You can use KDE, Gnome, Xfce, and with PCBSD 9.1, many, many more windows managers that come with it.   

All the BSD operating systems were developed from the Berkley Software Distribution's development of Unix.  The researchers at the Univ. of California - Berkley had developed numerous improvements to AT&T's Unix code.  It's a long story, but AT&T who owned the copyright to Unix code, started a lawsuit against Berkley.  "The lawsuit slowed development of the free-software descendants of BSD  for nearly two years while their legal status was in question, and as a  result systems based on the [Linux kernel]("http://en.wikipedia.org/wiki/Linux_kernel"), which did not have such legal ambiguity, gained greater support. Although not released until 1992, development of [386BSD]("http://en.wikipedia.org/wiki/386BSD") predated that of Linux. [Linus Torvalds]("http://en.wikipedia.org/wiki/Linus_Torvalds") has said that if 386BSD or the [GNU kernel]("http://en.wikipedia.org/wiki/GNU_kernel") had been available at the time, he probably would not have created Linux."  (Source:  [http://en.wikipedia.org/wiki/Berkeley_Software_Distribution](http://en.wikipedia.org/wiki/Berkeley_Software_Distribution), citing to, Linksvayer, Mike (1993). ["The Choice of a GNU Generation - An Interview With Linus Torvalds"]("http://gondwanaland.com/meta/history/interview.html"). *Meta magazine*. Retrieved 2009-01-20; and  L. Torvalds (January 29, 1992). "[Re: LINUX is obsolete]("news:1992Jan29.231426.20469@klaava.Helsinki.FI")". [comp.os.minix]("news:comp.os.minix"). [(Web link)]("http://groups.google.com/group/comp.os.minix/msg/9f3c7c165aacc83f"). Retrieved 2006-05-11.)  Thus, it is not accurate to say that the Unix kernel is the basis of the  Linux kernel, since Torvalds developed the Linux kernel to avoid infringing  on AT&T's copyright.

Some BSD's are open source and some are closed or proprietary.  The open sourced BSDs include FreeBSD, OpenBSD, NetBSD, OpenSolaris, and several others.  The closed or proprietary BSDs include OSX, SunOS, Solaris, AIX, HP-UX.  Here is a nice chart showing the history and relationships of the BSD operating systems:

[http://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg](http://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg)

All of the BSD-based operating systems are very secure.  It's all in how they are set up.  Notably, OpenBSD is very proactive about security, and developed many functions and integrated cryptography to protect the system.  When OpenBSD is installed, it's default choices are all about security.  NetBSD and FreeBSD have adopted many of the OpenBSD developments, so they are very secure too.  However, they can be hardened further.

PC-BSD is a great desktop system, and I hope you like using it.  Consider doing some research on PC-BSD and FreeBSD.  The BSD community is very friendly, and new users do not get flamed for getting something wrong.  There are some excellent documentation and publications, many free including the FreeBSD Handbook ([www.freebsd.org](www.freebsd.org)).  PC-BSD alone has many resources such as its Forum and mailing lists.  Also consider the Dru Lavigne book titled "*The Definitive Guide to PC-BSD* " (2010).

Please remember that you are using a Release Candidate version.  Things can break or go wrong in beta or release candidate versions.  The final version will be an improved over that, so evaluate on a final release version.

---

