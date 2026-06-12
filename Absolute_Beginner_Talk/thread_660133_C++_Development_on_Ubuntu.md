---
title: "C++ Development on Ubuntu"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Kartari on 2008-01-06
Hi all,

I've been a C/C++ software developer for many years on Windows with MSVC++.  But I have been eying Linux for the longest time, with Ubuntu in particular in the back of my mind for a couple of years now.  I've made some changes already, and am happy with Firefox, Thunderbird and, more recently, GIMP for my occasional art forays.

My question is, if I switch to Ubuntu, what are my options for C/C++ development?  I recall using gcc and emacs way back in the mid 90's on a Unix network (Sun Solaris I believe), but I admit I've become fond of the MS IDE, as much as I can't take Windows for much longer for other reasons. :)  I am willing to go back to IDE-less development if need be, and have spotted a few forum posts on gcc, but would appreciate knowing all my options before making the plunge.

Also, while I am interested in developing on a Linux platform, I intend to make software that works on not only Linux but Windows and Mac as well.  I'm unfamiliar with this, as I've always developed on Windows for Windows to this day.  I figure I'll need to be running all three OS's to test them properly, but could I develop entirely on Linux/Ubuntu?  Or would I need to recompile my code on each OS separately?  Also, I am assuming anything I develop on Ubuntu will work across most, if not all, Linux distributions, since they all use the same kernel... is this a correct assumption?

Thanks so much for any insight!

---

### Post by Vadi on 2008-01-06
gcc and emacs are still about.

For IDE's though, the major options are KDevelop, Code::Blocks, Anjuta, Eclipse, and a ton of programming editors.

(I have no idea about cross-Linux compatibility though, so I'm interested in the answer there too)

---

### Post by Kartari on 2008-01-06
Thanks Vadi.  Your response made me think of a new question.  Would it make any difference as far as C/C++ development goes if I went with Kubuntu instead of Ubuntu?  I noticed that KDevelop sounds like it got its name from KDE, so I looked it up and it appears to only work with KDE, and I know that Kubuntu uses KDE while Ubuntu uses GNOME.

---

### Post by Vadi on 2008-01-06
Nono. You can have KDE apps run on Ubuntu fine, you just install the kde libraries (when you install kdevelop, it'll ask you for like 100mb of kde libraries).

I use Ubuntu myself, because I don't like KDE as the desktop enviroment. But KDE has great apps (kdevelop, amarok) and they work just fine (really.) in my ubuntu.

---

### Post by zero-9376 on 2008-01-07
this might be of interest particularly the comment at the end related to ubuntu:

[http://thebeezspeaks.blogspot.com/2007/12/cross-compiler-blues.html](http://thebeezspeaks.blogspot.com/2007/12/cross-compiler-blues.html)

apart from wine there is also the option of running windows in a virtual machine using virtualbox. i think there is pearpc or something for mac as well.

---

### Post by angryfirelord on 2008-01-07
Try Geany. It's lightweight and does the job well.

---

### Post by ivancamilov on 2008-01-07
Well, if you are only going to use ANSI C++, then you shouldn't have any compatibility issues on Windows or Mac. On the other hand, you probably won't stick to just ANSI, since you'll probably need a lot of OS specific functions.

As for the editor, Agreeing with angryfirelord, I would recommend geany.

Finally, of course, if you are going to use your programs in other OS, you'll need to recompile them for each OS, since every OS needs it's own object code. You don't need to do it in the other OS though; just install the compiler that you need. For example, I think (but I'm not sure, you might want to check this) that g++ is the C++ Intel Compiler for Windows.

---

### Post by Kartari on 2008-01-07
Thanks everyone, this is great.

As far as gcc/g++ goes, I just perused the documentation and found that, while C++ is of course supported, Chapter 2, Language Standards Supported by GCC, fails to specify its compatibility with Standard C++.  It's mentioned here that support for the 1999 revision of Standard C is "incomplete", so I'm concerned about C++ and how completely it's supported.  Anybody know about this?  Thanks.

---

### Post by Vadi on 2008-01-07
One thing I can tell you from cross-platform experience is that it's quite ironic. It's easier to compile for windows from linux (via a virtualization solution + mingw) than for mac, which use the gcc/g++ natively.

First off because Apple prohibits anyone on their EULA to run the OS in a virtual machine, and there has been limited sucsess by people in getting a cross compiler working (I tried, gave up after weeks). Joined the #macdev chat for help, in the end, they told me that the only way to develop for a mac is on a mac. So, I guess apple made a bit of an oversight there.

---

### Post by lvleph on 2008-01-07
Delete

---

