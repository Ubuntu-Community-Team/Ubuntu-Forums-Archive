---
title: "Unable to Down loading Realplayer"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by cjpkot on 2005-10-30
Could someone give me a step by step procedure on installing Realplayer.
I'm completely lost.  I've read about it on other sights but I'm totally confused.
Thxs

---

### Post by Xian on 2005-10-30
Read the wiki entry: [How To Install RealPlayer 10](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483)

---

### Post by cjpkot on 2005-10-31
I've down loaded the file RealPLayer10GOLD.bin OK
I opened terminal and entered the code.  It doesn't reconize file

---

### Post by heimo on 2005-10-31
[quote=cjpkot]I've down loaded the file RealPLayer10GOLD.bin OK
I opened terminal and entered the code.  It doesn't reconize file[/quote]

Make sure that you run:```
sudo ./RealPlayer10GOLD.bin
```
in a directory where you placed the file. If you downloaded it to the desktop, run this:
```
cd ~/Desktop
```
You can list files using ls and change directories using cd.

---

### Post by Darrin on 2005-10-31
I was having a heck of a time also. Thanks to some well laid out instructions, I got it going. 
[View the thread here.]("http://www.ubuntuforums.org/showthread.php?t=80935")

---

### Post by Xian on 2005-10-31
[QUOTE=cjpkot]I've down loaded the file RealPLayer10GOLD.bin OK
I opened terminal and entered the code.  It doesn't reconize file[/QUOTE]
This is the step you are missing in the wiki:

*At the command line, change to the directory where you downloaded the file...*

In the open terminal you need to cd to the file location.
For example, if the file is on your desktop:

```
$ cd /home/username/Desktop
```

---

### Post by cjpkot on 2005-10-31
I can get to the directory but when I enter any code about the file it doesn't reconize it.  Do I need to down load from synaptic manager to get the rest of my code working.

---

### Post by Xian on 2005-10-31
You'd better copy/paste the commands you are issuing and the errors you receive back in the terminal. It is difficult to understand where you are getting snagged from your description.

---

