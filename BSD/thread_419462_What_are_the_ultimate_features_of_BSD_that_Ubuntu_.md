---
title: "What are the ultimate features of BSD that Ubuntu needs?"
date: 2007-04-23
forum: BSD
---

### Post by Sunnz on 2007-04-23
Just a continuation of these threads:
What are the ultimate features of OS X that Ubuntu needs?
What are the ultimate features of Vista that Ubuntu needs?
What are the ultimate features of Ubuntu that neither Vista nor OS X has?

**Feature - Votes**
securelevel(7) - 1
chflags(1) - 3
cflags - 2
BSD license - 1

Well please only suggest things that are common to the big 4 BSDs, Free, Open, Net and Dragonfly, it is kinda pointless to suggest about the performance of FreeBSD or the security of OpenBSD or etc. when Ubuntu is never going to reach that level of performance in FreeBSD and is currently adequate for desktop use anyway.

On the other hand it is not like Ubuntu actually needs to have these features implemented overnight, but just things that are nice to be implemented or I guess this thread also can be nice for those who want to learn about what's different about BSD's.

---

### Post by igknighted on 2007-04-23
put down another vote for chflags.  Heck, I wish ubuntu could have a make.conf so I could set compiler flags globally like gentoo (if there is, someone please correct me and I will be eternally grateful).  I also think that Ubuntu needs the code review system that BSD employs.  Lots of bugs slip though in linux compared to BSD, I think we can do a much better job.

---

### Post by Sunnz on 2007-04-23
I think you meant cflags. ;)

[*c**[size=4]h[/size]**flags(1)*]("http://www.openbsd.org/cgi-bin/man.cgi?query=chflags&apropos=0&sektion=0&manpath=OpenBSD+4.0&arch=i386&format=html") is a totally different feature that lets root to make various flags to files... for example if you are root, it can make it so that even root can't delete a certain files.

---

### Post by Pobega on 2007-04-23
c*flags, but that is about all; I find everything else a lot easier to use in GNU/Linux, the BSD versions are a lot more challenging to get used to.

---

### Post by Rounin on 2007-04-25
Can I say the BSD license? I know Linux wouldn't be Linux if it had to shed all of its FSF software, but I think it should be considered.

---

### Post by Sunnz on 2007-04-25
Hmmm may I ask, why?

You could port all BSD userland (a non-trival task) to Linux, it would be still Linux. The exact opposite has happened, as there are Gentoo/FreeBSD - Gentoo running on a FreeBSD kernel... but the question always has been, why not just use FreeBSD? And I think that question applies here as well.

---

### Post by Rounin on 2007-04-25
I do actually wish for an Ubuntu flavour of BSD, with the same ease of installation and use, but without the license problems that come with using proprietary software and binary drivers. As I mentioned in another post, imagine seeing actual new games on Li... er, BSD. So to clarify my earlier statement, it's not necessarily a changeover to BSD software I'm arguing for, but rather the use of a BSD-like license, which I think is a very powerful, albeit dangerous, "feature" of BSD.

By the way, I know this wasn't exactly what you asked for, so I guess a small apology is in order. I think it's an interesting thought experiment, though.

---

### Post by mips on 2007-04-25
> **Rounin said:**
>  So to clarify my earlier statement, it's not necessarily a changeover to BSD software I'm arguing for, but rather the use of a BSD-like license, which I think is a very powerful, albeit dangerous, "feature" of BSD.


Personally I prefer the BSD license to the GPL....

---

### Post by Sunnz on 2007-04-25
> **Rounin said:**
> I do actually wish for an Ubuntu flavour of BSD, with the same ease of installation and use, but without the license problems that come with using proprietary software and binary drivers. As I mentioned in another post, imagine seeing actual new games on Li... er, BSD. So to clarify my earlier statement, it's not necessarily a changeover to BSD software I'm arguing for, but rather the use of a BSD-like license, which I think is a very powerful, albeit dangerous, "feature" of BSD.

By the way, I know this wasn't exactly what you asked for, so I guess a small apology is in order. I think it's an interesting thought experiment, though.
I don't quite understand where you are coming from...

GPL terms of GNU/Linux does not restrict users to run properiety, closed-source software, should they choose to.

In fact, the output of GPL programs need not be GPL, e.g. you are free to make closed-source software compiled by GCC... might I also add, BSD uses the GPL'd GCC compiler, and the output of GCC that is BSD, is licensed under BSD.

To my understanding, the lack of commercial games on BSD is due to demand, market, economic, and all that cr ap.

Anyway, there are actually lots of free games on BSD... they are not all 3D bleeding edge type you see, but the old school one like 3D Tetris, boomberman, etc... anyway, I find them pretty enjoyable as well, sometimes I can play it for hours... then there is a bunch of command line games, some of them are actually pretty amazing and interesting in some way... well it is interesting to see what games can be made using no 3D, 2D or pxiel graphics, but plain ascii art!!! Otherwise it feels like visit a museum... I would recommend anyone on BSD to check those out. (in /usr/games/)

---

### Post by Rounin on 2007-04-26
> **Sunnz said:**
> I don't quite understand where you are coming from...

GPL terms of GNU/Linux does not restrict users to run properiety, closed-source software, should they choose to.
But only if you don't use any GPLed libraries. Certain companies, like Trolltech, have a very strict interpretation of the GPL whereby even statical linking is taken to create a derivative work. So just by linking you're in a legal grey zone. That same problem also applies to drivers - one might ask why anyone would want to run proprietary closed-source software in kernel space, of course, but on a desktop system there might be very legitimate reasons why one would want to do so.

Perhaps the problem could be solved by moving such drivers out of the kernel altogether and running them in user space in a microkernel-like manner, though? That way, the FSF crowd could have their GPL and those users that needed it could have their proprietary drivers, and we'd all be happy.

It would seem a lot of people have thought of this before me, even. Though I suppose there's at least one good reason why it hasn't yet been done...

---

### Post by Sunnz on 2007-05-06
Well there's plenty of proprietary software on Linux, because core libraries tend to be licensed under the LGPL: [http://www.gnu.org/licenses/lgpl.html](http://www.gnu.org/licenses/lgpl.html), not the GPL.

---

### Post by Rounin on 2007-07-22
At any rate, it seems like it's not so much of an issue anymore, as it was just announced that Linux is to have a stable API for userspace drivers. I suppose that settles it then; hopefully proprietary drivers can now coexist with Linux without posing a security risk to the rest of the system or needing a license change. Let's hope certain vendors make use of it!

[http://developers.slashdot.org/developers/07/07/22/0442236.shtml](http://developers.slashdot.org/developers/07/07/22/0442236.shtml)
[http://liquidat.wordpress.com/2007/07/21/linux-kernel-2623-to-have-stable-userspace-driver-api/](http://liquidat.wordpress.com/2007/07/21/linux-kernel-2623-to-have-stable-userspace-driver-api/)

---

### Post by howdy1 on 2007-07-27
*BSD's has always been the operating system that GNU/Linux should have been.

nuff said.

---

### Post by kosmic on 2007-08-02
Yap, I love BSD...just wish ubuntu had "chflags"...and "jails" man i love Jails, Ubuntu should use jails instead of chroot, and of course it should also use "IPFW" or "PF" instead of "IPTABLES", it is so simple and powerful to configure a firewall with "PF" or "IPFW" it's miles away from "IPTABLES".

Most of the time I only need 2 rules in "IPFW/PF" to block something, and to block the same thing with "IPTABLES I need 4 rules :(

---

### Post by AnRa on 2007-08-02
> **Rounin said:**
> I do actually wish for an Ubuntu flavour of BSD, with the same ease of installation and use, but without the license problems that come with using proprietary software and binary drivers.You may try [PC-BSD]("http://www.pcbsd.org/") or [DesktopBSD]("http://www.desktopbsd.net/"). ;)

---

