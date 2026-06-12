---
title: "A multitude of problems and questions."
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by DennShin on 2007-03-01
Ok, I guess I will start with my problems first.   

Problem #1 
I am trying to install this splash screen. 

[http://www.gnome-look.org/content/show.php?content=50468](http://www.gnome-look.org/content/show.php?content=50468)

and can follow these instructions up **until the install section**. 

[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

Where it mentions **"usplash-theme-fingerprint.so"** I get confused.  I dont have any file named that.  I have a directory called **"usplash-fingerprint-sources"**.  And inside that I have a Debian folder some .png files and 3 files one called **makefile** another called **usplash-theme-ubuntu.c** and another called **usplash-theme-ubuntu.c-2**.  

Now I have copied this directory over to **"/usr/lib/usplash/"**  and I have gone to the console and typed **"sudo update-alternatives --config usplash-artwork.so"** and it returns the error. 

```
There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.

```

So I enter **"sudo update-alternatives --config usplash-default.so"** and it returns the error. 

```
No alternatives for usplash-default.so.
```

Now before I ask what I am doing wrong.  I would like to ask some questions.  the file named "Makefile" with no extension, I was under the assumption that that file was to be ran with "make" in the CLI.  But attempting I get the following error. 

```
bash: make: command not found
``` 

I also get this with the command "cd.." which I thought was supposed to bring you back or "up" one directory in the file system under the CLI.  

```
bash: cd..: command not found
```

Assuming I am doing something wrong, since I probably am being very new to this OS how exactly do I handle a makefile? And backup into a directory besides typing cd /dir/ over and over. 

I appreciate any help that is given. 

Thank You.

---

### Post by spoot on 2007-03-01
#1
I think you downloaded the source code package instead of the binary package, is that possible?
[https://sourceforge.net/project/showfiles.php?group_id=187765&package_id=219345&release_id=482324](https://sourceforge.net/project/showfiles.php?group_id=187765&package_id=219345&release_id=482324)
(pick one of the bottom three depending on your system, I386 being the most common)

#2
The command to change directory is indeed called "cd". One slight difference with Windows (I think) it that you cannot use "cd..", it will see that as one command. Instead, put a space in there; "cd ..", hope that fixes it ;)

---

### Post by DennShin on 2007-03-06
Thank You, that was exactly the problem.  I apologize I did not notice that sooner.

---

