---
title: "Copy files from Ubuntu to Windows"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by TANDEMCYKELN on 2007-12-22
Dear friends,

I'm trying to copy files from Ubuntu to Windows but I get an error. Could anybody please give me some help of what I am doing wrong.

Both machines are connected to the same router and I have got no problems accessing files through the GUI.

This is the error that i get when I try to copy a file through the terminal:

danneman@kitchen:~$ cp -u /home/danneman/Documents/alkoholintag.ods smb://danne/Big%20Sam%20(N)/dokument
bash: syntax error near unexpected token `('

I have tried to change the share name on the Windows machine, because I thought that the share name might be the problem, but I couldn't change the share name in Windows.

I tried to google the problem, but I couldn't find any help. It seems like the problem is such a newbie thing and I feel so stupid.

---

### Post by StGeorge on 2007-12-22
Don't feel Stupid as most of us new to Linux are.
As a windows user, I know.
It's a new learning curve.
I take it as you are using a network that you want to copy from one machine to another.
If so do you see a padlock on the files?
Do not change network settings unless given advice by someone whos a Linux techie.
Have you got explore2fs on your windows machine?
I have no URL handy but google it.
Its a self ex program with no install.
Extct what you want from windows.

---

### Post by DirtDawg on 2007-12-22
Put quotes around file or path names any time there are spaces or unusual characters in them. For example:
```
 cp -u /home/danneman/Documents/alkoholintag.ods "smb://danne/Big%20Sam%20(N)/dokument"
```
should work.

---

