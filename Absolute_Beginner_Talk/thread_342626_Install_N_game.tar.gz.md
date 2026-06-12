---
title: "Install N game.tar.gz"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Duppy on 2007-01-20
I downloaded n game from here:

[http://www.harveycartel.org/metanet/downloads.html](http://www.harveycartel.org/metanet/downloads.html)

The linux version.

And it is called "n_v1linux.tar.gz"

When i extract it there is one blue file inside and the rest are text files.

When i double click the blue file, nothing happens:( how can I install the game?

---

### Post by taurus on 2007-01-20
Open a terminal and change to wherever you unpacked it.  Then, paste the output of this command here.

```
ls -la
```

---

### Post by Duppy on 2007-01-20
**Unpacked it on desktop, so:**
total 1436
drwxr-xr-x  4 kieran kieran    4096 2007-01-20 20:31 .
drwxr-xr-x 38 kieran kieran    4096 2007-01-20 20:31 ..
-rw-r--r--  1 kieran kieran    2424 2007-01-02 18:48 firefox.desktop
-rw-r--r--  1 kieran kieran    4803 2007-01-19 15:55 gaim.desktop
drwxr-xr-x 10 kieran kieran    4096 2007-01-19 23:32 HumanAzul2
-rw-r--r--  1 kieran kieran    2757 2006-10-20 11:42 nautilus-home.desktop
drwxr-xr-x  2 kieran kieran    4096 2005-05-15 18:25 n_v1linux
-rw-r--r--  1 kieran kieran 1430315 2007-01-20 16:12 n_v1linux.tar.gz



**If you meant do it in the actual folder then:**
total 3700
drwxr-xr-x 2 kieran kieran    4096 2005-05-15 18:25 .
drwxr-xr-x 4 kieran kieran    4096 2007-01-20 20:31 ..
-rw-r--r-- 1 kieran kieran   82944 2005-05-16 01:53 editor_manual.doc
-rw-r--r-- 1 kieran kieran   20665 2005-05-16 01:54 editor_manual.txt
-rw-r--r-- 1 kieran kieran    1926 2005-05-02 19:12 license.txt
-rw-r--r-- 1 kieran kieran    2556 2005-05-15 04:22 n_cheats.txt
-rwxr-xr-x 1 kieran kieran 3213436 2005-05-15 18:25 n_v14
-rw-r--r-- 1 kieran kieran   11449 2005-05-16 05:09 readme.txt
-rw-r--r-- 1 kieran kieran  421047 2005-05-16 05:03 userlevels.txt

---

### Post by taurus on 2007-01-20
Change to that directory and run it with

```
./n_v14
```

---

### Post by Duppy on 2007-01-20
kieran@kieran-desktop:~/Desktop/n_v1linux$ ./n_v14
./n_v14: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by lamego on 2007-01-20
You will need to install libgtk1.2 for that game:
```
sudo apt-get install libgtk1.2
```

---

### Post by Duppy on 2007-01-20
Ok done, now what?

---

### Post by Bachstelze on 2007-01-20
Try to run your game again. If it complains about other missing libs, install them too.

---

### Post by Duppy on 2007-01-20
I dont know what to install.

> kieran@kieran-desktop:~/Desktop/n_v1linux$ ./n_v14
./n_v14: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

---

### Post by Duppy on 2007-01-20
What thing do i need to install now?

---

### Post by Perfect Storm on 2007-01-20
```
sudo aptitude install libstdc++6
```

You might read thte readme.txt to see what's required.

---

### Post by Duppy on 2007-01-20
Done what you said in terminal, nothing installs, it says 0 package was installed.

Readme file says do this:

> start N in console like this:



nice -n 20 ./n_v14

Is console = terminal?

I try it in terminal and doesnt work. Can you tell me exactly what to write into terminal please?

> kieran@kieran-desktop:~/Desktop/n_v1linux$ nice -n 20 ./n_v14
./n_v14: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

---

### Post by jack_teagarden on 2007-12-08
This did the trick for me

install package libstdc++2.10-glibc2.2

```
 sudo aptitude install libstdc++2.10-glibc2.2
```

---

### Post by jlapaglia on 2008-03-07
I'm having the same problem, i installed the libgtk1.2 and then i installed the  libstdc++2.10-glibc2.2 but i still get this

Desktop/n_v1linux/./n_v14: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


 when i try to run the program through this command


Desktop/n_v1linux/./n_v14

---

