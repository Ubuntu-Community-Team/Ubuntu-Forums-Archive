---
title: "How change color depth?"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by ddbann on 2006-12-04
2. Change your color depth to 24 bit, if you haven't already

How?

---

### Post by bodhi.zazen on 2006-12-04
DefaultDepth 16

---

### Post by ddbann on 2006-12-04
where do i change it though?

---

### Post by bodhi.zazen on 2006-12-04
Sorry, I could not resist.

In a terminal:```
gksudo gedit /etc/X11/xorg.conf
```

Look for the line> DefaultDepth 24

And change it to:> DefaultDepth 16

Save and exit.

Now re-start X (ctrl-alt-backspace or sudo /etc/init.d/gdm restart)

---

### Post by aliyanage on 2006-12-04
Hi,

I changed my default color depth in the xorg.conf file. Before you make any changes make sure you do a backup copy of the file
go to:
```
cd /etc/X11/
cp xorg.conf xorg.conf.bak
vi xorg.conf
```

then under the section screen change the default depth to 24.
to be able to write press "i" to exit editing mode press "esc" and then save by typing ":wq" and hit "enter".

that's it... :-)

---

### Post by bodhi.zazen on 2006-12-04
> **aliyanage said:**
> Hi,

I changed my default color depth in the xorg.conf file. Before you make any changes make sure you do a backup copy of the file
go to:
```
cd /etc/X11/
cp xorg.conf xorg.conf.bak
vi xorg.conf
```

then under the section screen change the default depth to 24.
to be able to write press "i" to exit editing mode press "esc" and then save by typing ":wq" and hit "enter".

that's it... :-)

Backup is a good idea, 

should that not be```
**sudo** cp xorg.conf xorg.conf.bak
```

---

### Post by aliyanage on 2006-12-04
yeah sorry totaly forgot, the first thing I type when get into bash is **sudo -s** so I dont have to write any sudo no more. Got used to that... :-D

---

### Post by Not-very-wise-monkey on 2007-02-18
I want to run some Windows apps with Wine but they fail as they require a different resolution and colour depth.  What I want to do is have a script that sets up the screen correctly and then runs the app.  I have figured out how to change the resolution in script but not the color depth - any ideas?

Monkey

---

