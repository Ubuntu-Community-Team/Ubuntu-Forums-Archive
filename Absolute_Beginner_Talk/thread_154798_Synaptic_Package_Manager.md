---
title: "Synaptic Package Manager"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by NGDanny on 2006-04-03
Hi Everyone!

I'm using the SPM to add some programs 1) gnucash 2) gnuchess.

SPM doesn't add them to my "Applications".  I can find the files using "Search File". 
How do I get these programs to run. 

Have I done something wrong with the SPM?

NGDanny

---

### Post by henriquemaia on 2006-04-03
Try opening a terminal and type:

```
killall gnome-panel
```

Your panel will restart. Then check to see if the apps are available on the menus.

---

### Post by stalefries on 2006-04-03
Did you make sure to click "Apply" at the top of the screen?

If you did, could you list all the steps, in detail, so we can see where you went wrong?

---

### Post by catlett on 2006-04-03
You can always start an installed program by typing it's name in the terminal. ```
gnucash
```
All programs don't show up in the gnome menu. If you like to see everything install the Debian Menu. I got it through installing Automatix (if you want Automatix go to the main forum page and scroll down there is a link). You can do a search and probably find a way to install it without Automatix but I don't know how. The Debian Menu lists everything you have installed.
 You could try running update-menu and see if that helps.(or it might be update-menus, you might have to search the wiki for the exact wording,sorry for the lack of detail)

---

### Post by NGDanny on 2006-04-03
Thanks for all the quick replys!
I was able to run the programs in terminal.  I was also able to add a desktop icon and and application icon, both manually.  used - which gnucash -

I went to SPM
clicked - Search
typed in- gnucash
pressed -Mark for installation
then pressed - Apply

Again the programs are on my computer and will run in terminal, but not loaded 
Applications

Thx - Danny

---

### Post by Madpilot on 2006-04-04
No, they're loaded, but they don't have menu entries.

Adding gnucash to your menu is fairly easy:

- right-click on your Applications menu, select Edit Menus
- click on the Office category in the left-hand frame, then hit the New Entry button
- in the new entry box: Name: GnuCash, Comment: (anything, this is just the popup you see with menu items), Command: gnucash;.

For an icon, just click the square and look for the 'gnucash' directory for it's own icons.

---

### Post by NGDanny on 2006-04-04
Thanks everyone for the help!  Got things back under control!

Linux forever!!!

---

