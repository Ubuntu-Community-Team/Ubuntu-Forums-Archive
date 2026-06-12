---
title: "Complile Problem"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by the gnome on 2006-12-01
I'm getting the following error when attempting a compile:

```
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

I checked config.log, but it was so huge, and I have no idea what I'm looking for so I didn't see anything too meaningful.  

I'm hoping I'm just missing a library.

---

### Post by ewl1217 on 2006-12-01
Did you install the build-essential package? If not, then use
```
sudo apt-get install build-essential
```

---

### Post by po0f on 2006-12-01
the gnome,

As posted above, you are most certainly going to need [build-essential](http://packages.ubuntu.com/edgy/devel/build-essential).  Depending on what it is you are compiling, you will also need *-dev packages of whatever libraries the program you are compiling use.

---

### Post by Sef on 2006-12-01
Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

### Post by the gnome on 2006-12-01
That would be it, thank you sir!

---

