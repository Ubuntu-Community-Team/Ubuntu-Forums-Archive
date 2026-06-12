---
title: "How to disable autorun?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by slavisa4ec on 2007-04-02
Hello everyone :D

I`am new in Ubuntu, last night I put it on my machine... I have so many questions to ask you people, I dont from which one to start... OK, first this, how to turn off autorun in Ubuntu?

---

### Post by chewearn on 2007-04-02
Welcome to the community! :popcorn:

Not sure what autorun are you talking about, can you elaborate?

---

### Post by slavisa4ec on 2007-04-02
Tnx for welcome :D

Autorun for cd and dvd? btw, i am totally new in linux, so please have patient. Tnx in advance :D

---

### Post by chewearn on 2007-04-02
Go to here:
Top panel Menu > System > Preferences > Removable Drives and Media

---

### Post by slavisa4ec on 2007-04-02
Thats it, tnx!

Second question, i have installed Gnome Baker for burning cd`s and dvd`s and i`am not quiet satisfied (sorry about my english), which program you use?

Third: how to remove efects in linux, efects like when i click on minimize button? And when i wanna select multiple files that colored box that apear?

4th: Thunderbird is ok for mail?

5th: services, where can i find some discriptions about started services in linux so i could remove ones i dont use, like bluetooth etc etc...

---

### Post by chewearn on 2007-04-02
> **slavisa4ec said:**
> Second question, i have installed Gnome Baker for burning cd`s and dvd`s and i`am not quiet satisfied (sorry about my english), which program you use?
I rarely burn any cd/dvd; the last time I did was in WinXP, so someone else in this forum will have to answer this one.

> Third: how to remove efects in linux, efects like when i click on minimize button? And when i wanna select multiple files that colored box that apear?Open a terminal window (Applications > Accessories > Terminal).  Type in:
```
gconf-editor
```This will launch Gnome Configuration Editor; I have not find the need to tinker with the effects, so have no experience to give you here.  You will have to explore the relevant settings yourself (or search this forum). 
Be careful though, the gconf-editor is similar to Registry Editor (regedit.exe) in WinXP, so be carefui of your tinkering.

> 4th: Thunderbird is ok for mail?I tried Evolution for awhile, find it too bloated for simple email use.  It is meant to be an all-in-one solution like Outlook or Lotus Notes (with calendar, meetings, etc; on top of email).  I have since switched to Thunderbird (I am also using Thunderbird in WinXP)

> 5th: services, where can i find some discriptions about started services in linux so i could remove ones i dont use, like bluetooth etc etc...Haven't been playing around with this one either; no experience or pointer to give you; sorry.

---

### Post by slavisa4ec on 2007-04-02
I have tried that gconf-editor but that is complicated for me, i thought something like right click on my computer pa that visualization card in XP where i can what i want and what i dont want

My configuration:
MSI K7N2-Delta2
AMD Sempron 2600+
1GB DDR1 on 200Mhz
Radeon 9550

and Ubuntu is wery sLoWWWWW, have you done something to speed up your ubuntu?

---

### Post by 23meg on 2007-04-02
> 
Second question, i have installed Gnome Baker for burning cd`s and dvd`s and i`am not quiet satisfied (sorry about my english), which program you use?


Check out Brasero, Graveman and K3B.

> 5th: services, where can i find some discriptions about started services in linux so i could remove ones i dont use, like bluetooth etc etc...

System / Administration / Services

---

### Post by chewearn on 2007-04-02
> **slavisa4ec said:**
> I have tried that gconf-editor but that is complicated for me, i thought something like right click on my computer pa that visualization card in XP where i can what i want and what i dont want

My configuration:
MSI K7N2-Delta2
AMD Sempron 2600+
1GB DDR1 on 200Mhz
Radeon 9550

and Ubuntu is wery sLoWWWWW, have you done something to speed up your ubuntu?

I am guessing your desktop is slow because you have not install ATI binary driver.  I'm not up-to-date on the ATI driver installation (I have gone nvidia only).  There should be a how-to page somewhere in this forum.

---

### Post by kinson on 2007-04-02
> **slavisa4ec said:**
> Thats it, tnx!

Second question, i have installed Gnome Baker for burning cd`s and dvd`s and i`am not quiet satisfied (sorry about my english), which program you use?



Try K3B. I've installed GnomeBaker before, but I really didn't like it. K3B so far has been good. Give it a try :)

Cheers,
Kinson

---

### Post by slavisa4ec on 2007-04-02
i have installed ati driver using synaptic, but i dont know have i installed that binary driver, i will look over the forum...

---

### Post by johnny4north on 2007-04-02
K3B is the better burner app.  :)    thanks Ubuntu

---

### Post by slavisa4ec on 2007-04-02
I`ve tried this K3b, but every time I check verifying data, K3b says that cd burning failed, even though i can copy from cd to hdd... Anyway, K3b is better then Gnome Baker, tnx for software tip :D

---

