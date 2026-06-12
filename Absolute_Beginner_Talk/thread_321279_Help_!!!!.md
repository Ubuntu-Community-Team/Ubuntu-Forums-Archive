---
title: "Help !!!!"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by rasputin1575 on 2006-12-18
Hello. FIrst of all, i'm new to linux. I got hold of Ubuntu and the installation process went fine. I need to tell you that the laptop am using it on has no internet connection, hence cant run any automatic updates.
Now all i need to do on my Ubuntu is run few softwares (maths based) like tetex, xfig, gnuplot, etc.. and of course a few more which might come handy.
the problem is that am big time stuck.
i've been browsing on how to install files (i downloaded the sources) and nothing works.
for example:-

./configure gives me an error

"make" is absolute greek to it.

pls help.

email me on [email]bkahoolash@hotmail.com[/email] PLS PLS PLS !!!

---

### Post by d3v1ant_0n3 on 2006-12-18
If you're completely new to Linux, then building from source might be a bit of a giant step to be starting with...

I would recommend trying to find the .deb packages for the programs you need- you can install them simply with gDebi installer (although you might run into dependency problems with not having internet).

---

### Post by rasputin1575 on 2006-12-18
thx, i'll try the deb file.

---

### Post by lamego on 2006-12-18
Have you tried the Add/Remove programs menu ?
Most of the software you have mentioned is available to be installed from the repositories, there is no need to compile it from source...

---

### Post by d3v1ant_0n3 on 2006-12-18
The OP said that comp didn't have an internet connection, hence my suggestion of debs rather than add/remove (which would be ideal).

---

### Post by rasputin1575 on 2006-12-18
yup, as i dont have internet connection on the laptop am using for ubuntu , i'll do with deb file. 
i did get holdof the deb file but am stuck again (sorry guys, just bear with this novice:) ).
it says something like libss10.9.7 is not installed.... i did lookup in the synaptic and i have the 10.9.8 instead.
any suggestions?

---

### Post by Sef on 2006-12-18
> ./configure gives me an error


To compile, build essential needs to be installed.

```
sudo aptitude update
```

```
sudo aptitude install build-essential
```

Since you don't have an internet connection, you can't download that.

You could try [packages.ubuntu.com]("http://packages.ubuntu.com"), all the packages for ubuntu are located there from a computer that you can use to access the internet.  Download and burn the packages to a cd rom then install on your laptop.

---

