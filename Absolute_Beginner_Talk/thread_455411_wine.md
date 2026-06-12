---
title: "wine"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by windows hater on 2007-05-26
im new to ubuntu and i heard alot about wine runing windows programs like games is there an easy way to get it without terminal

---

### Post by lazyart on 2007-05-26
Wine will run some windows software but don't expect it to be the solution for everything.

The easy way to get it is actually with the terminal:```
sudo apt-get install wine
```However you can go to System>Administration>Synaptic Package Manager and search for wine and install it.

Don't be afraid of the terminal.  It's usually the most efficient way to do things.

---

### Post by p_quarles on 2007-05-26
If you're using Feisty Fawn, you can install Wine from the repositories. One component is the "Wine File Browser." It doesn't automatically show up in the main menu, but you can make it show by changing the "Main Menu" settings. 

And, no, Wine doesn't really play any games. It might play some older games, but it mainly works with lighter and simpler windows apps.

---

### Post by windows hater on 2007-05-26
im not afraid of terminal its just it dosnt work with any thing sudo and what programs do install through synaptic package

---

### Post by windows hater on 2007-05-26
im looking for it to play games like counter strike and w.o.w

---

### Post by Cloudedbrains on 2007-05-26
If you browse the WineHQ application database here:
[http://appdb.winehq.org/](http://appdb.winehq.org/)
It will tell you what Wine can and cant run :)

I can tell u for sure it runs - Adobe Photoshop 7 and Rollercoaster Tycoon 2 ;)

---

### Post by windows hater on 2007-05-26
whats the exact files i need to download through synaptic package

---

### Post by Outrunner on 2007-05-26
Did you use [this]("http://www.winehq.org/site/download-deb") page? It tells you what commands to type to install wine. You can just copty/paste.

---

### Post by windows hater on 2007-05-26
it dosnt work in terminal i need the package part

---

### Post by Outrunner on 2007-05-26
What doesn't work in the termial, maybe you should be more specific so we can help...

---

### Post by windows hater on 2007-05-26
ever time i type sudo it ask for pass well thats when it freezes and wont type thats y i cant do terminal

---

### Post by Outrunner on 2007-05-26
OK well no it doesn't freeze it just doesn't show you the password. Type it anyway and press enter and you will see that it'll work it's magic

---

### Post by Cloudedbrains on 2007-05-26
Yep it does look like it freezes but type password hit enter and bingo off it goes ;)

In synaptic go to search type in wine hit enter
When results come up scroll down to the one named simply WINE (in the first coloumn
Mark to install
Apply and install

---

### Post by windows hater on 2007-05-26
well i got it installed now what do i do to get it to run windows stuff

---

### Post by Enverex on 2007-05-26
Follow the FAQ in my sig which tells you how to use Wine. I have to point out though that it's not a program for people that aren't experienced with Linux or the terminal.

---

### Post by windows hater on 2007-05-26
well is there any other emulator like wine that can run  games and is easy to install and run

---

### Post by Enverex on 2007-05-26
There's Cedega but that's based around hacks on hacks, so your app is only likely to work if it's on the top of their "To do" list.

---

### Post by windows hater on 2007-05-26
what do u mean it runs on hacks slugish bad if runs as long as it runs i dont care

---

### Post by Enverex on 2007-05-26
I'm not entirely sure what you just said...

Erm, look here for what works and what doesn't: [http://cedegawiki.sweetleafstudios.com/wiki/Main_Page](http://cedegawiki.sweetleafstudios.com/wiki/Main_Page) (I don't trust their official DB, well, I don't trust them at all but that's another matter).

---

### Post by lazyart on 2007-05-26
Bottom line is- if you want to play windows games you're best off installing windows.

---

### Post by Nythain on 2007-05-26
newest versions of wine do a great job playing most windows games... though newer versions tend to break support for some of the more popular games sometimes.

cedega, if you dont mind wasting money for a pretty GUI is buggy as hell but will run some games wine wont...

Dual Boot windows if you play a LOT of games, nothing really beats windows in this department yet, damn directx programmers

follow these directions to add the wine repository to your sources.list and get the most current version of wine
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
the version of wine in the repos is kind of old now

---

