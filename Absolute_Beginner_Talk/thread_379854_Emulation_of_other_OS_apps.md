---
title: "Emulation of other OS apps"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Ebacherville on 2007-03-08
OK I wanted to try using some xp apps on my Ub 6.10 install.. seems there are many options:

WINE
VM ware
WinforLin
Crossover 

And more

CAn any one suggest the best of these types of apps for reliable usage of my windows stuff on ubuntu..

Also is there a emulator for OSX apps in Ubuntu... or a way to run osx apps like a wine for OSX stuff... 

I have parallells on my macbook and I have to say its the most impressive piece of software i have used on the mac... very fast and reliable, basically looking for a parrallels for the Ubuntu system.

I know this is kind of a opinion type of thing but your opinion counts more if you can give some facts or examples of why you like what you like.

One more note , I Love Ubuntu, Cant wait till my nvida card gets here so i can get Beryl installed :)

Thanks
Ebacherville

---

### Post by AngryGnome on 2007-03-08
I don't think any emulator will run ALL windows programs well.  The one I've had the most experience with is Wine.  It tends to run most things pretty well... with a few glitches here and there.  There are some programs it runs flawlessly... and of course there are programs it won't run at all.  Wine is also very easy to use.  

I don't have much experience with the others so I can't say either way... but I'd suggest giving Wine a try.

---

### Post by Ebacherville on 2007-03-09
I downloaded wine via the add remove software tool .. It installed and now its not in my applications list, so I went into the term and did a whereis and found where its sitting but what do I run to execute it?

Ebacherville

---

### Post by mackyman on 2007-03-09
> **Ebacherville said:**
> I downloaded wine via the add remove software tool .. It installed and now its not in my applications list, so I went into the term and did a whereis and found where its sitting but what do I run to execute it?

Ebacherville

The first thing you shuld do when you have installed or upgraded wine is run the command:

```
wineprefixcreate
```

to make shure that the program works better, when upgrading, this is important.

Then you try to run programs with

```
wine <application>
```

eg.

```
wine setup.exe
```

when in the applications folder.

If it doesn't work well, or not at all, try

```
winecfg
```

and add the program to the application list and set the operating system to windows xp (if it's a xp application assumed).

You can also run around a bit in the config and set those things you know of you computer up.

To get guides for you application, and check how well it works with wine, goto [HTML]http://appdb.winehq.org/[/HTML] and search for your program. And on [HTML]http://winehq.com[/HTML] and check for some documantion, or search  the forums and ubuntuguide. There's some really good things there.

Goodluck!

---

### Post by Patrick K on 2007-03-09
You can also run this command:
> winefile
It opens the wine file manager.

---

### Post by mackyman on 2007-03-09
> **Patrick K said:**
> You can also run this command:

It opens the wine file manager.

Nice! I have never used that. Looks lite it can be a bit helpful when installing and testing some new apps before you have made your own shortcuts to them =)

---

### Post by Ebacherville on 2007-03-09
Thanks everyone, Ill try this when I get on my Ubuntu Box.

Ebacherville

---

