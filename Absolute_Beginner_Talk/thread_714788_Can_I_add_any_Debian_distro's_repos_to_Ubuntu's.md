---
title: "Can I add any Debian distro's repos to Ubuntu's?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2008-03-04
I was thinking about experimenting with using Debian repos instead of most of Ubuntu's.

It should work alright, right? If Ubuntu uses the same packages, I'd think it would be okay.

I'm experimenting with this because I heard that Debian packages are more vanilla than Ubuntu's and I want to see if I can notice a performance(or aesthetic) difference in Gnome and XFCE if I reinstall them from the debian repos. Plus I just like to poke stuff until it breaks...

---

### Post by kerry_s on 2008-03-04
> It should work alright, right?

go for it, back up your stuff and prepare to reinstall. ubuntu and debian are very different in the way they were built. ubuntu is based on debian, yes, but they are barely even compatible anymore.

here's my repo's for your little project.
```
deb http://ftp.us.debian.org/debian/ etch main contrib non-free
deb http://ftp.us.debian.org/debian/ lenny main contrib non-free

deb http://security.debian.org/ etch/updates main contrib non-free
deb http://security.debian.org/ lenny/updates main contrib non-free
```

---

### Post by sayakb on 2008-03-04
@OP
I had a broken cache thrice since I has the debian packages in my repos... Maybe I shouldn't have always gone for Etch packages..

---

### Post by AndyCooll on 2008-03-04
Well you can try it as an "experiment", however it isn't normally recommended.

Ubuntu takes a snapshot of Debian unstable every six months and then spends time modifying the packages to bring about stability and ensure everything works together (including dependencies). So, in many ways Debian and Ubuntu packages are NOT necessarily the same, and you are increasing the possibility that some apps may not work properly.

:cool:

---

### Post by SunnyRabbiera on 2008-03-04
it would be safer if you just used selected packages from debian rather then add a repo for it.
there are a few packages you can get from the debian repos that wont screw with your system but some of them can frack you up

---

### Post by sayakb on 2008-03-04
Personally, I wouldn't even install each package separately.. Most of the packages depend of libc6 and if that debian package isn't somehow "compatible" with the installed dependencies, you could end up with a broken libc6, that would not allow you to install any package furthur. When tried to fix the broken cache, it would remove almost all your necessary packages including ubuntu-desktop, ubuntu-panel, etc. So you might lose your system.. If there might be a way to recover from a broken libc6, then you may experiment..

---

