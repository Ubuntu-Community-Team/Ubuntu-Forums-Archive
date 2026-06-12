---
title: "[FIXED] Problems with keyboard layout after last update :("
date: 2017-12-27
forum: Arch and derivatives
---

### Post by dantruong02 on 2017-12-27
[COLOR=#000000]Hello, I got strange problem with keyboard layouts after the last update. Before the update I could see what layout currently in use, using the keyboard indicator on gnome panel, and every window had the layout I set for it, like if I was chat with someone in Russian, the pidgin window had Russian layout when I opened it (maximized) and other windows like firefox had English layout.[/COLOR]
[COLOR=#000000]After the update, keyboard indicator don't show the layout in use anymore but always shows "USA" no matter what language I'm using now (Layouts do change when I press Alt+Shift, I just can't see what layout is in use now) + all layouts are global, than means if in Firefox I switched to Russian, then pidgin will have Russian too, and even urxvt sometimes.[/COLOR]
[COLOR=#000000]In keyboard preferences I do have a "v" in "Separate layout for each window" but it does not work.[/COLOR]
[COLOR=#000000]Its pretty annoying and very hard to work in this way.[/COLOR]
[COLOR=#000000]Can somebody help me? Even if its possible to tell me what version was prior to the update so I could downgrade.[/COLOR]
[COLOR=#000000]Thanks a lot![/COLOR]

[COLOR=#000000][Solved][/COLOR]
[COLOR=#000000]I downgraded libxi to 1.1.4 instead of 1.2.0 [/COLOR]:smile:

---

