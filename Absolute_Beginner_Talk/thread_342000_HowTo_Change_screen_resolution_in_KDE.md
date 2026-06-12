---
title: "HowTo: Change screen resolution in KDE"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by old_geekster on 2007-01-19
I installed "Ubuntu 6.10 Edgy Eft" with the Gnome desktop.  I have used KDE in the past, in SuSE 10, so I decided to install it.  The fact is if you use the "Redmond" desktop setup, it is much more like Windows and easier for me to accomplish tasks.  This gives me more time to learn how to use the Konsole and commands.

Now, for my problem.  In Gnome I can go to "System/Preferences/Screen Resolution" to change  the Resolution.  In KDE, I cannot find anywhere to accomplish this task.  I have set 1024 x 768 - 75MHz as the default for Gnome, but when I go to KDE it is evidently at 1600 x 1200 (max for my monitor) because I can hardly read the print.

Is there a way to accomplish this task in KDE without using the Konsole?

---

### Post by mand0 on 2007-01-19
> **old_geekster said:**
> I can hardly read the print.

I am not 100% on this but can't you increase the font?

---

### Post by jeremy on 2007-01-19
Maybe this isn't the answer you are looking for, but you can right-click on the desktop, then 'Configure Desktop...'

---

### Post by davebgimp on 2007-01-19
Hit ALT-F2 and type kcontrol. Before you hit enter, click on the options and set it to run as root. Check around in that app when it opens.

---

### Post by old_geekster on 2007-01-19
> **mand0 said:**
> I am not 100% on this but can't you increase the font?
Thanks to all of you for your replies.

I used the above suggest and it worked.  I consider it to be a work-around, but it did what I wanted to accomplish.

At least, now, I don't have to use a magnifying glass along with my eye-glasses to read what it says on the screen.

---

### Post by davebgimp on 2007-01-19
Another thing to check is your xorg.conf file

From a terminal:
**sudo kate /etc/X11/xorg.conf**

Check for what resolutions you have available and what is set as the default.

---

