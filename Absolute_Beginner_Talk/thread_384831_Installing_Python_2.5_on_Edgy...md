---
title: "Installing Python 2.5 on Edgy.."
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by rabbitsushi on 2007-03-14
Hi everyone,

I'm a bit of a noob when it comes to Ubuntu..

Anyway, I wanted to install Python 2.5 on my Edgy install because that's what I use at work. so I thought I'd go into Synaptic and get it from there. I selected the package and it got installed etc. Then I tried running it from the command line but 2.4.4 started up, so I thought I'd go and remove 2.4. I didn't realise that gnome depended on 2.4.4 and there was a whole bunch of packages that also got removed.. I'm not sure how correct what I've just said is, so corrections are very welcome.

Anyway, I noticed that a whole bunch of stuff was missing from the desktop menus and wasn't sure how to repair it... So I re-installed Ubuntu. How could I have fixed this?

Basically I'd just like some explanation of how things work and how Gnome and Python are dependent on each other etc. I'm just wanting to learn :)

Thanks!

---

### Post by seshomaru samma on 2007-03-15
I know nothing about python
But if you uninstalled some gnome packages you can just open a terminal and reinstall gnome
```
sudo aptitude install gnome-desktop 
```

---

### Post by m3mitsuppe on 2007-03-17
Hi,

I also wanted to run python2.5 instead of the default 2.4, so I installed 2.5 using synaptic. 

After some searching I realized that in /usr/bin there is a symbolic link named "python" that points to "/usr/bin/python2.4". Of course next to it is also the executable "python2.5". So you can use 2.5 by typing "python2.5 myscript.py"

BUT there are a lot of open questions for me. For instance, I want to use wxpython. I installed it, but it was installed within the site-packages directory of python2.4, and it also seems to be a version that is specifically tailored to be used with this python version. When I tried to run wx from python2.5 (after tweaking some symbolic links in site-packages), I cound successfully import wx, but only with a number of warnings about non-matching api versions. 

So if anyone has a clue how I can install the wxpython for python2.5 at the right place, I'd be very happy to learn about it.

Cheers,
m3mitsuppe

---

