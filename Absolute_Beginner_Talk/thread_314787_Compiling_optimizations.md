---
title: "Compiling optimizations"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by linga on 2006-12-08
I am new to linux and I since my computer is really slow(400Mhz,192Mb) I want to compile programs myself to get them optimized.

I have done some reading and I want to use .O2 and -march when I compile.

Is there a way to make these settings included automatically? I've read about make.conf, but I cant find it on my system.

Also, which directories should I use?

Finally, is it a waste of time to compile the libraries needed to? If so would it be a good idea to use auto-apt to get these libraries?
[https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

---

### Post by mcduck on 2006-12-08
I believe that all ubuntu packages already have those optimizations.

---

### Post by Perfect Storm on 2006-12-08
Aye, and many of applications you compile are running a script which automatically set the right things to optimize nowadays. The thing you get more likely is smaller package when you compile stuff, but again you need to download the right headers and dev packages.

---

### Post by elettronicha on 2006-12-08
> **linga said:**
> I am new to linux and since my computer is really slow(400Mhz,192Mb) I want to compile programs myself to get them optimized.


I think the best, simplest and fastest way to make a distribution lighter is turning off the unneeded running services, recompiling the kernel and using a lighter desktop environment (such as xfce). Often with hard system optimization you don't get that much advantages in speed and lightness. Generally speaking, if you want, you can first recompile the whole tool chain (glibc, the compiler and some other thing), the kernel, the X server, the desktop env and that's it. By recompiling that stuff you'll get the most of the speed improvements, recompiling more packages is excessive in my opinion.
Also keep in mind that if you want to fully optimize your system and recompile all the packages, you may need some distro such as Gentoo which was born to do that.

---

### Post by linga on 2006-12-08
Thanks a lot! That was very useful. You got me thinking about using gentoo instead, that might be a better choise considering what I am trying to do here.

---

### Post by po0f on 2006-12-08
linga,

Note that it is going to take a *while* to get a GUI up and running using Gentoo with specs like that.  If you think Ubuntu is too heavy for you, there are lighter distros out there without going to the excess of Gentoo.  (Just trying to save you a little frsutration!)  :)

---

