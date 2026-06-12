---
title: "intstalling .tar.gz files"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by feest on 2006-06-28
hi i've recently downloaded winrar for linux but now i need to know how i install .tar files and how i call the application... help please...

---

### Post by shoot2kill on 2006-06-28
[QUOTE=feest]hi i've recently downloaded winrar for linux but now i need to know how i install .tar files and how i call the application... help please...[/QUOTE]

you can use a different rar extracting program

```
sudo aptitude install rar
```

does the same job.. just not WinRAR

---

### Post by Jagot on 2006-06-28
tar, not rar:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

Or point 4 here:

[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)

---

### Post by shoot2kill on 2006-06-28
[QUOTE=Jagot]tar, not rar:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

Or point 4 here:

[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)[/QUOTE]

i thought WinRAR (what he wanted) was the same as RAR, (what i sugested..)

---

### Post by Jagot on 2006-06-28
Yep, but he wanted to install .tar.gz files which you don't need winrar to extract or install the application contained within.

---

### Post by aysiu on 2006-06-28
You don't need to install extra software to extract a .tar.gz

And *rar* is the program you would need as the equivalent to *winrar*. There's also a program called *unrar*. I think you may need [extra repositories enabled](http://www.psychocats.net/ubuntu/sources) to get these installed.

---

### Post by feest on 2006-06-28
i tried to use unrar-free (no idea how i installed it but whatever...)

> sven@ubuntu:~/Desktop/desktop$ unrar-free -x file.rar  /home/sven/Desktop

unrar 0.0.1           Copyright (c) 2004 Ben Asselstine


Extracting from /home/sven/Desktop/desktop/file.rar

Extracting  file1.exe                                                Failed
Extracting  file2.nfo                                              Failed
2 Failed
sven@ubuntu:~/Desktop/desktop$


whats wrong now?

---

### Post by aysiu on 2006-06-28
Maybe you need the nonfree version of *unrar*? ```
sudo aptitude update
sudo aptitude install unrar
```

---

### Post by Breezy Badger on 2006-06-28
hey feest.  Get easy ubuntu.  There is a good thread on here with the link.  It will download you all the tools you need, and you can just right click on what you want to extract and do it, like windows almost

---

### Post by feest on 2006-06-28
[QUOTE=Breezy Badger]hey feest.  Get easy ubuntu.  There is a good thread on here with the link.  It will download you all the tools you need, and you can just right click on what you want to extract and do it, like windows almost[/QUOTE]

well thats not really my point my point is how to use unrar-free and to learn something...

---

### Post by Breezy Badger on 2006-06-28
well if you want to learn then learn on.  If you want to be able to get something done try easy ubuntu

---

### Post by topcat37 on 2006-06-28
This might help you, It helped me. 
Go here: [http://www.ctssn.com/](http://www.ctssn.com/)  then go to lesson eight. I've been doing allot of the tutorials and that one  seemed to work for me. TC

---

