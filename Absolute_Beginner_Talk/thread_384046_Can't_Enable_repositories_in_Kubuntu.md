---
title: "Can't Enable repositories in Kubuntu"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by wheelhorse2347 on 2007-03-14
Hello,
I am a noob to the KDE environment, as well as to Ubuntu all together.  I've messed around with Ubuntu quite a bit and am now dual booting Ubuntu and Kubuntu (Both are version 6.10 with AMD 64 support).  

Anyway, I am trying my best to enable the universe/multiverse repositories.  I tried using 'Adept' but that didn't work for some reason.  I went to 'manage repositories' and there were none there to manage.  I attempted to add a repository via a url, but I believe I messed it up more than it was before.

Now when I attempt to open Adept I get this message.  
"The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem."

I was wondering if anyone could first, help me fix my screw up, and second, how can I get my repositories working?  

Thanks one million!!

Jordan

---

### Post by aysiu on 2007-03-14
Follow these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by orkim on 2007-03-14
> **wheelhorse2347 said:**
> Hello,
I am a noob to the KDE environment, as well as to Ubuntu all together.  I've messed around with Ubuntu quite a bit and am now dual booting Ubuntu and Kubuntu (Both are version 6.10 with AMD 64 support).

There are no differences in Ubuntu and Kubuntu besides the default package sets that are installed.  You can run "apt-get install kde-desktop" (if I remember correctly) to "convert" a Ubuntu desktop to a Kubuntu desktop.  Just FYI.  This is in the FAQ at the Kubuntu site I believe.

> **wheelhorse2347 said:**
> Anyway, I am trying my best to enable the universe/multiverse repositories.  I tried using 'Adept' but that didn't work for some reason.  I went to 'manage repositories' and there were none there to manage.  I attempted to add a repository via a url, but I believe I messed it up more than it was before.

Typically the best package manager for newer users is Synaptic.  You should find it on the menu and its a nice graphical package installation suite.  Repositories can also be managed once you open this application.

> **wheelhorse2347 said:**
> Now when I attempt to open Adept I get this message.  
"The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem."

I was wondering if anyone could first, help me fix my screw up, and second, how can I get my repositories working?

I'm not familiar enough with adept to help you fix your problem.  You might be able to find specific information about it by searching the forums.  

> **wheelhorse2347 said:**
> Thanks one million!!

Jordan

No problem!  I only hope that this information helps!

-orkim

---

### Post by wheelhorse2347 on 2007-03-14
Thank you sooooo much!  I've been trying for hours to fix this 'on my own' hoping that I could gain some satisfaction by doing it myself but obviously it doesn't hurt to ask. 

Thank you.

---

