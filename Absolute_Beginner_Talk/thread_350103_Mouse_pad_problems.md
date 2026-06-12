---
title: "Mouse pad problems"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by dannyboy2k on 2007-01-31
Hi,

This is a minor irritation. I've installed Ubuntu on my laptop which, like most, has a mouse pad at the front of the keyboard.

Ubuntu works perfectly well with this (in fact I think it's awesome) but it enables the mouse pad to select things by tapping on the pad rather than just using the buttons (windows did this in when I first got it to). This means that if I'm typing and my thumb brushes over the pad it will move where I type to where the cursor is on the page or it will select all the writing up to where the cursor is, delete it and start me writing there again.

Like I say this is a minor irritation, I can always use the undo button. But if somebody could explain how I can turn off the 'tap on pad to select' function, like I did in windows, it would be great. [-o< 

I've checked the mouse preferences in: **systems>preferences>mouse**. But there is nothing about the mouse pad there, just the cursor icon, etc.

Other than that Ubuntu is working amazingly well, like I said it's awesome! Well done!


Cheers\\:D/ 

Dan

---

### Post by mikewhatever on 2007-01-31
I don't know which touchpad you have, so it's hard to say. Mine is Synaptic, and after installing gsynaptic support, more features appeared, tapping included.

---

### Post by dannyboy2k on 2007-01-31
I think my mouse pad is synaptics. So I've installed the gsynaptic through synaptic package manager.

Now I have a touchpad option in my **system>preferences>** menu.

But when I click on it I get the following message:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

So I:

sudo gedit /etc/X11/xorg.conf

And the part about the mouse does say true! Hmm.....

I'll try restarting my computer and see what happens then.

Cheers

---

