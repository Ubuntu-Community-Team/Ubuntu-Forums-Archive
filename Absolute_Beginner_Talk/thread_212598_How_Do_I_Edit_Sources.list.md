---
title: "How Do I Edit Sources.list?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by yosef on 2006-07-10
I am running edubuntu and when I open the text editor to edit sources.list I cannot save it because I dont have permissions... how do I sudo open the text editor and changes sources.list?

---

### Post by Titus A Duxass on 2006-07-10
Edit it through a terminal, then sudo will work.

---

### Post by lordlollo on 2006-07-10
```
sudo gedit /etc/apt/sources.list
```

cheers

---

### Post by skull_leader on 2006-07-10
Before you edit it, I'd make a copy of it like so:

> sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup 
Then, like lordlollo said:

> sudo gedit /etc/apt/sources.list 

Also, you should check out this wiki page, in case I missed anything important:
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by crystal on 2006-07-10
Just a note from [Ubuntu Documentation -> RootSudo](https://help.ubuntu.com/community/RootSudo):
> NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.

So one might write:
```
gksudo gedit /etc/apt/sources.list
```
or
```
sudo nano /etc/apt/sources.list
```

---

### Post by aysiu on 2006-07-10
To further expand on that:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by lordlollo on 2006-07-10
Thank you for the note. I did not know. :oops: 
Actually, I generally use vi for this kind of stuff, but I wanted to suggest yosef an editor with just a bit more of gui... 
Thanks again.

---

