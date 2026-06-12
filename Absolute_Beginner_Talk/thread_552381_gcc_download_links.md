---
title: "gcc download links"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by sazan on 2007-09-16
please provide me wid links where i can download gcc ......

---

### Post by Jawsman on 2007-09-16
Doesn't it come with Ubuntu by default?

---

### Post by sazan on 2007-09-16
didnt install gcc before and dont hav the cd now.... can u tell me the steps that i can follow in terminal so that it can download from net...

---

### Post by Luinar on 2007-09-16
Okay, first you want to go to System > Administration > Software Sources. In there, you want to uncheck the boxes under "Installable from CD-ROM/DVD" in order to stop things trying to install from the CD. Make sure all of the boxes listed under "Downloadable from the internet" are checked.

Then, open up a terminal and do:

```
sudo apt-get update
```

to refresh the repository information and then do:

```
sudo apt-get install gcc
```

and that should install gcc for you.

---

### Post by jordanmthomas on 2007-09-16
Yep, installing from the repositories is your best bet.  After all, how would you compile gcc without gcc?  (You could do it, of course, but it's complicated and involves getting someone else's compiled gcc to compile yours, which then compiles itself)

---

### Post by sazan on 2007-09-16
cant find software sources in my administration section... !!!:(

---

### Post by Luinar on 2007-09-16
Hmm, odd, I thought it should have been there by default. I may have added it onto my menu though, so maybe my mistake. Oh well, open Synaptic Package Manager and go to Settings > Repositories and that will give you the Software Sources window.

You should then be able to do the rest of the commands, or if your prefer, click the Reload button in Synaptic, then search for gcc and install it via Synaptic.

---

### Post by nonewmsgs on 2007-09-16
are you using 7.04?

did gcc not come with sudo apt-get install gcc

just out of curiosity, why are you after gcc?

---

### Post by sazan on 2007-09-16
nah not using 7.04 .. . 

i need gcc for compiing some packages .....

---

### Post by louieb on 2007-09-16
Just my two cents. Your probably going to want more than the gcc compiler: get the build-essential meta package.

---

### Post by sazan on 2007-09-16
where wil i get that build -essential metadata ??

---

### Post by jordanmthomas on 2007-09-16
The same way as you get gcc, just do this instead of apt-get install gcc:
```
sudo apt-get install build-essential
```

---

