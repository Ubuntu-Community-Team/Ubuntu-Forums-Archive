---
title: "7Zip and unrar installed but not in menu?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-05-10
I just installed 7zip which appears as ticked in Add/Remove programs and unrar which appears as installed under synaptec but neither of these apps are appearing anywhere in applications. 

Also I have a .rar i am trying to open and it automatically opens archive manager. If I right click and try to use "open with another appliction" 7zip or unrar they dont appear in the list of software. Did I make a mistake somewhere?

I have installed a couple of other bits of software perfectly after this as a test. Any ideas?

---

### Post by taurus on 2007-05-10
Try to run it from a terminal.

Applications -> Accessories -> Terminal
```
unrar x **filename.rar**
```

---

### Post by tabithaboof on 2007-05-10
Thanks very much, I got unrar working from the terminal but I still seem to be lacking 7zip.

---

### Post by taurus on 2007-05-10
```
locate 7zip
```
to search for it to see if it's on your machine or not.  Chances are it's in /usr/bin if you have installed it.

---

### Post by tabithaboof on 2007-05-10
I really appreciate the help, I ran the above command and got this back but I dont really nderstand it.

/usr/share/app-install/desktop/7zip.desktop

looking in usr/bin I have two files one is "7z" and its a 39byt  shell script. The other is called 7za and its an executable just under 1 meg.

How would I go about adding 7zip to the menu?

---

### Post by Pisi-Deff on 2007-05-10
The 7-Zip for linux is a command-line program.
You can only use it throw the terminal and non-grafically.
I forgot the command tho

---

### Post by tabithaboof on 2007-05-10
aaah gotcha! Thanks very much for the help.

---

