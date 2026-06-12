---
title: "What's the file location of the evolution mail starter?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-19
I was editing my start-up programs and accidentally substituted the executable file that starts evolution mail and would like to know what the location is so that I can correct my  screw up.  Any help will be appreciated.


VC

---

### Post by charles.g.moore on 2007-06-19
> **videocheez said:**
> I was editing my start-up programs and accidentally substituted the executable file that starts evolution mail and would like to know what the location is so that I can correct my  screw up.  Any help will be appreciated.


VC

I did a locate and found the executable in /usr/bin/evolution

If you dont know how to do a locate just ask...

---

### Post by videocheez on 2007-06-19
thx

---

### Post by Dragonflyoh on 2007-06-23
How do you perform locate?

---

### Post by videocheez on 2007-06-23
Go to places> Search for Files>files name

---

### Post by Dragonflyoh on 2007-06-23
Thank you. I thought there was a way to locate files from a terminal.

---

### Post by videocheez on 2007-06-23
I'm sure there is but I'm too much of noob to know how. ;)

---

### Post by charles.g.moore on 2007-06-24
> **videocheez said:**
> I'm sure there is but I'm too much of noob to know how. ;)

If you want to locate something from a terminal you can use the command:

sudo locate *what you are looking for*

alot of times there are many instances of that "word" so i pipe the locate command through less

sudo locate *what you are looking for* | less

(that | is the delineator(shift + \))

A good place to check out is:  [http://www.linux.org.mt/node/49#N1029A](http://www.linux.org.mt/node/49#N1029A)

---

