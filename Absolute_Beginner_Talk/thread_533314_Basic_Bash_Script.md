---
title: "Basic Bash Script"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-08-23
I'm wanting to have an applet on my panel that updates my system with one click. 
I'll want it to open in a terminal and prompt me for passwords or a "y" or "n". What 
would I need to make the commands open in a terminal then continue the script?

Thanks for your help!

---

### Post by Ink-Jet on 2007-08-23
What do you mean by updating your system?

apt-get upgrade?

---

### Post by Blutack on 2007-08-23
Hmm, zenity would be neater.
sudo aptitude install zenity
and follow the guide here
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by shanepardue on 2007-08-23
Yes Ink-jet and I'll check it out blutack

---

### Post by Ink-Jet on 2007-08-23
Something like

```
#!/bin/bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
exit
```

should do it

---

### Post by shanepardue on 2007-08-23
> **Ink-Jet said:**
> Something like

```
#!/bin/bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
exit
```

should do it
Yeah, that's what I have, but the terminal needs to open to prompt me for my password and any "y" or "n"s

---

### Post by K.Mandla on 2007-08-23
Maybe use gksudo? and so something like ...

```
gksudo apt-get -y upgrade
```
I don't use gksudo much though. Maybe that won't work.

---

### Post by shanepardue on 2007-08-23
> **K.Mandla said:**
> Maybe use gksudo? and so something like ...

```
gksudo apt-get -y upgrade
```
I don't use gksudo much though. Maybe that won't work.
That'll prompt for a password for sure, but that won't prompt me will it? I can't tell since I 
don't have any needed updates, but I have a feeling it wouldn't as it doesn't open a terminal.

*I posted this then saw you had edited it with a "y" argument. I guess that 
would solve the argument, but I would still like to see the prompt to make sure 
I want the update.

Sorry for the pickiness! thanks for your help!

---

### Post by K.Mandla on 2007-08-23
No problem. :) Like I said, I don't use that much, but I think it will at least do the trick for you. 

Is there a reason you don't use the system update utility?

---

### Post by shanepardue on 2007-08-23
> **K.Mandla said:**
> No problem. :) Like I said, I don't use that much, but I think it will at least do the trick for you. 

Is there a reason you don't use the system update utility?
It just seems a little too heavy on the resources and also I prefer aptitude.

---

### Post by K.Mandla on 2007-08-23
Did you know that aptitude has its own "graphical" interface?

```
sudo aptitude
```
[[img]http://xs118.xs.to/xs118/07345/2007-08-24-102223_652x391_scrot.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs118&d=07345&f=2007-08-24-102223_652x391_scrot.jpg)

Maybe that's a solution for you. You can't get much lighter on resources than that. Of course, it might take a little to figure it out, since the keystrokes are different. (You can use the mouse too, though.)

---

### Post by shanepardue on 2007-08-23
Yeah, I'm aware of the graphical interface. I'm actually wanting to make an aptitude 
update with one click. I want less steps than I already take. Does that make sense?

Again, I really appreciate all of your input!

---

