---
title: "gksudo gedit not working"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Botunda on 2007-02-05
Hey all, for the last couple of days I have been trying to get gedit to work in gksudo or sudo. What happens is:
First time I try and launch:

ME@ME:~$sudo gedit /etc/X11/xorg.conf

I get:
password:

I input password and then I get nothing. I just have blinky.

Next time run:
ME@ME:~$sudo gedit /etc/X11/xorg.conf

I get nothing

It just hangs until I hit ctrl+z

Then it bumps me back into the term

What the heck am I doing wrong? Can someone light the way?

TIA

---

### Post by Happy_Man on 2007-02-05
Have you tried 

```

sudo nano /etc/X11/xorg.conf

```
?

Nano is a command-line text editor, unlike GEdit, which uses a GUI. Try that out and see what happens, and then post back.

---

### Post by Botunda on 2007-02-05
> **Happy_Man said:**
> Have you tried 

```

sudo nano /etc/X11/xorg.conf

```
?

Nano is a command-line text editor, unlike GEdit, which uses a GUI. Try that out and see what happens, and then post back.

I've tried nano, but I am not comfortable enough yet to use it. I likes me the gui. should I just suck it up and go wif the nano? There is still something going on with gedit that I would like to get resolved.

---

### Post by Botunda on 2007-02-05
I just tried nano and I can't seemt to edit ***anything!*** I can only ctrl+z out of it. Hrm, wierd. Maybe the Ubuntu gods don't want me to write or edit anything.

---

### Post by ardchoille42 on 2007-02-05
You shouldn't be using sudo with GUI apps, it can break things. Use gksudo with GUI apps like gedit.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

What happens when you:  gksudo gedit /etc/X11/xorg.conf ?

---

