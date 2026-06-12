---
title: "compile gcc 3.0 or higher vertions"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by SwaroopKunduru on 2006-04-18
Hi All,

I have installed ubuntu5.10 and working to install some packages like MPlayer, when i am following the instructions I have few errors. It was asking to install gcc3.0 or higher vertion. Where can I find documentation on this. Please help me in this.

Regards,

Swaroop.

---

### Post by Kimm on 2006-04-18
A simple

sudo apt-get install build-essential

in the terminal should set you up :)

---

### Post by SwaroopKunduru on 2006-04-18
Kimm,

Thanks for the reply. What is the file I have to download for installing gcc?

Regards,

Swaroop.

---

### Post by orkim on 2006-04-18
There is no file to download.  apt will take care of getting all the files it needs.  As Kimm said:

sudo apt-get install build-essential

Simply drop to a terminal window (xterm, gterm, konsole, etc.  take your pick) and type that line.  It will install all the common packages you need.  Including gcc, build libraries, and so on.

Of course, to use apt to download the package, you will need to be connected to the internet. :)

Or you could grab these packages off of the installation cd (i think, someone want to correct me if im wrong here?).

Good Luck

---

### Post by SwaroopKunduru on 2006-04-19
Thanks Kimm &  Orkim,

I got it fixed.

Regards,


Swaroop Kunduru.

---

