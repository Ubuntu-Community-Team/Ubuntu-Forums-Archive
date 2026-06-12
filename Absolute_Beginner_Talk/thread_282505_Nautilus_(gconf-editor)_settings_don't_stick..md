---
title: "Nautilus (gconf-editor) settings don't stick."
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by BackInTimeMan on 2006-10-22
I used the Nautilus settings in gconf-editor to put a link to the Home folder on the desktop and to change the default background colour of folders. It hasn't worked. I logged out and back in again but still no go. Also, I've noticed a few other settings in there do not correspond to actuality.

Any ideas why this might be so and what to do about it?

---

### Post by CatKiller on 2006-10-22
I haven't tried to do what you've tried to do, but the icons won't appear on the desktop unless /apps/nautilus/preferences/show_desktop is set to true, and the default background colour of folders setting won't have any effect unless /apps/nautilus/preferences/background_set is set to true.

You may know all of this already, of course, in which case I can't help you.

---

### Post by BackInTimeMan on 2006-10-22
> **CatKiller said:**
> I haven't tried to do what you've tried to do, but the icons won't appear on the desktop unless /apps/nautilus/preferences/show_desktop is set to true, and the default background colour of folders setting won't have any effect unless /apps/nautilus/preferences/background_set is set to true.

You may know all of this already, of course, in which case I can't help you.

Well /apps/nautilus/preferences/show_desktop was set to true and I've just set /apps/nautilus/preferences/background_set to true, too. Still no good.

Thanks though, I'll log out/in again in a bit and see if it makes any difference :)

---

### Post by BackInTimeMan on 2006-10-22
Nope, the settings are still not sticking. Any other ideas about this issue?

---

### Post by CatKiller on 2006-10-22
> **BackInTimeMan said:**
> Nope, the settings are still not sticking. Any other ideas about this issue?


Not really. Unless you're using a funky window manager or anything - I've read that Compiz knackers up the desktop icons.

As an alternative, you could drag-n-drop the Home folder from the Places menu to the Desktop for a launcher, and try changing the folder background through the Backgrounds and Emblems settings page of a Nautilus window.

Otherwise, I'm out. Sorry.

---

### Post by BackInTimeMan on 2006-10-22
No, not using Compiz. I've done the drag-n-drop to get a shortcut for now and changed the folder backgrounds as you suggested. Thanks CatKiller!

Anyone else, I still would like to get Nautilus (and anything else) to accept settings done through gconf-editor, so if you have any suggestions about what the problem may be I would like to hear them.

---

