---
title: "never got to ubuntu..."
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by bobathia on 2006-04-17
first time noob posting... just finished installation... and now i'm prompted for my user name in a command prompt, then I enter my password... at this point, in the guide it says:

Type the username you selected earlier, followed by the password for the user account, and the Ubuntu desktop will appear. But that never happens. Instead of the graphical user interface appearing... I get this message:

Last Login.... blahblah on tty1

Linux ronak 2.6.12-9-386 $1 Mon Oct 10 13 hours 14 minutes 36 seconds BST 2005 i686 GNU/Linux

The programs included with the Unbuntu system are free software;
the exact distribution....blah blah

ronak@ronak:~$


I'm thinking the installation didn't go properly... it was a bit messy... I had some trouble getting past the base installation point ( a lot of restarting) Am i just an idiot that's not loading it properly? How can I get to the Ubuntu desktop from here? Should I re-install everything? Thanks in advance for your help!

---

### Post by aktiwers on 2006-04-17
I have installed Ubuntu 4 times now, and every time it loads a grafical interface.

But try typing:

startx

that should load Gnome.

---

### Post by bobathia on 2006-04-17
tried that.... and now its saying:

-bash: startx: command not found


hmmm... don't know what to do. thanks for the suggestion though... have any more?

---

### Post by user1397 on 2006-04-17
[quote=bobathia]tried that.... and now its saying:

-bash: startx: command not found


hmmm... don't know what to do. thanks for the suggestion though... have any more?[/quote]
maybe "sudo startx" and then type in your password

---

### Post by Randomskk on 2006-04-17
sudo apt-get install ubuntu-desktop

It may be a big download, but that should get you a desktop.

---

### Post by aktiwers on 2006-04-17
Else I would try to install it again.

Did you install it as server? If yes, thats the reason you have no Desktop. I have read that the server version dont have this.

Else try what Randomskk says :)

---

### Post by aktiwers on 2006-04-17
Sorry dobblepost.. delete pls.

---

