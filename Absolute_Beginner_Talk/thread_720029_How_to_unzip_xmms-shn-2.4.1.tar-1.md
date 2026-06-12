---
title: "How to unzip xmms-shn-2.4.1.tar-1"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2008-03-09
gunzip doesn't work with this file. How do I unzip it.
Thanks

---

### Post by hhhhhx on 2008-03-09
open it with archive manager

---

### Post by RichPicker on 2008-03-09
Archive Manger won't open it. 

I also have this on my desktop      xmms-shn-2.4.1

It is a folder. But what and how to intall?

---

### Post by RichPicker on 2008-03-09
Okay, Now I have this file on my desktop
xmms-shn-2.4.1.tar-2

But how to unzip it. Archive manager can't find it, or can't open it. I don't know. I'm a newbie at this. I've installed several apps in the past, but can't get this one for some reason. Sorry to be such a retard.

R-

---

### Post by hhhhhx on 2008-03-09
> **RichPicker said:**
> Archive Manger won't open it. 

I also have this on my desktop      xmms-shn-2.4.1

It is a folder. But what and how to intall?
```
$ make
$ make install
```

i think that you can get xmms from the repositories though.

---

### Post by RichPicker on 2008-03-09
rich@rich-laptop:~$ cd ~/Desktop
rich@rich-laptop:~/Desktop$ make xmms-shn-2.4.1
make: Nothing to be done for `xmms-shn-2.4.1'.
rich@rich-laptop:~/Desktop$ make install xmms-shn-2.4.1
make: *** No rule to make target `install'.  Stop.
rich@rich-laptop:~/Desktop$ 

That didn't work.

---

### Post by Oldsoldier2003 on 2008-03-09
> **RichPicker said:**
> rich@rich-laptop:~$ cd ~/Desktop
rich@rich-laptop:~/Desktop$ make xmms-shn-2.4.1
make: Nothing to be done for `xmms-shn-2.4.1'.
rich@rich-laptop:~/Desktop$ make install xmms-shn-2.4.1
make: *** No rule to make target `install'.  Stop.
rich@rich-laptop:~/Desktop$ 

That didn't work.

you have to cd into the directory...

but honestly why make it if its in the repos?

```
sudo apt-get install xmms
```

---

