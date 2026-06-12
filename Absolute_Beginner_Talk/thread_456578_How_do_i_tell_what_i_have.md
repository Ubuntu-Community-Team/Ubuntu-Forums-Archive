---
title: "How do i tell what i have?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-05-27
hey guys! to start, i'd just like to say thanks for all the support so far... I'm still a linux n00b but at least I'm not deadly terrified of the command console anymore :D

so.

I'm taking a computer science course next semester and i thought i would pre-empt it by learning some Java. I've got this book that has helped my friend in the past learn the basics, and it recommends using Jcreator. 

I've gone to the Jcreator website and i now see a lot of different options to download. 

I can get an RPM self extracting file

a normal self extracting file

or the 64 bit versions of each.



1) Is there a way to tell which version i need to download?

2) Is there a super efficient way of using the Command line to download what i need?

---

### Post by drs305 on 2007-05-27
Please tell us what version of Ubuntu you are running and what type of processor and if you give us the site you are visiting for the download we can probably answer your question with more certainty.

If you end up downloading an rpm file you can install a program called ' alien ' that will convert it to a deb file, which is the normal format for downloaded apps in ubuntu.

The normal way of installing a program is through the Synaptic installer: System, Administration, Synaptic, then choose the program from the list. I didn't find jcreator listed there however.

---

### Post by Tyke91 on 2007-05-27
lol... was just coming back to edit that

I'm running feisty and my processor is an intel core 2 duo with 2.13 GHz on each cpu.

---

### Post by drs305 on 2007-05-27
> **Tyke91 said:**
> lol... was just coming back to edit that

I'm running feisty and my processor is an intel core 2 duo with 2.13 GHz on each cpu.

Are you running 32 or 64 bit feisty, and what is the address of the site you want to download from?

Added: Actually, I just went to the jcreator.com web site. Since I think you are talking about a paid program, I think you should aks for opinions on open source programs from experienced members of this forum beofre you purchase it. (I am not experienced about this topic).

---

### Post by Tyke91 on 2007-05-27
ah... this is where i hit the first snag. 

Am I running 32 or 64 bit Feisty?

I don't know. How do i find out?

I'm getting the links to the downloads from this site

[https://sdlc6d.sun.com/ECom/EComActionServlet;jsessionid=895F05666A21F34E7697BC38F7F05F53](https://sdlc6d.sun.com/ECom/EComActionServlet;jsessionid=895F05666A21F34E7697BC38F7F05F53)

---

### Post by Tyke91 on 2007-05-27
Jcreator is completely free.

---

### Post by Tyke91 on 2007-05-27
oops... nvm. Jcreator only works on windows. 

ill just install it normally on windows then. thx anyway :)

---

### Post by Tyke91 on 2007-05-27
You know what... I'm on my windows hard drive right now and it's not nearly as great as the Ubuntu one...


Can anyone recommend a good java IDE that works on linux  (and and also solve my problem about JDK?)

sorry if the above posts confused you... i wasnt installing jcreator, i was trying to install JDK and get the API docs.

---

### Post by joe.turion64x2 on 2007-05-27
> **Tyke91 said:**
> ah... this is where i hit the first snag. 

Am I running 32 or 64 bit Feisty?

I don't know. How do i find out?

I'm getting the links to the downloads from this site

[https://sdlc6d.sun.com/ECom/EComActionServlet;jsessionid=895F05666A21F34E7697BC38F7F05F53](https://sdlc6d.sun.com/ECom/EComActionServlet;jsessionid=895F05666A21F34E7697BC38F7F05F53)
Type in a console:
> uname -a

---

### Post by Tyke91 on 2007-05-27
kk


this is what's come up

2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

---

### Post by joe.turion64x2 on 2007-05-27
> **Tyke91 said:**
> kk


this is what's come up

2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
You are running the 32 bits version, otherwise it would read:
2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 x86-64 GNU/Linux[/QUOTE]

---

### Post by joe.turion64x2 on 2007-05-27
> **Tyke91 said:**
> kk


this is what's come up

2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
You are running the 32 bits version, otherwise it would read:
2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 x86-64 GNU/Linux

---

