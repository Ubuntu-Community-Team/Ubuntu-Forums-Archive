---
title: "Cannot change directorys"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Mr.Stress on 2007-03-05
Hello, and yes I'm a newby to linux, I know my way around dos in windows but I can't seem to change directories at a linux terminal. Several programs I downloaded I can't install because it says file not found. Heres what I'm typing for example to change directorys. 
 cd /home/username/Desktop/  no matter which directory I try to go to cd/home for example or anything else it says file or folder not found which makes it impossable to install any software from the terminal.
     I installed the ubuntu 6.06.1 server and got the gui installed, the synaptic package manager works fine.

---

### Post by wpshooter on 2007-03-05
Do this.  Always make yourself a "download" directory in your HOME directory.  Then USUALLY, but not necessarily always, point downloads to that directory.

Please note that apparently linux is very selective about CASE.  Make sure when you are typing the path string that you get the CASE correct in each and every parameter.  For instance the x11 directory is **X**11 not x11.  A lot of the downloads place capital characters in only certain places in words.  For instance, adobereader is usually **A**dobe**R**eader.

Good luck.

---

### Post by annda on 2007-03-05
also, if possible, use tab-completion. this is a great feature.

for example, if you have a directory called "my CATS" on your desktop and you want to navigate to it in the terminal, go:

```
cd
```

this will get you to your home directory (otherwise known as ~)
```

cd D
```

and hit TAB - this will finish the name of the directory that starts with a capital d. if there are more, hit TAB again and you will see all the possibilities. or add 'es' and then hit TAB again.

then type 'm' or 'my' and TAB again. you will see something like this:

cd Desktop/my\ CATS/

see, that way you can get around special characters too - like spaces, apostrophes etc.

---

