---
title: "Putty"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by witham on 2007-07-05
I have installed putty onto my computer to connect to a server through putty and it is all configured except that the outline of the box is in question marks. I have fiddled with the configuration but cannot seem to get it to render properly.
The other problem is that I can't make it launch directly from the shortcut I placed on the desktop and it doesn't fill the window like it did in windows.

Sorry for the list but I am new to Ubuntu and would really appreciate the help.

Thanks

---

### Post by Skrynesaver on 2007-07-05
PuTTY is a bit over thetop for your needs, try ssh user@hostname in a terminal.  This gives you your own terminal settings as a default as an advantage :)
If you want to use PuTTY the ??? outline is a result of choosing the wrong character set or terminal emulation in PuTTY's session configuration

---

### Post by witham on 2007-07-06
Thanks very much the reason I want to use Putty is that is what the other PC's use and it is the only telnet application I hhave used.
I did use the ssh and it connected however the it seemed more complicated than just loading from putty, is it a case of just going through the settings, it is a unix server so should I set the keyboard for Linux as it is currently set to SCO?

---

### Post by witham on 2007-07-10
I have since solved the problem of Putty rendering properly and it now looks fine, my next question is that I can't seem to maximise the window?
I would also really like to load the program directly from the shortcut without having to load the particular session, in windows I used to modify the shortcut to both load the session and maximise the window is this possible in ubuntu?

I would really apprecitae the help.

---

### Post by Skrynesaver on 2007-07-11
Right click on the title bar>Change settings>Window behaviour 
Select Full screen on Alt-Enter

That's the maximization issue, congratulations Your Windows box is now a client to a real OS. (Most of my working life :D )

Part of security is having to authenticate, that's the way it works.  You could ha ve an ssh script with saved keys if you were allowed run a real OS at work <rant>Work</rant>

---

### Post by witham on 2007-07-23
I tried but when I click on the title bar it only lists maximise, minimise, always on top ect, am I right-clicking the correct box?

---

### Post by witham on 2007-09-04
Sorry its been a while but I am still having real problems making puTTy maximise its window, the window maximises but the actual puTTy window remains the same and doesn't fill this new bigger window it just sits with black window space around it?
I have played around with the window rows and column settings but with no joy.
This is the last thing to sort before I can roll out the first Ubuntu computer onto our network and start the process of changing all the PC's over onto a more stable and user friendly OS. 
However to convince the "users" puTTy must load maximised from the shortcut on the desktop. I would really appreciate some help.

Thanks

---

### Post by Skrynesaver on 2007-09-04
You could create a shotcut to ssh user@host and select run in terminal on your desktop.  This would give you a better experience, in my opinion, coupled with ssh keys (look up key_gen) it would give you a series of clickable icons which connect, one for each server.

PuTTY is really meant as a tool to allow Windows users access a remote unix shell, you already have a unix shell, so why not use it?

---

### Post by asmoore82 on 2007-09-04
> **Skrynesaver said:**
> PuTTY is really meant as a tool to allow Windows users access a remote unix shell, you already have a unix shell, so why not use it?

I Second that ...

you are using a *copy *of a *copy *of the **Real Thing**
that was already pre-installed with your OS at
"Applications -> Accessories -> Terminal"

---

### Post by witham on 2007-09-05
Thanks for that I have been using windows to connect to a Unix server that long it was an oversight. I have got connected but it is in black and white, is there a way of making the screen colour?.
Also how exactly do I get the shortcut from the terminal window onto the desktop?

---

