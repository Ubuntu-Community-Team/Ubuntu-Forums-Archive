---
title: "Dependency loop"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by tridings on 2006-07-30
Hello

I have hit a vicious circle while installing dependencies ...three files that each reference the other as a dependency not being satisfiable!

A note of explanation I am new to Ubuntu and at this time haven't been able to get my modem up and running (a winsoft item) and so have been downloading on a Windows machine and copying to a CD ....

	...in the process I have the following:

- libgnome32  (asking for)  gnome-libs-data
- gnome-libs-data  (asking for)  gnome-bin
- gnome-bin  (asking for)  libgnome32

How to I break the cycle - I am trying to install Tomboy

My machine is an amd64 running Dapper and loading 64 bit files.

With thanks,  Terry

---

### Post by Indras on 2006-07-30
With things like this, you need to install them all at the same time.  I don't know how to do this from Nautilus, but from my Red Hat days, I would imagine you can do this easily from command line:
```
dpkg -i <package1.deb> <package2.deb> <package3.deb>
```

Once you get your modem working and online, I suggest you use Synaptic, since it will resolve these dependencies automatically.

---

