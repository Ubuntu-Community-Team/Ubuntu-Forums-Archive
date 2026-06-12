---
title: "Empty Applications Menu!?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by sid32 on 2007-05-04
I've been using Ubunutu for a week now. I opened the menu editor just as my pc crashed, now when I click on      the applications menu I get an empty list. I read other posts about this and found the applications.menu file, which is all of 3.9k and seems to be empty. How do I get my applications back? 

Thank You..

---

### Post by ronmarley1 on 2007-05-04
> **sid32 said:**
> I've been using Ubunutu for a week now. I opened the menu editor just as my pc crashed, now when I click on      the applications menu I get an empty list. I read other posts about this and found the applications.menu file, which is all of 3.9k and seems to be empty. How do I get my applications back? 

Thank You..
Mine is also 3.9k, but has a bunch of text listings for the shortcuts.  I can send you a copy of mine if you want, but I have customized it a bit.  How about booting to a live CD and copying the applications.menu from that and pasting it to your current setup?  It seems that would work also, and you would have the "basic" menu from a fresh install.

---

### Post by jargoman on 2007-05-04
a last resort might be to go into synaptic manager and mark all the missing applications for reinstallation. it beats editing every single one by hand I once had to on a gentoo machine and just ended up reinstalling

---

### Post by sid32 on 2007-05-04
I tried to over write it, but I get a "you don't have permission to overwrite this file" error. I can't get to an update manager, when I try to install a package from the net, it doesnt make any application items at all. 

I don't know if it is the application.menu being corrupt. As it has also wiped out all of my firefox bookmarks and wont let me add any or import any. Right now I can run programs by clicking on a file(.avi, .mp3), but nothing else seems to work. 

Any ideas? I have another account I can login to, but its not my admin. account, so I don't have a lot of options.   Is there a way to rebuild a missing menu system? 

I can try to uninstall- renistall, but no access to either update manager.

---

### Post by sid32 on 2007-05-05
Is there  a way to repair with the 7.04 cd? I can get menu files from another account, but I can copy them over. Any help? 

ps. alt-f2 and alacarte doesn't work. Menu editor never loads

---

### Post by roketa on 2007-05-07
To get applications menu back just delete applications.menu file. To correct alacarte issue I followed this instruction "If one removes or moves ~/.config and ~/.local/share the original menus are restored". I had some write protected files in there which rm command warned me of. I didn't delete those.

---

### Post by fakie_flip on 2007-05-07
If you create a new user, it will have all the menu items.

---

