---
title: "Changing openoffice menu buttons functionallity in Xubuntu."
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by tommie74 on 2007-04-08
When I installend Openoffice in Xubuntu there were a few things I didn't like about it. Here I describe how I resolved these.

**1) The openoffice looks ugly compared to other programs, it has a different feel, lettertype etc.**
- installing the openoffice.org-gtk package solved this for me. Now it has a more Xubuntu look.

**2) in the Applications menu under Office there are different "buttons" all activating the same universal Openoffice starter window where you are next supposed to open an existing document, from template and choose your openoffice application. So selecting the openoffice.org Drawing option has the same result as selecting the openoffice Word Processing option. This I found inconvenient, I prefer to make my selection directly in the Appllications menu.**
- To solve this you can change *programname*.desktop files. They are to be found in /urs/share/applications. To open such a file you need to have root privilages. I opened a terminal, and typed "sudo thunar". This opens a Thunar file browser with root privileges. (leave the terminal open, otherwise Thunar also closes) I don't know if this is neat, I am totally new on linux (four days). In Thunar browse to /usr/share/applications. There you can find the different openoffice icons (files). First I renamed them, for they have a name too long to be nice in a menu. For example *Openoffice.org Drawing* I renamed to *Ooo Drawing*. Renaming can be done by right clicking the icon in Thunar and then choosing Rename. 
Next I opened the .desktop file I want to change in mousepad, this can be done by right clicking the icon in Thunar and then choosing open wit Mousepad. In mousepad you see the settings. Look for a line which looks like:
Exec=ooffice -draw %U
I think this is the command for executing the program. I am not going to explain how, but I found out that removing the *%U* stops the openoffice application from opening in a universal way, but opens, in this case, Openoffice Drawing, directly. If you remove the %U, and save the file in mousepad, this doesn't have effect immedeately.  To make the change effective I found out that selecting *Settings* from the Applications panel and then *Menu editor* opens a window where you can change the visabillity, do this, and then close the window and save. This makes all changes made in the .desktop file effective. Don't forget to change the visabillity back later!

**3) Some applications do not appear under the right category in the Applications menu.**
- Next thing to change in de .desktop file can be where in the Applications menu you want the program to appear. This you can modify by changing a line which looks like:
Categories=Graphics;VectorGraphics
In this case you can insert for example *Office;* in front of Graphics:
Categories=Office;Graphics;VectorGraphics
This makes the program appear in the Applications menu under Office in stead of under Graphics. 

**4) Some applications that do have a .desktopfile in /usr/share/applications do not appear in the Applications menu.**
- Another line in the .desktop file I changed is about the visabillity in the menu This can be set by a line in the .desktopfile that look like:
*NoDisplay=false*
Changing " false"  for " true" , or inserting the whole line at the end of the .desktopfile when it is not part of the file yet will remove the item from the Applications menu. Desktopfiles which are not visable in the applications menu, like *Openoffice.org Formula*, you can make appear by changing true to false. 

**5) You can probably make your own .desktop file for any program by copying an existing .desktop file and modifying it to your own purpose.**

I hope that somebody finds this usefull. I am absolutely new into linux so please forgive me if this is bad advise. 

Thomas de Graaff.

---

