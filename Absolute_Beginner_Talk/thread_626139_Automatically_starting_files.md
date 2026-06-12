---
title: "Automatically starting files"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by APMT19 on 2007-11-28
I have a batch file or at least thats what they call it on windows. How do I make it so that it launches that file automatically when I log on? Running 7.10 Desktop

---

### Post by jken146 on 2007-11-28
Go in System>Preferences>Sessions.
Add an entry for the command you want to run.  Usually this is of the form <program command> <file name>, e.g. gedit /home/bob/file1.txt

---

### Post by Arthur Archnix on 2007-11-28
In >system >preferences >sessions you can add stuff to start automatically. Add your bash script in there. If it literally is a batch file it won't work, but if it's the Linux equivalent (i.e. a bash script) it will.

EDIT: This is why I don't like answering new questions. I'm too slow.

---

### Post by jken146 on 2007-11-28
By batch file do you mean a script?  If so you may have to put ./script.sh ( ./ means execute)

---

### Post by Dr Small on 2007-11-28
> **Arthur Archnix said:**
> In >system >preferences >sessions you can add stuff to start automatically. Add your bash script in there. If it literally is a batch file it won't work, but if it's the Linux equivalent (i.e. a bash script) it will.

EDIT: This is why I don't like answering new questions. I'm too slow.
I was going to suggest that, but since I am not in Gnome right now, I thought what the heck..

---

