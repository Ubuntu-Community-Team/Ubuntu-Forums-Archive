---
title: "UK keyboard help, pls"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by fzf3 on 2006-10-30
I can't get the sterling/pound symbol working in openoffice.
I applied a fix for this some time ago (the details of which I can't remember). It worked until I restarted Ubuntu.

Also, since applying this fix (which no longer works), every time I login, I get this error message:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

TIA for any suggestions.

---

### Post by funkyade on 2006-10-30
sounds like a missing or corrupt keyboard map...

try reinstalling a few things -

```
#> sudo aptitude reinstall libxklavier xmodmap libxkbfile1  openoffice.org2-l10n-en-gb
```

and see if that makes a difference.

---

### Post by fzf3 on 2006-10-30
That made no difference.

Shift-3 still results in a "3", not a pound sign.

---

### Post by fzf3 on 2006-10-30
anyone?

---

### Post by steve.horsley on 2006-10-30
Does this happen in a console too? Press Ctrl-Alt-F1 to find out, and Ctrl-Alt-F7 to the the GUI again.

If it helps, my UK keyboard has this entry in /etc/X11/xorg.conf:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

```

I have **no** idea how to fix a console keyboard layout.

---

### Post by fzf3 on 2006-10-30
Yes, it happens in console, too.

xorg.conf contains this:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "uk"
EndSection

---

### Post by radwis on 2006-10-31
I have the same issue, but with Polish diacritic symbols. The system errors are the same. I reported a bug in the Launchpad.

The possible workaround, which is a temporary solution for me is to add a line into Gnome-Session:
code:
xmodmap /usr/share/xmodmap/xmodmap.pl


for your case it should probabely be ....xmodmap.uk

radwis

---

### Post by pattymnaish on 2006-10-31
Try changing ```
Option "XkbLayout" "uk"
``` to ```
Option "XkbLayout" "gb"
```

---

### Post by fzf3 on 2006-10-31
Thanks, radwis.

If I open a console window and enter:

xmodmap /usr/share/xmodmap/xmodmap.uk

then I get the "£" symbol when I type shift+3, which is what I want!

However, when I logout or restart the system, shift+3 reverts back to just giving me a "3" again!  ](*,) 

So, I suppose now I'm looking for a way to have this "xmodmap" command executed every time I login.

---

### Post by fzf3 on 2006-10-31
Hard to believe that I'm the only UK user of Ubuntu 6.06 with this problem.

Does anyone have a solution or able to tell me how to run the xmodmap command automatically on startup?

---

### Post by PriceChild on 2006-10-31
> **fzf3 said:**
> Thanks, radwis.

If I open a console window and enter:

xmodmap /usr/share/xmodmap/xmodmap.uk

then I get the "£" symbol when I type shift+3, which is what I want!

However, when I logout or restart the system, shift+3 reverts back to just giving me a "3" again!  ](*,) 

So, I suppose now I'm looking for a way to have this "xmodmap" command executed every time I login.System>Preferences>Sessions.

Startup tab, add it there :D

---

### Post by fzf3 on 2006-10-31
Add WHAT there?

I tried that already. Creating a text file containing the command and adding it as you suggest. It did nothing.

Kindly spell it out. 

I'm a complete NOOB to Linux. That's why I'm here. I can't believe it's so ****** difficult to get a damn pound sign working from my kbd.

---

### Post by radwis on 2006-11-01
just insert the line
xmodmap /usr/share/xmodmap/xmodpam.uk 

at the gnome-sessions (System->Preferences->Sessions then tab Startup Programs or something)

so, then with every login, gnome-session will start that for you

---

### Post by radwis on 2006-11-01
in the above post I made typo, the line should be:

xmodmap /usr/share/xmodmap/xmodmap.uk

---

### Post by Mr_Bond_UK on 2006-11-01
Surely if tou go to the admin or preferance tab and change the keyboard layout there it'll work? thats all i did and it seems to be fine! my biggest problem was the @ sysmbol being shift 2. as well as the £ symbol not working. just experiment with the keyboards on there.

---

### Post by fzf3 on 2006-11-01
Nope. System > Preferences > Keyboard > Selecting UK keyboard doesn't work (every other key on my kbd works OK, except shift+3 still gives a "3" not a "3"  (see what I mean?, that should be a pound sign).

Neither does adding the xmodmap command into my startups.

---

### Post by hellodotcom on 2006-11-01
lol](*,) ](*,) ](*,) ](*,) :KS :KS

---

### Post by Zeerak on 2006-11-01
Personally I use abiword and I haven't had a problem with that, perhaps temporarily use it until there's a fix?

---

### Post by Andrew_Mackay on 2007-02-10
In the xorg.conf file (in /etc/X11), under the keyboard section, try replacing:

Driver "kbd"
by
Driver "keyboard"

I think this was the important change. Other options I used were ( I have an old UK keyboard):

Option         "CoreKeyboard"
Option         "XkbRules" "xorg"
Option         "XkbModel" "pc101"
Option         "XkbLayout" "gb"

This now works for me.

---

### Post by bryncoles on 2008-02-04
i'm also having this problem with 7:10, gutsy. i've no pound sign, get the Xkb error, and though id like toi try these solutions, i dont know how to open the xorg.conf file so that i can save changes. i dont have permissions! 

how can i resolve this please?

*edit*

oops, fixed it! im getting good at asking questions then figuing out the answer.... right clicking, aelecting 'open with' and adding 'gksudo' to the begining fixed it. 

also: fixed the keyboard problem by following someone elses thread : 

terminal 'gconf-editor', then desktop -> gnome -> peripherals -> keyboard -> Kbd and change 'layout' to your country code. mines 'gb'!

---

