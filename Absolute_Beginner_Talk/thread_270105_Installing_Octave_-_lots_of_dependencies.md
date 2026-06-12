---
title: "Installing Octave - lots of dependencies"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Joe72 on 2006-10-02
Hi NG,

I would like to install Octave 2.1, but when I look at the dependencies on [http://debian.org](http://debian.org) it has a lot. Some of the dependant packages even have dependencies themselves.

Is there any way to auto-install a program an all the known dependant packages in one go?

Thanks!

Best,

Joe

---

### Post by ButteBlues on 2006-10-02
If that package is in the repositories, you can use the following command to install it:

> 
sudo aptitude install {packagename}

If Octave 2.1 is in the repos, then aptitude should drag in all of its dependencies when it is going to be installed.

---

