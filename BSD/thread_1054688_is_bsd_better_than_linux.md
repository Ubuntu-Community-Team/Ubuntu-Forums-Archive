---
title: "is bsd better than linux?"
date: 2009-01-29
forum: BSD
---

### Post by mamamia88 on 2009-01-29
i'm just wondering seeing how i've never used bsd if it's better than linux

---

### Post by cardinals_fan on 2009-01-29
No operating system is universally "better" than another.  They all have their pros and cons.

With that said, I do have a certain passion for BSD systems.  My favorite is NetBSD, which is lightweight and simple.  FreeBSD is also very solid.  DesktopBSD is FreeBSD with a KDE graphical system by default.

BSD requires a somewhat different mindset.  The greatest things about BSD lie in stability, security, and systems administration, not flash or bling.  Flash is always a challenge (version 7 is perfect through Linux emulation, 9 is thready).

If you are in the mood for something new, trying a BSD system can be very rewarding.  If you post more about what you want, I can recommend one.

---

### Post by -grubby on 2009-01-29
The "Best" OS is subjective. "Use what works for you".

---

### Post by kk0sse54 on 2009-01-29
Like cardinals_fan said there's pros and cons for both so it really just comes down to personal preference. Ask me and I'd say my favorite operating system is NetBSD, ask another random person and hell it might even be OS X for them :p.

Unfortunately, I think the biggest problem is that most users don't understand *BSD so either they dismiss it or when they try it out they expect it to be like Linux.

Here's a nice comparison that focuses more on the functional differences instead of why you should use one over the other
[http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php)

---

### Post by RiceMonster on 2009-01-29
Why don't you try and find out?

That said, I still need to try *BSD. I haven't been interested in trying any new distros/OS's yet though.

---

### Post by SunnyRabbiera on 2009-01-29
In servers BSD is best, but for the average user maybe linux is better.
If you use a lot of flash sites I would not suggest using BSD though.

---

### Post by mamamia88 on 2009-01-29
cool i think i'll at least give it a shot in virtualbox.

---

### Post by kk0sse54 on 2009-01-29
> **mamamia88 said:**
> cool i think i'll at least give it a shot in virtualbox.

Virtualbox has horrible support for *BSD ,particulary NetBSD. Try using vmware server instead, KVM, or Qemu (although I've been mixed reports on using qemu with openbsd in a vm)

---

### Post by cardinals_fan on 2009-01-30
> **mamamia88 said:**
> cool i think i'll at least give it a shot in virtualbox.
Virtualbox is horrid with BSD (and anything else, but that part is opinion).  Qemu works very well with all of them except OpenBSD, and I think even that works to some extent.

---

### Post by Sorivenul on 2009-01-30
"Better", as has already been stated, is a matter of personal opinion. 

I enjoy the BSD systems, and personally prefer FreeBSD, as you can see from my signature. 

As with Linux distributions, the BSDs vary in capability and philosophy regarding development goals. OpenBSD focuses on security, NetBSD on portability, and FreeBSD performance and stability. Of course each distribution has other goals, as well, but these seem to be the most mentioned regarding each BSD. 

[NetBSD is been proven to run on a toaster]("http://www.embeddedarm.com/software/arm-netbsd-toaster.php"), well, technically and ARM, but it's an ARM running a toaster.

The OpenBSD group has developed quite a bit of software that "advanced" users and security-minded folk know and love, such as OpenSSH, bcrypt, and pf - Google them if you want to learn more. 

FreeBSD powers many sensitive, high volume servers in the world. At one time, and possibly still, Yahoo, MP3.com, and Hotmail (Yes, a Microsoft product), were run on FreeBSD. It also was part of the base for Darwin, which in turn is the base for Apple's OS X.

Reading material and more:

FreeBSD - - -
[LIST]
[*][FreeBSD is NOT Windows]("http://vtbsd.net/notwindows.html")
[*][Why FreeBSD?]("http://www.ibm.com/developerworks/opensource/library/os-freebsd/")
[*][The FreeBSD Diary]("http://www.freebsddiary.org/")
[*][FreeBSD Basics]("http://oreilly.com/pub/ct/15")
[*][FreeBSD Portal]("http://www.freebsdportal.com/")
[*][DesktopBSD - FreeBSD with a KDE Desktop]("http://www.desktopbsd.net/")
[/LIST]
OPENBSD - - -
[LIST]
[*][OpenBSD 101]("http://www.openbsd101.com/")
[*][OpenPorts - OpenBSD ports collection]("http://openports.se/")
[*][BSDanywhere - OpenBSD LiveCD]("http://bsdanywhere.org/")
[/LIST]
NETBSD - - -
[LIST]
[*][NetBSD on a Toaster]("http://www.embeddedarm.com/software/arm-netbsd-toaster.php")
[*][NetBSD pkgsrc]("http://www.netbsd.org/docs/software/packages.html")
[*][Jibbed - NetBSD LiveCD]("http://www.jibbed.org/")
[/LIST]

Cheers!

---

### Post by Vince4Amy on 2009-01-30
It's different but something that is different can't really be "better". I like BSD and when the ATI Support is stronger I will use it because I prefer it to Linux.

---

### Post by Frak on 2009-01-30
I just like BSD. I think it's better than Linux. Talk to most people here, and they'd say Linux was better than BSD.

Better is subjective.

---

### Post by techmarks on 2009-02-01
I like FreeBSD very much.

Is it better than Linux? I think it mostly is, but it also depends on what you are doing.

For virtualization BSD is not as good as Linux, other than that I think it's better.

I installed it on my laptop.  After having wireless issues, and annoyances with the Linuxes, FreeBSD was so simple.
I installed it and the wireless card just started up!
I didn't even have to scan for a signal is automatically found it and connected.

Just be aware that the FreeBSD install is very basic.

You'll have to configure everything yourself to set it up for a desktop environment, (I'm using XFCE with it)

The Linux compatibility is nearly perfect, you can run just about any Linux software (Flash is still a problem because Adobe will not release a FreeBSD version) and there's no difference in speed.

Also some of the commands are a little  different than in Linux. (I think it's because FreeBSD was not System V based)

---

### Post by handy on 2009-02-01
I used PC-BSD (FreeBSD) a couple of years or more ago for a while.  It was fine, the community was nice but quite small.  I couldn't do some things that I wanted to with PC-BSD so I moved on.

I currently use FreeNAS, which is a superb FreeBSD based NAS distro(?).  The only fault I could find with it (FreeBSD) is the somewhat limited hardware support for things like PCI SATA cards.  It certainly supports a lot of RAID cards though.

---

### Post by mikjp on 2009-02-01
The question is exactly as good as: is openSUSE better than Ubuntu? Or: Is Ubuntu better than Fedora?

Greetings,

m

---

### Post by handy on 2009-02-01
> **mikjp said:**
> The question is exactly as good as: is openSUSE better than Ubuntu? Or: Is Ubuntu better than Fedora?


To a point I agree.

Though there is an unfortunate difference, in that the BSD's don't get quite as much support as the Linux distro's do; demonstrating itself in the fact that there is software that is available & running on most of the Linux distro's that is not available on the BSD's.

---

### Post by Sorivenul on 2009-02-01
> **handy said:**
> Though there is an unfortunate difference, in that the BSD's don't get quite as much support as the Linux distro's do; demonstrating itself in the fact that there is software that is available & running on most of the Linux distro's that is not available on the BSD's.
Thus, the BSD Linux emulation layer.

---

### Post by glotz on 2009-02-01
The original question has very much to do with licenses. BSD uses a "weaker" free software license than Linux, which uses the "strong" GNU GPL copyleft free sotware license. Those two are incompatible, thus you must choose one. I much prefer the GNU GPL.

[http://www.gnu.org/philosophy/why-copyleft.html](http://www.gnu.org/philosophy/why-copyleft.html)

---

### Post by Sorivenul on 2009-02-01
> **glotz said:**
> The original question has very much to do with licenses. BSD uses a "weaker" free software license than Linux, which uses the "strong" GNU GPL copyleft free sotware license. Those two are incompatible, thus you must choose one. I much prefer the GNU GPL.
No need to start a flame war on licensing and rights. If you are going to put a comment like this in a thread, explain *why* the BSD license is "weak" and why the GPL is "strong. And do so in your own words.

The BSD license states that whomever can do whatever they wish with the source, including close it, but that there is no warranty, and none of the original authors have any liability. This is about as "free" as in "non-restrictive" as licenses come, without being Public Domain. The GPL, in general protects the code, in that it ensures that the code stays free, more than the coder.

Now that my two cents are in, some further reading:
[LIST]
[*][Why choose the BSD license?]("http://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html")
[*][GPL vs. BSD, a matter of sustainability]("http://www.matusiak.eu/numerodix/blog/index.php/2007/12/15/gpl-vs-bsd-a-matter-of-sustainability/")
[*][GPL vs BSD: A GPL advocate's perspective]("http://slashdot.org/articles/99/06/23/1313224.shtml")
[*][Linguistic problems of GPL advocacy]("http://news.slashdot.org/article.pl?sid=08/07/08/1832255")
[*][Make Your Open Source Software GPL-Compatible. Or Else.]("http://www.dwheeler.com/essays/gpl-compatible.html")
[/LIST]

---

### Post by glotz on 2009-02-01
You don't understand the question if you see a flame war here. It's obvious on the other hand already since you seem to support the BSD side of things. The OP asked a question and I answered it.

These terms strong and weak are [not my invention](http://en.wikipedia.org/wiki/Copyleft#Strong_and_weak_copyleft). Strong means you cannot restrict the rights of consecutive users. Weak is the opposite. Copyleft licenses are better for the end user and the community.

---

### Post by Sorivenul on 2009-02-01
> **glotz said:**
> You don't understand the question if you see a flame war here. It's obvious on the other hand already since you seem to support the BSD side of things. The OP asked a question and I answered it.
1.) The original question is subjective, as is the matter of licensing preferences.
2.) Don't assume I support one side. I support choice. I also support comprehensive education. If somebody wants to use the GPL, that's fine. If somebody wants to use the BSD license, that's fine. Let them learn about both.
3.) I don't see how restricting the subjective matter of OS preference to another subjective matter like licensing answers any question. 

Also, from the GNU website, see the [Licensing Compatibility List]("http://www.gnu.org/philosophy/license-list.html"). The 3-clause BSD license and 2-clause BSD license (FreeBSD license) are GPL-compatible.

---

### Post by cardinals_fan on 2009-02-01
> **glotz said:**
> The original question has very much to do with licenses. BSD uses a "weaker" free software license than Linux, which uses the "strong" GNU GPL copyleft free sotware license. Those two are incompatible, thus you must choose one. I much prefer the GNU GPL.

[http://www.gnu.org/philosophy/why-copyleft.html](http://www.gnu.org/philosophy/why-copyleft.html)
Why exactly do you say that they are incompatible?  I run lots of GPL software on my NetBSD system, and lots of BSD-licensed software on my SliTaz system.

---

### Post by glotz on 2009-02-01
@ soverinul Ok, you got me confused now. Are you a lawyer by any chance? I mean, how can a copyleft license be compatible with a non-copyleft license? Doesn't that make copyleft moot?

@cardinals_fan See the Licensing Compatibility List link soverinul posted above.

I don't know about you guys but freedom is the reason that convinced me to start using free software. No, this is not an insult, it's just a statement.

---

### Post by cardinals_fan on 2009-02-01
> **glotz said:**
> @ soverinul Ok, you got me confused now. Are you a lawyer by any chance? I mean, how can a copyleft license be compatible with a non-copyleft license? Doesn't that make copyleft moot?
I can't speak to the legalese in the link, but there is a difference between compatible use and compatible development.  I can use GPL'd software on BSD system without having it be GPL-licensed, and vice-versa.  What I can't do is modify the GPL code and distribute it as BSD-licensed.
> **glotz said:**
> 
I don't know about you guys but freedom is the reason that convinced me to start using free software. No, this is not an insult, it's just a statement.
I want to have the source available.  That's all I need.

---

### Post by Sorivenul on 2009-02-01
> **glotz said:**
> @ soverinul Ok, you got me confused now. Are you a lawyer by any chance? I mean, how can a copyleft license be compatible with a non-copyleft license? Doesn't that make copyleft moot?
I'm not a lawyer; I enjoy reading.
[LIST]
[*][What does it mean to say two licenses are compatible?]("http://www.gnu.org/licenses/gpl-faq.html#WhatIsCompatible")
[*][What does it mean to say a license is "compatible with the GPL?"]("http://www.gnu.org/licenses/gpl-faq.html#WhatDoesCompatMean")
[*][On why the original BSD license is incompatible, while newer versions are.]("http://www.gnu.org/licenses/gpl-faq.html#OrigBSD")
[*][Permissive vs. Copyleft licensing]("http://en.wikipedia.org/wiki/Free_software_licence#Permissive_versus_Copyleft_controversy")
[*][More on License Compatibility]("http://en.wikipedia.org/wiki/License_compatibility")
[/LIST]
Freedom is a large part of what convinced me to join this world as well. [Definitions of this term may vary]("http://en.wikipedia.org/wiki/Copyleft#Types_of_copyleft_and_relation_to_other_licenses").

Peace.

---

### Post by handy on 2009-02-01
> **Sorivenul said:**
> Thus, the BSD Linux emulation layer.

Is it correct that that layer still does not allow all Linux kernel based software to run on it.  Or at least run on it as well as it runs on Linux?

I am asking the question out of ignorance.  I know that I could not get Flash, Cedega & Wine to work on PC-BSD a couple of years ago.  Things have very likely changed since then.  Hopefully?

---

### Post by kk0sse54 on 2009-02-01
> **glotz said:**
> 
I don't know about you guys but freedom is the reason that convinced me to start using free software. No, this is not an insult, it's just a statement.

When referring to freedom in a software sense, I can almost assure you that OpenBSD is much more free than whatever linux distro you are currently using.

---

### Post by glotz on 2009-02-01
> **glotz said:**
> @ soverinul Ok, you got me confused now. Are you a lawyer by any chance? I mean, how can a copyleft license be compatible with a non-copyleft license? Doesn't that make copyleft moot?

[QUOTE=Sorivenul]
[*][Permissive vs. Copyleft licensing]("http://en.wikipedia.org/wiki/Free_software_licence#Permissive_versus_Copyleft_controversy")[/QUOTE]

For the ones also puzzled by my question and not so keen to read, here's the relevant passage. To make a long story short, the answer is **one way compatibility**.

Quote: *Code licensed under a permissive free software licence, such as the BSD licence, can be incorporated into copylefted (e.g. GPL'd) projects. Such code is thus "GPL-compatible". There is no need to securing the consent of the original authors. In contrast, code under the GPL cannot be relicensed under the BSD licence without securing the consent of all copyright holders. Thus the two licences are compatible, but the combination as a whole must be distributed under the terms of the GPL, not the permissive licence.*

---

