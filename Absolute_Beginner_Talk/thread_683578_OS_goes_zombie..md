---
title: "OS goes zombie."
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by B-Z-Z on 2008-01-31
I oftenly find temporal grey window problems (maybe, this results on my 384 mbyte of RAM) but the following is far more serious. 
Once while I was using GIMP the GIMP window everlastingly turned grey and I couldn't click on anything on the screen even the shut down button. I than tried pressing on every buttons on the keyboard but the there was no response and eventually had to pull the power cord off. What cause this problem and how can I avoid any further this kind of problem?
I also don't know how to close the Force Quit window and would appreciate if someone can tell me how to do so.

---

### Post by startherepodcast on 2008-01-31
Such a total system crash is always frustrating, I think saving often is the best protection against data loss. Otherwise: Did you try restarting the X Server (Ctrl+Alt+Backspace)?

---

### Post by Kilz on 2008-01-31
> **B-Z-Z said:**
> I oftenly find temporal grey window problems (maybe, this results on my 384 mbyte of RAM) but the following is far more serious. 
Once while I was using GIMP the GIMP window everlastingly turned grey and I couldn't click on anything on the screen even the shut down button. I than tried pressing on every buttons on the keyboard but the there was no response and eventually had to pull the power cord off. What cause this problem and how can I avoid any further this kind of problem?
I also don't know how to close the Force Quit window and would appreciate if someone can tell me how to do so.

The way I force quit applications is with a Force Quit icon on my panel. Left click on a panel, select Add to panel, then select the Force Quit from the available icons. Then when a program wont behave all you have to do is click that icon then the application.

---

### Post by Joeb454 on 2008-01-31
Do you have compiz enabled by any chance? This may be the reason you're getting the issues...compiz likes RAM (though not half as much as Vista does ;))

---

### Post by B-Z-Z on 2008-02-02
to startherepodcast:
I didn't try Ctrl+Alt+Backspace yet but did try Ctrl+Alt+Delete  and the turn on/off  button on the keyboard (I'm using a laptop, so it is no case); nothing really happened after i did so.

to Kilz:
I could't force quit GIMP 'cos nothing on on the entire screen was able to be clicked. 

to Joeb454: 
the os became zombie again yesterday and I don't think I undeliberately enabled compiz in  both times. 

i feel like the os sometimes work slowly from the start till the end. 
while I was using (illegal) windows xp, the same old computer worked much more smoothly and total system zombie didn't occur (,but I had to change 'cos too much malwares accumulated). by the way. How to close the Force Quit window?

---

### Post by ugm6hr on 2008-02-02
> **B-Z-Z said:**
> to Joeb454: 
the os became zombie again yesterday and I don't think I undeliberately enabled compiz in  both times. 


Compiz is on by default in Ubuntu 7.10.  And if the window turns grey - I think you *must* have it on, since that is Compiz way of indicating "window busy / not responding".

Go to the Appearance page in System Menu and select No Desktop Effects.  Hopefully that will make things more stable for you.

If everything is running slowly - perhaps you might prefer a different Desktop environment?  It might be a bit trickier to use, but will give you a speed boost.  XFCE (Xubuntu) is easy to install, and a bit quicker than Gnome (Ubuntu).  If you want XP-like equivalent look, IceWM is a good option (but requires editing of text files for configuration).

---

### Post by barbedsaber on 2008-02-02
I get the same problem ALWAYS when i use firefox, and when i am scrolling very quickly (to get to the bottem of a page.)now i just press end to get to the bottem, slow it down when i ams scrolling a bit, and live wiht it. I like firefox and opera dosnt do it for me, (neither do anyyof the other browsers i tried) i have 2 gigs of ram, and I will wait for the next firefox, if that dosnt work, i will try getting it fixed, or using another browser.

---

### Post by angry_johnnie on 2008-02-02
it's quite possible that your problem is all due to compiz fusion being enabled.  hit Alt + F2 and type:   "metacity --replace"  (minus quotes) before you start getting any gray screens.  Or, just go to system > preferences > desktop effects, and disable them.  Ctrl + Alt + Backspace should get you out of an unresponsive session.  And the "force quit"  button on the panel should take care of any crazy apps.  As an alternative, you could hold down Alt + F2 and type:  "xkill" (again, minus quotes), that will display a skull-shaped cursor.  Left-click on the app that is causing you trouble, and it will go away.  If nothing works --that is, if you can't force quit, or log out or anything-- then you could hold down Alt + Printscreen and (still holding those two) type: R E I S U B.   This will kill every process and restart your computer.  It's a harsh thing to do, but not nearly as harsh as unplugging the power chord.  Just don't do it unless you really have no other choice.  If you keep getting this problem even when compiz fusion is not enabled, then maybe you should start looking for a different desktop environment.  XFCE is pretty good, and quite popular, too.  But there's a ton of 'em out there.:guitar:

---

### Post by B-Z-Z on 2008-02-07
eventhough the compiz has been removed and no prcess but system monitor is running, the system still uses over 90% out of my 375.5 mb of ram. what is minimum size of ram does gutsy gibbon need in order to make it works smoothly? 
if i had konwn that ubuntu requires extremely much  bigger size of ram than windows xp i wouldn't install it.

---

### Post by fiddledd on 2008-02-07
That is odd, with only System Monitor running I was using less than 130mb of RAM. However I know that Linux doesn't like to waste  RAM so it will reserve a lot for cache. This is released as soon as it is needed though, so it's not actually used up just waiting to be released if you get what I mean.

---

