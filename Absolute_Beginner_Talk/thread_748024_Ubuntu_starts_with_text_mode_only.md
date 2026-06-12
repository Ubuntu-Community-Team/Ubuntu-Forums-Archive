---
title: "Ubuntu starts with text mode only"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Mosaab on 2008-04-07
I have a problem that ubuntu starts command based only,
and when I type startx  it gives me an error message.

I want to say that the problem is that I wanted watch a movie on my TV so I missed around with graphical tool in prefrences. and I think that this is whats causing the problem. I didnt touch any thing else other that this.

I dont know if this helps... but when I type "runlevel" it outputs "N 2"

is there a way to reset the configurations?

Thanks

---

### Post by rjmoerland on 2008-04-07
Reconfiguring the x server might help. In a terminal, type:

sudo dpkg-reconfigure xserver-xorg

Just a thought

---

### Post by SunnyRabbiera on 2008-04-07
well what tool did you play around with may i ask?

---

### Post by Mosaab on 2008-04-07
I dont remmember the name exactly .. but its the tool where you set your default monitor.

---

### Post by SunnyRabbiera on 2008-04-07
that might be your problem there... was it the one you had to type in your password with?

---

### Post by Mosaab on 2008-04-07
Actually I dont remmeber if it asked me for a password ... but its the one that has 2 screens and you click on a screen so you can set it as your default screen ... 

and I would like to add here ... that when I start ubuntu .. the screen flickers acouple of times to determine the right resolution!

---

### Post by Mosaab on 2008-04-07
running this:
sudo dpkg-reconfigure xserver-xorg 

solved my problem, thank you so much guys.

but do you know what is the configuration file was changed exactly ? (just to know)

---

### Post by guilly on 2008-04-07
that would be your xorg.conf file located at /etc/x11/xorg.conf

---

### Post by Mosaab on 2008-04-07
why the output was "N 2" when I typed runlevel ? was I running ubuntu in level 2 ?

---

### Post by ByteJuggler on 2008-04-07
Yes, runlevel 2 is the default Ubuntu runlevel.  (You can have several runlevels defined on your system, with different sets of services and text consoles  and/or XWindows either enabled or disabled, e.g. configured seperated per runlevel.)

---

### Post by Mosaab on 2008-04-07
So this means that ubuntu chose the runlevel for me when it found that the configuration file is messed up.

---

### Post by guilly on 2008-04-07
yes exactly... It just defaulted to run level 2 when it couldn't start X

---

### Post by jkeyes0 on 2008-04-07
you might also check what's in the /var/log/Xorg.0.log file
```
nano /var/log/Xorg.0.log
```

There will be something in that file that shows you an error message. (or if you can post that file here, we might be able to help out by reading it)

---

### Post by ByteJuggler on 2008-04-07
> **Mosaab said:**
> So this means that ubuntu chose the runlevel for me when it found that the configuration file is messed up.

Well not exactly.  The normal runlevel is 2.  It would be 2 even when your graphics were working.

---

