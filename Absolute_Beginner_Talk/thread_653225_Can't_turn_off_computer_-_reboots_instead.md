---
title: "Can't turn off computer - reboots instead"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by lila on 2007-12-29
Hello,
just installed Gutsy 7.10.  On the whole impressed, will need to iron out a few problems though.  Most importantly: I can't turn off my computer anymore.  I click on the red button in the top right hand corner of the screen and choose the shut down option, and it just reboots.  I really don't like using the unplug "method"...  
To specify:  this is a problem that has happened since Gutsy install.  Never had this with Breezy, which I was using before.  So I don't think it's a hardware problem.
Thanks for any ideas,
Lila

---

### Post by p_quarles on 2007-12-29
I'd start by testing the shell commands for shutting down. The first one to try (I believe this is what the Gnome power button uses) is this:
```
sudo poweroff -f
```
Does that do the same thing?
Then try this one:
```
sudo shutdown -P now
```
Either of them work?

---

### Post by lila on 2007-12-29
Thanks - 
sudo poweroff -f 
works.  I suppose I can do that from now on, it certainly is better than unplugging:) - but it would be handy to be able to use the button.  Do you know what I could do to fix it?  Also, when it shut down, it just sort of did it very quickly, like switching off a TV.  Normally, it is a whole procedure, or has that changed under Gutsy?
Lila

---

### Post by p_quarles on 2007-12-29
It's been awhile since I've used Gnome, so I can't remember where exactly that setting is. But, ultimately you should be able to change the command associated with the button to the one that works. Hopefully someone else here knows and will chime in.

---

### Post by lila on 2007-12-29
Ehem - I have no idea how or why, but now the button works.  I wanted to turn off the computer for the night, fully expecting to need to use the terminal, but thought - well, let's try and see.  And it worked.  Maybe the sudo command somehow fixed things? So I turned it back on to post this.  Hopefully, it will work again once I've logged off.  I'll let you know tomorrow! Thanks again, and good night.
Lila:lolflag:

---

