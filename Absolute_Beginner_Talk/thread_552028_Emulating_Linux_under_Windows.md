---
title: "Emulating Linux under Windows"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-09-15
I want to emulate Ubuntu or a Debian based OS with at best, a light GUI. I would prefer a light GUI like fluxbox or something rather than just a command-line.

PS: Does anyone know if Ubuntu has good hardware support for my new laptop? It's in my sig.


EDIT: I would prefer if I didn't have to rely on a virtual OS program, something. I used some thing called QEMU with a USB based distro.

---

### Post by Hospadar on 2007-09-16
Well really the only way to emulate would be to run a virtual copy of linux.  There really isn't anything like WINE for windows to run linux applications.  That said:
A) I gather that virtualization like that isn't all that hard to set up, I belive a lot of people do it.  Look into vmware or xen
B) I would assume you don't want to dual boot, but it's always an option.
C) If you have another machine, you could always consider running linux/ubuntu on that and connect to it with ssh from windows with a windows xserver like xming.  This is also not very difficult to set up, and will let you use the gui apps on the linux machine.

---

### Post by kavon89 on 2007-09-16
> **Hospadar said:**
> Well really the only way to emulate would be to run a virtual copy of linux.  There really isn't anything like WINE for windows to run linux applications.  That said:
A) I gather that virtualization like that isn't all that hard to set up, I belive a lot of people do it.  Look into vmware or xen
B) I would assume you don't want to dual boot, but it's always an option.
C) If you have another machine, you could always consider running linux/ubuntu on that and connect to it with ssh from windows with a windows xserver like xming.  This is also not very difficult to set up, and will let you use the gui apps on the linux machine.

I know it is sort of easy to do it with VMware, but I would prefer if it ran like a windows application. I once had it like that on a USB and I brought it to school and loaded it up. It did admirably on those old Pentium 4s with not too much ram.

---

### Post by alienexplorers on 2007-09-16
Why don't you just dual boot and have the best of both worlds.

---

### Post by misfitpierce on 2007-09-16
or just switch to linux and get the best of 2 worlds within 1 plus no windows :)

---

### Post by Paul133 on 2007-09-16
So you want to put the LiveCD in a USB drive? Or do you want to install Linux to your HD but make it acessible within Windows. FOr the former, I believe it's possible, but I'm not sure how to do it. For the latter, use wubi ([http://wubi-installer.org/](http://wubi-installer.org/))

---

### Post by newman on 2007-09-16
> **misfitpierce said:**
> or just switch to linux and get the best of 2 worlds within 1 plus no windows :)

Perhaps he wants to keep Windows installed so that he can play and copy DVD's, play games, have a working wireless connection, decent 3D video, etc.
I guess some people's idea of "worlds" is different...

---

### Post by Sayers on 2007-09-16
Linux runs great on thinkpads.

---

### Post by sumguy231 on 2007-09-16
> play and copy DVD's, play games, have a working wireless connection, decent 3D video, etc.
I can do all of those things except for playing Windows games. Your experience has a lot to do with what hardware you have and how much nonfree stuff you're willing to use. Not that I wouldn't still recommend a dual boot.

---

### Post by asmoore82 on 2007-09-16
> **sumguy231 said:**
> I can do all of those things except for playing Windows games. Your experience has a lot to do with what hardware you have and how much nonfree stuff you're willing to use. Not that I wouldn't still recommend a dual boot.

[SIZE="6"]++[/SIZE]

I can do all that AND PLAY GAMES.

---

### Post by AnRa on 2007-09-16
Take a look at [Cygwin](http://www.cygwin.com/) and [BB4Win](http://www.bb4win.org/). ;)

---

### Post by gn2 on 2007-09-16
[http://www.tuxs.org/dslwin.htm](http://www.tuxs.org/dslwin.htm)

---

### Post by kavon89 on 2007-09-16
I want to keep Windows because I have applications which rely on it and will not work in Linux. I might have consider a dual boot,  but we'll see how it goes.

Question #1: If I run DSL in windows, is DSL it's entirely own system, and if I connect places will only Linux be known to people on the internet when I do things inside DSL on Windows? I have reasons for this which I won't explain at the moment. ;)

I'll download Damn Small Linux and try it out, I hope it is Debian based.

---

### Post by nonewmsgs on 2007-09-16
> **kavon89 said:**
> I want to keep Windows because I have applications which rely on it and will not work in Linux. I might have consider a dual boot,  but we'll see how it goes.

Question #1: If I run DSL in windows, is DSL it's entirely own system, and if I connect places will only Linux be known to people on the internet when I do things inside DSL on Windows? I have reasons for this which I won't explain at the moment. ;)

I'll download Damn Small Linux and try it out, I hope it is Debian based.

your question is a little confusing, but yes, any data your browser/computer gives off says linux. 

from wikipedia
DSL has built in scripts for the download and installation of Debian's Advanced Packaging Tool (APT), and Synaptic, a GUI front-end to APT. Once the repositories are enabled, (as of 3.0.1) it draws from the rather old Debian Woody repository.

---

### Post by kavon89 on 2007-09-16
I just like downloading a .deb file and installing it. I think I use alien on the .rpms right?

---

### Post by brennydoogles on 2007-09-16
> **newman said:**
> Perhaps he wants to keep Windows installed so that he can play and copy DVD's, play games, have a working wireless connection, decent 3D video, etc.
I guess some people's idea of "worlds" is different...

Wow... That's all the stuff I do on Ubuntu for free, rather than paying to do it on windows. What a coincidence!!

---

