---
title: "Missing Source files"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by nuttycat on 2006-01-20
Hi everyone,
I am new to Linux as is, but am quite proficient in programming in the windows environment. I am pretty good at c/c++.  I would not go to the extent of calling myself a power user in windows, but i can say that i am nearing that. 

I got breezy badger installed. and found problems in the installed options. my primary problem is in GCC. After about 30 mins of fiddling, i found out that i need to "apt-get install gcc ", which worked. GCC got installed.

but the developer files seem to be missing. Even a simple "hello world" example does not compile. It quotes Error: stdio.h - no such file or directory. and same for all other standard headers.

i looked in /usr/src but found it to be empty. How do I get the headers? 
I saw from a google search (that took me to [http://linuxhelp.blogspot.com/2005/12/essential-house-keeping-in-ubuntu.html](http://linuxhelp.blogspot.com/2005/12/essential-house-keeping-in-ubuntu.html)) 

that i should run 

$ sudo apt-get install build-essential
$ sudo apt-get install manpages-dev autoconf automake libtool
$ sudo apt-get install flex bison gcc-doc g++

now, do i need to run all three? Do these commands make apt-get download from the net or is it from the ubuntu cd? 

If  it will download from the net, what kind of download sizes am i looking at? I don't have a very fast connection and my data transfer is limited by volume per month, so I would like to look at the possible sizes of files that i am trying to download.

or is there some other way i can get gcc to find the missing headers? This is the first time, i've encountered a compiler that installs, but then reports that the standard headers are not to be found.

I have other problems too, but i think, i'll put those in another thread.

Thanks.
Computernut

---

### Post by dueY on 2006-01-20
I would think you would atleast need the build-essential.  I would try that one first.  And after you type ```
sudo apt-get install build-essential
``` it will tell you before you download how much you are downloading.  Which probably shouldn't be too much.

---

### Post by nuttycat on 2006-01-20
Thanks dueY, i'll go try that, and see what happens.

---

### Post by hen3rz on 2006-01-20
> it will tell you before you download how much you are downloading. Which probably shouldn't be too much.

duey is right it tells you how big the file is your downloading and bow big it will be once installed and will ask you to type Y to proceed or N to cancel.

---

### Post by nuttycat on 2006-01-20
Thanks both of you.
I ran apt-get install .. and it worked like a charm...
now i've got the basic libraries.

this is a great community.
thanks.

Nuttycat

---

### Post by az on 2006-01-20
If you need to compile something with, say, gtk, make sure that you install the -dev package, example: libgtk2.0-dev.  The same goes with any other library.

Each distro names the developmental header packages differently....

---

