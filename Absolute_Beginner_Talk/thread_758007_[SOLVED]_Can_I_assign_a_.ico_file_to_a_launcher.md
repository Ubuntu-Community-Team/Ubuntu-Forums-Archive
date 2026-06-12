---
title: "[SOLVED] Can I assign a *.ico file to a launcher?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-04-17
I have learnt how to get a launcher into a panel.Tthe thing is I have a *.ico icon I want to assign to the launcher, instead of the spring thing. This is to remind me which launcher is which.
It would be much appreciated if there was a really easy way to achieve this.
Regards
John

---

### Post by TheLions on 2008-04-17
to add image to your launcher: open launcher properties (right click with your mouse on launcher then properties) and click on the image (in your case the spring) and then select another image...

---

### Post by forrestcupp on 2008-04-17
You may need to open the ico file in the Gimp and save it as a png or xpm, though.  I'm not sure if ico files work.

---

### Post by Andavane on 2008-04-18
Thank you both.
I have converted the .ico file using GIMP to both .png and .xpm format.
However when I right click on launcher then the picture
then browse to the required destination, the icons do not appear in the screen for me to click on.
I have looked at the help file which says:

> Type

                   Use the drop-down list to specify whether this launcher starts an application or opens a document: 

                 Application

                           The launcher starts an application.

                        Application in Terminal

                           The launcher starts an application in a terminal.

                         File

                          The launcher opens a file. 

However, when I click on the drop-down, I only get the option of "Application" or"Application in Terminal". there is no file drop-down option for "file", so I guess it is not hunting for a file.

Can you assist further?

Regards

John

---

### Post by joshrobinson on 2008-04-18
yeah its weird like that, drag and drop the .png file on the little spring icon in the create launcher menu

---

### Post by goiggles on 2008-04-18
to browse for an icon within the launcher you browse to the folder and open that then all the images in the folder will appea. This isnt the most user friendly way but its how it works

---

### Post by forrestcupp on 2008-04-18
> **Andavane said:**
> 
However, when I click on the drop-down, I only get the option of "Application" or"Application in Terminal". there is no file drop-down option for "file", so I guess it is not hunting for a file.

Can you assist further?

Regards

John

You don't click that drop-down box for the icon.  When you create a launcher, you set the type, name, command, and comment on the right.  Then to change the icon, you click the box with the 'spring' icon in it on the left.  When you click that box, it brings up another window where you can browse to the directory with your icons.

---

### Post by Andavane on 2008-04-18
> **forrestcupp said:**
> You don't click that drop-down box for the icon.  When you create a launcher, you set the type, name, command, and comment on the right.  Then to change the icon, you click the box with the 'spring' icon in it on the left.  When you click that box, it brings up another window where you can browse to the directory with your icons.
Yes Sir but when I browse to that directory where the icon is, no icons appear in the window, even though I can see them clearly in another i.e. nautilus window. Oh, and I get the same result on the laptop.
Regards
John

---

### Post by Andavane on 2008-04-18
> **joshrobinson said:**
> yeah its weird like that, drag and drop the .png file on the little spring icon in the create launcher menu
That doesn't work when I try it, but it launches the program.
If I attempt to drap the icon I want into the source file

"/usr/share/icons/hicolor/48x48/apps"

it says I don't have permission.

I have selected one of the icons already there, though and it's fine.
I know what it means.

Regards
John

---

### Post by forrestcupp on 2008-04-18
> **Andavane said:**
> Yes Sir but when I browse to that directory where the icon is, no icons appear in the window, even though I can see them clearly in another i.e. nautilus window. Oh, and I get the same result on the laptop.
Regards
John
You just need to browse to the folder where you know you put the png file.  It won't show the files in the open dialog, it only shows directories.  Go to that folder and click open and it will put that directory's graphic files in the icon chooser window.  I just tried it myself and I can verify that it at least allows jpg's and png's.

---

### Post by Andavane on 2008-04-18
> **forrestcupp said:**
> You just need to browse to the folder where you know you put the png file.  It won't show the files in the open dialog, it only shows directories.  Go to that folder and click open and it will put that directory's graphic files in the icon chooser window.  I just tried it myself and I can verify that it at least allows jpg's and png's.

AHAAA! & doesn't it just? :cool:

Well I never... thanks very much
It's really great when you've been trying hard and then it works!
Lovely

---

