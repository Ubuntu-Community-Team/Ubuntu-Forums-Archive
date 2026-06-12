---
title: "Included VNC/Remote Desktop mostly frustrating"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by BagOBones on 2006-08-07
When I first installed Ubuntu I saw the Remote Desktop menu item and said "Great finally someone gets it" however after finding out it only works if you leave your desktop logged in I was very disappointed.

I have followed several threads about how to fix this yet non seem to work. I got SSH up and running no problem so I can get in via command line, but the lack of remote GUI is sort of frustrating as I am not a Linux command line GURU.

Any chance in the future another checkmark could be added such as "Allow remote access to login screen"?

---

### Post by scxtt on 2006-08-07
install a vnc server ... i use (here's a shocker :p) **vncserver** on a daily basis, installed from the repos ... i ssh to my box, type **vncserver** and then connect to it w/ a vnc viewer ...

---

### Post by BagOBones on 2006-08-07
I followed several threads describing how to set that up but it would not work.

The only time it works is if the desktop is already logged in.

I think it is silly that the included feature requires that the user leave the system logged in. It doesn't make much sense.

---

### Post by scxtt on 2006-08-07
i'm talking about an entirely different program -- the included Remote Desktop is **vino**, i'm talking about installing **vncserver** specifically ... it will solve your 'problem' ...

and vino is working the way it's supposed to, it's just not what you want ...

$:> sudo apt-get install vncserver

then

$:> vncserver
(it'll prompt you for a password the 1st time)

then (from another box)

$:> vncviewer <ip address of box running server>:1

---

### Post by BagOBones on 2006-08-07
The other threads I looked at suggested the vnc4server package...

Seems that I am able to log in after installing the vncserver package but with a great deal of graphic issues... I will see what I can do with this.

---

### Post by BagOBones on 2006-08-07
Ok great.. got it working.

I would rate your first reply as poor, but your second as excellent.

I wouldn't have posted in the Absolute Beginner Talk section unless I really didn't have a clue what was going on.

---

### Post by scxtt on 2006-08-07
[QUOTE=BagOBones]Ok great.. got it working.[/quote]
good ... :)
[QUOTE=BagOBones]I would rate your first reply as poor, but your second as excellent.[/quote]well this isn't paid technical support, so you get what you pay for ... :rolleyes:
[QUOTE=BagOBones]I wouldn't have posted in the Absolute Beginner Talk section unless I really didn't have a clue what was going on.[/QUOTE]if you want your hand to be held, you should say so ... all your initial post did was complain about vino ...

---

### Post by BagOBones on 2006-08-07
Well considering by default you connect with a VNC client I somewhat assumed that there was already a VNC server installed.

Following the directions from another thread they suggested getting the vnc4server package, so now I can assume I have 2 VNC server packages installed?

Following your second set of directions actually worked.

I would rate my self as a novice Linux user but I have many years of experience on other systems.

I will try and make sure my future posted are less complaint and more question.. However I still think the default option is sort of questionably useful as you are sort of screwed if you remote reboot your system or it is rebooted from a power failure and sitting at its login screen.

---

### Post by scxtt on 2006-08-07
i agree w/ you - i never use vino - but it's not meant to act in the way you (and i) want a vnc server to act ... it's also not ubuntu's M.O. to make it so we can vnc to our boxes (the packages are in the repos, and it's a simple apt-get install to take care of the "problem" - so i don't feel it's justified to complain about vino) ...

vino is meant to be used more in a "hey take a look at my desktop, i need some help" than a *1-person server/client* manner ...

---

### Post by cantormath on 2006-08-07
> **BagOBones said:**
> I followed several threads describing how to set that up but it would not work.

The only time it works is if the desktop is already logged in.

I think it is silly that the included feature requires that the user leave the system logged in. It doesn't make much sense.

thats not true......you are completely incorrect. 
vncserver
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)
freeNX
[http://www.ubuntuforums.org/showthread.php?t=97277&highlight=change+kubuntu](http://www.ubuntuforums.org/showthread.php?t=97277&highlight=change+kubuntu)

---

### Post by scxtt on 2006-08-07
he's not incorrect, vino does ONLY work w/ your :0 connection - so if there isn't one (i.e. you're not logged in) then you can't view it ...

---

### Post by BagOBones on 2006-08-07
> **cantormath said:**
> thats not true......you are completely incorrect. 
vncserver
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

That is what I tried first.. Never got anywhere with it. As did others in that thread who said they could not get it to work.. Someone must be leaving a step out somewhere.,
> **cantormath said:**
> 
freeNX
[http://www.ubuntuforums.org/showthread.php?t=97277&highlight=change+kubuntu](http://www.ubuntuforums.org/showthread.php?t=97277&highlight=change+kubuntu)

Given its name I would never have found freeNX or known what it does.. I will take a look at it as it appears to have some nice options.


The included options still sucks ;)

---

