---
title: "Changing keyboard layout..."
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by hartnady on 2006-01-30
Anyone know how to change **keyboard layout** in Breezy? NB: Keyboard **LAYOUT**... not keyboard settings.

I only have base settings (i.e. no GUI) so I will need to manually update files.

I have a **FRENCH SWISS** keyboard layout, and I want to change it back to standard **US-104**.

Anyone know what file to edit, and how to reinstantiate it?

PS: Please don't suggest me to click on System -> Preferences (I deliberately do not have GNOME or any other GUI as this is a server).

Many many many hundreds of thanks.

---

### Post by s6dalane on 2006-01-30
Fire up the terminal and type
> sudo gedit /etc/X11/xorg.conf

Then find the following line
> Option		"XkbLayout"	"xx"

Change the xx's to 'en' or 'us' and restart.
This worked for me, hopefully does for you too.

---

### Post by Commuto on 2006-03-07
Also have a look at [http://bugzilla.ubuntu.com/show_bug.cgi?id=15372](http://bugzilla.ubuntu.com/show_bug.cgi?id=15372) , cuz there is some bug associated with it

---

