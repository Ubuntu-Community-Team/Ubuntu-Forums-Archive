---
title: "Can't enable XGL"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-16
I tried using instaling XGL using this instruction 
[http://www.ubuntuforums.org/showthread.php?t=216480&highlight=xgl](http://www.ubuntuforums.org/showthread.php?t=216480&highlight=xgl)
And it doesn't seemed to work!
Can you tell me what I can do to make it work?

---

### Post by mostwanted on 2006-07-16
What is your graphics card called? Do you have 3D acceleration enabled? At what step did it fail?

---

### Post by kris2pe on 2006-07-16
> **mostwanted said:**
> What is your graphics card called? Do you have 3D acceleration enabled? At what step did it fail?

ATI radeon 9800 & I'm following this procedure
[http://www.ubuntuforums.org/showthread.php?t=216480&highlight=xgl](http://www.ubuntuforums.org/showthread.php?t=216480&highlight=xgl)

---

### Post by Drakkor on 2006-07-16
Here is the guide I used to make it work, alot of good info
Xgl is about 2/3 s down under "Turning up the graphics"

[http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)

---

### Post by kris2pe on 2006-07-16
But I already followed the procedure b4 me! Will it affect the the process?

---

### Post by Drakkor on 2006-07-16
I might be wrong,but I don't think so it's I guess trying to get to the same end possible through the same steps which may or may not be in order of each other. I must say it is a lot of terminal work,and it's a nice toy, or even impress your friends, However for me when using an Xgl session some of my other programs like streamtuner,and tvtime do not work properly.just thought you might want to know.But you can always just log out and do a regular gnome session.

---

### Post by kris2pe on 2006-07-16
Ok I was able to start the session using XGL the problem is that its super slow. I don't know why!!!
I have 1 gig of mememory & I have an ATI 9800 which I think is a pretty decent for this kind of setup!!!
Is there a way for us to diagnose this?
BTW it doesn't show the effects @ all it just slows down!!!

---

### Post by Drakkor on 2006-07-16
Did you get your ATI drivers ?

---

### Post by kris2pe on 2006-07-16
> **Drakkor said:**
> Did you get your ATI drivers ?
I tried doing another process & it got worst
[http://ubuntuforums.org/showthread.php?t=131253&highlight=xgl+slow](http://ubuntuforums.org/showthread.php?t=131253&highlight=xgl+slow)
Now I can't access ubuntu 
I gives the error
Failed to start Xserver (your graphical interface). Its likely it is likely that its not set up properly. Would you like to the xserver output? to diagnose the problem? 
It actually got worst!!!
IS there away to undo this?

---

### Post by kris2pe on 2006-07-16
If this helps its got an error
(EE)Xf860penSerial cannot open device /dev/wacom 
No such file directory
What should I do w/ this?

---

### Post by GuitarHero on 2006-07-17
The X server issue problem can be fixed with dpkg-reconfigure xserver-xorg
Just follow the screens choosing settings as you go.  Dont know about that other error.  Do you even have a wacom tablet?

---

### Post by kris2pe on 2006-07-18
No! But I did made it to work!!!

---

