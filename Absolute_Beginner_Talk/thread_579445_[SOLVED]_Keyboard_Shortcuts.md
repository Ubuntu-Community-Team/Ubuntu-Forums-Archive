---
title: "[SOLVED] Keyboard Shortcuts"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Tteddo on 2007-10-18
Is there a way to add keyboard shortcuts? Specifically for the Desktop Switcher. On my Windows 2000 machine I use VirtuaWin and have 4 desktops, each assigned a function key, F1 to F4. In Preferences>>Keyboard Shortcuts there are only shortcuts for the first 2 desktops.

I looked in gconf-editor and there are more in there, but changing them in the 2 sections I could find made no difference. I even (horrors!) tried rebooting.

---

### Post by AtrejuT on 2007-10-18
I don't know if that is what you are looking for but
Ctrl+Alt+Left/Right changes desktops. true, you can only directly go to a desktop next to the one you are on, but that never yet bothered me...

---

### Post by Tteddo on 2007-10-18
I just wanted it to be the same as I am used to. I have been trying to find the answer for a couple of days, off and on, and the minute I posted I went back into gconf-editor and found it. It was under apps/metacity/global_keybindings.
It figures!

---

