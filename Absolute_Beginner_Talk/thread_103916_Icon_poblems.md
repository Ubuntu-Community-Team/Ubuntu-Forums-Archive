---
title: "Icon poblems"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by da1 on 2005-12-15
HeLLoooooo!! 
I think i'm missing a basic concept of icon changing but have no idea how to o where to or why...
I'm trying to personalise all my icons etc... now its all goin good, however evolution mail has stumped me:
The icon in the desktop panel for some reason doesn't want to change. under properties it shows a colourful globe, then in the panel its a black and white different looking globe..
I downloaded some other icons and saved them in my newly created icon folder esp for different icons and when i choose browse to change the icon, the icons ive saved can't be chosen... why???
and its not only evolution playing up so its clearly something i'm missing.. please help this newbie...

Thank you

---

### Post by Sutekh on 2005-12-18
[QUOTE=da1]HeLLoooooo!! 
I think i'm missing a basic concept of icon changing but have no idea how to o where to or why...
I'm trying to personalise all my icons etc... now its all goin good, however evolution mail has stumped me:
The icon in the desktop panel for some reason doesn't want to change. under properties it shows a colourful globe, then in the panel its a black and white different looking globe..
I downloaded some other icons and saved them in my newly created icon folder esp for different icons and when i choose browse to change the icon, the icons ive saved can't be chosen... why???
and its not only evolution playing up so its clearly something i'm missing.. please help this newbie...

Thank you[/QUOTE]

When you say it can't be chosen, do you mean that the icons are greyed out when browsing?  When you change the Custom Icon and you browse to the folder that has your icon, you are actually browsing for the folder *not* the icon.  

When you originally click Custom Icon it opens a dialog box with the contents of '/usr/share/pixmaps/' displayed.  

Click browse and go to your icon folder and click ok, then it should go back to the first dialog box.  Just press return to update the path and it should display the contents of your icon folder.

Check out post #4 by audax321 in this thread for some pictures that will step you though it.
[Access to Icons themes]("http://www.ubuntuforums.org/showthread.php?t=89835&highlight=icons+greyed")

---

### Post by Griff on 2005-12-18
You could also just move those new icons to the above folder.

sudo mv /(absolutepath)/(filename) /usr/share/pixmaps/(filename)

Yay for the command line! ;)

---

