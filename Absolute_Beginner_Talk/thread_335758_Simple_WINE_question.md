---
title: "Simple WINE question"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by konungursvia on 2007-01-10
I've got a Dapper / Xp dual boot on my Inspiron 8200. I have two questions that I can't find answers to in the WineHQ or in the threads.

a) can I not tell Linux to look on my ntfs partition and wine-run installed apps from it? If not, why not? 

b) can I install iTunes on the linux side and use wine with it?

:confused:

---

### Post by scrooge_74 on 2007-01-10
b) dont use it son I dont know the answer but there is a replacement for itunes in linux, saw it mentioned here but dont remember the name

a) wine makes a false c: drive on its directory and register the program the same way it does in windows.  i have read that for some programs you can just copy the files and put then in the false c: drive

after installing wine check in your home directory a folder call .wine
you will see what i mean about a false drive c:

---

### Post by Ocxic on 2007-01-10
I doub't it would work, wine/windows programs need the windows registry, wine creates a fake one, I dunno if it'll work. it could possible messup your programs on the ntfs drive, i wouldn't attempt it. but I've never done anything with wine b4, so i don't really know what to say, if anything, for sure.

---

### Post by scrooge_74 on 2007-01-10
> **Ocxic said:**
> I doub't it would work, wine/windows programs need the windows registry, wine creates a fake one, I dunno if it'll work. it could possible messup your programs on the ntfs drive, i wouldn't attempt it. but I've never done anything with wine b4, so i don't really know what to say, if anything, for sure.

Yes it will be risky to write to the ntfs from wine, and in most cases the program will fail becasue the wine installation does not have it register

---

### Post by Frak on 2007-01-10
[iTunes]("http://www.apple.com/itunes/") **WILL** work under [WINE]("http://winehq.org/"), use [WINETools]("http://www.von-thadden.de/Joachim/WineTools/") to help you if you need it, because iTunes has to be installed a little differently than with most programs you install on [WINE]("http://winehq.org/"), as in you have to reboot, only [WINETools]("http://www.von-thadden.de/Joachim/WineTools/"), [Crossover]("http://www.codeweavers.com/"), and some users can do it.

---

