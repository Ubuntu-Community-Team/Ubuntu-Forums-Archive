---
title: "pidgin"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by tkafik on 2007-10-05
Where i can find pidgin to ubuntu?
How to install this pidgin?

---

### Post by por100pre1 on 2007-10-05
[Here]("http://www.getdeb.net/release.php?id=1462") but I suggest you to wait for Gutsy instead.

---

### Post by tribaal on 2007-10-05
It's pretty easy really:

add the two following lines to your /etc/apt/sources.list file:
```

deb  http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse

```

Then type in the following command:
```
sudo apt-get update && sudo apt-get install pidgin
```

There you go :)

Hope this helped :)

- trib'

---

### Post by Hugolp on 2007-10-05
Pidgin old name was Gaim, but they had to change it due to legal actions.

You have three options right now:

-Use Gaim wich is allredy included in a normal Ubuntu install. (Kopete for Kubuntu).
-Compile Pidgin tar from the pidgin page (can be tricky if you are not very used to linux).
-Wait for Gutsy, the new Ubuntu version that is due 18 of October (thats two weeks) and I believe Pidgin is allredy installed by default.

Hugo

---

### Post by kevdog on 2007-10-05
Compile from source 

Why ??

You get to customize your pidgin and add in things that are not included in the "standard version".  Same with the pidgin plugin pack.  Its not that hard, although shagging down the dependencies can take a while.

---

### Post by tkafik on 2007-10-05
[QUOTE=tribaal;3479384]It's pretty easy really:

add the two following lines to your /etc/apt/sources.list file:
```

deb  http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse

```

where i need to copy this? in which line?

---

### Post by tkafik on 2007-10-05
OK i installed but where is the pidgin now?

---

### Post by por100pre1 on 2007-10-05
> **tkafik said:**
> OK i installed but where is the pidgin now?

It should be under Applications> Internet.

---

### Post by tkafik on 2007-10-05
I need restart?

---

### Post by por100pre1 on 2007-10-05
> **tkafik said:**
> I need restart?

No, no need to restart.

---

### Post by tkafik on 2007-10-05
So, i dont see pidgin only the GAIM

---

### Post by LowSky on 2007-10-05
type pidgin in the terminal

---

### Post by por100pre1 on 2007-10-05
> **tkafik said:**
> So, i dont see pidgin only the GAIM

Let's see where it is (in terminal):

```
which pidgin
```

EDIT: if you get an answer to that command do this:

```
alacarte
``` 

and create a launcher there.

---

### Post by tkafik on 2007-10-05
I typed "which pidgin" and see nothing.
No message

---

### Post by por100pre1 on 2007-10-05
Weird. Maybe Pidgin is now using the gaim launcher, launch gaim to see if it is now Pidgin. :-k

---

### Post by LowSky on 2007-10-05
are you sure you installed it correctly?

Try re-installing it.

---

### Post by kevdog on 2007-10-05
Pidgin is not in the feisty repositories -- just an FYI -- only in Gutsy's.  So if you added those multiverse and universe repositories to your sources list, they are not going to help you.  I installed pidgin from source, and it works great, however it took me a long time to track down all the dependencies.  If you dont want to do this there are a couple options:

1. Precompiled package from: lone wolf
[http://howto.landure.fr/gnu-linux/ubuntu-feisty-fawn-1/software-for-ubuntu-feisty-fawn/pidgin-previously-gaim-on-ubuntu-feisty-fawn](http://howto.landure.fr/gnu-linux/ubuntu-feisty-fawn-1/software-for-ubuntu-feisty-fawn/pidgin-previously-gaim-on-ubuntu-feisty-fawn)
2. There is another precompiled package from getdeb.net

However just a word of caution.  These are third party repositories.  They wont ruin your system, however you might get apt or aptitude complaining time to time about dependency issues, and when upgrades show up to pidgin, you basically have to wait for the repository to update its version which could be a few weeks.

When you compile from source, yes you have to uninstall the old version and then recompile and install the new version, however at least you dont have to wait.

Pidgin will be included by default with Gutsy, so many of these problems will "go away" in the next release, however many of the packages offered in Ubuntu/Debian repositories are old -- meaning they might be a few versions back.  If you want the newest stuff, then you need to rely either on compiling and installing from source, third party repository, or just simply waiting until the next ubuntu release cycle rolls around to get the updated version (approx every 6 months).  As you can see there is no ideal solution.  Ive found compiling from source the best for me, but it took some work, and I dont think everyone would want to extend such an effort.  At least with Gutsy and if you want to compile from source, many of the dependency issues should be resolved.

---

### Post by mivo on 2007-10-05
J followed tribaal's instructions on a fresh Feisty installation, and it worked flawlessly (thanks!). The GAIM icon in Applications/Internet was properly updated as well.

---

