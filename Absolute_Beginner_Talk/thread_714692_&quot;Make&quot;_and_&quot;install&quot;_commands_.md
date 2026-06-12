---
title: "&quot;Make&quot; and &quot;install&quot; commands problem"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by aborigine on 2008-03-04
I must be a little stupid...
I've downloade some software in "tarball" format ./configure works fine - lots of lovely text on the screen!
When I go to "make" I gat command invalid - is there a package I am missing in the installation and if so _which one ??_

---

### Post by kpkeerthi on 2008-03-04
You need **build-essential** package.

```
sudo aptitude install build-essential
```

---

### Post by aborigine on 2008-03-04
Will try that, thanks

---

### Post by aborigine on 2008-03-11
what I found was that according to synaptic, the package was already installed... whats happening and how do I correct it (ie how to make the system recognize the packages that ARE there).

---

### Post by mrfraser89 on 2008-03-11
I'm assuming you're not running the make install command from the directory of the tarball?

You can extract the file, then navigate to the folder in terminal (if you don't know how to do this, just ask :)) then run sudo make install.

---

### Post by aborigine on 2008-03-11
I was in the directory and had just run ./configure, which normally is followed by make and install, but I got the massage "no such command", or something to that effect.

---

### Post by mrfraser89 on 2008-03-11
That's pretty odd then, however, can you make install with other tarballs?

---

### Post by hyper_ch on 2008-03-11
if the programs are there, you may need to also install their -dev versions... make should tell you where it fails.

---

### Post by mister_pink on 2008-03-11
Does the make one work? Because its "make" then "make install" not just "install". Have you tried checkinstall too? Its a useful program that makes it easier to remove packages installed in this way. Install it from add remove programs, then instead of "sudo make install" you can do "sudo checkinstall". It will make a deb package, so that it comes up in your Add/Remove programs and synaptic. 
If make fails then you're probably missing dependancies. What package are you trying to use?

---

### Post by hyper_ch on 2008-03-11
first he needs to compile the sources by issuing make... only after that make install or checkinstall can be issued.

---

### Post by mister_pink on 2008-03-11
I know, just trying to work out at which stage he got the error. I suspect make has run (although not necessarily successfully) and he's then trying to do "install", which will obviously give a no such command error.

---

### Post by hyper_ch on 2008-03-11
> **mister_pink said:**
> I know, just trying to work out at which stage he got the error. I suspect make has run (although not necessarily successfully) and he's then trying to do "install", which will obviously give a no such command error.

> When I go to "make" I gat command invalid

make did not run (properly)

---

### Post by mister_pink on 2008-03-11
Whoops, fair enough. I read a later post immediately before replying which wasn't so clear!

---

