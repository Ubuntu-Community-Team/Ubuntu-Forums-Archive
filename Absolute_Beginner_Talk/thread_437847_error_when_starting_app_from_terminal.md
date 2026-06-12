---
title: "error when starting app from terminal"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-05-09
I've installed an app using the .deb package installer on dapper, but it hasn't appeared on the menus, or on Alacarte menu editor, so I'm using the "how to install anything" instructions [http://monkeyblog.org/ubuntu/installing/#where_did_it_go](http://monkeyblog.org/ubuntu/installing/#where_did_it_go) 

When I run from the terminal, the app loads and runs, but the terminal shows this error:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

The only requirements given in the app are:
"You certainly need to use qt3.x.x.  If you want to use RTF, I personally recommend to install qt3.0.5, at least. Since qt3.0.4 does have a bug in formating linebreaks.
I strongly recommend to use qt3.1.1 or above since the copying of text between notes has improved a lot."

How can I find out more about this error? 
TIA

---

### Post by LaRoza on 2007-05-09
What app is this?

---

### Post by hartz on 2007-05-09
The error message that you quoted above is something I have seen on kubuntu.  I think it is when using Gnome apps on kubuntu, and in those cases when I noticed it, it was not fatal - the application still worked fine.

I'm not much of a KDE fan so I never spent the energy to try and resolve it, and as I say, the applications worked despite spewing the error you see.

Some of the various apps which produced this error under kubuntu includes, for example Synaptic package manager and gnome-terminal.

Do you have any more error message information besides this message?

Does the app return the command-line prompt immediately after the error?

Does the app maybe launch an applet sitting in the menu bars somewhere?

And to Echo LaRoze - What app is this?

---

### Post by freesitebuilder on 2007-05-09
Tuxcards (notes) [http://www.tuxcards.de/](http://www.tuxcards.de/)

I get the command-line prompt back OK when I exit, and the app seems to be working perfectly OK. I'm using gnome.

---

