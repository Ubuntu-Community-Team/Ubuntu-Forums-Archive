---
title: "How to use wine?"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Mike-e on 2007-08-17
Help! im having some issues getting windows programs to work in wine

could someone point me in the right direction of a **basic** users guide as this is all pretty new to me :)

Thanks for your patience in advance

---

### Post by original_jamingrit on 2007-08-17
well, I'm not sure I know of anything much more basic than the documentation that comes with wine.  to run a program normally, just enter ```
wine PROGRAMNAME.EXE
```
Are you trying to install a program from a disc?

---

### Post by Mike-e on 2007-08-17
im just trying to use a very basic windows program for a motec ecu. very small, no installation files but whenever i attempt to open a .exe file i get the same error message

"No application suitable for the automatic installation is available for handling this kind of file"

:confused:

edit: also when i try to read the install documentation that comes with wine it comes up blank :(

---

### Post by mc4man on 2007-08-18
You have to accept that _alot_of windows programs don't and probably will never run in wine. That being said you can experiment with changing the windows versions, using native dlls., copying in different dll. versions to system32,and sometimes a certain combo will work. Winecfg allows you to create separate application setups if you find one that works for a particular prog.To further muddle things each wine version can break/fix what previously worked/didn't

---

### Post by fenario on 2007-08-18
Hoi Mate

I'm new to wine too.

Here is what I did to NetMeter:

After I installed it into a folder that I created I had to :

Configure wine by:
open a terminal >  type : winecfg
Wine Configuration pops up
Tab: Applications > Add Application > search the exefile (wherever you put it) and click and open.
So it now knows that when you click on the .exe file or the shortcut to it to open with wine.

Then you can create a shortcut to the launcher panel

goto launcher panel > System > Preferences > Main Menu
In Menus on the left highlight a category of the type your application relates to,
on the right click: + New Item
Create Launcher pops up.
Enter a name for your program
browse for the .exe file in Command > click : open
click on:  no icon
select a pic > OK

you will find the launcher in > launcher panel > Applications > Category (you chose above)

furthermore; you can right click on that icon and chose: Add this launcher to panel
and it will appear up there.

Done

Let us know if that worked for you

fen greets

---

