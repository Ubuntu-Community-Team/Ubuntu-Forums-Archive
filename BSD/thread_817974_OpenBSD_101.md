---
title: "OpenBSD 101"
date: 2008-06-04
forum: BSD
---

### Post by HuBaghdadi on 2008-06-04
Hi.
Why OpenBSD is considered secure?
Because of OpenSSH, Kerberos, PF and other security tools or because it encrypts every file on the hard disk? 
For Ubuntu we have Synaptic and Ubuntu repositories, what about OpenBSD?
Can I use GNOME on OpenBSD?
I'm a developer (Java, Python, Erlang), do you think that OpenBSD would serves me well?
How to know OpenBSD fits my laptop? could I depend on VirtualBox to decide?
Thanks.

---

### Post by MONODA on 2008-06-04
> For Ubuntu we have Synaptic and Ubuntu repositories, what about OpenBSD?
you have the ports system and pkg_add.

> How to know OpenBSD fits my laptop?
many open bsd developers use laptops, and there is support for many wifi cards

---

### Post by cardinals_fan on 2008-06-04
My brief experience with OpenBSD was not pleasant.  The ports system is the worst of any major BSD.  With that said, its very secure and you can certainly try it out.  If it doesn't work out, try FreeBSD or NetBSD.  They're also very secure.

---

### Post by MONODA on 2008-06-04
> My brief experience with OpenBSD was not pleasant. The ports system is the worst of any major BSD. With that said, its very secure and you can certainly try it out. If it doesn't work out, try FreeBSD or NetBSD. They're also very secure.
I am quite interested in trying NetBSD out, it seems like exactly what I want. I just have one question for you, what is the difference between freebsd ports and netbsd pkgsrc besides the number of packages? thanks

---

### Post by cardinals_fan on 2008-06-05
> **MONODA said:**
> I am quite interested in trying NetBSD out, it seems like exactly what I want. I just have one question for you, what is the difference between freebsd ports and netbsd pkgsrc besides the number of packages? thanks
They aren't really very different.  However, I have always found pkgsrc (not wip!) to be more stable and reliable.  Read the [pkgsrc guide]("http://www.netbsd.org/docs/pkgsrc/index.html").  You can also check out [pkgsrc-wip]("http://pkgsrc-wip.sourceforge.net/") (work-in-progress).  Wip isn't nearly as reliable, but it has more packages. Get it via a tarball, not CVS - CVS is very slow from them for some reason.

If you try NetBSD, here are a few thoughts:
[LIST]
[*]An oft-repeated quote in the NetBSD community is that "NetBSD users are smart enough to accept that there's no 3D support".  While it is possible to have 3D support, it's very unlikely.
[*]Keep something else around.  It's not that I don't love NetBSD (believe me, I do!), but it's good to have another option with 3D support, etc.  I alternate between NetBSD and SLAX; yesterday I was on my NetBSD partition, today I'm using SLAX.
[*]Get used to running things through the Linux binary compatability layer.  Don't think of WINE here (where many things fail and you take a huge performance hit).  The so-called 'Linuxulator' usually works very well.  You'll need it for proprietary software such as Opera.  If you can deal with a slightly technical discussion, you should read the 'How does it work?' section [here](http://www.netbsd.org/docs/compat.html).
[*]You may hear that NetBSD packages are old.  This is not true.  What **is** true is that NetBSD likes their software very stable.  If you want brand-spanking-new new stuff, use pkgsrc-wip.
[*]The NetBSD installer is absolutely awesome.  I usually get a system installed in under three minutes.
[*]Since you probably won't get 3D support anyway, the XFree86 bundled with the install disk usually works fine.  Just install a KDE metapackage and you're up and running.
[*]If you've used FreeBSD, you know that ports can take a while to compile.  Pkgsrc is the same; it *automates* compiling, but doesn't accelerate it.  You can install most stuff quickly with pkg_add, something else that should sound familiar from FreeBSD.
[*]Experiment!  NetBSD is a fun system to tinker with.
[/LIST]
Sorry for derailing the OpenBSD 101 thread.  We can get back to topic now ;)

---

### Post by stream303 on 2008-06-06
> **HuBaghdadi said:**
> Hi.
Why OpenBSD is considered secure?

It might take ages to explain, but check out the site itself at

[http://www.openbsd.org](http://www.openbsd.org)

For a beginner, you might be interested in this great project page:

[http://www.openbsd101.com/](http://www.openbsd101.com/)

When searching for BSD-related material, Google has a nice way of just appending BSD (or linux for that matter)

[http://www.google.com/bsd](http://www.google.com/bsd)

---

### Post by HuBaghdadi on 2008-07-16
I hope I'm not awaking a zombie :)
Ubuntu takes care of all the dirty jobs (mounting CD, DVD, flash memory, iPod)
If I'm using OpenBSD, should I do these tasks by hand?

---

### Post by Bachstelze on 2008-07-16
> **HuBaghdadi said:**
> 
If I'm using OpenBSD, should I do these tasks by hand?

Yes ;) The FAQ explains it all, though.

---

