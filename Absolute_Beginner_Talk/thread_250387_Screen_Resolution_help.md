---
title: "Screen Resolution help"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-09-04
I just bought a new viewsonic VA903b LCD monitor to replace my old dell CRT and supposedly the optimum resolution is 1280x1024 @ 60Hz

I have the latest nvidia drivers installed but when I try to change the resolution either through the Apps > system tools > nvidia settings or system > preferences > screen resolution ubuntu wont let me go above 1024x768 and the refresh rate isa locked at 85Hz

Can anyone tell me how to get the screen res up, or do I even have to?

Truthfully the resolution is fine as it is but I also heard that if your refresh rate is off you can fry the monitor, is this something I should be worried about?

---

### Post by Wotcher on 2006-09-04
I would also like to know about this. My monitor can go higher than 1024x768 but Ubuntu won't let me. Is there anyway I can get more screen "real estate"?

---

### Post by bodhi.zazen on 2006-09-04
to both of you:

Start with a back-up and then a re-configuration of X:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then re-start X -> Ctrl-Alt-Backspace

If that does not work it will likely take a manual configuration of xorg.config.

Need to know the technical specifications of your monitors- specifically
HorizSync and VertRefresh rates.

Edit this section of xorg.conf (For example):
```
Section "Monitor"
	Identifier	"Monitor1"
	VendorName	"DEL"
	ModelName	"DELL P1110"
	HorizSync	29-121   **# PUT YOUR MONITORS INFO HERE**
	VertRefresh	50-180   **# PUT YOUR MONITORS INFO HERE**
EndSection
```

If you can not follow this advice post:

xorg.conf and your monitor (Brand and model #) and I will try to help further.

---

### Post by charles.g.moore on 2006-09-04
that worked perfectly 

but while i was waiting for a response a stripe about 3 inches wide appeared on the right side of my screen

It's as if where the black stripe is the monitor has been turned off

any ideasd whats going on?  I got a feeling I f-ed this thing up or something...

---

### Post by bodhi.zazen on 2006-09-04
> **charles.g.moore said:**
> that worked perfectly 

but while i was waiting for a response a stripe about 3 inches wide appeared on the right side of my screen

It's as if where the black stripe is the monitor has been turned off

any ideasd whats going on?  I got a feeling I f-ed this thing up or something...

Not sure. Is the stripe covering part of the desktop or is the desktop fully displayed?

If the stripe covers part of the desktop, you likely have a hardware problem.

If the desktop is fully displayed -> adjust your monitors settings (size and position) via buttons on monitor.

---

### Post by gannina on 2006-09-04
I was following along this thread, since I also have trouble with my monitor settings, and I hit crtl-alt-backspace and now my gui is gone... How can I get it back?

---

### Post by charles.g.moore on 2006-09-04
The stripe covers part of the desktop, everything "under" the stripe is accessible.

When you say hardware problem you mean that the monitor may be defective right?

Could I have caused that stripe?  Like I said I surfed around for about a half an hour before I came across your help and finally changed the refresh rate from 85Hz to 60Hz(suggested settings for the monitor) 

I'm trying to figure out whether or not I broke the monitor cause if I didnt Im going back to fry's tomorrow and try and get a replacement...

Wherther I broke it or not im going back to see if i can get a replacement...

---

### Post by charles.g.moore on 2006-09-04
gannina 
it should kick you right back to the login screen but if you are at a prompt try typing 

startx

---

### Post by bodhi.zazen on 2006-09-04
> **gannina said:**
> I was following along this thread, since I also have trouble with my monitor settings, and I hit crtl-alt-backspace and now my gui is gone... How can I get it back?

first: Did you back up?

second: what did you do? did you:
> sudo dpkg-reconfigure -phigh xserver-xorg

If you backed-up:

first log into the system. If you are not at a log-in prompt Ctrl-alt-F1, then log in.

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
should restore X

Type:
```
sudo gdm
```

---

### Post by bodhi.zazen on 2006-09-04
> **charles.g.moore said:**
> The stripe covers part of the desktop, everything "under" the stripe is accessible.

When you say hardware problem you mean that the monitor may be defective right?

Could I have caused that stripe?  Like I said I surfed around for about a half an hour before I came across your help and finally changed the refresh rate from 85Hz to 60Hz(suggested settings for the monitor) 

I'm trying to figure out whether or not I broke the monitor cause if I didnt Im going back to fry's tomorrow and try and get a replacement...

Wherther I broke it or not im going back to see if i can get a replacement...

Sounds like a defective monitor. I do not know that you broke it as modern monitors should not do this, but it is possible.

---

### Post by bodhi.zazen on 2006-09-04
> **charles.g.moore said:**
> gannina 
it should kick you right back to the login screen but if you are at a prompt try typing 

startx

If you trash your xorg.conf GDM will fail as well. It harsh.

stratx will start the defalut desktop, but not GDM.

Once you have restored or fixed xorg.conf; to start gdm; use **sudo gdm** as above.

---

### Post by charles.g.moore on 2006-09-04
thanks for all of the help as far as the screen resolution config.  

I guess ill go and try and get the replacement tomorrow and be sure to do the screen res. config as soon as i plug the monitor in.  

hopefully it wasnt me and they dont give me any crap about it.

once again thanks alot...

---

### Post by bodhi.zazen on 2006-09-04
> **charles.g.moore said:**
> thanks for all of the help as far as the screen resolution config.  

I guess ill go and try and get the replacement tomorrow and be sure to do the screen res. config as soon as i plug the monitor in.  

hopefully it wasnt me and they dont give me any crap about it.

once again thanks alot...

If you get the same monitor you should not have to re-configure X.

---

