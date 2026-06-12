---
title: "437 icons in gnome pannel"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2008-02-02
Hi,

A little slip of the mouse pad had me place a link to all 437 deb's in my archive folder, in the top Gnome Panel. There isn't a free pixel left to right click and remove the panel. Is there somewhere a config file that i can hack about in or some quick way to remove these icons or the panel?

Thanks for any advice,

Rudolf

---

### Post by misfitpierce on 2008-02-02
Not sure but try locking the first icon closest to something that is locked alrdy (ex. Ubuntu menu etc) and then right click menu or w/e and delete that see if space is made without icons moving.

---

### Post by zabien1970 on 2008-02-02
Can you access Places > Desktop in the top left?

---

### Post by mcduck on 2008-02-02
Sorry, I don't know hoe to remove applets/launchers  from panel without using their right-click menu. But I have an idea you could try, it might allow you to remove the while panel..

If the panel is not expanded it has bars on both ends that allow you to access the panel's menu. Even though the panel will take the whole screen with that many launchers, the end bars should be always visible, so all you need to do is disable the panel's 'expand'-option. As you can't directly access the panel's menu to do this, we'll use gconf-editor instead:

1. Press Alt-F2 and run 'gconf-editor'
2. Browse to apps/panel/toplevels/YOUR_PANEL (all panels you have will be listed here with their own names)
3. disable 'expand'-key.

Now you should see the bars at the ends of your panel. Right-click on that bar, select "Delete This Panel" and your panel with all 437 launchers is gone.

Then just right-click on your other panel, select "New Panel" to create a new panel, and then right-click & "Add to Panel" to fill the new panel with whatever applets and launchers you want.

---

### Post by RudolfMDLT on 2008-02-03
Thanks, That sorted it out! :)

---

### Post by tgalati4 on 2008-02-03
I wanted a sceenshot!

---

