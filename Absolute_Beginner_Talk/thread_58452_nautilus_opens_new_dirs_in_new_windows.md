---
title: "nautilus opens new dirs in new windows?"
date: 2005-08-20
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-08-20
Is there a way to get nautilus to behave like windows explorer (sorry!) in that it never opens a new window when you go into a new directory but stays in the existing one? I am sure I saw the option somewhere but I can't find it now.

---

### Post by heimo on 2005-08-20
Can't verify it, but I believe the option you're looking for is in Edit->Preferences->Behaviour->Always Open in Browser Windows

---

### Post by gammyhand on 2005-08-20
[QUOTE=heimo]Can't verify it, but I believe the option you're looking for is in Edit->Preferences->Behaviour->Always Open in Browser Windows[/QUOTE]
 Pretty sharp heimo, pretty sharp :)

---

### Post by Kvark on 2005-08-20
Wow, that has been annoying me for quite some time. Thanks for pointing out the solution! :grin:

This should be default! To open a new window and close the old one doesn't make sence when keeping the current one achieves the same result but without jumping around.

But... these huge useless buttons suddenly appeared on top of the window, any way to make them smaller or hide them entirely?

---

### Post by heimo on 2005-08-20
You can disable closing of parent directory by setting no_ubuntu_spatial using System Tools->Configuration Manager. Path is: ```
/apps/nautilus/preferences/no_ubuntu_spatial
``` 

I don't know abot the buttons, check View menu.

I really, really like Breezys Nautilus (2.11.91, will be 2.12 in release I think).

Third screenshot on this page shows what I mean (but doesn't cover all the nice new features, like tree view):
[http://www.generation-nt.com/actualites/8461/Gnome-212-annonce-la-couleur](http://www.generation-nt.com/actualites/8461/Gnome-212-annonce-la-couleur)

---

### Post by gammyhand on 2005-08-20
[QUOTE=heimo]You can disable closing of parent directory by setting no_ubuntu_spatial using System Tools->Configuration Manager. Path is: ```
/apps/nautilus/preferences/no_ubuntu_spatial
``` 

I don't know abot the buttons, check View menu.

I really, really like Breezys Nautilus (2.11.91, will be 2.12 in release I think).

Third screenshot on this page shows what I mean (but doesn't cover all the nice new features, like tree view):
[http://www.generation-nt.com/actualites/8461/Gnome-212-annonce-la-couleur](http://www.generation-nt.com/actualites/8461/Gnome-212-annonce-la-couleur)[/QUOTE]
 I have treeview on hoary....have you missed it? Or is it enhanced?

---

### Post by heimo on 2005-08-20
[QUOTE=gammyhand]I have treeview on hoary....have you missed it? Or is it enhanced?[/QUOTE]

Oh, could be that I missed it. Can Hoarys nautilus do sidebar treeview? I think that's new. Anyway, it's neat file browser and first one on Linux OS that I have used for real work.

---

### Post by Kvark on 2005-08-20
[QUOTE=heimo]You can disable closing of parent directory by setting no_ubuntu_spatial using System Tools->Configuration Manager. Path is: ```
/apps/nautilus/preferences/no_ubuntu_spatial
``` 

I don't know abot the buttons, check View menu.[/QUOTE]
Opening a new window without closing the parent window was what warty did, and what hoary does on middle click (i think, but now mine doesn't :?). It resulted in a LOT of open windows.

Can't find anything about the buttons in the view menu. :|

[QUOTE=heimo]Oh, could be that I missed it. Can Hoarys nautilus do sidebar treeview? I think that's new. Anyway, it's neat file browser and first one on Linux OS that I have used for real work.[/QUOTE]
Yep, the treeview in hoary is on the side, kinda like the bookmarks when you press Ctrl+B in firefox.

---

