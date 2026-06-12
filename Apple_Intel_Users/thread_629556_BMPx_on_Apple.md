---
title: "BMPx on Apple"
date: 2007-12-02
forum: Apple Intel Users
---

### Post by HokeyFry on 2007-12-02
My friend saw the BMPx player on my laptop and thinks its pretty good. He wants it. Unfortunately he has a Mac and does not want to switch to Linux. Because Mac OSX is based on Unix, is it possible to compile a program like BMPx on a Mac platform and run it?

---

### Post by sethvath on 2007-12-02
Short answer no

---

### Post by andrego on 2007-12-02
It's possible you could compile it, provided he has X11 installed, but it would be anywhere from annoying (experienced user) to nearly impossible (if he is a new user).

Try [www.macports.org](www.macports.org), which, as it sounds, contains patches/ports to allow most common software to build on OS X w/ X11.  It even has pre-compiled binaries.

EDIT: Though the BMPx package isn't in macports, macports would allow you to install the dependancies (gtk, etc), and then you could simply download the source tarball, extract, './configure', and 'make install'.

*should* work, but I've not tested it, so ymmv

---

### Post by sethvath on 2007-12-02
Look at the [bmpx dependencies list]("http://bmpx.beep-media-player.org/site/BREAK_MY_BMP%21") and try compiling it on tiger/leopard yourself. I've tried it on tiger and it didnt work. 

Until someone convinces me otherwise I'm sticking to my previous answer of no. Macports does not list bmpx as one of its ports either.

---

### Post by andrego on 2007-12-02
I have no interest to run the software, so I don't feel like spending a few hours trying it out.  Just trying to be helpful and give him some options.

Since you've tried it and it didn't work, what issues did you run into?  Error messages during compile?  Missing dependancies?

---

### Post by HokeyFry on 2007-12-02
oh i havent tried compiling it yet, i just wanted to know if it was possible

---

