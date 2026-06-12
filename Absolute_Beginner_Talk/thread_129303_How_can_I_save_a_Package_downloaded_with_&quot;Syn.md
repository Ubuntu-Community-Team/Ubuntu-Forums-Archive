---
title: "How can I save a Package downloaded with &quot;Synaptic Package Manager&quot;"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-13
Hello all!

I downloaded a Package (the "Mozilla-mplayer plugin") through the "Synaptic Package Manager".

I would like to keep the "Downloaded" Package, in case in future I need to clean install Ubuntu again.
In such a case, I do not want to "Download" again & again, the same Packages I have already downloaded in the past.

In which directory does "Synaptic" keep downloaded packages so that I can go and make a copy of it & put it in my preferred Backup directory?

Thank you!

---

### Post by mcduck on 2006-02-13
Apt-get/Synaptic keeps it's file cache in /var/cache/apt.

here's also something that might interest you. It's about how you can create a CD of your files and use that to install packages to other computers: [https://wiki.ubuntu.com/AptMoveHowto]("https://wiki.ubuntu.com/AptMoveHowto")

---

### Post by bonzodog on 2006-02-13
While I can understand what you are saying, it makes little sense to do it that way. It is more efficient to download the software that you need from synaptic, as synaptic also installs dependencies as well. But in case you are interested, look in /var/cache/apt/archives - this has EVERY package that you have installed so far, including those used in initial install.

---

### Post by dvarsam on 2006-02-13
You Said:

[QUOTE=bonzodog]While I can understand what you are saying, it makes little sense to do it that way.
It is more efficient to download the software that you need from Synaptic, as Synaptic also installs dependencies as well. [/QUOTE]

Ok, so you are saying that Synaptic also installs Dependencies...

That is understandable.

However:

1. Are these Dependencies included (incorporated) in the ".deb" file that has 
    downloaded?

**OR**

2. A different ".deb" file is also downloaded in my PC for which I was not informed 
    at all?


**Cause:**
1. If it is the first case:
    That is OK for me.
    In any case, I am not trying to avoid using Synaptic, I just do NOT want to 
    download things again & again. I want to experiment with the programs I need 
    on my system & then perform a clean install for the ones I want.

2. If it is the second case:
    That could be dangerous. To download & install files I was never informed 
    about...?
    At the same time, I do NOT know which additional files I am looking for to 
    Backup...
    In this case, how can I find which additional Dependency files are needed to be 
    installed to Back them up too?
    At the same time (if this is the case), Iet me suggest to programmers to make 
    things easier for us, because:

    What if I want to install the SAME program (for example) in 10 company 
    computers?
    
    You are asking me to download the SAME program with Synaptic 10 times, from 
    10 diff PC's - which are located in 10 diff locations within the company?
    
    And what if I do NOT want some of the PC's to have access to the Internet?
    So, in this case you are telling me:
    "Do NOT install a program on a PC NOT connected to the Internet"?
    **OR**
    "Setup 10 diff PCs to access the Internet & then trash the 10 setups you have 
    created to prevent internet access for those 10 PCs"?

    And repeat this again & again every time I have something NEW to install...


Oh come on, what is the case?

And what is the solution?

---

### Post by az on 2006-02-13
Maybe this is what you want:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by carlosqueso on 2006-02-13
dvarsam:

Neither is truely the case.   Linux is set up a bit different than windows, as different programs need other programs to run.  (Actually, windows is set up the same way, but most programs just install a new copy of their dependencies). These programs are called dependencies.  They are not contained in the .deb file that you installed and apt and synaptic always ask before they install a dependency.  However, you may have installed the dependency in the base install, or when installing somewhere else. 

What this means to you: you can try to install the .deb if you want, because it knows what its dependencies are and won't install if you try to install it, but it very well may be too much trouble.   You should do what azz says, but I wanted to explain why.

EDIT: if you want to find out about the dependencies of a .deb as well as a bunch of other info, you can type ```
dpkg -I <name of package>
``` Remember to use a capital I not a lowercase i or you'll install the package (you don't want to do that)

---

