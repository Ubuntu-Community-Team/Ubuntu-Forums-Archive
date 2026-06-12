---
title: "dvorak keyboard layout but keyboard shortcuts are in qwrty"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by grundew on 2007-11-03
Hi,
I've installed gutsy on my laptop with dvorak keyboard layout. This works fine, however i have to use qwrty on the keyboard shourtcut. For instance in the shell i have to press ctrl-d to logout (this should have been ctrl-h if your layout is dvorak). Same story with xpdf but not with emacs or nautilus. Don't understand where this comes from? Anyone have an idea?

---

### Post by laklare on 2007-11-05
I ran across this same issue in Gusty, but it have always existed. I had Dvorak as my default layout and Qwerty installed, but not selected. When I pressed the left control key in gnome-terminal it would switch to Qwerty layout while the ctrl key was pressed. This occurred with ctrl+alt+d to display the desktop as well so it's something to do with gnome, not just the terminal program. I didn't see any option enabled that I know of that would make left ctrl change the layout. Strange.

I solved this in the short term by removing Qwerty entirely under the keyboard control panel. As long as Dvorak is the only layout listed, then it doesn't switch back to Qwerty with left ctrl. I never thought to try the right ctrl key, so I can't say if that behaved differently.

---

### Post by Chonnawonga on 2007-11-06
This is just speculation, but is the CTRL button being used to switch keyboard layouts? I'm using Dvorak, and I haven't had any such problems.

---

### Post by grundew on 2007-11-11
I use both ALT-keys to change keyboard layout, so that shouldn't be the problem. The strange thing is that it's not entirely consistent. In epiphany the keyboard shortcuts are in dvorak, but not in gnome-terminal and tilda.

It was fixed when I removed the qwerty layout completely. Also works when my qwerty layout is below the dvorak layout in the list of keyboard layouts in the keyboard preferences.

---

### Post by john.morales on 2007-11-20
Confirm using Gutsy, just did an inplace upgrade this weekend from fiesty and getting the same problem. Still trying to understand its extent but keyboard is mainly dvorak with shortcuts in qwerty.

---

### Post by brendankehoe on 2007-11-28
I had the same problem with control-key sequences, and did what was described above with removing the non-dvorak layout.  This left "U.S. English Dvorak" and "United Kingdom Dvorak" layout groups in place, and now things like Ctrl-U and Ctrl-C worked.

As an experiment, I then right-clicked on the Keyboard Indicator on the bar at the top of the screen and selected Keyboard Preferences.  I selected the Layouts tab, clicked "+ Add", and added "U.S. English".  This put it at the bottom of the list of selected layouts---and didn't break my ability to do Ctrl-C, etc., in any windows.  I can click on the Keyboard Indicator to change to that layout, and it works as expected.

But I can also go back to one of the dvorak layouts, and they work correctly!  :)  It seems to suggest the control-sequences are based on the first layout in the list...if I'm not misinterpreting a red herring.

B

---

### Post by Dieter@be on 2007-12-15
Maybe this is intended behaviour.
On Mac OS X there are 2 Dvorak layouts, I think they were called "Dvorak" and "Dvorak-qwerty", the first one is the normal Dvorak, while the latter is Dvorak except for keyboard combinations. (upon pressing ctrl it temporarily switches to qwerty)  Maybe what you guys are experiencing is because of a similar concept on Linux.

I'm running Xubuntu and do I not experience this behaviour. (maybe because i just do setxkbmap manually, the keyboard settings dialogue in Xfce is a bit broken)
Ironically enough I would *like* the behaviour you guys described, I think Dvorak is great for typing, but qwerty is much better for short cuts imo.  I'm trying to figure out how I can get this behaviour..

edit : Okay I now managed to get closer : i get qwerty when i type ctrl+shift+... but not yet on ctrl+...
Also my apple key now works on dvorak (with dvorak layout), it didn't before

---

### Post by tiberius_k on 2007-12-21
I don't know about xcfe, but in Gnome this behavior can be acheived by checking a box in the settings(I think) tab, under "group shift-lock behavior." I'm not in front of the computer now but it says something like Left CTRL changes layout. No good to me as I would have to re-re-learn the shortcuts.
Cheers,

I am in front of **a** computer, but at work they only allow KDE or Microsoft, whichever is more approved of by Microsoft.

---

