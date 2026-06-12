---
title: "files downloaded"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by yimmmy on 2007-05-14
i just downloaded a program off the internet and its dowent have a run or setup im not sure how to open it , im a linux newb so i dont reallly know how to do this
the files name is kaid-7.0.0.7-linux-x86.tar.gz . they all have that .tar.gz at the end of them so im guessing i have to put that some were 
any help would be great

---

### Post by mejy on 2007-05-14
You ideally want a .deb, otherwise you'll have to build it.  A typical scenario would involve 'sudo apt-get install build-essential', then installing any necessary libraries, then 'cd'ing into the necessary directory and running './configure', 'make' 'sudo checkinstall'.

---

### Post by taurus on 2007-05-14
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Kobalt on 2007-05-14
A .tar.gz file is an archive. Double-clic on it and select a directory to which you can extract what's inside this archive (with the Extract button). 
What is it you are trying to install ? Kaid ? Have you tried searching in the Add/Remove menu to install your program before ?

---

### Post by hyper_ch on 2007-05-14
Is that program not in any repository?

---

### Post by yimmmy on 2007-05-14
im not sure what  you mean repository
and i dint check the add/remove program   i dont really think it will be in there

---

### Post by gigaferz on 2007-05-14
always try first the repositories, How???

Click on System
                       -administration
                                              - synaptic Package manager
In there search for the program you need.

Also  the THIRD post is telling you everything you will ever need.

---

### Post by Fangthon Funk on 2007-05-14
Maybe the 2nd post in [this thread]("http://ubuntuforums.org/showthread.php?t=90051&highlight=kaid") can help?

Good luck

---

### Post by yimmmy on 2007-05-14
im not sure what  you mean repository
and i dint check the add/remove program   i dont really think it will be in there

---

### Post by yimmmy on 2007-05-14
sorry

---

### Post by gigaferz on 2007-05-15
did anything work for you?

---

