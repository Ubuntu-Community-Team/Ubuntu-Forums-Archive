---
title: "Confused: some basic help needed please"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by elkdanger on 2006-08-31
Hi

Basically what I'm trying to do is execute an ELF program, which I have in placed in /home/steve/test. This program uses a library test.so which I have placed into /usr/lib, but when I execute the program with "./test.e" from the terminal it tells me that the shared library or object cannot be found: unknown file or folder.

As far as I know the library should be picked up in /usr/lib. To get it there I had to copy it from /home/steve/test into the correct location, using sudo cp test.so /usr/lib. Now, when I explore the folder using the GUI I can see the library there but the icon for the file has a little red square with a white cross in it. When I do a "locate test.so", it can't find the library in the /usr/lib folder.

Or maybe I'm doing this wrong. I'm just trying to get my program to run. Can anyone help me out?

Thanks in advance.

---

### Post by Eproxus on 2006-08-31
> **elkdanger said:**
> Hi

Basically what I'm trying to do is execute an ELF program, which I have in placed in /home/steve/test. This program uses a library test.so which I have placed into /usr/lib, but when I execute the program with "./test.e" from the terminal it tells me that the shared library or object cannot be found: unknown file or folder.

Running the command below will parse the libraries folder and check for new libraries. It should work after that.```
sudo ldconfig
```

> As far as I know the library should be picked up in /usr/lib. To get it there I had to copy it from /home/steve/test into the correct location, using sudo cp test.so /usr/lib. Now, when I explore the folder using the GUI I can see the library there but the icon for the file has a little red square with a white cross in it.
That's because it's not your file, it's the "administrators" file. It is owned by root.

> When I do a "locate test.so", it can't find the library in the /usr/lib folder.

The locate command uses a cached database, to update this database run the command
```
sudo updatedb
```

---

### Post by elkdanger on 2006-08-31
> **Eproxus said:**
> Running the command below will parse the libraries folder and check for new libraries. It should work after that.```
sudo ldconfig
```


I was fairly sure I tried that, but i'll give it a go tonight.

Thanks for the reply, much appreciated.

---

### Post by elkdanger on 2006-08-31
Using ldconfig hasn't worked :-( When I run the program it still complains that the shared object libCcCpiTools.so is missing.

Locate now finds it, and it's definitely in /usr/lib. Is there maybe something I'm missing with an environment path variable or something?

---

### Post by Eproxus on 2006-09-04
Is it supposed to be named test.so or libCcCpiTools.so?

---

