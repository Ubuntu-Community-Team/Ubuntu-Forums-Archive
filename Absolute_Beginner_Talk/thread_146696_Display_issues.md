---
title: "Display issues"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-03-18
I'm _really_ new at this and have just loaded ubuntu to a partition of a 250GB SATA drive with XPHE on the other half.  However during the ubuntu install I think an unrealistically high display resolution was selected and so when the install is completed and ubuntu desktop image appears with the drum beat, the display is unintelligible--just an odd herring bone pattern.
So--question is:  how do I get back to choose a lower resolution for the monitor like 800 x 600?
Thanks--hope I'm a quick learner 'cause this looks like it will be fun!

---

### Post by rjwood on 2006-03-18
You can try doing it >system>preferences>screen resolution or you can 
```
sudo dpkg-reconfigure xserver.xorg
``` and when it gets to the monitor and screen resolution---change it there. Hope this helps---good luck and welcome to Ubuntu!!

---

### Post by flyingsolo on 2006-03-18
Thanks but how do I enter anything since screen image is garbled?  How can I enter code when I can't read the screen?  I can restart the computer and get my boot selection screen but if I let it go through to Ubuntu it is the same herringbone pattern.  I'm pretty basic with this so probably need really specific instructions!  Thanks.

---

### Post by DiscoKiller on 2006-03-18
Hit ctrl-alt F2, that should drop you to a command line. then type sudo dpkg-reconfigure xserver-xorg and u should be fine

good luck!!

DK

---

### Post by flyingsolo on 2006-03-18
OK--ctrl-alt-F2 got me to the command line (I guess-since I haven't been here before!)  It asks for my login and password which had been set in the initial install, so OK so far but I can't run the string: sudo dpkg-reconfigure xserver-xorg as suggested because it replies with:
unable to lookup ubuntu<my username> via gethostbyname()
More help please!

---

### Post by DiscoKiller on 2006-03-18
hmmm, very odd. i`m a little out of my depth now i`m afraid, my assumption is that theres something wrong with the username ur using i.e. it is wrong. i`m probably wrong, at the login try using root as ur username wiith your system password, i cant think whether or not it is possible to log in like this but it is workth a shot
then execute the command ommitting the sudo (not needed)

DK

---

### Post by flyingsolo on 2006-03-18
Still floundering!  Just to reassure me, the command line has the following as it's prompt, right?: ~S or ~$ (it isn't clear which symbol it is to me)
I am logged in as a specific usr so how do I get to root if that's where I need to be?

---

### Post by chettyk on 2006-03-18
flyingsolo, I suggest you reboot your computer. Immediately after the computer finishes the initial boot-up tests and before Ubuntu begins booting, you'll get the GRUB menu that lets you choose which operating system to boot. One of the options in the GRUB menu ought be one item that reads something like:
**Ubuntu, kernel {some numbers} (recovery mode)**

Boot the one marked "(recovery mode)". That will deposit you in the root shell.  You ought then to be able to run the command that rjwood suggested without sudo:
```
dpkg-reconfigure xserver.xorg
```

See if this works. Good luck -- and keep persisting.

---

### Post by flyingsolo on 2006-03-19
The last advice above sort of worked...at least I got to the xorg configuration menus which asked a **lot** of questions, many of which I just chose the default answer but still no go at the end of it all.
I think the problem may be related to the nvidia graphics card, a PCI-E 6800GS.  Does anyone know if this is a problem card for some reason and are there any work-arounds?  By the way, the monitor in use is an old 15" Sony CRT marketed under Dell but I had the same display issues when I substituted a recent Dell 17"LCD.
...ongoing thanks for all advice...

---

