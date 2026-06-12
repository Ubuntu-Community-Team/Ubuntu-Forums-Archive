---
title: "restarting the explorer without restarting?"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by goltoof on 2007-10-07
I just used the ever handy xkill function to close a program which wasn't responding. But instead of clicking on the program I clicked on the task bar.. woops!  Now I have no taskbar just the browsers I got open.  Is there a way to restart the explorer (or whatever you call it in Linux, but in Windoze it's the explorer/taskbar) without restarting?

---

### Post by Malibu Illusion on 2007-10-07
ctrl+alt+backspace

---

### Post by frup on 2007-10-07
You can press CTRL ALT Backspace to restart X and go back to the Login Screen

Or you can press CTRL ALT f1 etc to go to a large terminal from there you can type something like /etc/init.d/gnome restart or the like.

There are heaps of options, I'm lazy so I would just use CTRL ALT Backspace, also this is not a problem I get ever :S.

---

### Post by Malibu Illusion on 2007-10-07
**@frup**:

The path you are looking for is:

```
sudo /etc/init.d/gdm restart
```

kdm for KDE.

---

### Post by goltoof on 2007-10-07
> **Malibu Illusion said:**
> ctrl+alt+backspace

Thanks.  Upon seeing your message I didn't hesitate to try it.  As soon as I did it went restart x-windows and displayed what I can only describe as an orgy of system errors. Then I got to a blue screen saying it can't restart xwindows and something about my graphics drivers not working right (I use nvidia).  Here's the one error that looks to be the source of the problem that I wrote down:

Error: bcm43xx_microcoda5.fw not available load failed.

Now I can't get my GUI to start at all it just brings me to a command prompt. I'm writing this in Windoze... ugh.

---

### Post by Whiffle on 2007-10-07
Can you get to /var/log/Xorg.0.log ?  

This will tell you why Xorg crashed in some form or another... 

You can probably do this from windows if your linux drive is formatted with ext3 if you use the driver from here:

[www.fs-driver.org](www.fs-driver.org)

---

### Post by goltoof on 2007-10-07
> **Whiffle said:**
> Can you get to /var/log/Xorg.0.log ?  

This will tell you why Xorg crashed in some form or another... 

You can probably do this from windows if your linux drive is formatted with ext3 if you use the driver from here:

[www.fs-driver.org](www.fs-driver.org)


Yes I have access to it but I don't know what to look at.  I see no reference to the "bcm43xx.fw" error I've been getting.
 
Anything in particular I should be looking for?

---

