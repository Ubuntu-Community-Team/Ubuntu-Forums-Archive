---
title: "Screensaver Lock Dialog Help?!"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by moto89 on 2007-10-10
Hi all, I've been using Ubuntu for all of a week now, and I thought I was starting to get the feel for it, but low and behold I've been put in my place by a screensaver of all things. Basically, I would like to use [SIZE="4"]**[COLOR="Blue"][this]("http://gnome-look.org/content/show.php/lock-dialog-turbolence?content=67573") [/COLOR]**[/SIZE] lock dialog as a screensaver, but I honestly I have no clue how to add a screensaver. Sure, I can pick one of the default screensavers from the list; system>preferences>screensaver, but how do I make the linked lock dialog work as my screensaver?

---

### Post by cameronw on 2007-10-11
This cannot be used as the screensaver, well to the best of my knowledge. This is a theme for the dialog box that pops up prompting you for your password.
To install > Unpack and copy each file (4) to /usr/share/gnome-screensaverThen use gconf-editor to
>  Set key "lock-dialog-theme" to "turbolence" on gconf, /apps/gnome-screensaverIf thats any help

---

### Post by moto89 on 2007-10-11
Hmm... that seems odd to me. Why would it be listed under the "gnome screensavers" section of gnome-look, when there is a separate section for GDM themes? Does anybody know of a screensaver that requires a login to go back to the active session?:confused:

---

### Post by FuturePilot on 2007-10-11
They're not under GDM themes because they are not GDM themes. There's an option in the screensaver settings where you can have your screen lock when the screensaver comes on. You have to enter your password to get back to your desktop.

---

### Post by moto89 on 2007-10-11
Well, I feel pretty dumb for not seeing that one, but how would one go about changing the lock screen to the one I mentioned in the first post for instance?

---

### Post by cameronw on 2007-10-11
As before just extract the archive file you download the move files (4 it says) to  the /usr/share/gnome-screensaver folder then using gconf-editor (sudo apt-get install gconf-editor if you don't have it) go to the "apps" section then find "gnome-screensaver" and change the key "lock-dialog-theme" to "turbolence". Of course then you will need to check the lock screen box in the screensaver prefs to enable it. All should work fine.

---

