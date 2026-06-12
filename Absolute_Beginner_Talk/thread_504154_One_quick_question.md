---
title: "One quick question"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Belliinator on 2007-07-18
I have a dual boot of windows 2K and ubuntu 6.06. How do I change which one automatically starts when the user does not intervene, or how do I stop Ubuntu loading up automatically after 60 seconds or whatever it is.

---

### Post by ddrichardson on 2007-07-18
Type sudo gedit /boot/grub/menu.lst from a terminal and change the "default" value to the menu entry for Windows.

---

### Post by Belliinator on 2007-07-18
Its not connected to the internet

---

### Post by kyphi on 2007-07-18
Applications -> Accessories -> Terminal:

```
sudo gedit /boot/grub/menu.lst
```

Alter the default (line 14 in my machine) from 4 to 0 if you want Ubuntu to start first or 0 to 4 if you want Windows to start first.

To change the time for automatic start go to the next paragraph and where you see timeout, change the value.
The default, I think was 10 seconds.  I have mine set to 4.

Don't forget to save before exiting.

---

### Post by Anzan on 2007-07-18
It doesn't need to be.

---

### Post by scrooge_74 on 2007-07-18
To be connected to the internet has noting to do with making changes in your grub boot list.  you need to edit menu.lst   the values start at 0 which is at the moment the first item on the list, you have to take into account any line that appears in the grub list even a text line counts.  Somewhere you will find how much is the delay time an even how long to see the menu, the colors, etc

---

### Post by ubanchaos on 2007-07-18
use the code:sudo gedit /boot/grub/menu.lst

---

### Post by kyphi on 2007-07-18
I need to add something to the advice I gave above and that is:

While you are in the boot menu list, consider changing the line that says #howmany=all to #howmany=1

That way, your boot menu will always only show one kernel entry and not confuse the boot loader.  Otherwise the numbering sequence is upset.

---

### Post by anewguy on 2007-07-18
As a general note, since this is an Absolute Beginner forum, it may be helpful to state this to those who may be new and don't know:

If you see something, such as the initial reply to this post (and as indicated in the 3rd post), that states put this or do this in "terminal" or "a terminal", it is actually a reference to using the command line.  To access the command line, at least from Ubuntu, look on your top bar, click on "Applications", then just move your mouse over "Accessories" and then move over to "Terminal" and click.  This will open up a "terminal" window.  In this usage, use of "terminal" refers to the command line, and not to anything that deals with the internet.

I hope that helps some of the people who are really new.  The 1st and 3rd replies in this post are great - just remember how to get to the "terminal" for a command line!:)

---

