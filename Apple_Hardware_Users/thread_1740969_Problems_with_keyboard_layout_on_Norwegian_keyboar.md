---
title: "Problems with keyboard layout on Norwegian keyboard."
date: 2011-04-27
forum: Apple Hardware Users
---

### Post by Aybara on 2011-04-27
I'm running 11.04 on my MBP with Norwegian keyboard layout, and I have some modifier issues I need to sort out.

I followed a blog post that told me to set the following in layout options:
Set “Left Alt is swapped with left Win-key”.
Set “Press any of Alt keys to choose 3rd level”

The behaviour I have now is:
Cmd-Right behaves as super.
Cmd-Left behaves as alt.
Alt-Left doesn't seem to do anything.

If I remove “Left Alt is swapped with left Win-key”, Left Alt still doesn't work.

The behaviour I (think I) want:
Left Alt is Left Alt
Left & right Cmd behave like the WinKey/Super.

I also have the problem that I have to use Esc as Meta in Emacs, but I believe that's an Emacs configuration I can take care of after fixing this other fun stuff.

---

### Post by Aybara on 2011-04-27
Actually the Alt keys work. I use those to get to {}[] on the number keys, but I have to use Ctrl+LeftCmd to switch workspaces instead of Ctrl+LeftAlt.

---

### Post by Aybara on 2011-04-28
Removing the customizations I mentioned in my first port, alt and cmd keys work like the should for launcher, unity, emacs and switching workspaces. I can *not* get to any of the other signs on the number-keys that are reached with shift-cmd in osx (square and curly brackets, for instance).

---

### Post by Aybara on 2011-05-01
I'll continue my rambling:

There's two different scenarios, and I can get neither to work properly.

1. Out of the box. Cmd (Win/Super) and Alt work like they should. I can switch desktops, use unity, use Alt as meta in Emacs. What I can't do is choose 3d level on my keyboard (which I need to get curly/square brackets). All the options I can set for keys to choose 3d level seem to interfere with something else.

2. If I go to layout options and check "left alt and win is swapped", Cmd works as alt, and I can choose 3d level by pressing Shift+Cmd. The Alt key does, however, not begin to function like Cmd did, and does not work as meta.

---

