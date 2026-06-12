---
title: "Keyboard shortcuts for keyboard indicator on Ubuntu Gutsy"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-04-07
hello everyone, 

I constantly need to switch between four working languages when I'm on OpenOffice.org. At the moment, I'm using the keyboard indicator. It'd be much handier (and faster!) if I could allocate a keyboard shortcut (ideally four combination ctrl + 0 / ctrl + 9 / ctrl + 8 / ctrl + 7) to each working language. 

Does anyone know how to do this?

Many thanks.

---

### Post by FreewareFan on 2008-04-07
You might try either of two programs that are available thru your Synaptic program manager.  They are "hotkeys" and "keytouch".  Might do what you are looking for, with some configuration.

---

### Post by al.adab on 2008-04-07
thanks FreewareFan

I installed both, and tried to run them on terminal. Keytouch asks me to select from a list of keyboards (where no HP pavillion dv2000 is listed) and Hotkeys asks me to set my keyboard on terminal...now, I checked "keyboard" (system>preferences) and found (at "layout") that my keyboard model is *Generic 105-key (Intl) PC*.

Can you tell me exactly what to type in terminal after I get the following: 

[I]~$ hotkeys
hotkeys: You must set the keyboard type, use hotkeys -t <type> to set it[/I]

provided that this is what I should do with "hotkeys" in the first place"? What about "Keytouch"?

Thanks!

---

### Post by FreewareFan on 2008-04-07
I personally have never used hotkeys, so for you, a "man hotkeys" might be in order.  As for Keytouch, after you install it, go to System - Administration - Keytouch Editor and follow the routine.  Again, if you need more help with it, use the "man keytouch" command, or visit either one of their homesites for further information.

---

### Post by al.adab on 2008-04-07
I know this is going to sound rather dumb, but I really didn't get anywhere close to configuring a shortcut for the language switch. I tried everything I could think of and had a look at the info available. 

 If the info available is clear enough for anyone to work it out, than it's really me who's dumb. I just wonder if 

a) anyone who's got an HP Pavillion dv2000 knows exactly what to do (starting from having the right keyboard name which I can't insert in Keytouch;
b) what commands I should exactly use to modify any "man-hotkey" in terminal;
c) why isn't it possible to either enable a language switch shortcut through "keyboard indicator>keyboard preferences" or "System>Preferences>keyboard shortcuts". 

thanks again.

---

### Post by FreewareFan on 2008-04-07
I believe you misunderstood me.  It's not man-hotkey, it's  man hotkey.  That stands for "show me the manual for the program hotkey."   Same for man keytouch.  Those commands will bring up the entire user manual, and you can read through the instructions for configuring and such.

---

