---
title: "problems with synaptic sources and wine"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2006-05-12
i'm going mad trying to get wine installed!! i've been trying for days now and its just not working. first off i can't connect to the url [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt). as mentioned in this thread [http://www.ubuntuforums.org/showthread.php?t=172648](http://www.ubuntuforums.org/showthread.php?t=172648). when i reload the ropository, after enabling that url all i get is error 404 could not connect to budget dedicated. everything else downloads fine. so for starters i don't understand that.
next.......when i click synaptic>settings>Repositories>add> i get this screen:
[IMG]http://i74.photobucket.com/albums/i247/dales618/Screenshot-AddChannel.png[/IMG]
when i tick these two boxes that say universe and multiverse i go back to synaptic and click reload with the url from the previously mentioned thread andit doesn't work. and next time i do that those to boxes are un checked again somehow???
next..............when i type in a terminal sudo gedit /etc/apt/sources.list i get this:
[IMG]http://i74.photobucket.com/albums/i247/dales618/Screenshot-sources.png[/IMG]
can anyone tell me from looking at that if i have the universe and multi verse enabled. 
thanks....................

---

### Post by richbarna on 2006-05-13
Yeah, they look like they're enabled (I can't see the complete sources list).
Ok try getting Wine this way :-
Open your console, and type > sudo apt-get install wine
That should work, if not, post again.
If you want a GUI for wine as well, do this afterwards :-
> sudo apt-get install xwine

---

### Post by e1ektrob0y on 2006-05-13
```
dales@dales-desktop:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
dales@dales-desktop:~$

```
thats what i get. man its driving me crazy

---

### Post by Kimm on 2006-05-13
Add the repository from the wine website, then you'll get regular updates and allways have the latest version.

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by e1ektrob0y on 2006-05-13
[QUOTE=Kimm]Add the repository from the wine website, then you'll get regular updates and allways have the latest version.

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main[/QUOTE]
in my first post i said i already have them added and i can't connect for some reason. i keep getting error 404.

---

### Post by e1ektrob0y on 2006-05-13
[IMG]http://i74.photobucket.com/albums/i247/dales618/Screenshot-synaptic.png[/IMG]
thats what i get from that url

---

### Post by richbarna on 2006-05-13
Ok, this is a long-shot because I don't use Dapper,
Try changing the repository address to :-
> [http://wine.budgetdedicated.com/apt/dists/dapper/main/](http://wine.budgetdedicated.com/apt/dists/dapper/main/)

I noticed that the URL has nothing from Firefox as it is,
But if you put apt/DISTS/dapper it comes up (not in capitals though)

So what I'm saying is, in the repository address try putting "dists" before "dapper".
Maybe it will find the folder.

---

### Post by e1ektrob0y on 2006-05-13
didn't work. i tried copying the url straight from this thread [http://www.ubuntuforums.org/showthread.php?t=172648](http://www.ubuntuforums.org/showthread.php?t=172648).  too and it didn't work. i don't understand cause it seems to work for everyone else. obviously i'm doing somethign wrong but what is it??

---

### Post by richbarna on 2006-05-13
Well, the repository is there, you just need to change the link in the sources.list.
Sorry I can't help further,
Good luck :)

---

### Post by catlett on 2006-05-13
Edit. Didn't see you were using Dapper. My suggestion was Breezy only.

---

### Post by YokoZar on 2006-05-13
Are you using an AMD-64 cpu?  There are no 64 bit packages.

---

### Post by e1ektrob0y on 2006-05-14
yes i am using amd 64-bit but i followed this guide and got the same problem.
[http://ubuntuforums.org/showthread.php?t=167765](http://ubuntuforums.org/showthread.php?t=167765)

---

