---
title: "[SOLVED] Like screwed things up.."
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by reefsrt4 on 2008-01-01
Ok, so I have been using linux for about 3 weeks now.  So far, I have been able to find solutions to every question I have had by searching these forums.  A great tool indeed.  However, I feel my small level of knowledge gained here has only made me a bit dangerous.  Here's the background on what I did:

I was adding launch icons to awn.  I found I was able to left click (hold) and drag icons from the app menu over to the awn dock.  Later, I added applets to awn and saw my launch icons disappeared.  So, I removed them from the launch menu.  When I went back to the app menu to drag them back over, I noticed they were no longer there.  One of my missing app menu icons was terminal.  So, I launched it via alt-F2 "gnome-terminal".  Since I only wanted to get it to show up, I ran "sudo apt-get install gnome-terminal".  It failed because it was already installed.  So, to my demise I assumed that I could just remove, then reinstall and that would get it back in full again.  I ran "sudo apt-get remove gnome-terminal".  Once I saw all of the packages it was going to remove, I panicked and thought I would lose my entire desktop environment and closed terminal.  Now I cannot use synaptic at all, can't run "sudo apt-get install gnome-terminal" in terminal.  This is the error it gives me when trying to do either action..

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

What can I do to fix this?  I am unfamiliar with the methods it is telling me I must do..

Thanks in advance for any help you can provide to me. :(

---

### Post by PmDematagoda on 2008-01-01
Execute:-
```
sudo dpkg --configure -a
```
as suggested by the error. That should fix your problem.

---

### Post by reefsrt4 on 2008-01-01
Thanks.  For whatever reason, I assumed it was eluding to some more difficult process.  I ran the code as described in terminal.  Then ran the "sudo apt-get install gnome-terminal" again to get it full restored.  It came back stating it was already installed.

I guess all I really still need to do is get the launch icon back into my main menu, under accessories.  How do I go about doing that?

---

### Post by reefsrt4 on 2008-01-01
Nevermind.

I found right clicking on "Applications" and choosing edit menus, I can add the launchers back in by hand.

I appreciate the assistance and will likely need it again in the future.



Happy new year all.

---

