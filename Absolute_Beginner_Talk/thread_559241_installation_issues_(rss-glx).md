---
title: "installation issues (rss-glx)"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by cailamaia on 2007-09-24
Hello all,

Here's to hoping someone out there can help me. I'm just starting out with a brand new install of feisty (dualbooting with WinXP, if that matters) and I'm having some trouble getting things to install properly. I have already double-checked and tried to troubleshoot this as best I can.

This is what the terminal spits out at me when I try to install anything. I'm going to use the screensaver package I found [here]("http://www.reallyslick.com/downloads.html") as a reference point.

[I]cailamaia@cailamaia-laptop:~$ cd /home/cailamaia/Desktop/rss-glx_0.8.1
cailamaia@cailamaia-laptop:~/Desktop/rss-glx_0.8.1$ ./configurechecking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
configure: error: cannot run /bin/bash ./config.sub[/I]

And then it opens up a new prompt.

What do I do?

---

### Post by mesilliac on 2007-09-25
rss-glx is available in the Ubuntu repositories. To install it you can just use synaptic package manager, which you will find under System > Administration in the main GNOME menu. It's always a good idea to check if a package is available through Synaptic before trying to install it manually.

Still, if you need to build a package from source code you first need to install all of its build dependecies. It can be quite complicated, but usually you get a more helpful error message. I'm pretty sure this particular one about config.sub could be fixed by installing "libtool"
```
sudo apt-get install libtool
```

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) might help if you have any more problems compiling.

---

### Post by cailamaia on 2007-09-25
I see. Thanks for the heads up. I'll just go try that, and see how it works.

... 5 minutes later ...

Well, that helped. It's gotten stuck a bit farther on in the process, though. For that, now that you've been kind enough to point out what should have been obvious, is search for it first.

Thanks.

---

