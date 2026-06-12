---
title: "E: Couldn't find package beryl.."
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by urk_nono on 2007-01-09
**sudo apt-get install beryl emerald-themes**
[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl[/I]

Anyone got a word of advice? :confused:

---

### Post by urk_nono on 2007-01-09
Right, nevermind. Saved the repository to the backup.list instead of the original one. Will probably need some help in 5 minutes when this PC shuts down and I'm crying and slamming my head on the table. Thanks in advance. Urk

---

### Post by tonyr1988 on 2007-01-09
Make sure, once you add the repo, to sudo apt-get update

...another common problem. :) In advance, what graphics card do you have, and which HowTo are you following?

---

### Post by urk_nono on 2007-01-09
> **tonyr1988 said:**
> Make sure, once you add the repo, to sudo apt-get update

...another common problem. :) In advance, what graphics card do you have, and which HowTo are you following?

Well, I got it working, but now I don't even know how to use "Emerald Themer", damn I feel dumb.](*,)

---

### Post by crimesaucer on 2007-01-09
Emerald is very easy to learn. What do you need to know?

I made this Emerald window theme today. I used the vrunner engine and the buttons from a theme called sleep:

[img]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-10-4.png[/img]

---

### Post by energyarts on 2008-01-10
I need some help guys...Couldn't find package emerald , how can i install it ? and the other problem i am having is compiz it looks installed but i cant access it i cant find it on system>preferences is just not there Advanced settings, please some hel i am new to this .
thank you

---

### Post by forestpixie on 2008-01-10
you need to make sure you have the repos enabled - go to software sources in system > admin and make sure the boxes are ticked 

then you should be able to get both

sudo apt-get install emerald compizconfig-settings-manager

---

