---
title: "Installing Software directly off of the web"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by transdink on 2007-07-15
I am trying to install Crossover-standard on my feisty fawn.  I downloaded the file in Firefox, and it appeared on my desktop.  I double clicked and gedit opened and told me of a language problem.  I just want to install it.  Help! I have installed many things using Ubuntu's tools, but I am at a loss with the .sh file.

---

### Post by machoo02 on 2007-07-15
in a terminal type in:```
sh install-crossover-version.sh
```replacing version with whichever version you purchased/downloaded

---

### Post by transdink on 2007-07-15
I get a message  sh: can't open install-crossover-standard-6.1.0.sh

---

### Post by machoo02 on 2007-07-15
What was the language problem that you got?  Also, be sure to navigate to your desktop folder in the terminal```
cd Desktop
```You could also try setting the script as executable as well before running it to see if that helps (although I don't remember having to do that when I installed crossover):```
chmod u+x install-crossover-standard-6.1.0.sh
sh install-crossover-standard-6.1.0.sh
```

---

### Post by avik on 2007-07-16
Also, are you sure you navigated to the Desktop folder first (cd Desktop)?

---

### Post by justgimmeascreen on 2007-09-06
I have also been attempting to install crossover (the demo version).  I am a total n00b at linux, and i barely know what I am doing.    I would like to use Office 2003 for school, and I thought I would give the CodeWeavers demo a try.  I tried OpenOffice, but Open Office Presentation isn't quite cutting it.  

i downloading the DEMO directly from CodeWeavers and followed the instructions per the website.


Here is the code I used:
> 
cd Desktop
sh install-crossover-demo-6.1.0.sh

This is what came back:
> 
sh: Can't open install-crossover-demo-6.1.0.sh

Can someone please enlighten me to what may be my trouble?  oh, and please break it down for the layperson.  I am a biology geek and not a computer geek.

PS:  I also tried this, (run from Desktop directory)

IN:
> 
chmod u+x install-crossover-demo-6.1.0.sh

OUT:
> 
chmod: cannot access `install-crossover-demo-6.1.0.sh': No such file or directory

---

### Post by justgimmeascreen on 2007-09-06
OMG, I am such an idiot!  

should have been:

> sh install-crossover-standard-demo-6.1.0.sh

works fine now

:guitar:

---

