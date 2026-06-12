---
title: "Issues Installing Ubuntu"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Bubonic on 2008-01-03
I'm new to Linux and was told that Ubuntu is one of the more user friendly builds out there.
I've been trying to install ubuntu but I keep on running into problems.
I have two problems. The first one is that sometimes while trying to boot from the ubuntu CD a message will flash up on the screen mentioning something about battery power then it will proceed to a black screen with the ubuntu timer on it. (The mouse cursor) This is after I have had the ubuntu time on the screen with an orange background. The funny thing is that I am using a desktop PC and it does not have a battery.
Second problem. When ubuntu actually loads up, I am prompted for a user name and password... I thought it was supposed to go directly to the desktop. If I click on options the who thing just freezes and I have to reboot my computer.

If anyone can tell me what the password is or how to change it without freezing the whole thing? :confused:

---

### Post by CCNA_student on 2008-01-03
So to clarify, you do not have Ubuntu installed yet? And could you post what hardware you have please? That might explain something.

---

### Post by Bubonic on 2008-01-03
No I do not have it installed yet.

PS: 500W
CPU: Intel Core2 Quad 6600 2.4ghz
RAM: 2gb DDR2-800
Hard drive: 160gb SATA
Motherboard: Asus P5K
Graphics: nVidia 8800GTS 320mb pci-e
Sound:  Creative Audigy ZS2

Edit:
The main problem I am having is that when Ubuntu boots up off the CD it asks for a user name and password instead of going directly to the desktop. When ever I click on the "Options" button the system seems to freeze and the CD drive sits there reading the CD for a ridiculous amount of time (15-20minutes plus). If I press F10 to "bring up a menu" the same thing happens. 

I need to know what this user name and password is for the copy of Ubuntu that boots off of the CD.

---

### Post by Bubonic on 2008-01-04
I've tried installing again and I managed to get screen shots of what happens when I am unable to get to the ubuntu log in screen.

Here's what I do.
1: I choose "Start orInstall Ubuntu"
[IMG]http://i19.photobucket.com/albums/b172/jwillia5/step1.jpg[/IMG]
2:Ubuntu starts to load off of the CD
[IMG]http://i19.photobucket.com/albums/b172/jwillia5/step2.jpg[/IMG]

Then after about five minutes a bunch of text scrolls onto the screen.(large images)
[http://i19.photobucket.com/albums/b172/jwillia5/error2-1.jpg](http://i19.photobucket.com/albums/b172/jwillia5/error2-1.jpg)
[http://i19.photobucket.com/albums/b172/jwillia5/error3.jpg](http://i19.photobucket.com/albums/b172/jwillia5/error3.jpg)
[http://i19.photobucket.com/albums/b172/jwillia5/error1-1.jpg](http://i19.photobucket.com/albums/b172/jwillia5/error1-1.jpg) (Edited this one to bring out the text more)

---

### Post by lisati on 2008-01-04
I don't know quite why, but the second screenshot looks like Ubuntu is shutting down. Anyone?

---

### Post by seventhc on 2008-01-04
if it gets to a part asking for a uid and password, i would try leaving it blank and just hit enter or click ok....also is this a good cd??maybe there is something wrong with the cd?? but really I am not sure. But i sort of remember i got asked for a username and password and since i knew there wasnt any, i just hit the enter key.

---

### Post by Bubonic on 2008-01-04
I tried just leaving the user name and password fields blank but it  didn't work. It said I *have* to enter a user name and password.

---

### Post by steve8track on 2008-01-04
Are you using a normal Ubuntu CD?

Try these:

1.  run "Check CD for defects" from your first screenshot.  You could also try downloading it again or a different version just to make sure the CD is different.
2.  Try installing in text mode.  I don't know how, but I think there should be an option to go through the installation process by text instead of graphics.  If the desktop edition doesn't have it, you could try the server edition, which for sure has a way to install through text (but you might have to secure it afterward if this isn't intended to be a server).  You can install the graphical user interface later if the server edition doesn't install it.

The second suggestion should decrease the time it takes you to see the errors substantially.

I've gotton logical block errors on my live flash drive, and I think it's caused by the live CD not knowing where to look for the hard drive or CD.  What's even stranger is I thought the live CD only uses RAM (at least at first), so I would think it's having trouble finding that?!  Are you just selecting the first option on the live CD?  Try in safer graphics mode.

I assume you are wiping your hard drive clean to install Ubuntu.  What I would try if you still can't get it to work, I would download another Linux distro, like Mepis, and boot it's live CD, reformat the drive, and then see if having a cleaned up hard drive helps any (in case for some reason Ubuntu thinks it's installed when it's not).  Maybe this last idea is crazy, but I think it's always good to start fresh.

These are just my guesses, but I hope it helps.

One other thing, you can try "root" as the user name, and "root" as the password.  That is what Mepis used for their defaults I think.

---

### Post by Bubonic on 2008-01-04
Ah Ha! I checked for errors on the CD and it found a bunch. I re-burnt the iso to another CD and it works!

Thanks for the help!:biggrin:

---

