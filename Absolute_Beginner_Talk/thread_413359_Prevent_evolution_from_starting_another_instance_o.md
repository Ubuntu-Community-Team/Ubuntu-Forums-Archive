---
title: "Prevent evolution from starting another instance of itself"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by vanadium on 2007-04-19
Gnome can conveniently be launched from the bar in the default Ubuntu configuration. However, troubles arise when the user clicks the launch icon a second time. Rather than switching to the running instance, a new instance of evolution starts. That second instance starts slowly and then is incapable of showing the email from an IMAP server if the other instance is already pointing to the imap account. Is there a possibility to have a new launch activate an already running instance rather than launching a new instance?

---

### Post by ghowells on 2007-04-19
I don't believe so as these are simply launcher buttons rather than Mac-style dock buttons that double-up as a task bar.  All those buttons do is run the command for the app in this case "evolution" so I don't think there is a way of getting them to do what you want. Sorry!

---

### Post by vanadium on 2007-04-24
This is probably something that needs to be taken care off by the executable. The executable should check if an instance is already running. If it is, it should switch to the running instance. If it isn, it should launch an instance.

This is the way it works with the Gimp. Actually, the gimp has a separate binary to control such behaviour, gimp-remote. In the graphical menus, Gimp is configured with a call to Gimp-remote:

gimp-remote-2.2 %U

This allows you to load graphics in an already running instance instead of in a separate instance.

This should also be possible with evolution (and perhaps it is). Now, clicking the launcher starts a second "crippled" session of evolution. It is simply inconvenient for the user who wants to check his calender to first have to see whether evolution is already running before clicking the launcher.

Probably this could also be done with a script, but hey, this is the Absolute Beginners forum.

---

