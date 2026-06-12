---
title: "Questions about wine"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by StifflerNewb on 2006-06-18
Ok, so I play a MMORPG (Linage 2 to specify the game) and I have now decided to run Ubuntu 100%, without windows installed at all. Altho I am a newb and I dont quite understand this about Wine.

To the questions:
1) Do I really have to have windows installed to emulate the game?
2) How do I install the game, since all I have is a .exe file
3) If anyone has ever done this with Linage 2 I'd be really happy if that person could give me a link to a guide or write a guide on how to get it to work.
4) If anyone has a good link to how Wine works (not the one on their website) I'd like that aswell.

Thats about it.

---

### Post by xXx 0wn3d xXx on 2006-06-18
[QUOTE=StifflerNewb]Ok, so I play a MMORPG (Linage 2 to specify the game) and I have now decided to run Ubuntu 100%, without windows installed at all. Altho I am a newb and I dont quite understand this about Wine.

To the questions:
1) Do I really have to have windows installed to emulate the game? 

No that's what wine is for. To run windows apps and games on linux.

2) How do I install the game, since all I have is a .exe file. 

After installing wine, double click the file.

3) If anyone has ever done this with Linage 2 I'd be really happy if that person could give me a link to a guide or write a guide on how to get it to work. 

I have not used it but not all games and apps work under wine.

4) If anyone has a good link to how Wine works (not the one on their website) I'd like that aswell.

There are debs on winehq.org.

Thats about it.[/QUOTE]
Hope that helps

---

### Post by ????? on 2006-06-18
> 1) Do I really have to have windows installed to emulate the game?
No
> 2) How do I install the game, since all I have is a .exe file
sudo wine /home/username/path/tofile.exe

Wine calls your ubuntu / partition "drive z"



EDIT: I got beaten..

---

### Post by AndyCooll on 2006-06-18
I can only answer your first question:

No, you don't need Windoze installed (that's the idea of Wine, it provides a layer that emulates the functions of Windoze).

:cool:

---

### Post by keithjr on 2006-06-18
Hi, I can't answer all of your questions but I have a couple of tips:

1) You do not need windows installed at all, that's the whole point.  Wine isn't an emulator, technically, it's just a compatibility layer.
2) there are several ways to go about this, but you use wine to run the executable with a certain degree of support from its built-in dummy-windows dlls.  

I can't provide much specifics, but I do have a link that I've been working with  the past couple days to try to get some games running:

[http://www.linux-gamers.net/modules/wiwimod/](http://www.linux-gamers.net/modules/wiwimod/)

Unfortunately, their how-to for configuring wine is outdated and has several mistakes (or things that just plain won't work), such as the existance of a x-window-system-dev package for ubuntu.  

Edit:  I got beaten too.  This forum is much more effective than the others man.  3 replies in 5 minutes.

I'll update later on how much progress I've made.  I'd also look around our own forum for a how-to for the version of ubuntu you're using.  If you're using Dapper like me, you might be in for a rough ride.

---

### Post by Kilz on 2006-06-18
[QUOTE=StifflerNewb]Ok, so I play a MMORPG (Linage 2 to specify the game) and I have now decided to run Ubuntu 100%, without windows installed at all. Altho I am a newb and I dont quite understand this about Wine.

To the questions:
1) Do I really have to have windows installed to emulate the game.[/QUOTE]

No, and as others have pointed out wine is available. But wine can be hard to setup and not every program can be run under wine. Games are especially hard. 
[Cedega]("http://www.transgaming.com/") is a program that will play a lot of windows games a lot easier. But its not free. It costs $15 dollars for a 3 month subscription. During that time you can download the program and any updates( updates add new games). You can even let the subscription run out and the program will still work, but if you need an update to get a new game running you will have to subscribe again. I paid the $15 myself, and saved a lot of headache and problems. Its up to you.

---

