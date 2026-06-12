---
title: "Wine with Ubuntu"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Spline64 on 2008-04-04
Hello All,

I was wondering if someone out there has written an install / config guide for using Wine with Ubuntu or do I just download Wine and read the directions lol. I am completely new to Ubuntu and not sure if there are subtle differences between the different distros of Linux that would require you to install Wine differently. Thought I'd ask before diving in.

And just on a side note, I was impressed with how easy Ubuntu was to install. I am soooo sold on this OS. :biggrin:

---

### Post by nathansoz on 2008-04-04
Wine is fairly simple to use, and with many applications does not require much setup. In other cases, it can be tricky to get some applications working. In other cases, it wont work for an application. Anyways:

1. Install wine using synaptic or apt-get, your preference
2. To run a program or installer type
```
wine (program path)
```
in a terminal
3. If you have trouble with different applications, search around to find out if it is supported.

EDIT: Synaptic package manager is in your System-Administration manager.

I think you can also type 

sudo apt-get install wine 

into a terminal

---

### Post by Crafty Kisses on 2008-04-04
> **Spline64 said:**
> Hello All,

I was wondering if someone out there has written an install / config guide for using Wine with Ubuntu or do I just download Wine and read the directions lol. I am completely new to Ubuntu and not sure if there are subtle differences between the different distros of Linux that would require you to install Wine differently. Thought I'd ask before diving in.

And just on a side note, I was impressed with how easy Ubuntu was to install. I am soooo sold on this OS. :biggrin:

This [Link]("http://www.winehq.org/site/howto") may help you.

---

### Post by Tatty on 2008-04-04
```
sudo apt-get install wine
```

Its in the repos.  Thats your best bet, because then synaptic will take care of all the dependencies for you.

---

### Post by Spline64 on 2008-04-04
Wow! Thanks all for the help!!

Spline64

---

### Post by medley on 2008-04-04
> **nathansoz said:**
> Wine is fairly simple to use, and with many applications does not require much setup. In other cases, it can be tricky to get some applications working. In other cases, it wont work for an application. Anyways:

1. Install wine using synaptic or apt-get, your preference
2. To run a program or installer type
```
wine (program path)
```
in a terminal
3. If you have trouble with different applications, search around to find out if it is supported.

EDIT: Synaptic package manager is in your System-Administration manager.

I think you can also type 

sudo apt-get install wine 

into a terminal

Actually, these days I've found that you can just run the .exe without specifying wine, and Kubuntu figures out that it needs to invoke Wine. I installed Photoshop CS this way, and it was no different than installing it on Windows.

---

