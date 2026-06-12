---
title: "Help with terminal install"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-06-11
I'm trying to install software called pspvc (it's a video converter for the psp) but when I run the sh file I get the a bounch of coding then this error 
```
gcc -o x264 x264.o matroska.o muxers.o libx264.a -lm -lpthread -s
install -d /usr/local//share/pspvc/bin /usr/local//share/pspvc/include
install: cannot create directory `/usr/local//share/pspvc': Permission denied
install: cannot create directory `/usr/local//share/pspvc': Permission denied
make: *** [install] Error 1
-e \E[01;31mERROR during compilation or installation of X264

```
So what I did was went and put in ```
sudo chmod 777
```
for both of thoughs directorys but I'm still getting same error.
Please Help

---

### Post by ajmorris on 2007-06-11
> **microsoft92sucks said:**
> I'm trying to install software called pspvc (it's a video converter for the psp) but when I run the sh file I get the a bounch of coding then this error 
```
gcc -o x264 x264.o matroska.o muxers.o libx264.a -lm -lpthread -s
install -d /usr/local//share/pspvc/bin /usr/local//share/pspvc/include
install: cannot create directory `/usr/local//share/pspvc': Permission denied
install: cannot create directory `/usr/local//share/pspvc': Permission denied
make: *** [install] Error 1
-e \E[01;31mERROR during compilation or installation of X264

```
So what I did was went and put in ```
sudo chmod 777
```
for both of thoughs directorys but I'm still getting same error.
Please Help

Did you run the script as root?

---

### Post by microsoft92sucks on 2007-06-11
You'd think that would be the first thing I'd try but It wasn't.. That was really dumb of me but thanks for the help.

---

### Post by microsoft92sucks on 2007-06-11
Now It's installed but when I click on it nothing happens and when I tape it in it say command not found.

---

### Post by microsoft92sucks on 2007-06-11
why ant it working please help

---

### Post by microsoft92sucks on 2007-06-11
It says it can't find the pspvc executable. How can I fix this I've already tried a restart and reinstall nether help.
So Please Help.

---

### Post by microsoft92sucks on 2007-06-11
Can I get some help on this Please.
Thanks

---

### Post by lazyart on 2007-06-11
Did you give the executable permission to run?  That would be another chmod after it was compiled.

If you launch from the command line, you have to do```
cd /path/to/filename
./*filename*
```

---

### Post by microsoft92sucks on 2007-06-11
I don't know where it's at I just installed it and it went where ever it should have went. So where is that.

---

