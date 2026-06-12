---
title: "KDevelop - configure: error: newly created file is older than distributed files!"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-10-31
I just finished installing Kdevelop on my Kubuntu PC. The first thing I did was to start and build the "Hello World!" project to see if I would get any problems.
Sooooo first it gave me an error which I fixed by installing automake, then another one fixed by installing libtools.
Now I'm getting the following:
```
cd '/home/felipe/C++ Projects/hello1' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && cd '/home/felipe/C++ Projects/hello1/debug' && CXXFLAGS="-O0 -g3" "/home/felipe/C++ Projects/hello1/configure" --enable-debug=full && cd '/home/felipe/C++ Projects/hello1/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
autoheader
automake
autoconf
installing -c
checking whether build environment is sane... 
configure: error: ls -t appears to fail. Make sure there is not a broken
alias in your environment
configure: error: newly created file is older than distributed files!
Check your system clock
*** Exited with status: 1 ***

```

Don't really know how to fix this problem, and google isn't really giving me any solutions, though I'll keep looking.

---

### Post by Dual Cortex on 2006-11-02
... I guess this doesn't occur often.

---

### Post by Dual Cortex on 2006-11-03
seems like im better off installing eclipse

---

### Post by Dual Cortex on 2006-11-06
Been some time, but I'm giving this one more chance!
Though maybe I should check out Kdev's support...

---

### Post by Dual Cortex on 2006-11-06
Got it working... google link in first page that I hadn't checked out (after having gone until about page 10 or so)

My directory's name contained a space in it... making it one word fixed the error.
ALl I got to say is: hmmm sure... 
Anyway, back to checking Kdevelop out.

---

### Post by Klondikes on 2007-09-04
This is late, but I wanted to mention that I also ran into the same exact problem. I swore it was my profile b/c when I added another user or even logged in as root and compiled a helloworld app it would work. But not my own user. Turns out the project in my users was in a folder called "My Documents". The other user I created for testing had the project in their home. Everything is so much clearer now.  

It all boils down to a space. WTF?? Is this not a bug in ls -t??

I think personally moving from windows is the root of the problem. I'm used to having folders named "My This/That/Other" so naturally I'll start naming folders in Ubuntu the same way. But I guess that's out the door too. O well. Rock on! :guitar:

I have a small announcement. *cough* Ahem, your attention please!

When compiling projects in KDevelop (or any other application), and the program spits out the following error message, please read the statement in large bold red letters below the code snippet.

```
checking whether build environment is sane... 
configure: error: ls -t appears to fail. Make sure there is not a broken
alias in your environment
configure: error: newly created file is older than distributed files!
Check your system clock
*** Exited with status: 1 ***
```

[COLOR="Red"]**[SIZE="7"]DO NOT PUT SPACES IN YOUR DIRECTORY NAMES![/SIZE]**[/COLOR]

Thank you for your corporation.

---

### Post by tessmonsta on 2008-02-23
Yes, that's sound advice, but shouldn't kDevelop *warn you* that using spaces in the directory name can be a problem?

---

### Post by Z.Z. on 2008-02-28
hi!
so useful! 
thanks!

---

### Post by miguelf on 2008-06-24
Hi:

I made the same mistake, and it takes to me all day try to resolve that problem........that Red Advice i so useful!!......Thanks to everybody in this forum...=D>

Bye.

---

### Post by rajputrajat on 2008-06-25
Thanks Klondikes !!!
u saved my day....:guitar:

---

