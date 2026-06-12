---
title: "Cube problems"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by shakujou on 2007-08-14
Hey, for awhile I had my cube activated from Desktop Effects, and all was fine and dandy.  Then my friend did something unfortunate, he went into Desktop Effects, canceled, and then I was stuck with only one work space.  When I go to properties and change the amount of work spaces, it wont actually show the graphic of twirling around a cube when I change work spaces.

---

### Post by Hospadar on 2007-08-14
you should go back into the bery settings manager, either by right-clicking the tray icon, or doing "bery-manager" from the terminal,
go to "Desktop" and make sure "Desktop Cube" is checked

If it is, and you still arn't cubed properly, we can go from there.

---

### Post by jordanmthomas on 2007-08-14
> **Hospadar said:**
> you should go back into the bery settings manager, either by right-clicking the tray icon, or doing "bery-manager" from the terminal,
go to "Desktop" and make sure "Desktop Cube" is checked

If it is, and you still arn't cubed properly, we can go from there.

Desktop Effects != beryl
It's compiz.

Try this:
press Alt + F2 and type:
```
gconf-editor /apps/compiz/general/screen0/options
```
In the right pane of the window that comes up, make sure that hsize is set to something greater than 1 (4 is default) and that number_of_desktops is 1.  Close the program

Now, right click on your pager (workspace list) in your panel and go to properties.  Set the number of workspaces to 1 and you *should* be back in business.

---

### Post by shakujou on 2007-08-14
Thank you a lot (to the second poster), that worked right away, while the Beryl thing was acting really wonky...  I'll be sure to tell my friend (same person who did this to my computer did this to his before doing it to mine) how to fix it as well.

---

### Post by jordanmthomas on 2007-08-14
No problem.  I just wish I knew *why* I have to do this sometimes.

---

