---
title: "Remove Wine folder?"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by ELI7 on 2007-11-16
How do i remove the Wine folder in a safe and simple way from the applications drop-down menu? I uninstalled Wine, thought the folder, along with the "Starcraft" sub folder didn't vanish..

I've heard about the remove command in the terminal, but i'm not sure how to use it for this purpose..


BTW -- Keep up the good work with Ubuntu! :)

---

### Post by shad0w_walker on 2007-11-16
You can remove the entry from the menu using the menu editor. Right click on the menu bar and select Edit, the menu editor will open up. In there you just need to scroll down to the wine folder and untick it. Should be gone now.

---

### Post by ELI7 on 2007-11-16
Thank you! That worked!
Just curious, where is that folder in the harddrive? Can i remove it from there totally?

Thanks again

Edit: Nevermid, found it.

---

### Post by Darkade on 2007-11-18
All the files you install with wine are stored in a folder named .Wine in your home folder. Just delete that and you'll have completely uninstalled wine.
Though I have something to add, I did uninstalled wine, and I did delete the menu entry, and I did deleted the .Wine folder but now I want to reinstall wine but my menu entry won't appear again ¿I'm I the only one with this problem?

---

### Post by Sukarn on 2007-11-18
> **Darkade said:**
> Though I have something to add, I did uninstalled wine, and I did delete the menu entry, and I did deleted the .Wine folder but now I want to reinstall wine but my menu entry won't appear again ¿I'm I the only one with this problem?
You're not the only one with this problem. I have this problem as well.

---

### Post by Darkade on 2007-11-18
Hey I got it solved and decided to post how because lots of people seem to have the same problem.

0)You should have wine installed even though you can't see the menu
1) open your ~/.config/menus/applications.menu file
2) do a search for "wine" 
3) you'll notice that every entry that has to do with wine has a </deleted> tag, erase that tag
4) now save the file
You should now have wine menu back in your menu bar, I also changed the location of the applications-merged (It had wine related entries in it) folder but I'm not sure that has anything to do.

I got the Idea from here [http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/4de2f6c56102be46/c99a81771b0fb164?lnk=gst&q=wine+menu#c99a81771b0fb164](http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/4de2f6c56102be46/c99a81771b0fb164?lnk=gst&q=wine+menu#c99a81771b0fb164)
thanks to the wine community and I hope this works for all of you

---

