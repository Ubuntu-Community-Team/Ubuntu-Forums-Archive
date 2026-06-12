---
title: "some application doesnt launch"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-25
ok i have installed affinity, avant window navigator, beagle.. but i cant find them in applicaion or system.. i try to launch em through terminal.. it says command not found.. i check on synaptic and it says its installed.. whats wrong ? how can i launch em ? thank youi

---

### Post by HunkieChan on 2007-03-25
can anyone please help me ?

---

### Post by HunkieChan on 2007-03-25
uh man.. anyone ?

---

### Post by framinglory on 2007-03-25
try using locate whatyou'relookingfor in the terminal
example, locate beagle
it should show a list of files related to what it is you typed in, look for ones in /usr/bin and try typing them in terminal. it should be fairly obvious which ones you want.

edit:
you can also try this line in terminal, it'll give a simpler answer
sudo dpkg -L X|grep /usr/bin/
just replace x with the name of the program you installed, and this line should return a list of files that were placed in /usr/bin, usually one of which will run the program you're looking for
if it's an administrative program, replace /usr/bin with usr/sbin, and games will be in /usr/games

---

### Post by HunkieChan on 2007-03-25
> **framinglory said:**
> try using locate whatyou'relookingfor in the terminal
example, locate beagle
it should show a list of files related to what it is you typed in, look for ones in /usr/bin and try typing them in terminal. it should be fairly obvious which ones you want.

edit:
you can also try this line in terminal, it'll give a simpler answer
sudo dpkg -L X|grep /usr/bin/
just replace x with the name of the program you installed, and this line should return a list of files that were placed in /usr/bin, usually one of which will run the program you're looking for
if it's an administrative program, replace /usr/bin with usr/sbin, and games will be in /usr/games

thanks finally someone came in.. ill try it right away

---

### Post by HunkieChan on 2007-03-25
> **HunkieChan said:**
> thanks finally someone came in.. ill try it right away

when i try locate.. it works.. but how do i load them ?..

---

### Post by HunkieChan on 2007-03-25
> **HunkieChan said:**
> when i try locate.. it works.. but how do i load them ?..

edit: i get it now..

---

### Post by HunkieChan on 2007-03-25
ok.. avant-window-navigator .. doenst work

---

### Post by framinglory on 2007-03-25
can you please post the output of terminal for avant when you run the command?

---

### Post by HunkieChan on 2007-03-25
> **framinglory said:**
> can you please post the output of terminal for avant when you run the command?

i was able to beagle.. but i dont geet anything when i put avant in..

---

### Post by framinglory on 2007-03-25
okay, try typing avant-preferences into the terminal.
if it doesn't work, then it sounds like avant window navigator isn't installed.

---

### Post by HunkieChan on 2007-03-25
one thing.. how can i put beagle on desktop ?

---

### Post by framinglory on 2007-03-25
you can put it on the taskbar at the top by right clicking, click on add to panel, then scroll down until you find "run application" you can click on that, type in the command.
to add it to the applications menu, i think you can right click on applications, click edit menus, select the submenu you would like it in by clicking on that submenu on the vertical bar located on the left side. then click "new item" and title it what you'd like, and enter the terminal command in the box labelled command.
if you can't right click and edit menu, i believe there is a menu editor somewhere in the applications menu on some versions of ubuntu.

---

### Post by HunkieChan on 2007-03-25
> **framinglory said:**
> okay, try typing avant-preferences into the terminal.
if it doesn't work, then it sounds like avant window navigator isn't installed.

nothing comes up

but in synaptic it shows it's installed

one more thing how do i beagle in desktop or panel so that i dont have load it every time thrugh terminal

---

### Post by HunkieChan on 2007-03-25
> **framinglory said:**
> you can put it on the taskbar at the top by right clicking, click on add to panel, then scroll down until you find "run application" you can click on that, type in the command.
to add it to the applications menu, i think you can right click on applications, click edit menus, select the submenu you would like it in by clicking on that submenu on the vertical bar located on the left side. then click "new item" and title it what you'd like, and enter the terminal command in the box labelled command.
if you can't right click and edit menu, i believe there is a menu editor somewhere in the applications menu on some versions of ubuntu.

yeah i was able to do that thanks alot.. thank you somuch

---

### Post by framinglory on 2007-03-25
kind of a silly question, but do you have beryl/compiz running and working?

---

### Post by HunkieChan on 2007-03-25
i used to have beryl .. now i use compiz.. why is it a silly question ? why do you ask ?

---

### Post by framinglory on 2007-03-25
i guess it wasn't a silly question. but if beryl/compiz has any errors or issues it probably will affect avant. i'm not familiar with the software, so the only ideas i have are to look for issues in beryl/compiz, and to try and reinstall the software.
if you try reinstalling the software, use
sudo apt-get remove --purge packagename
this will remove the package, and erase all configuration files. you can then install it again.
hope this works, because i'm running out of ideas.
i've got to go for a while, i'll be back in a couple hours, good luck with getting everything running

---

### Post by HunkieChan on 2007-03-25
> **framinglory said:**
> i guess it wasn't a silly question. but if beryl/compiz has any errors or issues it probably will affect avant. i'm not familiar with the software, so the only ideas i have are to look for issues in beryl/compiz, and to try and reinstall the software.
if you try reinstalling the software, use
sudo dpkg --purge packagename
this will remove the package, and erase all configuration files. you can then install it again.
hope this works, because i'm running out of ideas.
i've got to go for a while, i'll be back in a couple hours, good luck with getting everything running

thanks for your help..i appreciate that.. thanks alot... i will try that..

---

### Post by framinglory on 2007-03-25
a quick note, i accidentally typed a wrong word into the code i told you, check the previous post i made, i edited it. sorry about that

---

### Post by HunkieChan on 2007-03-25
> **framinglory said:**
> a quick note, i accidentally typed a wrong word into the code i told you, check the previous post i made, i edited it. sorry about that

thanks.. but i didnt try it yet.. ill later.. thanks again

---

