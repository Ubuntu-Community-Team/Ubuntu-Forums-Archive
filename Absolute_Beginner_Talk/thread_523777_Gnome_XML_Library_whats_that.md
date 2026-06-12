---
title: "Gnome XML Library whats that?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-08-12
checking for GnomeXML libraries >= 1.8.5... configure: error: Did not find GnomeXML installed

i was trying to run ./configure on my GTK widget factory file then i got that error message, anybody know how to solve it?

---

### Post by MenZa on 2007-08-12
Sounds like what you want is libxml2, according to a quick repository search:

```

[17:28:47] menza@alderaan - ~ $ apt-cache search gnome xml
libxml2 - GNOME XML library

```

---

### Post by kinngg on 2007-08-12
chilin@Ubuntu-Laptop:~$ sudo apt-get install libxml2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxml2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

i tried installin it but i already have it

---

### Post by schorsch on 2007-08-12
You need the development package:

```
sudo apt-get install libxml2-dev
```

---

### Post by kinngg on 2007-08-12
> **schorsch said:**
> You need the development package:

```
sudo apt-get install libxml2-dev
```

chilin@Ubuntu-Laptop:~$ sudo apt-get install libxml2-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxml2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
chilin@Ubuntu-Laptop:~$ 

still the same it says i already have them

---

### Post by schorsch on 2007-08-12
Uhm, sorry, after reading your initial post for the first time ....

```
sudo apt-get install libxml-dev
```

---

### Post by kinngg on 2007-08-12
Thanks that worked great, but now i ran make, make install and now i dont know how to start my installed program,
i installed The Widget Factory and i cant find it in any of the menus.. some help please

and btw how do you remove, completely remove or delete things which you installed through the process of ./configure make make install thanks

---

### Post by schorsch on 2007-08-12
Where did you get the source file from? And have you seen there is a package called the widgetfactory available in Synaptic? It is in the universe repos.

If the programmer has done a good job you will be able to type

```
make uninstall
```

in the directory where you have compiled the sources. But sometimes you are simply out of luck. So it is always better to use precompiled packages and let the package manager do its job.

---

### Post by schorsch on 2007-08-12
I just installed the package from the repos and it is started with the command "twf" either in a terminal or in the application starter which can be reached by pressing ALT+F2 at the same time. So I do not need the info about the source file any longer .... :)

---

### Post by kinngg on 2007-08-12
Oh yeah, i found mine, mine could start by running 'gwf' and by the way how do you remove things you installed through source?

---

### Post by schorsch on 2007-08-12
Go the directory where you compiled the sources and type
```
make uninstall
```
If you are lucky that will do the job; otherwise you have to take a look at the logfiles in this directory and check where the compiled files are copied to.

---

