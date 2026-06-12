---
title: "Package dependency issues"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by fractilian on 2007-03-24
Ok I am trying to install a program from a package.  When I try to install it it cant because of dependency issues.  In the past the Package manager has just made a list of all dependencies and took care of the installation of those too.  What am I missing?  Or am I going to have to make a chart of the programs dependencies and the dependencies dependencies and the dependencies dependencies dependencies...  I am running a fresh installation of Ubuntu 6.10-d.  Thanks

---

### Post by 23meg on 2007-03-24
What exactly are you trying to install?

If it's in the repositories, you should use apt-get, Aptitude or Synaptic to install it, rather than by downloading the package manually. They'll take care of the dependencies for you.

Check these out for the basics of installing software:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Wally68 on 2007-03-24
> Ok I am trying to install a program from a package

A little more information would be helpful. Sounds like you just need to enable the "multiverse", "universe" and "restricted" repositories in synaptic. What is the full name and version of the package you are trying to install?

Tom

---

### Post by fractilian on 2007-03-24
Many thanks Wally68.  After enabling  multiverse and universe the packages I was looking for showed up.  I guess I am a linux renewbe.  Its been a while since I fooled around with linux.  Decided to jump back in man have things changed.  Thanks too everyone else as well.

---

### Post by ubromtoo on 2007-03-24
Please tell this newbie how to "enable multiverse and universe"

Am running 6.06  Dapper Drake.  Thanks      :)

---

### Post by 23meg on 2007-03-24
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html)

---

