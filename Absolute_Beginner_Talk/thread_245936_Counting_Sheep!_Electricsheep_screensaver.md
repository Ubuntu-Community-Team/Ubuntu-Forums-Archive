---
title: "Counting Sheep! Electricsheep screensaver"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Sprogg2001 on 2006-08-28
Someones going to tell me this is a stupid question to ask! but its like licking your elbow you cant help but do it :p 

Here goes,

_**Can you run the electric sheep screensaver on VMware'd ubuntu,**_  

I get the following when I do try 

desktop:~$ sudo apt-cache install electricsheep
E: Invalid operation install

(question what the hell is the E: bit?)

and how does apt know which package to install 32 or 64 I run 64bit will it alway run 64 bit packages or does it run 32 bit by default???

And why does apt-cache search - SUCK big time I mean if you searched for any of the below

electric - addons for emacs
Sheep- nothing
electric sheep - nothing
electric_sheep -nothing
screensaver - a few apps but no electric sheep. 

I didnt try goat or pig yet maybe that would work? ](*,) 


ok sorry questions over.

---

### Post by mcduck on 2006-08-28
First, you may need to enable universe&multiverse repositories. [https://help.ubuntu.com/community/Repositories/Ubuntu#what]("https://help.ubuntu.com/community/Repositories/Ubuntu#what")

Then the command to install stuff is apt-get, apt-cache only shows info about packages.

'sudo apt-get install electricsheep'

---

### Post by Sprogg2001 on 2006-08-28
thank you spot on got it to install, although Im still confused about apt does it automaticaly select 64bit packages for my box or can it use 32 bit packages as well?

---

