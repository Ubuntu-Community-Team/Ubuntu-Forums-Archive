---
title: "Amarok troubles."
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by DeadEagle on 2008-02-01
Well, I finally got Amarok to import MP3s, and now it plays just fine... so this is really just something I'd really LIKE to have. I have a multimedia keyboard, i.e. I have "next track" and "play" buttons and such. They work fine with Rythmbox, but for some reason they won't work with Amarok. Anyone have any ideas?

---

### Post by Rocket2DMn on 2008-02-01
In amarok under Settings->Configure Global Shortcuts you should be able to specify your keyboard buttons for control.  Double click the blank area (or maybe already filled area) of the Shortcut column next to the Action that you want to assign and you will be prompted for the shortcut key.  Hit your keyboard shortcut at this time and you'll be good to go.

---

### Post by DeadEagle on 2008-02-01
Yeah I got that far, now it's skipping tracks and pausing and such on command, but my "volume up" isn't working now :confused:

---

### Post by Rocket2DMn on 2008-02-01
You may want to disable the keyboard volume control from inside amarok (just leave those shortcuts blank) and let Ubuntu's volume manager deal with that.  You can adjust that again from System->Preferences->Keyboard Shortcuts.

---

### Post by lespaul_rentals on 2008-02-01
For some reason, I had problems with this in Gnome but never KDE.  Which desktop enviroment are you using?

---

### Post by DeadEagle on 2008-02-01
Gnome.

---

### Post by lespaul_rentals on 2008-02-01
That might be your problem, as Amarok is a KDE app.

---

### Post by rune0077 on 2008-02-01
In Amarok, go to Tools > Script Manager. Click Install Script, and from the list, install Gnome Multimedia Key's. Once the script is installed, set it to run, and that should fix the issue.

---

