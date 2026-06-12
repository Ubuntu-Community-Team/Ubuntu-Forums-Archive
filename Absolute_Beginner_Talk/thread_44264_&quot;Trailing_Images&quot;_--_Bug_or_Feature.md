---
title: "&quot;Trailing Images&quot; -- Bug or Feature?"
date: 2005-06-25
forum: Absolute Beginner Talk
---

### Post by polo_step on 2005-06-25
When I move windows around the desktop, I get a trail of the window's images dragging along behind it. Is this a bug or a feature?  :) 

Can I stop it?  It's really irritating as are some of the other video artifacts I'm encountering.

As always, thanks for any help!

---

### Post by Wolki on 2005-06-25
[QUOTE=polo_step]When I move windows around the desktop, I get a trail of the window's images dragging along behind it. Is this a bug or a feature?  :) 
[/QUOTE]

The black lines when you minimize the window are a feature, this sounds like a bug ^^;;

What graphics card do you have?

w

---

### Post by polo_step on 2005-06-25
[QUOTE=Wolki]The black lines when you minimize the window are a feature[/quote]

I'd like to turn that off, if I can.

> this sounds like a bug ^^;;

What graphics card do you have?

Originally, it was the on-board video on this ECS momboard.

Yesterday I changed to a BFGTech nVidia fx 5500oc.  The difference is that now I have to move the window faster to see these afterimages, but they're still definitely there.

It's just like that dumb mouse option for trailing images in MSWindows, which is why I thought perhaps it was someone's idea of a clever "feature."

---

### Post by TheDude on 2005-06-25
[QUOTE=polo_step]
Yesterday I changed to a BFGTech nVidia fx 5500oc.  The difference is that now I have to move the window faster to see these afterimages, but they're still definitely there.
[/QUOTE]

The true nvidia drivers are the best you can do to escape this. Or use KDE.

---

### Post by TristanMike on 2005-06-25
Yeah, me too.  Is it a bug or feature.  I'm running GeForce FX5200 and updated my drivers according to ubuntuguide.org and I get the window tracers/trailers.  And if they are features, how do you turn them off?
TristanMike

---

### Post by weekend warrior on 2005-06-26
Metacity, the default window manager in Gnome, unfortunately doesn't have an option for changing whether to show window contents or not while dragging/resizing.  Neither does it have an option for turning off the min/max animation AFAIK.

There are 3 options I can think of: 

1. Change to KDE. This desktop environment has easy tickboxes for showing content or not while moving, resizing, min/maxing windows and more.

2. Change to XFCE. This also has options for showing window content and doesn't animate min/maxing.

3. Change the window manager in Gnome. I believe Openbox has these options, though perhaps not with simple tickboxes. Here is a [How To for changing to Openbox](http://ubuntuforums.org/showthread.php?t=34239). Try asking there and see if they can tell you specifically if it can do what you're looking for.  

Whichever you choose, you should be able to search these forums for how to do it or find users who have.


EDIT: I forgot the easiest option 4. Just live with it.  :wink: 


HTH

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=weekend warrior]Metacity, the default window manager in Gnome, unfortunately doesn't have an option for changing whether to show window contents or not while dragging/resizing.  Neither does it have an option for turning off the min/max animation AFAIK.

There are 3 options I can think of: 

1. Change to KDE. This desktop environment has easy tickboxes for showing content or not while moving, resizing, min/maxing windows and more.

2. Change to XFCE. This also has options for showing window content and doesn't animate min/maxing.

3. Change the window manager in Gnome. I believe Openbox has these options, though perhaps not with simple tickboxes. Here is a [How To for changing to Openbox](http://ubuntuforums.org/showthread.php?t=34239). Try asking there and see if they can tell you specifically if it can do what you're looking for.  

Whichever you choose, you should be able to search these forums for how to do it or find users who have.


EDIT: I forgot the easiest option 4. Just live with it.  :wink: 


HTH[/QUOTE]


5. Use xcompmgr's fading effect with a Nvidia card. Makes the ugly lines get replaced with beautiful fading.

---

### Post by Wolki on 2005-06-26
> **polo_step]I'd like to turn that off, if I can.[/quote]

It's possible, but I don't remember how. Search the forums for it, there was a thread explaining how to do it. It might lose you some other features though. I got used to it really quickly said:**
> 
Originally, it was the on-board video on this ECS momboard.

Yesterday I changed to a BFGTech nVidia fx 5500oc.  The difference is that now I have to move the window faster to see these afterimages, but they're still definitely there.

It's just like that dumb mouse option for trailing images in MSWindows, which is why I thought perhaps it was someone's idea of a clever "feature."

That is not a clever "feature" but the windows not being redrawn fast enough. There are technologies in X that change that, but they're not fast and stable yet. The binary closed-sourde Nvidia drivers greatly help with both, but there are a few problems that hopefully should be fixed in breezy.

If non of WeekendWarrior's solutions satisfies you, try enabling Composite and run xcompmgr. This will introduce a few graphics bugs[1], but makes the desktop redrawing more smooth and (if you want to) you can enable eye-candy effects like drop shadows, translucency, and fading.
You'll find a howto for this in the Hoary Customization section of the forums. xcompmgr ist still under development, but with nvidia cards it's usable. Not a good solution if 3d Games and OpenGL Screensavers are very important to you, GLX and Composite together is very experimental. Read the HowTo thread for more infos.

[1] For example, the Logout dialog will not be shown. It still works though, hitting Return will log you out.

---

### Post by Sionide on 2005-06-26
[QUOTE=poofyhairguy]5. Use xcompmgr's fading effect with a Nvidia card. Makes the ugly lines get replaced with beautiful fading.[/QUOTE]

Do you *need* an Nvidia card for that?? It sounds nice...

---

### Post by Wolki on 2005-06-26
[QUOTE=Sionide]Do you *need* an Nvidia card for that?? It sounds nice...[/QUOTE]

For fading, yes. It's reported to be painfully slow on Ati. Drop shadows should work fine on Ati too. General compositing and transluceny should work fine too, not really sure about other cards. Without some sort of RenderAccel it will be quite slow.

You can try it out, it's easy to remove it if you don't like it. Knowing a command line text editor (I recommend nano) or how to move/rename files on the command line (if you're smart and do a backup :)) might be of help if you can't get into x anymore. What card do you have?

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=Sionide]Do you *need* an Nvidia card for that?? It sounds nice...[/QUOTE]


Yep....and I bought a cheap 5200 FX to replace my 9600 Pro to get that feature.

---

### Post by polo_step on 2005-06-26
[QUOTE=poofyhairguy]5. Use xcompmgr's fading effect with a Nvidia card. Makes the ugly lines get replaced with beautiful fading.[/QUOTE]
For a new guy, how do I get into xcompmgr to do this?  With this new card, the afterimaging is minimized enough to not be as distracting, but it'd be interesting to tweak this, just to see how to do it.  I don't see anything about it in the GUI "nVidia Settings" in "System Tools."

Oh, and how do I turn off those black lines when minimizing windows, the "feature" mentioned earlier?  I don't think anyone said...

What's really creepy is the angular "lightning bolts" that momentarily streak down across my black desktop when I click on certain launch icons.

Thanks for any help.

---

### Post by Kvark on 2005-06-26
I saw this a few times back on windows with skinned programs like winamp and trillian, didn't bother me. But here it is on normal windows too, which means we see a lot more of it :(

Hope it gets fixed for Breezy.

---

### Post by Sionide on 2005-06-26
I've got a laptop with 64mb gfx card, nothing special. I'll give it a shot and see what it's like...

---

### Post by scourge on 2005-06-26
> 5. Use xcompmgr's fading effect with a Nvidia card. Makes the ugly lines get replaced with beautiful fading.

Nooo!! That's just asking for trouble, I don't think we should recommend any new user to use Composite. Even though the effects work great without any performance hit with my GF 6600GT, weird things begin to happen to my poor Ubuntu system when I use Composite.

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=polo_step]For a new guy, how do I get into xcompmgr to do this?  With this new card, the afterimaging is minimized enough to not be as distracting, but it'd be interesting to tweak this, just to see how to do it.  I don't see anything about it in the GUI "nVidia Settings" in "System Tools."[/QUOTE]

xcompmgr is a new program that adds eye candy to the desktop.

[http://www.ubuntuforums.org/showthread.php?t=20769&highlight=xcompmgr](http://www.ubuntuforums.org/showthread.php?t=20769&highlight=xcompmgr)

Here is how to use it. Please note its a littel unstable- if I need to download something over night I turn it off.

> Oh, and how do I turn off those black lines when minimizing windows, the "feature" mentioned earlier?  I don't think anyone 

Basically there is no easy way. Either use xcompmgr, use KDE or do this:

[http://www.ubuntuforums.org/showthread.php?t=34239&highlight=openbox](http://www.ubuntuforums.org/showthread.php?t=34239&highlight=openbox)

The lines aren't a feature. but they also aren't a bug. Its just how Gnome IS.

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=scourge]Nooo!! That's just asking for trouble, I don't think we should recommend any new user to use Composite. Even though the effects work great without any performance hit with my GF 6600GT, weird things begin to happen to my poor Ubuntu system when I use Composite.[/QUOTE]


xcompmgr is unstable. I said that. I mean it. I'm just honestly telling how to fix this problem....besides using KDE (easiest way to fix that).

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=Kvark]
Hope it gets fixed for Breezy.[/QUOTE]

It won't. The Gnome developers don't see it as a bug. If it really bugs you...you have to do something else said here.

---

### Post by scourge on 2005-06-26
I didn't mean to sound rude or anything, my apologies if I did.

It's just that "unstable" is an understatement to describe xcompmgr. Unstable I can handle, but when a program makes the whole OS crash and sabotages important apps like Firefox, it's bad.

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=scourge]
It's just that "unstable" is an understatement to describe xcompmgr. Unstable I can handle, but when a program makes the whole OS crash and sabotages important apps like Firefox, it's bad.[/QUOTE]

Honestly it doesn't crash the whole OS....it just crashes the xserver...I get your point though. I turn it off over night....and just deal with its crashes.

You are correct that it might not be the best thing to show a new convert....as what might have sold them is Linux's "stability."

---

### Post by polo_step on 2005-06-26
OK, I get it.  It's not "broke," so I'm not going to fix it.

I have enough other things to work on -- like adding this new hard drive, if I can find the information on how to partition and format it in place.

---

