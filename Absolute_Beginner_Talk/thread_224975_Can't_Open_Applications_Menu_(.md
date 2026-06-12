---
title: "Can't Open Applications Menu :("
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by tawfer on 2006-07-28
Hello, I consider myself to be a mildly experienced linux user and I recently installed xubuntu (by far the easiest install of any linux i know of).  Anyway My hand twitched with the mouse and I don't know what I clicked, but now i cannot open the application menu.  The mouse and keyboard still respond.  I can middle click.  But if i right click on the desktop, nothing happens.  Also if i left click on the applications button in the top left corner, nothing happens.  I can right click on the applications button and open the menu editor.  Rebooting the computer doesn't fix anything.  My guess is I ended some process that I shouldn't have, what process would be accociated with this, and how should I start it back up.  Thanks.

---

### Post by OU812 on 2006-07-28
Hit alt+f2. The run command window will pop up. Enter

xfce4-panel

this will bring the menu bar back. You should be able to get the application menu from there. In preferences, (I'm doing this from memory) click desktop. I think you have to click the second tab. There should be a box to check that has to do with being able to right-click the desktop for the app menu (forgot the name). Also, this may be the bug that has been reported in several posts. I don't have them bookmarked, but it may be worth your time to search the forums.

john

---

### Post by christopher.newell on 2008-01-01
I tried the suggestion above and it gives me a panel that I can configure, but I don't really know what to do with it.  I can see my applications menu, but when I click it, I just get a wait cursor, and nothing happens.  Is this this something that has changed with 7.10?  I'm over a week in without using Windows, and I really want to make Ubuntu work on my main PC this time (I moved my calendar to my wife's XP laptop and I'm syncing my PDA there).  I don't know why the applications menu just stopped, but I need it back, and I don't fancy reinstalling.  Any help is appreciated.

---

### Post by christopher.newell on 2008-01-01
I found help indirectly elsewhere on the forum.  Thanks to the other post, I looked in /home/username/.config/menus and found my applications.menu file.  There were also a number of other undo files, and when I organized by date, the newest showed it was modified today, even though I didn't change it myself today.  I renamed that and took of the .undo from the otherwise most recent file and I was up and running again immediately.  I had been googling for hours and even tried removing and reinstalling my gnome menus.  There was even a hairy part where it didn't seem to want to reinstall.  I hope this prevents others from tearing their hair out.

---

