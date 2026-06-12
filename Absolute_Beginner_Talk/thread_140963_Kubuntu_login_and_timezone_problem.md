---
title: "Kubuntu login and timezone problem"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by Kiran on 2006-03-07
Hi, I've had Kubuntu running on my Toshiba Satellite 1800 (700 MHz) for a few weeks.  I am still trying to work out some issues.  One that's bothering me right now is that when I start up, sometimes the Kubuntu logo and check list will appear, then the screen grays out (which it usually does when it works properly as well) then instead of the Kubuntu GUI login screen, I get a text prompt to login, stating "toshiba tty1"
It accepts my login and password, but I don't know where to go from there.  What I do is hold down the power button and it will go through the shut down procedure.  This is happening recently about half the time, and seems to be increasing.  I just keep shutting down & trying again until I get the desktop.  I tried "startx" at the prompt, but got an error message.

Any ideas?

Also, I had a problem that the clock setting would not go to my local time zone (EST).  I managed to solve that for the desktop display, but it still puts Universal time on my e-mails etc.  I have changed the time in the Kontact preferences as well as the clock configuration, but the problem persists.

Thanks for all the advice & help on these forums.

---

### Post by nocturn on 2006-03-07
[QUOTE=Kiran]when it works properly as well) then instead of the Kubuntu GUI login screen, I get a text prompt to login, stating "toshiba tty1"
It accepts my login and password, but I don't know where to go from there.
[/quote]

The text prompt is in full text mode?  white text on a black background?
If so, this means your Xserver is not always starting.   This can be a  malfunction or an error with the driver configuration.

> I tried "startx" at the prompt, but got an error message.

What was the error message?

> 
Also, I had a problem that the clock setting would not go to my local time zone (EST).  I managed to solve that for the desktop display, but it still puts Universal time on my e-mails etc.  I have changed the time in the Kontact preferences as well as the clock configuration, but the problem persists.


Hmmm.  Are you using Windows on the machine too (dual boot)?
If you open a terminal and type 'date', what does it say?

---

### Post by jamesr on 2006-03-07
I found I had to, ie set it manually

```
sudo tzconfig
```

---

