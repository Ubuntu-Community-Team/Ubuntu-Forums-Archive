---
title: "Opening UIF files"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-09-28
I have a UIF file I need unzipped. How do i do this because i believe there is only application that can?

---

### Post by Majorix on 2007-09-28
I believe you will have to use MagicISO under WINE as there are no tools under Linux that can do UIF files.

---

### Post by intense.ego on 2007-09-28
damn, that is what i thought. thanks.

---

### Post by kokiperex on 2008-06-02
Yo can use UIF2ISO:

[http://freshmeat.net/projects/uif2iso/](http://freshmeat.net/projects/uif2iso/)

It's very simple.

First, download the zip. Then, install the required libs:

```
sudo apt-get install zlib1g zlib1g-dev libssl-dev
```

Unconpress the zip, go to .../uif2iso/src and open a console. Then:

```
sudo make
```
```
sudo make install
```

To convert an UIF to an ISO:

uif2iso filename.uif filename.iso

---

### Post by iraiscoming223 on 2008-06-13
thx! :D
Why did you use "sudo make" instead of just "make"? o.O
I guess it was just a mis-type...  :)

For every newbie reading this just use "make" instead of the "sudo make" command above.

Anyway, it's working fine here! Thanks again! :D

---

### Post by ene_dene on 2008-06-13
I use uif2iso.exe under wine, It works perfectly:
```
wine uif2iso.exe input.UIF output.ISO
```

---

