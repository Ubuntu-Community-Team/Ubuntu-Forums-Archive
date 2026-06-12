---
title: "Learning Ubuntu"
date: 2008-02-18
forum: Beginner Team
---

### Post by glmoring on 2008-02-18
I just started a Computer Science class and thought it would be a great idea to use Linux. I had a computer that some gave me because they downloaded a virus while opening an email attachment. So I loaded Ubuntu on it and it works great. I have always used Windows and I thought their would be a huge learning curve, I was wrong. Ubuntu, for the most part, was easy. All except for...

the scripting. 

In my Computer Science class we are learning C and C+. So I wanted to download a compiler. BIG MISTAKE! I worked all weekend until I finally gave up, And I never give up.

So I was thinking.. It would be a great learning tool to take us step by step though the process of download GCC in Ubuntu. I know it would help me. 

What you are doing here is great. I just hope that one day I can help others that are in the same position I am in now.

---

### Post by pt_lam on 2008-02-18
I'm not very sure, but... isn't gcc pre-installed in ubuntu?

---

### Post by frankos44 on 2008-02-18
$ sudo apt-get install g++

Tons of examples in google

---

### Post by bodhi.zazen on 2008-02-18
Every distro is a little different.

If you want to compile, there is a meta-package, build-essential.

```
sudo apt-get install build-essential
```

In Ubuntu the c headers are in the "dev" packages.

There is also "programming talk" :

[http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by Christopher Robin on 2008-02-19
I found all the packages I need already listed (and some already installed) in** System > Administration > Synaptic Package Manager**. They even have descriptions, and I just clicked my way through the download and installation (the only thing I needed to type was my password). What you're looking for might be in that list!

-Robin
on Day Two of Ubuntu

---

### Post by richard.stallman on 2008-02-21
> **glmoring said:**
> I just started a Computer Science class and thought it would be a great idea to use Linux. I had a computer that some gave me because they downloaded a virus while opening an email attachment. So I loaded Ubuntu on it and it works great. I have always used Windows and I thought their would be a huge learning curve, I was wrong. Ubuntu, for the most part, was easy. All except for...

the scripting. 

In my Computer Science class we are learning C and C+. So I wanted to download a compiler. BIG MISTAKE! I worked all weekend until I finally gave up, And I never give up.

So I was thinking.. It would be a great learning tool to take us step by step though the process of download GCC in Ubuntu. I know it would help me. 

What you are doing here is great. I just hope that one day I can help others that are in the same position I am in now.

i had the same problem. finally, i installed WINE and installed a windows-based C/C++ compiler. it works!!!

---

### Post by richard.stallman on 2008-02-21
> **Christopher Robin said:**
> I found all the packages I need already listed (and some already installed) in** System > Administration > Synaptic Package Manager**. They even have descriptions, and I just clicked my way through the download and installation (the only thing I needed to type was my password). What you're looking for might be in that list!

-Robin
on Day Two of Ubuntu
even C/C++ compiler???

---

### Post by LaRoza on 2008-02-21
> **richard.stallman said:**
> even C/C++ compiler???

See the sticky in the programming talk on how to use C and C++ on Ubuntu.

---

### Post by mali2297 on 2008-02-21
> **richard.stallman said:**
> even C/C++ compiler???

Install the package **build-essential**, it includes the C/C++ compiler gcc.

To compile something in the terminal, type
```

gcc -o example example.c

```

There are also IDEs available, like **Eclipse**, that you can install from Synaptic as well.

---

### Post by 504harry on 2008-03-11
> **LaRoza said:**
> See the sticky in the programming talk on how to use C and C++ on Ubuntu.

Hi, Similar problem - I want to program those PIC-devices - that usually means learning/using C ( or C++++ I don't know enough!).
Electronic Mags now provide the C-code to program these PICs and there is another (simpler) device here in the UK, "PicAxe" - it is a PIC with a simple "loader" so you can program it in BASIC - it also has a simulation program, so you don't need to wire the thing up! It's a bit slow, of course, but a good introduction to using these devices in school-projects, etc.

I haven't managed to find a C-compiler (if that's what I need?)....that is also an issue I guess...all I want to do is write the program and put it inside the PIC ( A product of Arizona Microchip I believe)....then when the PIC is mounted on a PCB it just works.  **You are probably using one right now! **- your Mouse controller is almost certainly a PIC ( right inside the mouse, - takes all the oprtical data and sends out a serial stream).

Cuirrently (To my shame!) I have to run the BASIC suimulation prog on an old Win-PC, because that's the OS the program needs. 

Am I right in thinking that C-compilers are only Sold? - ie they cost money and that's why they don't appear to be available for Windows OR Ububtu? ((-It surprises me, for it's an established language and close to the minds of those that compile Linux, etc.))

---

### Post by LaRoza on 2008-03-11
> **504harry said:**
> 
Am I right in thinking that C-compilers are only Sold? - ie they cost money and that's why they don't appear to be available for Windows OR Ububtu? ((-It surprises me, for it's an established language and close to the minds of those that compile Linux, etc.))

No. C is a standardized language. It is free.

Different compilers exist for it for different platforms. The must common C compiler on Linux is gcc, but there are others.

gcc is available for Windows as well.

Naturally, you need a compiler for whatever your target platform will be.

[http://gcc.gnu.org/](http://gcc.gnu.org/)

[http://fabrice.bellard.free.fr/tcc/](http://fabrice.bellard.free.fr/tcc/)

[http://www.mingw.org/](http://www.mingw.org/)

[http://cygwin.com/](http://cygwin.com/)

(A Windows IDE that uses MinGW) [http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html)

---

