---
title: "[SOLVED] How do I get cube windows?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by brett611 on 2008-01-22
This is a basic question - I want to try out the cube effect.  I have it selected yet I don't see it.  I guess I need to open a 'window' but it appears i don't know what that is.  I have multiple desktops working, I'm able to open various apps, etc but don't know what to do to get this cube going.

ubuntu 7.10

---

### Post by SunnyRabbiera on 2008-01-22
you need to turn on compositing effects...
you may have to download a few extra things though, like compiz-fusion-plugins-extra in the repos

---

### Post by boboyo on 2008-01-22
go to add/remove programs andi install CCSM

---

### Post by Tyke91 on 2008-01-22
if you've got the desktop cube turned on, you should see the cube effect whenever you switch windows. You should also see it if you hold down the middle mouse button and move your mouse (you can emulate the middle mouse button by pressing both buttons at the same time)


also, if you have selected the cube effect from the advanced desktop effects settings, make sure that you have desktop effects turned onto *custom* in the Appearance menu. otherwise you will not see any effects.

---

### Post by rosegarden78 on 2008-01-22
When I activated Beryl or Compiz cube effect on Ubuntu Edgy and Feisty it worked temporarily until X crashed I don't know if it was Beryl or my changing /etc/X11/xorg.conf and not knowing it.  At any rate good luck with the experiment!  Metacity has enough eye candy for me in Gutsy.

---

### Post by brett611 on 2008-01-22
[QUOTE=Tyke91;4187278]if you've got the desktop cube turned on, you should see the cube effect whenever you switch windows. You should also see it if you hold down the middle mouse button and move your mouse (you can emulate the middle mouse button by pressing both buttons at the same time)


also, if you have selected the cube effect from the advanced desktop effects settings, make sure that you have desktop effects turned onto *custom* in the Appearance menu. otherwise you will not see any effects.[/QUOTE

Thanks - Appearance was set to 'none'.  However, whenever I select anything else I get 'The Composite extension is not available'

All other suggested installs have previously been installed

---

### Post by Dreamlocked on 2008-01-22
Edit your /etc/X11/xorg.conf file by changing 

```

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

into

```

# Section "Extensions"
#	Option	    "Composite" "Disable"
# EndSection

```

or 

```

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

Both should work

---

### Post by brett611 on 2008-01-22
Tried both, neither worked.  Got same composite extension error

---

### Post by Vadi on 2008-01-22
Do you know what video card do you have?

Also, do **glxinfo | grep direct** for me in the terminal, what does it say?

---

### Post by brett611 on 2008-01-22
glxinfo = yes

I have an ATI card, everything else is working fine

---

### Post by rustutzman on 2008-01-22
If you have everything and you think it should work try holding ctrl - alt and hit the arrow keys.

Russ

---

### Post by Vadi on 2008-01-22
Ah, okay.

Run this in the terminal:

sudo apt-get install xserver-xgl

Then save all your work, and press ctrl+alt+backspace to restart X. That'll kick you back to the login screen.

When you login, go try enabling the visual effects again, it should work now.

---

### Post by brett611 on 2008-01-22
> **rustutzman said:**
> If you have everything and you think it should work try holding ctrl - alt and hit the arrow keys.

Russ

That switches desktops, works fine

---

### Post by trebor on 2008-01-22
(quote) 	
Re: How do I get cube windows?
Ah, okay.

Run this in the terminal:

sudo apt-get install xserver-xgl

Then save all your work, and press ctrl+alt+backspace to restart X. That'll kick you back to the login screen.

When you login, go try enabling the visual effects again, it should work now. 

This fix worked on mine.

---

### Post by Vadi on 2008-01-23
I think he already has Compiz working.

Did you mean you wanted to have the 3d windows when turning the cube about?

---

### Post by rosegarden78 on 2008-01-23
I got compiz working and a Mac-Dock here:
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
Awesome!

---

### Post by brett611 on 2008-01-23
> **Vadi said:**
> Ah, okay.

Run this in the terminal:

sudo apt-get install xserver-xgl

Then save all your work, and press ctrl+alt+backspace to restart X. That'll kick you back to the login screen.

When you login, go try enabling the visual effects again, it should work now.

Your steps worked, but then things started getting weird, so I uninstalled and now things are back to normal

marking as solved as this gave me what I was looking for but my ATI card must be fubar'ing me.

Thanks alls!

---

