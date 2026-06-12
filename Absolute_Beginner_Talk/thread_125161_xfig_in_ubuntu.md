---
title: "xfig in ubuntu"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-02-03
Hello, I'm currently working with a program called [xfig]("http://www.xfig.org") under linux fedora, with which it is possible to draw mathematical graphs and so on, and now installed ubuntu, and want to know, whether it is possible to use the program also under this system. How is it possible to use xfig under ubuntu?

thanks, niko

---

### Post by rmjokers on 2006-02-03
Try installing it like so:

sudo apt-get update
sudo apt-get install xfig

---

### Post by gagatz on 2006-02-20
This way brings the following output, from which i resume that it hasn't been installed properly:

niko@ubuntu:~$ sudo apt-get update
Reading package lists... Done
niko@ubuntu:~$ sudo apt-get install xfig
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xfig
niko@ubuntu:~$

What does this mean?

---

### Post by bjweeks on 2006-02-20
[QUOTE=gagatz]This way brings the following output, from which i resume that it hasn't been installed properly:

niko@ubuntu:~$ sudo apt-get update
Reading package lists... Done
niko@ubuntu:~$ sudo apt-get install xfig
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xfig[/B]
niko@ubuntu:~$

What does this mean?[/QUOTE]

That there is no package called xfig in the repo.

---

### Post by bjweeks on 2006-02-20
xfig is in universe so you need to enable it.

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

Then try again.

---

### Post by nickle on 2006-02-20
For making high quality scientific graphs, I might also recommend the programme R; it is available in the repository. It is actually an incredibly powerful stat/math package, but is also a serious professional tool for graphical exploration and depiction of data. It produces graphics that can be used directly in scientific publications. It has quite a steep learning curve, but also has extensive documentation and a support forum.
If you need to do graphical representation/exploration R regularly, consider investing some effort in R. You will not regret it....

---

### Post by gagatz on 2006-02-20
Where can I find this R?

---

### Post by natman on 2006-02-20
Hi, I am a PhD sudent in maths and use Xfig all the time for graphs, I use Brezzy 5.10 and 
> sudo apt-get install xfig
worked fine for me( just tried it ) so it is definitly in the repos. R is ok but xfig is the best especially if you need to put it into a latex document which is a nightmare under windows.

---

### Post by nickle on 2006-02-20
[QUOTE=gagatz]Where can I find this R?[/QUOTE]

Search for r-base in synaptic (it is in the mathematics section). There are also several sub-packages available...

I also had no problem installing xfig...

I would like to add, I must have been daydreaming today. R does not do the same thing as xfig (Somehow I mixed it up in my head with gnuplot,, sry). However, everything else I said about it is true. However, it is not primarily intended to draw diagrams, but depict and explore data. Sorry if I have caused any confusion....

---

