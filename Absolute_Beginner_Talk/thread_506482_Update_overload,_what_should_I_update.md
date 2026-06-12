---
title: "Update overload, what should I update?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by bokorpop on 2007-07-21
Every time I login to Ubuntu, there are boatloads of updates ready for mme to install. I have no idea what any of these really do, as I am a non technical person. Should I just trust Ubuntu and say yes to updating everything, or should I basically not update anything unless I fully understand the update. 

I am afraid of clogging up my memory with uselss updates, but also afraid of missing important things which mgiht improve my sytem.

---

### Post by forestpixie on 2007-07-21
have you installed any of them - or does the list keep getting longer

---

### Post by davidjmayo on 2007-07-21
The updates are security patches or bug fixes from ubuntu so you should download them if you have broadband (it's currently 150-170MB so not recommended on dial up)

They don't go to memory they are saved on your hard drive.

After that you will only see the new updates which are usually quite small.

So the bottom line is YES accept them.

---

### Post by AlexenderReez on 2007-07-21
you can always clean your system with 
> sudo apt-get autoclean

> sudo apt-get autoremove

:)

---

### Post by Old Pink on 2007-07-21
Yeah, non of them are going to do any harm, think about it, why would there be any that did harm? ;) 

If you have the connection for them, get it done, only takes 30 minutes or so on a low level broadband connection. :D

---

### Post by bokorpop on 2007-07-22
Im not thinking they are going to do harm, rather I think they are taking up precious hardrive space. To the poster who suggested I rtun "sudo apt-get autoclean" what exactly does that do?

---

### Post by AlexenderReez on 2007-07-22
> **bokorpop said:**
> Im not thinking they are going to do harm, rather I think they are taking up precious hardrive space. To the poster who suggested I rtun "sudo apt-get autoclean" what exactly does that do?

it clean old software installer that you doesn't need anymore.....
:)

---

### Post by pyros on 2007-07-22
> **bokorpop said:**
> Im not thinking they are going to do harm, rather I think they are taking up precious hardrive space. To the poster who suggested I rtun "sudo apt-get autoclean" what exactly does that do?

it helps to understand a bit about the apt technology behind the updates: in a nutshell, the updates will replace old versions of the same packages, so you aren't really adding things so much as replacing them. apt keeps a cache of the installed programs on your system, but they can be removed with the "autoclean" command. The autoremove command is useful, but doesn't really apply if you are just installing updates. Often, when you install a software package, it will need other programs installed so that it will work. If you remove the inital package, the additional packages that were installed will still be on the system. the autoremove command looks for those additional packages and removes them.

---

### Post by wak_maximus on 2007-07-22
i have a little similar to this problem..
do i need to update software provided by software manager in Ubuntu?
is it neccessary??

---

### Post by AlexenderReez on 2007-07-22
> **wak_maximus said:**
> i have a little similar to this problem..
do i need to update software provided by software manager in Ubuntu?
is it neccessary??

it is not necessary but if you are using stable version then it is better to upgrade your software...latest stable software mostly has more feature than the older:)

---

### Post by wak_maximus on 2007-07-22
i cannot download because my internet connection down..
can i download it manually,and install??

---

### Post by AlexenderReez on 2007-07-22
[aptoncd]("http://aptoncd.sourceforge.net/") is your solution...hm..as far as i know the nearest repo from Malaysia is in Indonesia :) .read manual guide after install it
> sudo apt-get install aptoncd

---

### Post by Old Pink on 2007-07-22
The updates, are quite literally updates.

They update software on your computer, replacing/overwriting/patching the older version. You're not using the same space again, there may be a tiny little more/less space used with version changes, but really it shouldn't take any space at all.

Of course, the downloaded .deb installation files will take up temporary space, but once they've been installed and you've rebooted they'll be removed. :)

---

