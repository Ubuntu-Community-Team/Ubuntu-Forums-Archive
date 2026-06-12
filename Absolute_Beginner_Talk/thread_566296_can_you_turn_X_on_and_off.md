---
title: "can you turn X on and off?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by 900donuts on 2007-10-03
i want to make a system with very little memory (an old 1990s sub-notebook that i plan to use as an alternative to the ipod) to accomplish this i would have to use the command line to do things like play movies and songs but i'm not good at configuring systems in the command line so i want to keep X around to do that stuff and turn it off when i'm not using it so theres enough resources to play movies (which comprise about 99.9% of my media collection)

P.S. dose logging out turn X off?

P.S.S. i'm looking at a system that could have anywhere between 32MB and 80MB of ram

---

### Post by Martje_001 on 2007-10-03
> **900donuts said:**
> P.S. dose logging out turn X off?
No, you still have a GUI. You have to prevent GDM from starting.
```
sudo apt-get remove gdm
```

---

### Post by Terl on 2007-10-03
> **900donuts said:**
> i want to make a system with very little memory (an old 1990s sub-notebook that i plan to use as an alternative to the ipod) to accomplish this i would have to use the command line to do things like play movies and songs but i'm not good at configuring systems in the command line so i want to keep X around to do that stuff and turn it off when i'm not using it so theres enough resources to play movies (which comprise about 99.9% of my media collection)

P.S. dose logging out turn X off?

P.S.S. i'm looking at a system that could have anywhere between 32MB and 80MB of ram

Just use the alternate cd.  It will install a basic CLI system for you.  No sense even installing X if you are not going to use it.  I do not know how well Ubuntu will work on the older pc you mention.  For what you describe I would install Slackware.  You could even use x with it as long as you used a very light window manager like openbox, fvwm, ratpoison etc.

---

### Post by Seisen on 2007-10-03
Try a minimal install here is a link on how to do it.

[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by Martje_001 on 2007-10-03
He says he want to keep it! Just remove gdm like i said in my previous post. If you want to start X do 'startx'

---

### Post by 900donuts on 2007-10-03
so i have to remove gdm. then how do i turn X on again when i need it? 

plus i thought the login splash screen thing was done with the framebuffer which is also used to display graphics without X like movies or tux

EDIT:yikes! you guys answer fast i spend 5 min to type a reply and 3 more posts aprear!

---

### Post by Seisen on 2007-10-03
With that little bit of memory the only option is a minimal system unless you want it to take 10 minutes to boot up. Also you have to have X to play any kind of media player.

---

### Post by Martje_001 on 2007-10-03
> **Seisen said:**
> With that little bit of memory the only option is a minimal system unless you want it to take 10 minutes to boot up. Also you have to have X to play any kind of media player.
No you don't. You can run a server, maby with LCD screen.

---

### Post by multifaceted on 2007-10-03
To switch out of x and into a console (Ctrl-Alt-F1) and then back to X (Ctrl-Alt-F7)

---

### Post by 900donuts on 2007-10-03
in the order they were posted

i don't need x to play movies iv'e done it on my desktop pc in the command line using mplayer and the framebuffer and i don't care if it takes 10min to boot after i type startx as long as it works once it gets there

a guy who has a similar note book told me the pcma slot is only 16bit. which means networking is going to be tricky, and wireless will be impossible.

if i press ctrl+alt+f1 x will still be in the background (right?)

---

### Post by Terl on 2007-10-03
Yes x will still be running.   I found this answer for Debian:  > You can prevent automatic running of the GUI when you boot your debian machine by disabling your login manager be it KDM, GDM or XDM from running at boot time. To disable the login manager from automatically running at boot up, run the following command as root

#update-rc.d -f gdm remove

Replace gdm with kdm or xdm if they are what you use.

To start X manually, you would then have to login at the command prompt and enter the command startx.

To reset your login manager so that it runs at boot up, do

#update-rc.d -f gdm defaults 


This should work for Ubuntu.  You would start in text after you run it so you would have to login text mode and startx when you wanted to have x.

I found it here:  [http://www.debianadmin.com/howto-boot-debian-in-text-mode-instead-of-graphical-mode-gui.html](http://www.debianadmin.com/howto-boot-debian-in-text-mode-instead-of-graphical-mode-gui.html)

---

### Post by 900donuts on 2007-10-03
one last question 

how do i turn it off again after i'm done?

---

### Post by Terl on 2007-10-03
```
sudo /etc/init.d/gdm stop
```

do that from the ctrl-alt-F1 terminal

---

### Post by 900donuts on 2007-10-03
any way to do it with less typing (like telling it if i say donut its to turn off)

EDIT: i don't mean voice command

---

### Post by Terl on 2007-10-03
I suppose you could make a script with a short name.  Not sure about an alias as I have not played with it much.  Alias should work.  See this:  [Bash tutorial]("http://www.hypexr.org/bash_tutorial.php#alias")  > alias donuts='/etc/init.d/gdm stop'

Are you going to be starting the system in text mode and only going to X occasionally, or the other way around?

---

### Post by 900donuts on 2007-10-03
text mode for play x for work since i'm building this so i won't ever have to buy a ipod play has priority

so yes i will only use x occasionally and maybe some day grow out of it

---

### Post by Terl on 2007-10-03
I would give the alias command a go.  You could even alias startx so like > alias x='startx' and use the one above "donuts" to turn it off.

---

### Post by 900donuts on 2007-10-03
i was just using donuts as an example i would probably use a 2 digit number or a function key but thanks for your help

you rock:guitar:

---

