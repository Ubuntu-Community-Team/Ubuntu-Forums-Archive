---
title: "Help with color"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by alex-quintero on 2006-10-15
Hello,

I've been using ubuntu for a couple of months. It has been a very good experience, I'm thinking about leaving windows in the tiniest darkest unused place of my latop. But there are some little annoyencies that trouble my heart when I'm using ubuntu : 

1. I can't use emacs
2. I can't use amsn (gaim is cool but I want others to se my pic when they talk to me)

the problem in both cases is the same I get the message : 

Undefined color: "black", or
Application initialization failed: this isn't a Tk applicationunknown color name "Black"

I have the spanish (Argentina) version of ubuntu, doest it have something to do? I supposse it's a missing library or something I have to edit, please help.

AQ

---

### Post by bodhi.zazen on 2006-10-15
This should work for you .

See here: [Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

[Enable Repositories Alternate Method](http://ubuntuguide.org/wiki/Dapper#Repositories)

Then:```
sudo aptitude install emacs
```Or use Synaptic.

See here:  [Colorize emacs](http://doc.gwos.org/index.php/ColorizeEmacs)

And for smsn:  [How to amsn](http://ubuntuforums.org/showthread.php?t=75276)

---

### Post by bodhi.zazen on 2006-10-15
If you have these applications installed, try this:

```
sudo ln -s /etc/X11/rgb.txt /usr/X11R6/lib/X11/rgb.txt
```

---

### Post by alex-quintero on 2006-10-15
thanks, no luck do. Now it says i dont have monospace 10 for emacs and amsn still gives me the same message

AQ](*,)

---

### Post by alex-quintero on 2006-10-15
help plz nothing has changed I've done what I've been told and I still have the same problem:( :frown: 

AQ](*,)

---

### Post by bodhi.zazen on 2006-10-15
> **alex-quintero said:**
> help plz nothing has changed I've done what I've been told and I still have the same problem:( :frown: 

AQ](*,)

Try this perhpas:  [Amsn_95](http://doc.gwos.org/index.php/Amsn0_95)

Or this thread:  [Amsn 0.97b](http://ubuntuforums.org/showthread.php?t=216689)

---

### Post by bodhi.zazen on 2006-10-15
You can also try this:

```
sudo ln -s /etc/X11/rgb.txt /usr/share/X11/rgb.txt
```

---

### Post by IYY on 2006-10-15
I don't know how to solve your problem, but

> gaim is cool but I want others to se my pic when they talk to me

You can set your display pic in Gaim, and others can see it, even if you don't see it on the screen.

---

### Post by alex-quintero on 2006-10-15
I like that option better. where?

AQ:confused:

---

