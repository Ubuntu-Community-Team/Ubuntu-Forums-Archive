---
title: "installing manually"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by mwanafunzi on 2006-01-27
To ubuntu,
I have been trying to install inkscape for a while know, I have not had much success. This has brought me into a very different realm that is not apt-get  or dpkg. 
What i did was download inkscape onto my desktop, I then extracted the files and left the folder on my desktop. From there I got into the folder and I did the whole
./configure
make and 
make install.

This is where I have a slight problem. I know that with synaptic all the work is done for you. That is the files are put in the appropriate places. Unfortunately I assumed that by manually installing the same thing would apply. My question is, where would I put the original inkscape folder (that is before I make install). 

e.g. would it go under /
or /bin
....etc...

thanks

---

### Post by agapito on 2006-01-27
In short, anywhere. The things you compile and install go automagicly to the prefix /usr/local/ after you run *make install*, unless you instructed otherwise that is, which I guess you didn't. So go ahead and install it. ;)

By the way, I got my Inkscape from the repositories... Maybe you should check this out to have all the packages:[http://www.ubuntuforums.org/showthread.php?t=92672]("http://www.ubuntuforums.org/showthread.php?t=92672")

---

### Post by mwanafunzi on 2006-01-27
would i be able to delete the folder on my desktop and how would i put a link in menu > graphics

---

### Post by Perfect Storm on 2006-01-27
[QUOTE=mwanafunzi]To ubuntu,
I have been trying to install inkscape for a while know, I have not had much success. This has brought me into a very different realm that is not apt-get  or dpkg. [/QUOTE]


???

Inkscape are avaible through apt-get

---

### Post by agapito on 2006-01-27
Yes, you can delete the folder, but I would keep it untill I tested the program, because you can do *make uninstall*. ;)  Remember to use *sudo make install* or else you won't be able to install it. The same is valid for uninstalling. To add the shortcut you can use the Applications Menu Editor, in the System tools. Notice that I have edited my previous post. I guess you're not using all of the repositories available. ;)

---

