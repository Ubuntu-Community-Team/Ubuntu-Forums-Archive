---
title: "Where is partion manager"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-06-28
I remember using it when i had the live cd. But I cant remember where its located. Please anyone wanna tell. I couldent find it by using the search engine in Ubuntu.

Little OT, but I remember seing someone had devolped something for linux, so it looked like windows. Anyone know what this is? Link?

---

### Post by x64Jimbo on 2006-06-28
run this from the command line:
sudo qtparted

---

### Post by jincast90 on 2006-06-28
It says command not found when you type that

---

### Post by classem2003 on 2006-06-28
Install it with synaptic  or with the command line

sudo apt-get install qtparted

---

### Post by richbarna on 2006-06-28
[QUOTE=x64Jimbo]run this from the command line:
sudo qtparted[/QUOTE]

Actually, I think it's :-

> gksudo gparted

---

### Post by jincast90 on 2006-06-28
Since we are in this partion things, can someone tell me how to acces my partion where Windows is installed on. I can se it from the Machine menu, but when I try to acces it, it tells me I dont have the rights to acces it.

---

### Post by bruce89 on 2006-06-28
[QUOTE=x64Jimbo]run this from the command line:
sudo qtparted[/QUOTE]
QTParted is the KDE program, not everyone here uses KDE.

I have noticed people giving advice for the environment that they use, and they are not aware that other people may not actually use the same one as them.

---

### Post by richbarna on 2006-06-28
[QUOTE=bruce89]QTParted is the KDE program, not everyone here uses KDE.

I have noticed people giving advice for the environment that they use, and they are not aware that other people may not actually use the same one as them.[/QUOTE]

You're right, in which case it would be :-

> kdesu qtparted

---

### Post by bruce89 on 2006-06-28
Neither QTParted or GParted are installed by default, so it is a bit pointless trying to run them.  To start QTparted in KDE, you would use ```
kdesu qtparted
```

---

### Post by jincast90 on 2006-06-28
I have to bump this thread just to ask about this again :)

Little OT, but I remember seing someone had devolped something for linux, so it looked like windows. Anyone know what this is? Link?

---

### Post by Adjutant on 2006-06-28
Hey guys, I'm having problems finding the partition manager myself. I've just reinstalled my Ubuntu using the Live CD... but it's not there anymore-.

My previous installation did have the partition manager included and everything. It came by default. Now I can't find it. I tried everything and it always says it doesn't exist, it's not in the repositories, it's no where. I checked Synaptic and there's no such thing as 'gparted'. There's only a program called 'parted' that I tried to use but does nothing....

What's going on here???

---

### Post by coffeecat on 2006-06-28
[quote=Adjutant]I checked Synaptic and there's no such thing as 'gparted'.[/quote] 
I've just checked Synaptic (in my Dapper laptop install), and gparted is definitely there. Not only that, I installed gparted from Synaptic in my other Dapper installation. Did you put 'gparted' in the search facility?

Just to repeat and clarify what I think has been said before -  Gparted can be found under System > Administration on the live Ubuntu Dapper, but it doesn't get installed. You have to install it later from Synaptic (or apt).

---

### Post by Adjutant on 2006-06-28
See attachment. I definately have not been messing with the repositories and definately remember Gparted being installed while installing Ubuntu. Think I'll reinstall again but with the alternate CD...

---

### Post by coffeecat on 2006-06-29
That's very strange. I don't think re-installing from the alternate CD will help you because I installed from the live CD on both machines. And I don't understand what you mean by remembering Gparted being installed while installing Ubuntu. As far as I remember, the install CD just installs a pre-defined package for you.

Have you tried doing reload in Synaptic. What about your sources.list?

Here's my Symaptic:

---

