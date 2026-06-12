---
title: "Alt+F2 and other f-keys not working correctly"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by sweetcancer on 2007-04-29
Hi

My problem is that when i press alt+f2, nothing happens. No run command box no nothing. I've also got beryl on, and when i press alt+f9, i'm supposed to get rain on my screen (the water effect is enabled) but nothing happens. Though when i push F1, the 'help' window appears. This means that the f-keys are somehow working, but not at alla as correctly as i wpuld want 'em to. My keyboard is a Microsoft Digital media keyboard 1.0A and i'm from finland, so i have ö's, ä's and å's. Could you please help me?

---

### Post by freebird54 on 2007-04-29
Two thoughts come to mind.  First off, are you using the right or the left <alt> key when trying these things.  It is possible to have overridden the settings for one or the other without intending it.  Second, on my system it is <shift><F9> to make it rain  :)

Apart from cruising around in System->Preferences->keyboard->Layout options-> and checking 'Alt/Win key behaviour and also third Level Choosers (as the most likely places to find overrides), I'm not sure where to go next...

Hope something in my meanderings helps  :)

---

### Post by sweetcancer on 2007-04-29
Oh shoot i meant Shift+f9, not alt+f9 :D sorry... But it doesn't work with Shift+f9 any better, and the alt+f2 problem isn't about pressing the wrong alt button, 'cause it doesn't work with ANY alt button... I'm not home now but once i get home i will try these tips you gave, Thanks! :)

---

### Post by mejy on 2007-04-29
Does this happen regardless of window manager?  As in, does alt + f2 do anything when using metacity?  Also, try running System -> Preferences -> Keyboard and select you're keyboard and localistaion settings etc.  Finally, run 'xev | grep keycode', click inside the window that comes up and press alt + f2.  Post the output here.

---

### Post by ggaaron on 2007-04-29
Run your beryl-manager
general options->shortcuts->general options->commands (or something like that)
set command0 to <Alt>F2
now in general options->general options->commands set command0 to "dcop kdesktop KDesktopIface popupExecuteCommand".

Works for me=)
Aaron.

---

### Post by H.E. Pennypacker on 2007-05-02
I am also having the ALT-F2 problem (the run window won't appear).  I am not using Beryl.  Just plain Gnome.  Neither ALT keys work when pressing ALT-F2.

---

### Post by sweetcancer on 2007-05-04
Sorry for the delay, haven't had much time to spend with computer... the problem is appearing in metacity also as well as in beryl... the keyboard layout is set to finnish as it should be, and the keyboard model is set to Generic 105-key (Intl) PC in the keyboard perfences (the list doesn't have the Microsoft digital media keyboard though it has some Microsoft models. setting the Keyboard model to any other than Generic 105-key (Intl) PC doesn't work any better, tried that already...) so i tried typing "xev | grep keycode" and when i clicked the box and pressed alt+f2, the result was:

```
hybrid@hybrid-desktop:~$ xev | grep keycode
    state 0x10, keycode 36 (keysym 0xff0d, Return), same_screen YES,
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    state 0x18, keycode 135 (keysym 0x0, NoSymbol), same_screen YES,
    state 0x18, keycode 135 (keysym 0x0, NoSymbol), same_screen YES,
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
X connection to :0.0 broken (explicit kill or server shutdown).
hybrid@hybrid-desktop:~$ 

 
```

What should i do next?

---

### Post by clintonthegeek on 2007-09-08
This thread is a  little old, and I hope this isn't an obvious point, but have you turned on the stupid F-Lock key in the top right that new Microsoft keyboards have?

---

### Post by matchstick on 2007-11-25
sorry for digging up an old thread, but i was having this same problem, and couldnt figure it out.  forgot about the f-lock key.  thanks clintonthegeek!

---

### Post by BlueKoala on 2008-03-20
LOL I had the same problem. I never had a F-lock key. 
This is the first time I hear of one actually.
(Brand new keyboard)
So WTF happenned to my break key? 
And why the heck do I have the useless #&#$ on my keyboad?
Hah! What a surprise! =p

---

### Post by ariel on 2008-03-21
> **matchstick said:**
> sorry for digging up an old thread, but i was having this same problem, and couldnt figure it out.  forgot about the f-lock key.  thanks clintonthegeek!

:) that was my probem
thxs!

---

### Post by ariel on 2008-03-21
You may also want to have a look at "keytouch", it's in the universe repos.
It let's you map the "F-locked keys" back to their non f-locked counterparts, basically overriding the F-lock state, if you want to.

---

