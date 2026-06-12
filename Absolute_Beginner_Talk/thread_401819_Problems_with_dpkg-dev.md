---
title: "Problems with dpkg-dev"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by NewJack on 2007-04-05
I am having problems installing dpkg-dev.  For some reason when I try to install it from Synaptic I get the following error:

dpkg-dev: Depends: dpkg (>=1.13.20) but 1.13.11ubuntu7 is to be installed

Apparently, it is telling me I need dpkg ver. 1.13.20.  I currently have dpkg 1.13.11 installed, How can I get it up to version 1.13.20 seeing as how it is not available to me through Synaptic?

Thanks in advance!!!
Joe

---

### Post by cantormath on 2007-04-05
> **NewJack said:**
> I am having problems installing dpkg-dev.  For some reason when I try to install it from Synaptic I get the following error:

dpkg-dev: Depends: dpkg (>=1.13.20) but 1.13.11ubuntu7 is to be installed

Apparently, it is telling me I need dpkg ver. 1.13.20.  I currently have dpkg 1.13.11 installed, How can I get it up to version 1.13.20 seeing as how it is not available to me through Synaptic?

Thanks in advance!!!
Joe

why not use the dpkg-dev 1.13.11?

---

### Post by NewJack on 2007-04-05
I would but for some reason it is not currently installed and when I try to install it, I get the above error message and won't install.

---

### Post by cantormath on 2007-04-05
oh, I see..

not to get into your business but why do you need dpkg?  it is usually installed when you install ubuntu.  

You might want to add some of the other repositories, universe, multiverse, etc.  But regardless, without changing the repo's the dpkg and dpkg-dev (ver 1.13.11) are in there,  if you see the picture below, I have them in my screen shot:

[IMG]http://img.photobucket.com/albums/v446/cantomath/dpkg.png[/IMG]

tell me if you see those.....as you can see I have them installed....

---

### Post by NewJack on 2007-04-05
Out of the 3 you are showing, I only have dpkg.

---

### Post by cantormath on 2007-04-05
add the universe/multiverse repository

---

### Post by NewJack on 2007-04-05
**PROBLEM SOLVED!!!**

When I went to check my repositories, I noticed that for some reason, the Edgy CD repositories were added to my list (I never added them manually).  This must have happened when I tried out the Edgy LiveCD.  When I unticked that box in the repository list, it allowed me to install dpkg-dev with no error message.

Thanks Cantormath, I wouldn't have thought to check there.

---

### Post by cantormath on 2007-04-05
> **NewJack said:**
> **PROBLEM SOLVED!!!**

When I went to check my repositories, I noticed that for some reason, the Edgy CD repositories were added to my list (I never added them manually).  This must have happened when I tried out the Edgy LiveCD.  When I unticked that box in the repository list, it allowed me to install dpkg-dev with no error message.

Thanks Cantormath, I wouldn't have thought to check there.

thats awesome.....

I thought those packages were in the standard repos......good luck......

---

