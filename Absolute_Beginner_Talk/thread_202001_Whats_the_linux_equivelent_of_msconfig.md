---
title: "Whats the linux equivelent of msconfig"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-06-22
How can i get programs (like skype,thunderbird etc) to start automatically on boot?

---

### Post by Zikes on 2006-06-22
I believe it's System -> Preferences -> Sessions, but I'm not at a Linux box right now so I can't confirm that.  The window that pops up will have a tab that lets you manage what programs start when you log in, but you'll need to know the commandline command to start each program.

If you have a problem tracking that command down you can open Synaptic, find the installed package, go to Properties and select the Installed Files tab.  In the list of files there will probably be a /etc/bin/thunderbird or /usr/bin/thunderbird (it's /something/bin/command, can't remember the exact details).  The last part is usually all you have to type in, but sometimes you'll need to specify the full path.

---

### Post by digimars on 2006-06-22
One thing you could do is go to System->Preferences->Sessions, then click on the Startup Programs tab.  Click the Add button and enter the command of the program that you want to run at startup.

EDIT: Zikes beat me to it.

---

