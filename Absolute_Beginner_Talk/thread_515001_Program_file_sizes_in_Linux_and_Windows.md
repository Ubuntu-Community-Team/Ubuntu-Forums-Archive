---
title: "Program file sizes in Linux and Windows"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-08-01
Hi again!

I just wonder...
Why is it that almost every Linux application is so much smaller than in Windows, often one tenth of the Windows-equivalent-app's size?
The Linux apps usually have the same functions as the Windows apps, but yet they're so much larger.

Why is this?

Joakim

---

### Post by skymera on 2007-08-01
Windows is packaged different.
it has all dependencies in one .EXE file.

linux however, is spread between multiple packages.
'Dependencies'

---

### Post by wolfen69 on 2007-08-01
probably because linux apps are more efficient with less bloat. not exactly a technical explanation, but probably true.

---

### Post by Malh on 2007-08-01
Yeah, windows apps tend to waste resources.

---

### Post by Tomosaur on 2007-08-01
While not true of ALL .exe programs, many Windows executables are self-contained. Everything they need to run is compressed inside the .exe file. While this has the obvious advantage of apps not being dependent on one another - it does mean that your system will end up with lots of code which does exactly the same thing. This is incredibly inefficient.

Linux favours modular design. This allows apps to share resources easily, reduces bloat, improves efficiency etc. For this reason, the actual executable file doesn't need to be so large. If it depends on anything, then your package manager will tell you. This can cause some problems, but if you use a good package management system (as Ubuntu does), then such problems should disappear.

Both approaches have advantages and disadvantages.

Both systems have

---

### Post by tgbrowning on 2007-08-01
There could be a variety of reasons. The chief factor in the size of an executable file is going to be the language that it was originally writen in, followed by the efficiency of the compiler. The OS will make a difference as well, but generally not as much as the first two.

Quite a bit of Windows programming, these days, is done in high level languages like C++ which has a huge amount of overhead, especially if the compiler isn't set to be as efficient as possible.  Then there are the numerous programs written in Visual Basic, which really takes up space. 

Most of the core of Ubuntu, if I'm not mistaken, seems to be written in C, which is generally a compact language. Once libraries have been written and thoroughly tested, they generally don't change much or require recompiling very often, which ultimately leads to leaner libraries. Function calls to them take up very little space.

Windows also has security issues stemming from the way it has evolved over the years, since it kind of *just grew* as an OS. Things were kind of taped into the operating system (like networking, modem communications, video, speech, etc). Also Microsoft has been forced by the market to avoid breaking older programs if at all possible and that carries a certain amount of overhead as well. One has to test to see which versions are running, you see, and accommodate them.   

Linux seems to have avoid that by working out the packaging sysem it uses which forces most programs to uninstall previous incompatible versions. If you notice, after an update, you'll see some packages have been uninstalled which makes for smaller files.

Browning>>>

---

