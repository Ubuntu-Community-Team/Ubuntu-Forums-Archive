---
title: "Resolution help!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-06-13
I am a total linux noob. 

I found this: [http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

but what is xorg?

Can anyone put that in really reallly really noob terms?

That would be awesome

---

### Post by HotShotDJ on 2007-06-13
Hold up.  Step Back.  Take a deep breath. :)
What, exactly, are you trying to accomplish.  There may be an easier way that doesn't involve editing xorg configuration files.

---

### Post by ajskhan on 2007-06-13
My current resolution is 800x600 with a refresh rate of 85mhz. On my tiny screen it is way to big. I want to make everything smalller and be able to fit more windows in teh screen.

---

### Post by Anonii on 2007-06-13
Most resolution problems are solved by following this guide: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
and I'd suggest you to do it too (Especially, if you have one of the most usual problems (Screen running on 640x480 etc.)). 

Apart from that, X.org (xorg) is the application that basicaly builds your Graphical User Interfaces. ( [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System) )(/etc/X11/)xorg.conf, which is the file you are probably refering to, is the configuration file of X. If I were you, tho, I would try following the advices of the guide I posted and then move in manual ones, like the edit of xorg.conf.

Good luck, sir, and don't forget to report back.

[B]EDIT: Seeing your new post:
If you are using Ubuntu, try this: System -> Preferences -> Screen Resolution, and try to change it to smaller numbers, like 640x480.
If you are using KUbuntu, try right clicking on the desktop, going to the Display tab, and then changing the resolution from there. 
If smaller resolutions are not available try the things I said above.[/B]

---

### Post by HotShotDJ on 2007-06-13
Ok.  Tell me what your hardware is (video card, monitor), laptop or desktop, and operating system (Ubuntu 6.10, Ubuntu 7.04, Kubuntu 7.04, etc.).  If you are working with Kubuntu, I can help.  If you are working with Ubuntu, we'll have to wait and see who else shows up in the thread to help you.

EDIT: AH.. cool.  Anonii has some good advise.  Listen to him/her.  I'm signing off this thread. :)

---

### Post by ajskhan on 2007-06-13
I actually, now that I think about this, don't know if it is possible. when i ran what you could call an OS of Widnows 2000 -  800x600 was all it let me go to also. Can I overright that and try and get a better resolution?

---

### Post by ajskhan on 2007-06-13
Smaller resolutions are available, how do I check my video card?

edt: I am currently set at 800x600, but 640x480 is available

---

### Post by Anonii on 2007-06-13
> **ajskhan said:**
> Smaller resolutions are available, how do I check my video card?

edt: I am currently set at 800x600, but 640x480 is available
Did you try 640x480? 
Does it fit to yout needs?
If it does it for you, you don't have to mess with video cards, etc.

---

### Post by ajskhan on 2007-06-13
It is even bigger, I need everything smaller! is it possible to get 1024x768 or whatever is the next increment?

---

### Post by Anonii on 2007-06-13
Heh, I missunderstood your big and small usage.

It is possible, indeed, to get bigger resolutions like 1024x768, or 1280x1024 (or much bigger.), if they are not already there (you can't select them from the menu?). To do that, follow this:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
The paragraph "Run the Autodetect Script Again", usually fixes such problems (Which for some reason are quite usual, and I don't know if it's a bug or something.).

---

### Post by ajskhan on 2007-06-13
> **Anonii said:**
> Heh, I missunderstood your big and small usage.

It is possible, indeed, to get bigger resolutions like 1024x768, or 1280x1024 (or much bigger.), if they are not already there (you can't select them from the menu?). To do that, follow this:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
The paragraph "Run the Autodetect Script Again", usually fixes such problems (Which for some reason are quite usual, and I don't know if it's a bug or something.).

HAHA, my bad...

I am running it now - although I am not sure if it is possible because it never let me do it in Win 2000 either...? Possible?

---

### Post by Anonii on 2007-06-13
Most probably, yes. Especially if you didn't install the driver for your video card in Windows. 

Anyway, try it out, and check if it works. The guide tells you how to make backups anyway ;)

---

### Post by ajskhan on 2007-06-13
And I just try the auto detect script, correct?

---

### Post by ajskhan on 2007-06-13
What should I change horizontal sync range to?

---

### Post by ajskhan on 2007-06-13
My card is:  ATI Technologies Inc Rage Mobility P/M AGP 2x___

---

### Post by Anonii on 2007-06-13
Unfortunately, I don't know what the horizontal sync range is, and where you can find it's preferable value.
If I were you I would wait for someone more knowledgable to tell you.

---

### Post by ajskhan on 2007-06-13
nothing happened... :(

---

