---
title: "Message for today"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-15
I  remember in old System V Unix days that the motd command displayed a random inspirational or smart alec quote.  Ubuntu's motd command just displays the contents of /etc/motd.  Is there another command that does what the Unix motd command did?

Carl

---

### Post by ghost_ryder35 on 2007-10-15
I have no idea.  I never knew that the Unix systems displayed something inspirational.  Got any screen shots from Unix?  Would make an awesome desktop wallpaper :)

---

### Post by schorsch on 2007-10-15
Just install the package "fortune-mod", add the following line to your .bashrc
```
/usr/games/fortune
```
and open a new shell.

---

### Post by phyrewall on 2007-10-15
Couldn't you run a daily cron job with fortune piping into the motd file? Then you could add the motd to bashrc or somewthing so you see it when you use the terminal..

--EDIT---
schorsch beat me to it.

---

### Post by LowSky on 2007-10-15
one of the widgets you can add to you gnome desktop bars is Wanda the fish, when clicked gives a message

---

### Post by cwmoser on 2007-10-15
I note that the fortune command works similarly to what I thought was the old Unix motd command.  Maybe I was wrong and its the fortune command and not the motd command that I remember in Unix.

Anyway, what I wanted to do was find the source code and port it to a system that reads text messages and plays them thru the sound card.  In effect, say every morning speak out via PC sound card speakers a fortune message.

Carl

---

### Post by cwmoser on 2007-10-15
Where do I find the source code for fortune.c?

Carl

---

### Post by Steveway on 2007-10-15
> **cwmoser said:**
> Where do I find the source code for fortune.c?

Carl

Google!


Also: [http://fortune4all.sourceforge.net/](http://fortune4all.sourceforge.net/)

---

