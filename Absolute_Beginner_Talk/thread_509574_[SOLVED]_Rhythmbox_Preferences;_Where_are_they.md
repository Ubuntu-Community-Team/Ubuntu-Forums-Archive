---
title: "[SOLVED] Rhythmbox Preferences; Where are they?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by altonbr on 2007-07-25
Where are the Rhythmbox preferences in ~/ folder? And why don't developers name all of their preferences after their program name? Such as .gimp-2.2/.gimp-2.3 or .mozilla-thunderbird etc?

And is that even the correct terminology to say 'preferences'? Googling 'Rhythmbox preferences" returns no relevant results.

---

### Post by kevinlyfellow on 2007-07-25
They use gconf for their configuration.  Open up gconf-editor (alt-f2 and run gconf-editor) and it is under /apps/rhythmbox  If you want the actual files, you can browse through ~/.gconf/

If you are look for some things like where playlists are stored, they are in ~/.gnome2/rhythmbox The lyrics are located in ~/.lyrics

---

### Post by altonbr on 2007-07-25
Why the scatter?

Thanks for the information; I'm looking to delete any entries to it because it seems unable to import my music folder at the moment.

---

### Post by kevinlyfellow on 2007-07-25
> **altonbr said:**
> Why the scatter?


Each has their own purpose.  Gconf is the true preference configuration file.  .gnome2/rhythmbox/ is used to store things like album pics and user generated stuff (it wouldn't be appropriate to put that in gconf).  The lyrics folder I'm not sure why it's on its own.  My guess is so that it can be shared with other music players.

> 
Thanks for the information; I'm looking to delete any entries to it because it seems unable to import my music folder at the moment.

Gconf editor won't help you there (I'm sure you've figured that out... It's annoying how you can just delete entries through it).  You can still use nautilus to delete the correct folder.

---

