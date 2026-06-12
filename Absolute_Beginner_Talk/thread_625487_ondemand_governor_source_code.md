---
title: "ondemand governor source code"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by osaka_dude on 2007-11-28
hello,I m all new to linux and started with ubuntu.I m thinking of doing some cpu power mangement work for my Freshman year project.So far i could enable cpufreq in Ubuntu and run CPU at different frequencies.I find the Ondemand and Conservative governors very interesting.I m thinking of doing some modifications to the source codes,but have no idea how to proceed.
1.how can i access the source codes of these governors?
2.is it possible to edit these source codes some way,may be if i want to try  with different  algorithms etc..?
I apologize if my questions are too simple(being a lifelong windows user just starting to realize the powers of Linux)
any adiitional tips  are  also appreciated.
regards
Harry
PC;Celeron D 3.06GHz,1Gb RAM,Ubuntu 7.10 Gutsy

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-28
Hi, welcome to Linux!

[LIST=1]
[*]You can get the source code, by typing this on terminal (Applications -> Accessoris -> Terminal):
```

apt-get source <package-name>

```
I believe cpu frequency is controlled by cpufreqd daemon, so type this:
```

apt-get source cpufreqd

```
You can then see the source codes in the cpufreqd-2.2.1 directory.
[*]That's highly possible (as long as you understand the code).
[/LIST]

I think your question is not that simple :)
Modifying the source code and installing to your system is not trivial.

Good luck!

---

### Post by Whiffle on 2007-11-28
The actual source code for the governor modules is part of the kernel.  If you have the "build-essential" and "linux-source" packages installed, you should have everything you need.  It will put a file along the lines of "linux-source-2.6.22.tar.bz2
" in your /usr/src directory, which you can unpack with "tar jxvf linux-source-2.6.22.tar.bz2."  Once you've modified them, you'll have to recompile and reinstall your kernel for it to take  effect.  There are several howtos on this.

The actual source code for the drivers should be in 
/usr/src/linux-source-2.6.22/drivers/cpufreq/cpufreq_ondemand.c

Be careful!

---

### Post by jordanmthomas on 2007-11-28
This file doesn't exist on my system (it's Arch, not Ubuntu)
This is the only file I have with any actual code in it:
```
/usr/src/linux-2.6.23-ARCH/include/linux/cpufreq.h
```
(obviously, your directory will be a little different)


EDIT
nevermind, I don't have the sources installed, just the headers.  sorry.

---

### Post by osaka_dude on 2007-11-30
hi thanx for all  the support,Whifle's method worked and now i've done  some source code modifications for ondemand.c;
how can i reinstall/recompile so that d changes take effect? i ve managed to get the kernel configuration screen using "menu xconfig",and"make-kpkg" etc,but have no idea how to proceed.
regards
harry

---

### Post by osaka_dude on 2007-11-30
and do i need to recompile the whole kernel every time ,instead of only the files i edited?
cheers

---

