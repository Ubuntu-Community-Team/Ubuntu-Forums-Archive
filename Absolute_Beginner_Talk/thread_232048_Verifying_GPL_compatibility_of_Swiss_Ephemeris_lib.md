---
title: "Verifying GPL compatibility of Swiss Ephemeris library"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by jamadagni on 2006-08-08
The Swiss Ephemeris is an astronomical ephemeris file set plus library which is licenced under the [Swiss Ephemeris Public Licence]("http://www.astro.com/swisseph/sepl.htm"). I would like to create an application using Qt for GUI and this library for astronomical data. 

Since using the Qt Open Source Edition means I have to licence my Qt-based program under the GPL, I wonder whether the SEPL says anything that makes it incompatible with the GPL. The [FSF GPL page]("http://www.fsf.org/licensing/licenses/index_html") has a list of GPL-compatible and -incompatible licences. But I wonder whether this SEPL is GPL-compatible.

In particular, I want to know whether my application will qualify for inclusion into a Linux distro like Ubuntu if I use the Swiss Ephemeris.

gnu.org and fsf.org are usually very slow in replying to mails, which makes having a meaningful communication with them impratical, so I ask this Linux-related question here.

Thanks in advance for your help.

---

### Post by MrHorus on 2006-08-08
> **jamadagni said:**
> 
Since using the Qt Open Source Edition means I have to licence my Qt-based program under the GPL, I wonder whether the SEPL says anything that makes it incompatible with the GPL. The [FSF GPL page]("http://www.fsf.org/licensing/licenses/index_html") has a list of GPL-compatible and -incompatible licences. But I wonder whether this SEPL is GPL-compatible.


My understanding is that you release your CODE under the GPL - you are not redistributing the library and if people don't want to accept the library's liscence then they won't install it.

You get where I am coming from there?

---

### Post by jamadagni on 2006-08-09
> **MrHorus said:**
> My understanding is that you release your CODE under the GPL - you are not redistributing the library and if people don't want to accept the library's liscence then they won't install it. You get where I am coming from there?
Well I am redistributing the library also with my app since it (the library) is not a standard feature on OS-es. So I need to statically link my app with it. 

[The GPL FAQ]("http://www.fsf.org/licensing/licenses/gpl-faq.html#GPLIncompatibleLibs") has something related to this, I believe. 

Further, a question is whether my app would be included in a Linux distro like Ubuntu. In relation to this, I examined the [XEphem licence]("http://www.clearskyinstitute.com/xephem/download.html") which says usage is "prohibited in commercial or military situations". But XEphem was included in SUSE, whose developers told me that anything that had an OSI-approved licence would be included in SUSE.

[XEphem was never in Ubuntu]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=xephem&searchon=names&subword=1&version=all&release=all") but [it was once in Debian]("http://packages.debian.org/oldstable/misc/xephem") under the non-free category. I wonder, is it possible to get a Debian SRC package and rebuild it under Ubuntu to get a Ubuntu package?

---

