---
title: "ubuntu 5.10"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by sanozuke on 2008-02-03
I have a pentium III, (old pc, very old), only with a compact disck and a floppy a:  . And in my house the system is ubuntu 5.10, and i don't mind.
Ubuntu 5.10 is the best :lolflag: .
What i want to know is how to unzip a folder
Where is the c compliler
How to install the new firefox in this system.
I tried it but with few results.
Thank's for your reply

---

### Post by theDaveTheRave on 2008-02-03
Sanozuke.

Unziping a folder shouldn't be an issue, you may need to use the command line to do so depending on the type of zip file, also you may need so "sudo" if it is a package download so as it has permisions to write into the required directories for its config fies etc.

I don't know where the "C" compiler is either, but I'm sure a search on the forums for it will tell you where it should be located (most likely in /bin or /etc among other?!).

the new Firefox may not run on a pentium III, I know that the Firefox project has a "lightweight" web browser, but I can't remember the name of it. but from memory I think it may come "budled" in with one of the lightweight x-window systems such as fvwm

good luck.

Dave

---

### Post by Rocket2DMn on 2008-02-03
To get everything you need to compile programs, including things you've written yourself, you need to install build-essential which is a metapackage that has all the compilers and correct libraries with it.
```
sudo apt-get install build-essential
```
Your 5.10 system is no longer supported, so they will not post real updates to the repositories anymore.  Standard release of Ubuntu only have an 18 month support cycle.  It is really tough for us to offer help on systems that aren't officially supported anymore, so we suggest that you upgrade to a new distribution, it should work OK on that computer, most definitely if you go with 6.06 - Dapper Drake (LTS - long term support), but I would recommend getting the next LTS, Hardy Heron, due to be delivered in April.

---

### Post by zvacet on 2008-02-03
For unziping files 

```
sudo apt-get install rar unrar p7zip p7zip-full
```


once when you have this installed just right click on file you want to unzip and select **unpack here**.

For upgrading Firefox try [this](http://ubuntuzilla.wiki.sourceforge.net/?f=print).

---

### Post by sanozuke on 2008-02-04
I have a pentium 3 pc, and it has a drive A: and a compact disk CD, that i doesn't record.
I found out about fluxbuntu, but I don't know if they send it to my house with out paying.
Fluxbuntu is light version of ubuntu.

---

### Post by sanozuke on 2008-02-04
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuguide.org/wiki/Ubuntu_pt](http://ubuntuguide.org/wiki/Ubuntu_pt) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				If you know very well ubuntu  5.10 and know's ubuntu 5.10 help files and guides see this page to lear a new language, only if you what to learn:

[http://ubuntuguide.org/wiki/Ubuntu_pt](http://ubuntuguide.org/wiki/Ubuntu_pt)

if you don't what  to learn Portuguese don't go to that page.

---

