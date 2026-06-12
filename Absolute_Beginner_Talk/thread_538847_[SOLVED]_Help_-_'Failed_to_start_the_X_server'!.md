---
title: "[SOLVED] Help - 'Failed to start the X server'!"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Magneticgravity on 2007-08-30
Help - Ubuntu wont let me log on, how do i configure the X server again?

I need to restart the 'GDM' when it is configured correctly!!

Help!

Thx in advance.

---

### Post by Majorix on 2007-08-30
```
sudo dkpg-reconfigure xserver-xorg
```

---

### Post by Magneticgravity on 2007-08-30
Where do i type that in?

I can log on, but it just gives me text...

---

### Post by bake7221 on 2007-08-30
that's called a command prompt (I think...) ... You say you log in? Do you log in through a GUI or is it just text? if it's just text than you type that in ... go through the steps, and restart and you're good to go ..

---

### Post by justleen on 2007-08-30
logon in the terminal (thats what the text is called :) )
if you dont see a login:  press ctrl-alt-f3 to open a terminal (or just alt-f3 if that wotn work)

type your credentials, and type the code.

---

### Post by Magneticgravity on 2007-08-30
OK, its all text, i can log in, i type in what the first poster said, but it says 'command not found.'

---

### Post by por100pre1 on 2007-08-30
There's a typo in that command. It should be:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Magneticgravity on 2007-08-30
Wait, im fine

---

### Post by Magneticgravity on 2007-08-30
Whats my mouse port? :S

---

### Post by Magneticgravity on 2007-08-30
Anyone?

---

### Post by por100pre1 on 2007-08-30
I don't know. Try:

[SIZE="4"]/dev/ttyS0[/SIZE]

---

### Post by rocknrolf77 on 2007-08-30
Do a 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

instead. And you don't have to go through all those steps :)

---

### Post by Magneticgravity on 2007-08-30
OK the mouse isnt working, i got the image back, can i configure the mouse from my desktop or should i reboot and just type in what rockrolf77 said and how?

---

### Post by rocknrolf77 on 2007-08-30
If you altered the mouse settings for xorg then you have to run

```
sudo dpkg-reconfigure xserver-xorg again
```

too configure your mouse properly

---

### Post by Magneticgravity on 2007-08-30
Could i use your our other command or is that a no go now?

---

### Post by por100pre1 on 2007-08-30
> **Magneticgravity said:**
> OK the mouse isnt working, i got the image back, can i configure the mouse from my desktop or should i reboot and just type in what rockrolf77 said and how?

CTRL+ALT+F1, login, and use the posted command.

---

### Post by Magneticgravity on 2007-08-30
Which one, the one where i go through the steps or the one where it does it for you?

---

### Post by Magneticgravity on 2007-08-30
OK thanks alot guys, all done :D

---

