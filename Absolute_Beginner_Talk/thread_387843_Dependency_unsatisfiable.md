---
title: "Dependency unsatisfiable?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Somebody-Z on 2007-03-18
Whenever I try to install a package I get some sort of "Error: Dependency Unsatisfiable :" Thing and at the end it is different depending on what package I'm trying to install. I was wondering what exactly does it mean, and how can I make it so that it does install? I'm sure it has something to do with connecting to the internet and downloading something in Ubuntu, but I can't because the computer that is running Ubuntu has no internet.

---

### Post by gameman12 on 2007-03-18
it means that there is a dependency that is needed to install another program. it means there is something that needs to be installed as a prequiste for another program.

i believe you will have to get your internet up and running to fix this. how are you connecting?

---

### Post by Somebody-Z on 2007-03-18
> **gameman12 said:**
> it means that there is a dependency that is needed to install another program. it means there is something that needs to be installed as a prequiste for another program.

i believe you will have to get your internet up and running to fix this. how are you connecting? Right now, I'm on a totally different computer.

But I can't get the internet running on the other computer, because the modem crapped out and I have no money to buy a new one. Also, the person I am trying to fix it for doesn't have an ISP. I don't know if this will help anything, but the things that are unsatisfiable always start with the prefix "lib"

---

### Post by gameman12 on 2007-03-18
oooo that's a mucho bummer.

i was having the same problem but using internet updates for the system, and the package manager cleared up that problem for me.

i know this isn't what you want to hear, but that's all i've got....sry...

---

### Post by Somebody-Z on 2007-03-18
Well, after some googling I found this > [http://packages.ubuntu.com/edgy/libs/](http://packages.ubuntu.com/edgy/libs/)

And some explanations. Somewhere I read that you could get these on a CD, but I'm not sure where I could do that.

---

### Post by Somebody-Z on 2007-03-19
Anyone?

---

### Post by gameman12 on 2007-03-19
if ur going to use the cd, you can use synaptic but make sure the repositories for the ubuntu cd are enabled.

this is from one of my threads

> You can however enable the install cd as a source in your sources.list.

[# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Alpha i386 (20070215.2)]/ feisty main restricted]
Remove the # from the beginning of the line and pop in the cd-rom.

You'll find your sources.list with
Code:

gksudo gedit /etc/apt/sources.list



---

