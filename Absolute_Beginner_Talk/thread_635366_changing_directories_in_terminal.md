---
title: "changing directories in terminal"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by tysonh on 2007-12-08
I'm trying to use the cd command to navigate to my desktop directory.  I can't use the cd command and get past my home folder.  If I use dir to show what in my current directory it shows the folder I need to go to but the cd command won't let me go to it.

I"m try to get to my desktop in terminal to install beryl unless someone knows a better way to do it.

---

### Post by schauerlich on 2007-12-08
What happens when you run ```
cd ~/Desktop
```

---

### Post by Dr Small on 2007-12-08
Usage:
```
cd /
```
That will take you to the root directory.

```
cd /home/
```
That will take you to your /home directory.

```
cd /home/`whoami`/
```
That will take you to you Home Folder.

```
cd ~
```
Will also do the same.

---

### Post by Teknyk on 2007-12-08
Don't forget that Linux is case sensitive.

"Desktop" and "desktop" are NOT the same thing

---

### Post by Dr Small on 2007-12-08
To change directory to the desktop, try:
```
cd ~/Desktop
```

---

### Post by HereInOz on 2007-12-08
The commands are fairly DOS like (DOS pinched them from unix) but there is always a space between the cd and the rest, unlike DOS.  Of course, you use a / rather than a \ as well.

So:
cd / will get you to the root directory

cd /home/myplace/pictures will get you to the pictures directory for the user "myplace" in the home directory

cd .. will get you back up one level

just plain cd will get you back to your home directory

If you are in your own home directory, then cd Desktop will do the job to get you to the desktop.  Note, no leading / and remember, command line in *nix systems is case sensitive.

---

### Post by tysonh on 2007-12-09
Thanks for all the help.  I don't know what I was doing wrong earlier but its working now. :lolflag:

---

