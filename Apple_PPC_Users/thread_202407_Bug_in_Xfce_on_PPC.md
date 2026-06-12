---
title: "Bug in Xfce on PPC?"
date: 2006-06-23
forum: Apple PPC Users
---

### Post by raysaunders on 2006-06-23
First, a word of thanks to those who put together Xubuntu for PPC.

Second, a little background info. I have a first generation iMac 233MHz Bondi that I have been using to research possibilities for operating systems. While I have had both Mac OSX and SUSE 10.0 installed and running successfully, they are inevitably a bit (?) slow... So I was very happy to read about the release of Xubuntu 6.06 in my latest Linux Format (UK) magazine.

Installation was a breeze and I find it the best option yet for running a modern operating system and applications on a less-than-modern PPC.

All has been going well until...

In the user account (non-admin) I have created, I have chosen (or, more accurately, tried to choose the System>Menu Editor (Xfce Menu). Since then, the Applications menu item is no longer active and I have no way of accessing anything!

I created a second user account - followed the same step with the same result. Thinking this might be a consequence of not having admin privileges on those accounts, I then (foolishly, in retrospect) tried the same thing in my admin account. Same result and now I'm really stuck!

When I right click on the Applications mnu item, I can access Edit Menu in the contextual menu. This opens a window titled Xfce4-MenuEditor /home/user/.config/xfce4/desktop/menu.xml but no items in the list. When I 'Add' an item (I tried to adda new launcher for Firefox, basing my entries on the Firefox icon in the top screen menu bar (which is the only thing left working apart from the top right clock and restart etc icon). I click on save, the window closes. Nothing is added to the Applications menu. I right-click on it again and, sure enough, the same xfce4-MenuEditor window opens with no items listed....

I guess this is some sort of bug that blew away the Xfce4 default menu contents and a write permissions issue prevents me from saving changes on the /home/user/.config/xfce4/desktop/menu.xml file?

A step-by-step solution would be helpful. I may also install another copy of Xubuntu onto an elderly iBook G3, just to conform if this is truly a bug or not.

Thanks, in advance, for helping me sort this out.

(Shame this happened, I was beginning to enjoy using this old iMac at a reasonably responsive rate..)

Ray

---

### Post by Ptero-4 on 2006-06-23
type this on your admin account:
```

sudo rm -f ~/.config/xfce4/desktop/menu.xml

```
Restart X and try to open the menueditor.

---

### Post by raysaunders on 2006-06-26
No effect, I'm afraid. Couple of things noted along the way.

After deletion, and launching xfce menu editor, the new menu.xml file created has read-only permissions for the user. I can't think that this is correct if this is the file used by the (admin) user to configure their own menu?

So, I tried chmod to give the (admin) user write permission. Tried adding a new item to the admin Applications menu and save. Still same result as before (xfce menu editor quits, nothing is saved and the menu.xml file remains empty).

:confused:

---

### Post by raysaunders on 2006-07-03
Sadly, I have now had precisely the same experience on a fresh install on a second Mac.

Until a solution is offered from the developers, I cannot recommend installing it despite the promise it shows for running on older equipment. Such a pity.

I hope that one of the developers can respond more positively with a solution.

---

### Post by RavenOfOdin on 2006-07-04
It works for me.

---

