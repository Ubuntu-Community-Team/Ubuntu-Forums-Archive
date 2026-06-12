---
title: "Is there a command to blank screen?"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by unbuntu on 2006-04-18
Is there a command that has the same effect as ScreenSaver->File->Blank Screen Now?

---

### Post by x5452 on 2006-04-18
if you go to system>lock screen, it goes to blank or whatever your screen saver is instantly, then you have to enter your password to come back, is that what you mean?

---

### Post by unbuntu on 2006-04-18
No, I want just a blank screen, you know, like when you open the screen saver dialog (Menu->System->Preference->ScreenSaver), In its menu: File->Blank Screen Now.

---

### Post by Nequeo on 2006-04-18
You can also use the key-combo 'ctrl+alt+L' to activate your screen-saver, too. If you're after something you can run from the terminal to black your screen... I'm sure there is, but sadly I'm at work right now (on a Windows box) and cannot go looking for it.

Cheers,

---

### Post by 5-HT on 2006-04-18
[quote=unbuntu]Is there a command that has the same effect as ScreenSaver->File->Blank Screen Now?[/quote] 
If dpms is enabled (same thing as the 'display power management' in the screensaver utility):```
 xset dpms force OPTION 
```; where OPTION takes one of {standby, suspend, off}

Hope that helps.

---

### Post by unbuntu on 2006-04-19
[QUOTE=5-HT]If dpms is enabled (same thing as the 'display power management' in the screensaver utility):```
 xset dpms force OPTION 
```; where OPTION takes one of {standby, suspend, off}

Hope that helps.[/QUOTE]

Thanks for the reply but that's not quite what I wanted.  Because I'm leaving my machine on all night, and yes I can change the time to invoke screen saver to 1 minute, but I don't want to change it back and forth.  So I just want a command to blank the screen when I go to bed.

---

### Post by 5-HT on 2006-04-19
[quote=unbuntu]Thanks for the reply but that's not quite what I wanted.  Because I'm leaving my machine on all night, and yes I can change the time to invoke screen saver to 1 minute, but I don't want to change back and forth.  So I just want a command to blank the screen when I go to bed.[/quote] 
Sorry, I didn't make myself clear.

That command forces a dpms state (standby, suspend, or off).
If you enter it, the monitor will be immediately forced into that state.

It does not interfere, nor has anything to do, with the regular time settings of dpms.

If you enter 'xset dpms force off', the monitor will immediately go into it's lowest power option (could use standby if you just want to blank the screen, but 'off' will use less power) and the normal dpms power management scheme will not be affected.

Hope that clears it up.

---

### Post by unbuntu on 2006-04-19
hooray!  it works.  thanks man.  i gotta make a bash command alias for this. :D

---

### Post by 5-HT on 2006-04-19
[quote=unbuntu]hooray!  it works.  thanks man.  i gotta make a bash command alias for this. :D[/quote] 
I'm glad you found what you were looking for!

---

