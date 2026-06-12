---
title: "Loki and Quake"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by ikemsd on 2006-09-25
I downloaded the compressed files, now, how do i play my games.  I tryed extracting loki-demos-1.0d.run.  I dont know. May i please have a big mug of help](*,)

---

### Post by croak77 on 2006-09-25
Just run  loki-demos-1.0d.run. Open a terminal and type sh /path/to  loki-demos-1.0d.run. Or ./path/to/ loki-demos-1.0d.run might work too.

---

### Post by ikemsd on 2006-09-27
I do that but it says not a directory, or if i change it a bit, it might say No such file or directory.](*,)

---

### Post by JNowka on 2006-09-27
Try changing to the directory of the file.  Once there type "sudo ./loki-demos-1.0d.run".  Make sure you put a period in the very front when you are in the same directory.  If you get errors please paste them here.

---

### Post by ikemsd on 2006-09-27
:~$ sudo ./loki-demos-1.0d.run
sudo: ./loki-demos-1.0d.run: command not found

---

### Post by joshuapurcell on 2006-09-27
> **ikemsd said:**
> :~$ sudo ./loki-demos-1.0d.run
sudo: ./loki-demos-1.0d.run: command not found

Looks like it may be related to permissions. You can try this from the directory you have the .run file in:
```
~$ chmod loki-demos-1.0d.run
~$ ./loki-demos-1.0d.run
```
Or just:
```
~$ sh ./loki-demos-1.0d.run
```Add sudo before running the file only if you want to install it somewhere other than your home directory (which isn't usually needed).

---

### Post by ikemsd on 2006-09-28
what do you mean by try this in the directory?  I only know the hardware parts of computers, not the programing or anything fancy like that.:???:

---

### Post by CatKiller on 2006-09-28
> **ikemsd said:**
> :~$ sudo ./loki-demos-1.0d.run
sudo: ./loki-demos-1.0d.run: command not found

I think that this means that you haven't made the .loki-demos-1.0d.run file executable. So when you try to run it, there is no executable file of that name. Right-click on the file, select Properties and select the Permissions tab. Tick the box marked Execute for the Owner, and close the window. Then the ./loki-demos-1.0d.run command should run.

---

