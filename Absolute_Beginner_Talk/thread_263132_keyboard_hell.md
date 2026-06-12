---
title: "keyboard hell"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-09-22
hi all,

I though i would be really clever tonite and set up keyboard shortcuts for things like next track etc. Since doing that the keys on related to the   short cut do not work

example
Next track == Ctrl+N
then "n" will not work on it own any more!

Is there a way to reset these to the defaults as there is no option in the GUI but there probably is through command line any one know how?

please help and apologies for any typos caused by this problem

cheers
niteblind

---

### Post by bulldog on 2006-09-22
Just reverse the steps you made.

Otherwise I don't know how to change your settings.

---

### Post by niteblind on 2006-09-23
surprisingly enough I have tried that before posting this question if it were that simple i would not habe asked!

anyone know if there is a reset option or even know of the file name where the short cuts are stored?

cheers
niteblind

---

### Post by bulldog on 2006-09-23
Did you have a look at the help pages?

There should be an solution,when you can change them you must have the opportunity to change them back.

---

### Post by heyzeus on 2006-09-23
anyone figured out how to reset to defaults. I'm having the same problem.

---

### Post by VTXer on 2006-09-23
Don't know if this will help or not.
Have you tried from a terminal the following:

loadkeys -d

or 

loadkeys defkeymap

---

### Post by VTXer on 2006-09-23
I may have given the wrong answer - I guess you are using the keyboard shortcut applet under >System >Preferences.

Try this:

To disable a keyboard shortcut, perform the following steps:

   1.

      Click on the action for which you want to disable the keyboard shortcut. The row is highlighted and the text “Type a new accelerator, or press Backspace to clear” is displayed in the Shortcut column.
   2.

      Press Back Space. The keyboard shortcut is disabled.

I'm guessing the changes are stored in one of the .gnome dirs in your home area.  Sorry about the first post

---

### Post by Frederico Camara on 2008-01-14
cd
ls .gnome2/accels/

Delete the program file. It resets all accelerators of said application.

For example, to reset epiphany accelerators:

rm .gnome2/accels/epiphany

---

