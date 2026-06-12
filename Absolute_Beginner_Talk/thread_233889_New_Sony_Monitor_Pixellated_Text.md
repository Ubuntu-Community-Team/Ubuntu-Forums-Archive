---
title: "New Sony Monitor Pixellated Text"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by lark on 2006-08-10
Hi everybody!

I'm still totally loving Ubuntu. :)

I got a new monitor yesterday -- it's a  Sony SDM-HS75 17" LCD (supposed to support up to 1280x1024 resolution w/75hz refresh rate).

Only one problem; all the text looks slightly pixelated under Linux.  In Windows the person setting it up had to run a special program to sharpen the text.

I used some other forum posts and ran the xorg-server, and I think I set everything up (all defaults, 1024x768 and 60hz) okay, but the text is still pixelated (although not as badly).  It's most noticeable in the panel bars and in form boxes like this one.

It gets worse if I switch to 1280 x 1024 resolution or to a higher refresh rate.  I can live with it, but it's kind of hard on the eyes (maybe I just need to get used to the new monitor?  LOL, it's already not bugging me so much).

Anyway, any help would be appreciated!

---

### Post by Anduu on 2006-08-10
Go to System>Preferences>Font....

Select subpixel smoothing and under details check full hinting and see if it helps...you may have to log out and back in to take effect...I'm not sure...

Also post a screenshot if you can.

---

### Post by Drifter on 2006-08-10
My advice, don't buy anything from Sony.  Products are good but with the rootkit and the copy laws they have been able to get passed I just try to avoid them.  However, it is up to the individual, this is just my opionion.

---

### Post by lark on 2006-08-13
Thank you, Anduu!  I tried the Font menu thing, but, sadly, it didn't really change much.  It looked like it would from the samples but nothing changed after I rebooted.

I did some more testing and it's also doing this weird off-set thing; my screen in Linux is half an inch to the right with a black bar, while my Windows screen is centered.  I can fix it -- I just use the auto refresh thing on the monitor's menu -- but I have to every time I dual boot (I know, I know -- just don't load Windows!).

Also, the screen boots at 75hz refresh rate despite changing it in xorg-server.  I've tried twice; now it's at 70hz refresh rate, but still not the 60hz I keep setting it to!

Do you think switching to KDE would help?  I like Gnome (I've got it exactly the way I like it) but I'd be willing to switch.

Drifter, I appreciate your input and can agree with you on the Sony thing.

I try not to buy anything with DRM in it; I got this monitor as a very, very good deal and, since it's the first almost new computer thing I've ever owned over $20 (I'm the end of the 'hand-me-down' chain in our house), I'm keeping it and darn the moral issues!!! (Just this once, anyway!) :)

---

### Post by lark on 2006-08-13
Just wanted to update, I checked KDE and it still has the issue.

Honestly, as this point I'm thinking it's the monitor, at least for the pixelation issue, and that there's not much to be done about it.  I talked to the guy who set up my Windows and he says he used "Cleartype Fonts" (from MS, so no luck on a Linux version!) to "tweak it".  So unless there's an Ubuntu equivalent, I think I'm out of luck.

As far as the weird black bar on the left and the refresh rate go, though, I have no clue!

---

### Post by Anduu on 2006-08-13
Another thing you can try is play with the DPI setting in your Fonts control panel...

---

