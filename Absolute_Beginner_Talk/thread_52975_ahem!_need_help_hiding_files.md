---
title: "ahem! need help hiding files"
date: 2005-07-29
forum: Absolute Beginner Talk
---

### Post by byen on 2005-07-29
hey gang,
ok...here is the deal!I am a 23 year old dude who has ...um how shall i put it.. certain prized possessions ;-) that I cant let others (my fam and gang) see... most of em are on my Fat drive and some are on my linux partition. Im heading home for a break and while I am there, will be using my laptop to show people how easy linux is and prolly help them get Ubuntu installed on their box. So, here are my questions:
1.Is there anyway I can password protect a folder? I know i could create a new user but is that the only option?
2.Is there a way I can password protect a folder on my FAT drive so that it becomes protected/inaccesable through windows?
3.If i could move a folder from my home to other folder..where can i move em (other than home)? most of the folders seemed write protected...which folders can I move files into?

thanks.

---

### Post by cwaldbieser on 2005-07-29
Maybe you should just zip the folder in a password protected zip file, or something similar.

---

### Post by poofyhairguy on 2005-07-29
Easy answer. Make a file in your home folder. Puts some docs in it or something. Then put in a hidden file (starts with ".") that has the goods.

No need for password...if your friends and family can beat that then there is little you can do.

---

### Post by Sam on 2005-07-29
If your box is multiuser, don't forget to chmod 700 the directory.

---

### Post by mctavish on 2005-07-29
It is possible to do serious encryption in linux, but not that straightforward. There is some information on this in the forums and in the wiki.

Briefly, it goes something like this: You create a virtual loopback device. This is then mounted via a third party encryption application.Or something like that.

The older method uses cryptoloop, but this is be phased out in favour of devicemapper.

Or you could burn your top secret material onto cd/dvd and hide it, if it isn't too much. :)

---

### Post by byen on 2005-07-29
> **poofy]Easy answer. Make a file in your home folder. Puts some docs in it or something. Then put in a hidden file (starts with ".") that has the goods.[/QUOTE]
Yeah that was by backup plan! but wondered if there was an encryption software available...well... mebbe i'll zip it..psswd protect  it (as suggested by cwaldbieser) and then put it in that folder  said:**
> 
It is possible to do serious encryption in linux...virtual loopback device...cryptoloop, but this is be phased out in favour of devicemapper....
man..those words brought tears in my eyes... seems so complicated man...thanks though
[QUOTE=sam]
If your box is multiuser, don't forget to chmod 700 the directory[/QUOTE]
what is it? can you explain a lil bit please?

thank you for your help guys!really appretiate it!

---

### Post by az on 2005-07-29
I would just create a partition (shrink your current one) and put all the stuff there.  Then mount it by hand when I "need" it.

---

### Post by byen on 2005-07-29
[QUOTE=azz]I would just create a partition (shrink your current one) and put all the stuff there.  Then mount it by hand when I "need" it.[/QUOTE]
 yup.... i will do that...my windows fat mounts automatically because I asked it too... i can disable that! kool! thanks azz! amazing how desperation makes a simple solution non-existant!

---

### Post by Sam on 2005-07-29
[QUOTE=byen]what is it? can you explain a lil bit please?[/QUOTE]
This is the permission of the folder. Run in terminal```
$ chmod 700 <directory>
```and only you can go inside (in the case your computer is shared with other users with differents accounts).

Type```
$ man chmod
```for more informations.

---

### Post by mctavish on 2005-07-29
> I would just create a partition (shrink your current one) and put all the stuff there. Then mount it by hand when I "need" it.

Yeah I reckon that would be a goer, just make sure if you are dual booting with windows that you don't make it a fat partition because windows will automatically mount it.

---

### Post by byen on 2005-07-29
unfortunately...it is an FAT... so i guess i'll just have to zip it and pswd protect it..that seems to be my only option! thanks mctavish

---

### Post by mctavish on 2005-07-29
But what about creating a *new* partition like azz suggested. I was just saying make sure if you make a new one that it isn't fat. Make it ext3 or similar.

---

### Post by Sam on 2005-07-29
I found this on the Wiki:

[EncryptedFilesystemHowto](https://wiki.ubuntu.com/EncryptedFilesystemHowto)
[EncryptedStorage](https://wiki.ubuntu.com/EncryptedStorage)

---

### Post by byen on 2005-07-29
[QUOTE=mctavish]But what about creating a *new* partition like azz suggested. I was just saying make sure if you make a new one that it isn't fat. Make it ext3 or similar.[/QUOTE]
 :-D point noted with gratitude.

PS- so i can break my current drive into smaller pieces (using gparted) without messing up my Ubuntu Install? or is it risky? just curious.

---

### Post by byen on 2005-07-29
wow...thanks sam. really . thanks!
looking into it right now!

---

### Post by Sam on 2005-07-29
You're welcome! Good luck :wink:

---

### Post by hatstand on 2006-02-05
Search these forums for "nautilus locked folder". There is a beta programme...

---

