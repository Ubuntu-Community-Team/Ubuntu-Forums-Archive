---
title: "[SOLVED] wine how to tutorial?"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2007-08-29
can anyone point me this way please

---

### Post by Sp4freel on 2007-08-29
[http://www.winehq.org/site/howto](http://www.winehq.org/site/howto) this is how I got it to work

---

### Post by liquidfunk on 2007-08-29
What do you want to know about?

 How to get it?

 In a Terminal: - Accessories - Terminal:

 sudo apt-get install wine

 Once that is installed.

 winecfg
 
 Which lets you change settings, have a look around there.

 To run/install things.

 Typing 'cd' will change directory. E.g. cd /media/cdrom0 
Will mean that you end up in the CD folder. 

 So as an example:

 cd /media/cdrom0

 wine Setup.exe

 Try it.

---

### Post by asmoore82 on 2007-08-29
immediately after the 'winecfg' step you should run ...
```
~ $ wine iexplore http://www.google.com
```
and Wine will automatically download the Gecko rendering engine.
This is needed for most games to run properly (like Counter-Strike).

---

### Post by jon zendatta on 2007-08-30
thanks everyone, already installed but had issues with installing from cd, got it now:)

---

