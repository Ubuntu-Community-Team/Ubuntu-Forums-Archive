---
title: "ndiswrapper"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Professorb on 2007-06-10
I need some help installing ndiswrapper.

I've unzipped it and I've run make on it but all I get is a long list of errors.

I'm not installing a wireless card, I'm trying to get the ethernet controller to work because it won't and the manufacturers cd and website only contain drivers for windows.

How do I compile and install the program?

---

### Post by Kobalt on 2007-06-10
Did you install build-essential ? ```
sudo apt-get install build-essential
```

---

### Post by Professorb on 2007-06-10
No, tried it then and it said "E: Couldn't find package build"

---

### Post by Malibu Illusion on 2007-06-10
There's a hyphen between "build" and "essential".

---

### Post by Professorb on 2007-06-10
Yeah I included that, forgot to type on to here.

---

### Post by dmfield on 2007-06-10
You could save yourself some bother, and install ndiswrapper using automatix. from getautomatix.com it should also give you a nice gui to install your ethernet card from. (please excuse the short post, typing this on a pocket pc on a train)

---

### Post by Professorb on 2007-06-11
Tried that.

But you need an active internet connection in order to install the auto program. So until I install ndiswrapper I can't get my ethernet to work, thus can't get on the internet.

So back to the drawing board.

---

### Post by ugm6hr on 2007-06-11
Does ndiswrapper work with wired ethernet?  

Might be worth finding your card on their wiki before wasting time with it:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

I'm surprised that your ethernet does not work in Linux - are you sure it's a driver issue?

If you haven't already - in Terminal try *lspci* and*ifconfig* to get information regarding it.

---

### Post by Professorb on 2007-06-13
Yeah it says on their project page that it works for some ethernets as well, but it can be hit and miss.

---

