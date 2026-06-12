---
title: "keytouch messing up my system"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by AlmaTlust on 2007-10-11
Hi,
I tried installing keytouch for my Sony Vaio PCG-K115S, played around with Keytouch editor, and now my keyboard's messed up. When I press the ctrl key, konqueror gets started, any combination with ctrl doesn't work any longer (no ctrl-alt-esc, no ctrl-alt-backspace, etc...)
What can I do?

---

### Post by philinux on 2007-10-11
I think if it was me I'd uninstall it and try again.

---

### Post by AlmaTlust on 2007-10-11
I did that already, but it didn't help... :-( 
It probably has written some stuff in some config file that is processed on startup, but I don't know where to look and what to do.

---

### Post by philinux on 2007-10-11
Go to synaptic and choose remove completely that will get rid of any config files.

---

### Post by AlmaTlust on 2007-10-11
Purging and restarting did the trick - thank you!
I still wonder why such a thing would happen, though... ;-)

---

### Post by philinux on 2007-10-11
Like you said you played around with the editor. You may have accidentally changed something important. Glad its solved. If you browse you home folder and click view - show hidden files you'll see all the folders where the config files live. They are all preceded with a . Like .mozilla
Thats why backing up your home folder can save a lot of time after a reinstall.

---

