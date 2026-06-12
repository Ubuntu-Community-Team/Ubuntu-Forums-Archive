---
title: "Can't Print from Eye of Gnome"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by Woggie on 2006-03-11
Trying to print pictures of the kids on 4x6 paper.  Not sure why, when I go to print, it acts like its sending the info to the printer but nothing happens.  It will print a test page and I can print from  office just fine.  Any suggestions would be very helpful.

---

### Post by Pragmatist on 2006-03-11
Two suggestions:
1.) Before you print, open up your printer manager (that is what it is called in KDE and can be found at Main Menu-->Utilities; However, I'm guessing your using GNOME so just look through the menus and you'll find it)  This will let you see if a job is recognized (which it probably is, since your printer is doing something) and see what the status is.

2.) Try printing from Gimp.  Gimp is known to handle printing very well.

These may not work, but give them a shot and report back to us.

---

### Post by Woggie on 2006-03-13
Ok, tried printing from GIMP and no-go.  According to the printer status, the job is being sent to the printer but it won't print.  All I get is a string of text across the top of the page, "%! PS-ADOBE-3.0 %%Creator: Print plug-in V4.2 for GIMP/Gimp-Print 4.2.7 (15 Jul 20... and it runs off the page.

I also tried copying the image to Office, but that didn't work either.  It wouldn't accept the 4x6 paper size that I selected.

---

### Post by Pragmatist on 2006-03-13
So it prints ok on 8.5x11 ?

---

### Post by Woggie on 2006-03-13
Not Pictures, at all.  I will print text from Office though.  That's why I tried pasting in a document.

---

### Post by Pragmatist on 2006-03-13
What is your printer make and model and is it USB or Parallel?

---

### Post by Woggie on 2006-03-13
Hp 7760 Usb.

---

### Post by Pragmatist on 2006-03-13
type this in a terminal:
```
gnome-cups-manager
``` 
When the GUI window appears double click your printer and another window will open then use the menus and go to: Printer-->Properties
Look at the various settings and especially give us the information under the driver tab. There will be a list of printers on the right and on the bottom, in gray, there will be a driver selected. Read everything on the bottom of that window. Are you using the recommended driver?

---

