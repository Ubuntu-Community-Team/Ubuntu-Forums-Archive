---
title: "How do I put Gnucash in my applications menu"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-02-13
I just installed gnucash and don't know how to add it to the applications menu.  I am starting it using the terminal and entering "gnucash"  I know how to add program to applications menu but I don't know how to find where or which file is the start/execute file for the program.  How can you tell which files are execute program files.  I know how to search for files.

---

### Post by v8YKxgHe on 2007-02-13
I'm not on Ubuntu atm, but if I remember correctly - just right click on the Applications Menu and select Edit Menu or something similar, from there you can add it in.

---

### Post by rggavubt on 2007-02-13
I figured it out and added it to the applications menu after going to user/bin and clicking the one listed as gnucash.  I would like to add a better icon....never ends!!

---

### Post by v8YKxgHe on 2007-02-13
When adding a new item, you get to add an icon with it aswell. Most application icons are in /usr/share/pixmaps so just have a browse in there for one you like =)

---

### Post by rggavubt on 2007-02-13
> **AlexC_ said:**
> When adding a new item, you get to add an icon with it aswell. Most application icons are in /usr/share/pixmaps so just have a browse in there for one you like =)

I want to change the icon....it is a blue rimmed box.  How do I change it?

---

### Post by mithras86 on 2007-02-13
The program you're using to change the menu is alacarte. You can start it with right mouse on your menu, or type it into the terminal or press Alt+F2 and enter it there. 
You have already added the menu item i see, so go to that item and choose to edit that entry. On the left top there is an empty icon button, so click it and you'll get a file choose dialog. Browse to /usr/share/pixmap or something (im not at ubuntu now) and search for the gnucash logo. Select it and you're done :)

---

### Post by rggavubt on 2007-02-13
> **mithras86 said:**
> The program you're using to change the menu is alacarte. You can start it with right mouse on your menu, or type it into the terminal or press Alt+F2 and enter it there. 
You have already added the menu item i see, so go to that item and choose to edit that entry. On the left top there is an empty icon button, so click it and you'll get a file choose dialog. Browse to /usr/share/pixmap or something (im not at ubuntu now) and search for the gnucash logo. Select it and you're done :)

I did that and the gnucash icon is not there.  When I go to the file usr/share/pixmaps the gnucash icon is there.  Why doesn't it show up in the listing of icons when I click icons after I click properties??

---

### Post by rggavubt on 2007-02-13
I figured it out.  I went to applications and edited gnucash.  I clicked the icon and then browsed files until I found the gnucash icon under /usr/share/pixmaps/gnucash and selected it.  That changed it in the applications menu.  I then deleted gnucash with no icon from the quick lanuch bar at the top of the window and reinserted it and it now had the new icon.

---

### Post by chaplanger on 2007-02-13
> **rggavubt said:**
> I figured it out and added it to the applications menu after going to user/bin and clicking the one listed as gnucash.  I would like to add a better icon....never ends!!

If you haven't already gotten the gnucash icon I've attached an image of it here.  Right click on the image and do a "save image as" to your machine

---

### Post by rggavubt on 2007-02-13
> **chaplanger said:**
> If you haven't already gotten the gnucash icon I've attached an image of it here.  Right click on the image and do a "save image as" to your machine

Thanks!!!

---

