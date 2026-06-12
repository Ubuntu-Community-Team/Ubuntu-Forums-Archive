---
title: "Compiling"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by simukas on 2006-08-16
i don't much about libratys and compilingand this just doesn't make sence to me.

---

### Post by LadyDoor on 2006-08-18
I don't know what you're trying to do, but generally if you're compiling something from source and it says you haven't installed something that you *know* you have installed, it's because you don't have the development files for it. So try to find a file in synaptic that's something along the lines of **libwhatever-dev** or **whatever-dev**.

I hope that helps!

--Door

---

### Post by oxEz on 2006-08-18
This is a problem with binairy distributions, like Ubuntu. What you need is to install something like sdl-dev, or libsdl-dev, etc.. For example, if you want to compile a GTK application, you'll have to install the development files for it: libgtk-dev. 

Good luck!

---

### Post by simukas on 2006-08-18
yeah .. tried to do that... but the freaking deb files nedds other deb file witch needs the deb deb file mentioned before ](*,) ](*,) ](*,) ](*,) ](*,) ]

---

### Post by taurus on 2006-08-18
Use synaptic to install those dev libs!!!

---

### Post by simukas on 2006-08-18
how.. i use the automatic intall (you know that debian package something). so when i get all the library's and the things they need i do what?

---

### Post by LadyDoor on 2006-08-18
Once you install the libraries it said it needed, do **./configure** again. If it works, go on to **make** and then **sudo make install**.

If it doesn't work, look to see what it thinks isn't there *this* time, and then install the development files for *that* program from synaptic. Lather, rinse, repeat.

--Door

---

### Post by simukas on 2006-08-18
yeah.. but how to use Sinaptec to install the packages coz when i use the debian package manager i get the freaking dependeces problems

---

### Post by LadyDoor on 2006-08-18
I don't know what "Debian package manager" you're talking about. Aptitude? If it wants to install dependencies, let it install them! Dependencies never hurt anyone. If it "breaks" packages, see what's broken by pressing "b," and then decide if it's something you can uninstall.

And to use synaptic (I see you're using GNOME) press <alt>F2 and enter **gksudo synaptic**. Easy as pie.

--Door

---

### Post by simukas on 2006-08-18
about the debian package i'm just running the debian packages and that's all. ok i'll try..

---

### Post by harisund on 2006-08-19
Also, I don't know how helpful it would be for you, but a useful tip. 

When you are building certain applications, they might look for libraries in particular, specific locations. Unfortunately, these might be Red Hat specific. 

Typical example, when you are compiling a kernel, you need the Qt development libraries installed. However, even after installing the required libraries, the kernel's "make xconfig" will refuse to work. 

If you will look at [https://launchpad.net/distros/ubuntu/+source/qt-x11-free/+bug/16864](https://launchpad.net/distros/ubuntu/+source/qt-x11-free/+bug/16864), you will realise it looks elsewhere, and therefore a simple symlink does the job.

---

