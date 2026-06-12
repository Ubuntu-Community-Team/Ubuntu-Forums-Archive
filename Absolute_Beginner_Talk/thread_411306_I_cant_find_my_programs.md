---
title: "I cant find my programs?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2007-04-16
I just installed TrueCrypt for 6.06 drapper with a .deb file.  In this instance the program is not in my applications menu.  Where would I find it?  Do i need to create a shortcut for this program?  If so, how do I do it?

---

### Post by jfinkels on 2007-04-16
Programs in the Linux world are run using commands entered at the terminal. Menu shortcuts are just a level of abstraction so that you can simply click instead of typing. Try typing "truecrypt" in the terminal and see if it starts up (note that all lowercase command names are a *nix convention). It may be "true-crypt" or something like that, so type the first few letters of what you think the name might be, then press <Tab> to see if it can be auto-completed by the bash shell.

---

### Post by Maestro23 on 2007-04-16
Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

---

### Post by ramjet_1953 on 2007-04-17
> **jfinkels said:**
> Programs in the Linux world are run using commands entered at the terminal. Menu shortcuts are just a level of abstraction so that you can simply click instead of typing. Try typing "truecrypt" in the terminal and see if it starts up (note that all lowercase command names are a *nix convention). It may be "true-crypt" or something like that, so type the first few letters of what you think the name might be, then press <Tab> to see if it can be auto-completed by the bash shell.

Jfinkels, I don't know where you are coming from?????
The whole reason for a GUI is to simplify things for users and integrate packages into the menu system.

When a programmer releases a package that doesn't enter it into the menu it is sloppy programming.

All GUI's for any OS merely are an overlay for the command line. Even Redmond's efforts are no different.

The whole reason why Ununtu exists is to make Linux available to everyone, not just computer nerds, who love the command line.

Regards,
Roger :)

---

### Post by msak007 on 2007-04-17
A lot of programs do have a menu shortcut if there's a corresponding GUI app for it. In the case of truecrypt though, it seems that there's no "official" GUI for it. I did find a few projects in the works though (try at your own discretion, I can't vouch for how well they work as I've never used them):

[forcefield]("http://bockcay.de/forcefield")
[truecryptgui]("http://code.google.com/p/truecryptgui/")

There's screenshots of both, but one thing I noticed is forcefield has a tray icon, while truecryptgui is probably a link in the menu to a script or app that launches it (the download is a .py script). 

If this is a test machine, I'd say try both and see which one works better. Otherwise it may be best to just bite the bullet and learn the commands in the terminal until a suitable GUI surfaces. Or you could just try them anyway regardless (not sure if there's any risk of data loss or messing something up if they don't work, I don't use truecrypt myself). Your choice :).

---

