---
title: "How to totally remove a program?"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by bankrupt on 2006-10-10
I wanted to do a full, clean reinstall of amarok, but it seems some remenants of it are being left after uninstallation.  I used Synaptic to remove amarok using the "mark for complete removal" option in the manager.  The problem is, when I reinstall the program, the songs I put into its library previously are still showing up, like I never removed the program at all.  The first time use wizard isn't running either like it did the first time I ran the program.  This leads me to believe there's something cached.  How can I fully uninstall the program so it runs like its never been installed before?

---

### Post by Kateikyoushi on 2006-10-10
Probably a config files remain in your home directory.
Change the view in nautilus to show hidden files (CTRL+H) there might be a .amarok file or something similar.

---

### Post by coolen on 2006-10-10
> **bankrupt said:**
> I wanted to do a full, clean reinstall of amarok, but it seems some remenants of it are being left after uninstallation.  I used Synaptic to remove amarok using the "mark for complete removal" option in the manager.  The problem is, when I reinstall the program, the songs I put into its library previously are still showing up, like I never removed the program at all.  The first time use wizard isn't running either like it did the first time I ran the program.  This leads me to believe there's something cached.  How can I fully uninstall the program so it runs like its never been installed before?

If I recall correctly, amaroK creates a database with your songs and such in it. When you purge a program (complete remocal) it removes the configuration files...but probably not any databases that it created and used during its time on your system.
If you could fine the database and delete it, that'd solve your problem. You'd need a more experienced user, though. I've never touched SQL.

---

### Post by mitch.c on 2006-10-10
> **bankrupt said:**
>  How can I fully uninstall the program so it runs like its never been installed before?

Assuming you are using the default SQLite db, you might try:
> sudo aptitude purge amarok
rm -rf ~/.kde/share/apps/amarok
Good luck

---

### Post by bankrupt on 2006-10-10
Thanks for the help guys.  Using Ctrl-H in Nautilis did allow me to find some Amarok files in a hidden .KDE folder.  I deleted all the amarok files I could find.  When i reinstalled amarok, the library entries were cleared and the first use wizard came up like it did when I first intalled the program.

---

