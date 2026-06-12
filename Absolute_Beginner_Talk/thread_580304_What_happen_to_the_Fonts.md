---
title: "What happen to the Fonts??"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Good_Newz on 2007-10-18
ok I just installed Gutsy its cool and all i love it..but the terminal font is terrible. What happen? Anyone know the name of the default Feisty font and how to switch back? 

PS. Is it just me or the ubuntu repositories currently down. Since i switched i cannot connect to them ([http://archive.ubuntu.com/bla..bla](http://archive.ubuntu.com/bla..bla) bla)

---

### Post by mivo on 2007-10-18
Rename .fontconfig (in your home directory) to .fontconfig.old and restart X (ctrl+alt+backspace) and see if that helps. If it does not, you can rename it back to .fontconfig. May have to enable the display of hidden files to see the folder. :)

---

### Post by Good_Newz on 2007-10-18
Yeah this made no difference. I think they changed the font to some other font (or at least it looks like so) 

PS. wow this was a fast response :)

---

### Post by ofb on 2007-10-18
> **Good_Newz said:**
>  Anyone know the name of the default Feisty font  

Do you mean the generic before-window-manager terminal view, or a terminal inside the GUI like gnome-terminal?

In the latter the Default profile's General tab has "Use the system fixed width font" checked off, with "monospace 12" greyed out immediately beneath. Under System>Prefs>Font, 'Monospace' is a full name - not a branded sub-variety like 'bitstream vera' or such.

---

### Post by bruce89 on 2007-10-18
> **ofb said:**
> Do you mean the generic before-window-manager terminal view, or a terminal inside the GUI like gnome-terminal?

In the latter the Default profile's General tab has "Use the system fixed width font" checked off, with "monospace 12" greyed out immediately beneath. Under System>Prefs>Font, 'Monospace' is a full name - not a branded sub-variety like 'bitstream vera' or such.

I think they are referring to the tty1-6 terminals.

---

### Post by Good_Newz on 2007-10-18
this might sound stupid but i think all i needed to do is enable subpixel smoothing. Thx a lot guys

---

