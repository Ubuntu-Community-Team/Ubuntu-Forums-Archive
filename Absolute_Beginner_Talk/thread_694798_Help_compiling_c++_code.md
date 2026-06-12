---
title: "Help compiling c++ code"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by browny254 on 2008-02-12
Hi, I just downloaded this file [http://www.bearcave.com/misl/misl_tech/wavelets/hurst/rand.tar](http://www.bearcave.com/misl/misl_tech/wavelets/hurst/rand.tar) and im trying to compile it, but it comes up with about 15 errors when i try it. I have no idea what they mean so i was hoping someone could see if they get the errors too and maybe explain them to me or let me know how to fix them. I am completely new to this so its probably something pretty simple.

once i have unpackaged the file above i go to the rand directory and use g++ rantest.cpp -o rantest
im not really sure what the -o does, but i read a few help sites that say its useful.

thanks for any help/advice you can give.

---

### Post by taurus on 2008-02-12
Have you installed the build-essential package on your machine first before you use the GCC compiler?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by browny254 on 2008-02-12
i told you it would probably be something simple :P

when i try that it asks me to use the install cd, is there some way i can do it without the cd, or check to see if i actually have the package beforehand?

---

### Post by amo-ej1 on 2008-02-12
You could try downloading it from the internet, but that won't be your only problem. When you look at the rand/Makefile in the tar archive you see that the code relies on the GSL (gnu scientific library) for the random number generator. So you should also install that one 

(apt-get install libgsl0-dev )

Then if you try to compile it, mind the extra includes I had to add, I get the following error: 


```

edb@Flying-Spaghetti-Monster:/tmp/rand$ g++ rantest.cpp  -Iinclude/ -I../histo/include/
../histo/include/histogram.h:199: error: ‘class histogram::bin_vec’ redeclared with different access
../histo/include/histogram.h: In function ‘void plotHistogram(rand_base&, size_t)’:
../histo/include/histogram.h:141: error: ‘class histogram::bin_vec’ is private
rantest.cpp:23: error: within this context


```

Okay, then I make the class public, and compiled it with:

```

edb@Flying-Spaghetti-Monster:/tmp/rand$ g++ rantest.cpp  -Iinclude/ -I../histo/include/ -lgsl -lgslcblas
/tmp/ccCLjRVp.o: In function `plotHistogram(rand_base&, unsigned int)':
rantest.cpp:(.text+0x8a): undefined reference to `histogram::calculate(double*, unsigned int, histogram::bin_vec&)'
collect2: ld returned 1 exit status

```
So that means it has additional dependencies on some files on the histo subdirectory  so in histo/src you type:

```

edb@Flying-Spaghetti-Monster:/tmp/histo/src$ g++ -o histogram.o -c histogram.cpp -I../include
edb@Flying-Spaghetti-Monster:/tmp/histo/src$ ls histogram.o
histogram.o

```

to create histogram.o and then again in the rand subdirectory you can link the histogram.o:

```

edb@Flying-Spaghetti-Monster:/tmp/rand$ g++ rantest.cpp  -Iinclude/ -I../histo/include/ -lgsl -lgslcblas ../histo/src/histogram.o -o rantest
edb@Flying-Spaghetti-Monster:/tmp/rand$ ./rantest 
-5.5000 1615
-5.3437 1568
-5.1875 1538
-5.0312 1530

```

and execute the rantest binary ....

sigh, haven't ms visual studio users never learned how to use make ?

---

### Post by taurus on 2008-02-12
> **browny254 said:**
> i told you it would probably be something simple :P

when i try that it asks me to use the install cd, is there some way i can do it without the cd, or check to see if i actually have the package beforehand?

If you don't have the installer CD, you can install it over the net.  Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-scr**.  Save it and then close down gedit window.  Now, see what happens when you run

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by mali2297 on 2008-02-12
> **browny254 said:**
> i told you it would probably be something simple :P

when i try that it asks me to use the install cd, is there some way i can do it without the cd, or check to see if i actually have the package beforehand?

Open Synaptic and go to *Settings > Repositories*. Locate the entry for the CD-ROM and disable it.

You can use Synaptic to install **build-essential**. (Search for it.)

---

### Post by browny254 on 2008-02-12
AWESOME! cheers mate, that was just the help i was looking for.

---

