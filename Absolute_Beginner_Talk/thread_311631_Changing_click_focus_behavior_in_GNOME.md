---
title: "Changing click focus behavior in GNOME"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Ferri on 2006-12-03
I've been using KDE until recently. I've switched to GNOME, and I'm quite satisfied with the change except for the behavior I get when I click on a window.
When I have to open windows I would like to get the focus on the window I point my mouse (which I have) but I don't want to get this window on top of the other, even if I click on it.
I find this very useful when I copy something from one window to the other, for example if I want to copy some instructions in a "how-to" in this forum to a terminal without having the browser hiding the terminal, using copy and paste.
It was possible to set this in KDE, but I can't find this option in GNOME.
Is this option hidden somewhere or it just doesn't exist?
Thanks

---

### Post by argie on 2006-12-03
System > Preferences > Windows may help if you're in Dapper. There you can choose how to focus. But I don't understand *"I don't want to get this window on top of the other, even if I click on it."*. How exactly do you get one window on the next otherwise?

---

### Post by Ferri on 2006-12-03
Thanks for the quick response.
> But I don't understand "I don't want to get this window on top of the other, even if I click on it.". How exactly do you get one window on the next otherwise?
If I have a Firefox window and a terminal one, for example (might be a text processor or whatever), if I select a text in Firefox in order to copy and paste it to the terminal, The firefox window comes on top and the terminal disappears. Of course, I can change again with alt-tab, but I'd like to be able to skip this, having the terminal window inactive but over the Firefox window, not going behind it like now.
In the preferences you mention I can set the focus setting but not the raise window one; in KDE you can chose if you want the window to raise or not when you click on it, is it possible in GNOME?

---

### Post by mcduck on 2006-12-03
I'm not sure if the option is in the GUI menu, and I can't check it now as I'm using Beryl.. But at least you'll find the option in Configuration Editor (alt-f2 and run 'gconf-editor'). Go to apps/metacity/general and disable 'raise on click'.

---

### Post by Ferri on 2006-12-03
Thank you very much. I had been quite a while searching for this option without luck... :oops:

---

