---
title: "question about &quot;My computer&quot; icon"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by thungmail on 2008-03-03
hi
I follow these thread at [http://ubuntuforums.org/archive/index.php/t-164859.html]("http://ubuntuforums.org/archive/index.php/t-164859.html")
but the icon does not show up. Can someone help me out.

---

### Post by jakl_53 on 2008-03-03
Which method are you using? If you go to Places and drag the Computer icon to the desktop to create the shortcut..

---

### Post by thungmail on 2008-03-03
I followed 
"In the terminal/command line, type gconf-editor
3. <enter> (a window will pop up)
4. In the panel on the left, click apps (applications on some machines) -> nautilus -> desktop"
What do you mean go to Places.

---

### Post by jimrz on 2008-03-03
try[[COLOR="Sienna"]_** this**_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=14166")

---

### Post by LuisGMarine on 2008-03-03
Give Ubuntu Tweak a try.  This program has some very promising features in the future.

[http://www.ubuntugeek.com/howto-tweak-ubuntu.html](http://www.ubuntugeek.com/howto-tweak-ubuntu.html)

---

### Post by kalwisti on 2008-03-04
Hi, thungmail,

Have you tried this procedure (which I have transcribed below from Rickford Grant's book)? Hopefully this will work for you . . .

This procedure will place a trash can, hard disk, and home folder on your desktop.

1. Press Alt+F2 to bring up the Run Application window. This keyboard shortcut is the equivalent of clicking the Run Application panel applet that you placed on the panel in your original user account.

2. Run the GNOME Configuration Editor by typing **gconf-editor** in that window and then pressing ENTER.

3. When the Configuration Editor window appears, click the small arrow next to **apps**, scroll down to **nautilus**, and click the small arrow next to that.

4. Click **desktop** in that expanded nautilus section, after which the options for that item will appear in the right pane of the window.

5. Check the boxes next to the items you would like to appear on the desktop. You have four unchecked choices to choose from: **computer_icon_visible** (like My Computer in Windows), **documents_icon_visible** (to create a link to your Documents folder, if you have one), **home_icon_visible** (for quick access to your home folder), and **trash_icon_visible** (for you-know-what).

6. When you're done, close the Configuration Editor.

*Note*: Changes made in the way I just described will affect all user accounts. If you choose, for example, to show the trash can on the desktop for one user account, it will appear there for all others.

**Source**:

Grant, Rickford. *Ubuntu for non-geeks : a pain-free, project-based, get-things-done guidebook*. 2nd ed. San Francisco : No Starch Press, 2007, p. 117-118. 
ISBN 978-1-59327-152-7. $34.95 retail.
(This covers 7.04 Feisty Fawn)

Good luck!

---

