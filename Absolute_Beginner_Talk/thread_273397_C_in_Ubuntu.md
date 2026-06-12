---
title: "C in Ubuntu"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-10-08
hey, i was wondering what is the equivalent of the GCC compiler(in fedora) in Ubuntu so that i can compile code in C. 10x

---

### Post by Marsolin on 2006-10-08
Ubuntu also uses [gcc]("http://linuxappfinder.com/package/gcc").

---

### Post by Mazen on 2006-10-08
how come the gcc comand is not available in the terminal!?

---

### Post by whiterabbit on 2006-10-08
You may have to install it.  Just apt-cache search gcc and it'll be in there somewhere.

---

### Post by Mazen on 2006-10-08
i found this so now how can i install it!...i know it's kind of a stupid question!lol

gcc-4.0 - The GNU C compiler

---

### Post by Mazen on 2006-10-08
ok i guess it's with the sudo command! lol..cool im getting the hang of this...thanks guys

---

### Post by whiterabbit on 2006-10-08
Yep, just...

sudo apt-get install gcc 

or 

sudo apt-get install gcc-4.0

---

### Post by po0f on 2006-10-08
Mazen,

You will most likely want gcc, as well as the glibc headers, make, and some other things (not all clear as to what's included with it).  If so, install **build-essential**:
```
$ sudo apt-get install build-essential
```

This way, when programming, you only have to install the relevant headers for whatever library your program is using, ie libgtk2.0-dev, for the headers (in this case, gtk+-2.0).

---

### Post by Mazen on 2006-10-08
thanks guys....but one more question..how do i install .tar.gz files in general....cuz i downloaded this vlc player and it won't install again!...is every file different form the other!?! i mean every .tar file has its own installation way !?

---

### Post by shanmuga on 2006-10-08
You have to unzip it and use the following commands in terminal:
./configure
make
make install

---

### Post by Marsolin on 2006-10-08
> **Mazen said:**
> thanks guys....but one more question..how do i install .tar.gz files in general....cuz i downloaded this vlc player and it won't install again!...is every file different form the other!?! i mean every .tar file has its own installation way !?

[VLC]("http://linuxappfinder.com/package/vlc") is in the Ubuntu repositories. You don't need to install from the tar.gz file.

---

