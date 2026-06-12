---
title: "Need Help Kicking AOL out of my desktop"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-03-19
I made a BIG mistake.  I installed AOL 5.0 on ubuntu using wine.  I tried to uninstall it via wine's uninstall wine software option, but the uninstall freezes.  I am completely new to linux (don't know anything about commands).  Is there something I can type in the terminal to kick AOL out of my life for good?  Also, how can I make a hyperlink shortcut on my desktop (not one that launches a program but one that opens a website)?

---

### Post by Diabolis on 2008-03-19
If you don't have any other programs, I would remove the **.wine** folder completely. It is located in your home folder, but its hidden. You can see hidden files by pressing **ctrl + h**. When I have trouble unistalling wine programs I usually just delete their folders which are inside the **.wine** folder. Also look for info about aol in the official [wine]("http://www.winehq.org/") site.

You can make a shortcut to a website by saving the home page (or the page that you want) as a html document. Just right click over the page and save page as.

---

### Post by The Titan on 2008-03-19
I'm Not sure about the link but you could try the AOL uninstall software included with the program in the "Program Files" folder.  If that doesn't work just delete the folder. There may be some registry keys leftover an i don't know how to delete those.

---

### Post by hikujk123 on 2008-03-19
I decided just to uninstall wine (I can reinstall it later if I need it...AOL was the only program).  I typed sudo apt-get remove wine.  The uninstall of wine appeared to be smooth.  I deleted the .wine folder.  HOWEVER, now I have another problem:  wine is still on my applications menu.  How do I get rid of it?

---

### Post by Diabolis on 2008-03-19
Type in terminal
```
alacarte
```

Its a menu editor where you can delete the wine entry. I assumed that you use gnome.

---

### Post by handydan918 on 2008-03-19
It may self-update on reboot...

---

### Post by hikujk123 on 2008-03-19
THANKS.  It worked!:KS

---

