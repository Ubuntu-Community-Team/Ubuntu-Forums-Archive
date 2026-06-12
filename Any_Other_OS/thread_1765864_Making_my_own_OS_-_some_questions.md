---
title: "Making my own OS - some questions"
date: 2011-05-23
forum: Any Other OS
---

### Post by Arightwizard on 2011-05-23
Hey, whatsup.
I've decided I might do a side-project of making an OS. (Nothing too big, not like windows 7 or something but better than something with just a "command prompt" and that's it. [Aka it'll have a GUI])

I haven't decided on even the basics, so I'm asking for your personal opinions on which would be the best and/or easiest way (I don't necessarily want to go the easiest direction, but if the easiest is more than good enough, then why not? Right?)

So far I've been working with the Cosmos kernel (For those who don't know, it's ***C# Open Source Managed Operating System***, but it lets you code (the entire OS!!) in either C# or VB.net), but it hasn't been working. It seems it's made to run only on a virtual machine..

Should it be linux-based? Or is there any way I could code all/most of the OS in a language like VB.net, Ruby, PHP (This would be _***epic***_ if I could do a whole php/html OS. But I doubt it.). Those are the 3 languages I'm most comfortable with (Never really ventured out to complex languages like C++ or anything. Just stuck with the lower level, but useful things)

If you have any other info/ideas, let me know! I've already decided on a name (I think. I might change it) But any other ideas are welcome!

Thanks!

---

### Post by Barrucadu on 2011-05-25
You will definitely need some knowledge of assembler (there are some things that simply cannot be done (on real hardware) in a high level language), so no, it's not possible to do it all in something like C# or PHP. Those languages themselves are very abstracted away from the hardware, and have their respective runtimes implemented in something lower level - so you will probably need to use C or C++ (it can be done with other languages, but not as easily).
Additionally, if you cannot handle C (and I mean no disrespect by this), I don't think you're ready to embark on an OS project, as C is significantly more simple than writing an OS. Additionally, most of the available documentation and help online assumes you are using C.

The osdev wiki is very good: [http://wiki.osdev.org/Main_Page](http://wiki.osdev.org/Main_Page)

---

### Post by psusi on 2011-05-25
Wow... that is like announcing that you are going to build a lunar lander in your garage on the weekends, but you don't really know anything about jet propulsion other than what you picked up playing with model rockets.

I think what you need to do is just play with linuxfromscratch.org.

---

### Post by helblaze on 2011-05-25
Have you considered messing around with SuseStudio, I believe you still need an invitation, but you can still make a customized distribution.

---

### Post by manzdagratiano on 2011-05-26
I share similar desires, and though I have been with C/C++ for about 10 years now (as well as some assembler), I don't think I understand enough OS stuff to start.

I was thinking of performing a **Linux From Scratch** install on a VM, which would hopefully get me down and dirty with GNU/Linux. I would suggest trying something similar before you embark on this noble venture? :)

---

### Post by galacticaboy on 2011-05-26
> **helblaze said:**
> Have you considered messing around with SuseStudio, I believe you still need an invitation, but you can still make a customized distribution.

You do not need an invitation to SuseStudio, I signed up yesterday, but the only bad thing about SuseStudio, is it seems that your custom OS will be based on Suse... I want something like SuseStudio that is super easy just like SuseStudio that I can build a Debian system with.

---

### Post by DangerOnTheRanger on 2011-05-26
> **galacticaboy said:**
> I want something like SuseStudio that is super easy just like SuseStudio that I can build a Debian system with.

Sorry, such a thing doesn't exist. I think there's something akin to SuseStudio for Ubuntu, but it has a CLI, no GUI.

Linux From Scratch (LFS) is the next best thing. You'll need quite a bit of resolve, though
: The first time I went through it (I've done it multiple times :)), it took me around 25hrs of PC time and a few GBs of HDD space to complete the book.

Granted, LFS is easier than the alternative: I've been working on my C++ OS for a few years on and off, and I don't even have decent memory allocation yet (I DO have a colorful command-line though :)).

Don't worry, OS development just takes some time! If you want to do this, go for it!

> **Barrucadu said:**
> You will definitely need some knowledge of  assembler (there are some things that simply cannot be done (on real  hardware) in a high level language), so no, it's not possible to do it  all in something like C# or PHP. Those languages themselves are very  abstracted away from the hardware, and have their respective runtimes  implemented in something lower level - so you will probably need to use C  or C++ (it can be done with other languages, but not as easily).
Additionally, if you cannot handle C (and I mean no disrespect by this),  I don't think you're ready to embark on an OS project, as C is  significantly more simple than writing an OS. Additionally, most of the  available documentation and help online assumes you are using C.

The osdev wiki is very good: [http://wiki.osdev.org/Main_Page](http://wiki.osdev.org/Main_Page)

+1. The OSDev wiki is my main source of information for "OSDeving", as it's called.
Also, I've seen an OS ([http://code.google.com/p/cleese/](http://code.google.com/p/cleese/), albeit extremely minimal) written in Python, though the developers *did *have to port Python, but it's *possible *to write the bulk of an OS in a high-level language (my OS is written in C++, if you can call that high-level).

All in all, though, Cleese is worth a look if you know Python, and aren't afraid of having to mess with someone else's unmaintained code.

---

### Post by rg4w on 2011-05-26
> **psusi said:**
> Wow... that is like announcing that you are going to build a lunar lander in your garage on the weekends, but you don't really know anything about jet propulsion other than what you picked up playing with model rockets.
I was planning on doing that this weekend.  Is it hard to do?  Do I need to know anything about physics?

---

### Post by manzdagratiano on 2011-05-26
> **DangerOnTheRanger said:**
> Sorry, such a thing doesn't exist. I think there's something akin to SuseStudio for Ubuntu, but it has a CLI, no GUI.

Linux From Scratch (LFS) is the next best thing. You'll need quite a bit of resolve, though
: The first time I went through it (I've done it multiple times :)), it took me around 25hrs of PC time and a few GBs of HDD space to complete the book.

Granted, LFS is easier than the alternative: I've been working on my C++ OS for a few years on and off, and I don't even have decent memory allocation yet (I DO have a colorful command-line though :)).

Don't worry, OS development just takes some time! If you want to do this, go for it!



+1. The OSDev wiki is my main source of information for "OSDeving", as it's called.
Also, I've seen an OS ([http://code.google.com/p/cleese/](http://code.google.com/p/cleese/), albeit extremely minimal) written in Python, though the developers *did *have to port Python, but it's *possible *to write the bulk of an OS in a high-level language (my OS is written in C++, if you can call that high-level).

All in all, though, Cleese is worth a look if you know Python, and aren't afraid of having to mess with someone else's unmaintained code.

Very interesting stuff! I just got into full-blown Python about four months ago... This is a new level!

---

### Post by MBybee on 2011-05-26
> **rg4w said:**
> I was planning on doing that this weekend.  Is it hard to do?  Do I need to know anything about physics?

Nope, just the location of the ER :D

Seriously though - some really good projects have come from deciding to code an OS as a hobby. I did one when I was younger, it was a blast (and I learned a lot).

Here's some good examples to check out:
[http://www.kolibrios.org/](http://www.kolibrios.org/)
[http://www.menuetos.net/screens.htm](http://www.menuetos.net/screens.htm)
[http://etoileos.com/](http://etoileos.com/)
[http://www.haiku-os.org/](http://www.haiku-os.org/)

You'll learn a LOT if you're serious.

---

### Post by smd0665 on 2011-05-30
You could do an Ubuntu minimal install:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This will install the basics without an UI. Then, you can decide what other programs you want and not get a bunch of things you don't want. Ubuntu's package manager will install the dependencies. This is what I've been doing for a while. I like LXDE, but Lubuntu installs things like Chromium (I prefer Firefox) and Totem (I prefer VLC). 

The Arch Linux distro is similar; it is a basic installation. You pick the programs you want after that. I used Arch for a couple of years. It is more hands-on than Ubuntu.

---

