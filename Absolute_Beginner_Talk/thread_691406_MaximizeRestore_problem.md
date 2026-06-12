---
title: "Maximize/Restore problem"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by BackBack on 2008-02-08
On any window normally when I double click the bar at the top (like on FireFox on the left it has it's icon, in the middle it has the title of the webpage, and to the right it has the minimize, restore, and close buttons), normally it would maximize/restore, but after installing Ubuntu Ultimate Edition it no longer does that.  What it does instead is hide the entire thing, but leaves the bar there, or the opposite, drops the window back.  Is there a way to get it back to maximize/restore?

---

### Post by red_Marvin on 2008-02-08
Panel menu -> system -> settings -> windows:
"The option Double click on the title bar to do the following: [dropdown menu |V]"
Choose "maximize"

The choice of words might be different from yours because I don't use the English locale, so I had to translate...

---

### Post by vamsibethapudy on 2008-02-08
i use gutsy.hope it is the same in yours
go to System>Preferences>Windows.
change the settings there.
i think it will work.

---

### Post by BackBack on 2008-02-08
I tried doing that, but Maximze was already selected, and when I change to anything else, it doesn't do anything different.  Is there another way of fixing this?

---

### Post by battlesound on 2008-04-21
I've got the same exact problem, I believe.

I use gnome, compiz, emerald.
I can change the setting for the "double click titlebar to perform this action" to maximize, but it doesn't seem to make a difference.
I can change the same setting in GL Desktop (for compiz) and it doesn't seem to make a difference either.

Anyone find a solution or realize what's going on?

---

### Post by battlesound on 2008-05-03
I also found an option for the title bar double click in Emerald Theme Manager.  Under the Emerald Settings tab I verified the title bar option was set to Max/Restore (already was set right).

I fixed my problem then by verifying all places for setting the option again.  All were set to Max/Restore (see above post).  Then I opened GL Desktop (not sure what the package name is, but I beleive it's "gnome-compiz-manager").  I think you have to click it a couple times to open the GUI for the application.  Keep settings.  Then, toggle off the option for use metacity theme.  Also double check the option for the title bar double click in this application (I don't think it actually changes anything, but I like to make sure it's set to what I want).

After switching off the use metacity theme option, I could finally maximize and restore by double-clicking the title bar!  Yay.  Hope this helps someone.

---

