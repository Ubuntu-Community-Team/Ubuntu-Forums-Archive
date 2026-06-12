---
title: "Notebook software"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Aryding on 2007-08-24
I have an ASUS W3J notebook with ASUS battery software called Power4Gear.  I'm looking to find a good alternative because I'm thinking of using Ubuntu quite often when on battery power.  Has anyone gotten Power4Gear to work at all?

Also, my notebook has quick buttons on the side to disable bluetooth/wireless/ect.... is there anyway I can utilize these buttons?

---

### Post by shearn89 on 2007-08-24
Not sure about the powergear stuff, but you should be able to get your keys to work by editing the keybindings... I'll do a quick hunt, cos i'm sure i've seen stuff on it before.

EDIT: I think i found it - press "alt-f2", and type "gnome-keybinding-properties"

---

### Post by Aryding on 2007-08-24
> **shearn89 said:**
> Not sure about the powergear stuff, but you should be able to get your keys to work by editing the keybindings... I'll do a quick hunt, cos i'm sure i've seen stuff on it before.

Wow, thanks!  I've looked around but have come up empty...

---

### Post by Aryding on 2007-08-24
> **shearn89 said:**
> 

EDIT: I think i found it - press "alt-f2", and type "gnome-keybinding-properties"

So if I press the keys it will tell me what it's "name" or whatever it is?  It's not any actual key on the keyboard.  It's on the side of the laptop.


It seems that I have found my forum threads:

[http://forum.notebookreview.com/showthread.php?t=118390&highlight=ASUS](http://forum.notebookreview.com/showthread.php?t=118390&highlight=ASUS)

[http://ubuntuforums.org/showthread.php?p=2489831#post2489831](http://ubuntuforums.org/showthread.php?p=2489831#post2489831)

Looks like the left buttons will be able to work but not the right side because they appear to trigger scripts in /etc/acpi.  Has anyone figured this out yet?

---

### Post by shearn89 on 2007-08-25
You might be able to get them to work by writing your own scripts, although it won't be that easy... A google for "laptop buttons /etc/acpi scripts" turned up a site that talked about an asus laptop ([here]("http://www.ngolde.de/laptop.html")), but the keybinding codes will be different for your buttons. I think with a little work you could make it all fully functional.

---

