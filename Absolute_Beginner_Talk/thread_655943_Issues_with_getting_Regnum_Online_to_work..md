---
title: "Issues with getting Regnum Online to work."
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Elvaanish on 2008-01-02
Hey, I've been playing around with ubuntu here the last week or so and I've pretty much gotten everything installed and running how I like, with the exception of one program that has kicked my *** time and again. Regnum online just doesnt seem to want to do anything for me! I know I'm almost certainly just making a silly mistake or oversight, but I'm just not seeing it.
So here is the dealio:
Thier website is [http://www.regnumonline.com.ar/index.php?l=1&sec=6](http://www.regnumonline.com.ar/index.php?l=1&sec=6)
I download the linux installer and extract it. Now I've tried extracting it with both the archive manager and through a terminal walkthrough, and I get this file (Displayed in the screenshot, rolauncher)
It shows as an executable, but when I click it does nothing.
In a youtube tutorial I watched once he clicked the extracted executible it launched.. so I dunno what I'm doing wrong. In "permissions" I have it set to 'allow executing file as a program' checked. 
Anyone know what I'm doing wrong?
Doesnt do anything, doesnt try to think about it. 
Does it execute with a different program openign it or something?
Thanks in advance!
[IMG]http://i39.photobucket.com/albums/e157/Elvaanish/Screenshot.png[/IMG]

---

### Post by SOULRiDER on 2008-01-02
Open a terminal in that directory. Then type this:
```
sudo chmod +x rolauncher
```
and then launch the game with ```
./rolauncher
```

I tried it some time ago but I didnt quite like it and the linux version was very buggy.

---

