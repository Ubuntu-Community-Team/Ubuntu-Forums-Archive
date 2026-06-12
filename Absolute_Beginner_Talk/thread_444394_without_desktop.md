---
title: "without desktop"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by DaDave on 2007-05-15
Is it possible to run programs without the desktop?

Does xserver have to be running in order to run programs from command line?

Hahaha... I'm trying to figure out how to ask this question right. I'm trying to use my computer like I did back in the (AIX) days but seem to have forgotten everything.

I just want to be able to run my few programs from a command line without all the desktop stuff. I don't care much about 'pretty' and 'one click use'. I tried turning off xserver, but that doesn't work. Or does it, and I just missed something?

Is that about as clear as mud?

---

### Post by taurus on 2007-05-15
It depends on what programs do you have in mind.  Try something like

```
sudo aptitude update
```
See.  You can run that program from a prompt without X.

---

### Post by earobinson on 2007-05-15
try pressing ctrl + alt + f1 and then ctrl + alt + f7 to get back to graphics mode.

Is that what you wanted? Or are you trying to do things remotly?

---

### Post by DaDave on 2007-05-15
> **taurus said:**
> It depends on what programs do you have in mind.  Try something like

```
sudo aptitude update
```
See.  You can run that program from a prompt without X.

haha good one!

I want to run whatever I feel like running. Firefox, Gimp...whatever. Do you remember DOS before Windows? Well, that's what I want.

---

### Post by 3rdalbum on 2007-05-15
You can indeed run any command-line or framebuffer programs from the command-line without the X server running.

Programs that are GUI in nature (i.e. they use an interface toolkit other than nCurses) require X running.

You can run X without too much overhead by installing a standlone window manager from the repositories like Openbox. Use the Options menu of GDM to change the session to "Openbox", log in, and right-click for the menu.

---

### Post by jfinkels on 2007-05-15
> **DaDave said:**
> haha good one!

I want to run whatever I feel like running. Firefox, Gimp...whatever. Do you remember DOS before Windows? Well, that's what I want.

Those two apps are designed to have Graphical User Interfaces that depend the X server running. There are many many programs that are designed without a GUI. You can browse the web using 'lynx', you can install software using 'aptitude', you can list your hardware using 'lshw', etc. To get to the terminal, go to Applications > Accessories > Terminal.

---

### Post by DaDave on 2007-05-15
> **jfinkels said:**
> Those two apps are designed to have Graphical User Interfaces that depend the X server running. There are many many programs that are designed without a GUI. You can browse the web using 'lynx', you can install software using 'aptitude', you can list your hardware using 'lshw', etc. To get to the terminal, go to Applications > Accessories > Terminal.

Yes, I understand that. Unfortunately, some programs require GUI. I think, maybe, I'm trying to cut down on 'eye candy'. Function before form.  I'm using xubuntu to trim down some of that desktop excess, but it's still not enough. Oh well, I'll figure it out. That's half the fun of LInux/Ubuntu, isn't it?

---

### Post by earobinson on 2007-05-15
you could try using blackbox or fluxbox

---

### Post by jfinkels on 2007-05-15
> **DaDave said:**
> Yes, I understand that. Unfortunately, some programs require GUI. I think, maybe, I'm trying to cut down on 'eye candy'. Function before form.  I'm using xubuntu to trim down some of that desktop excess, but it's still not enough. Oh well, I'll figure it out. That's half the fun of LInux/Ubuntu, isn't it?

For many programs (except perhaps GIMP, which inherently requires a GUI) there are equivalents that use the terminal for input and output. Ask around if you want a terminal-only equivalent to a certain program.

And as the previous poster suggests, try fluxbox or openbox! That's what you're looking for if you want function over form in a GUI.

---

### Post by RedSquirrel on 2007-05-15
> **DaDave said:**
> Yes, I understand that. Unfortunately, some programs require GUI. I think, maybe, I'm trying to cut down on 'eye candy'. Function before form.  I'm using xubuntu to trim down some of that desktop excess, but it's still not enough. Oh well, I'll figure it out. That's half the fun of LInux/Ubuntu, isn't it?


I don't like 'desktop excess' either. That's one of the many things I like about Fluxbox. :)

If you install Fluxbox, you will find that it has none of the eye candy or clutter by default. In fact, its initial appearance is quite plain. Some people add lots of eye candy to it, but I like to leave mine fairly clean.

Screenshot...

---

### Post by urukrama on 2007-05-16
If you want it even simpler (no toolbar, no transparency), try Openbox. Otherwise just use command line applications (elinks/links2, midnight commander, etc.). There is a Cubuntu out, which is Ubuntu with only the command line. See [here]("http://ubuntuforums.org/showthread.php?t=318833&highlight=cubuntu").

---

