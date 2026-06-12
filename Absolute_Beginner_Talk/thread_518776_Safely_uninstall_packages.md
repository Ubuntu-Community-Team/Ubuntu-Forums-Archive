---
title: "Safely uninstall packages?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by tobleron on 2007-08-06
I'm still new to Linux and playing around - bear with me... After having installed various stuff, I decided this morning that I could also get rid of a few things I don't need - e.g. all sorts of language packs for Chinese, Norwegian, Thai, Hebrew, etc. So I set all these various packages (and only them!) to "request uninstall" in Adept Manager. When I clicked "apply changes", it started uninstalling all kinds of packages and not only those I had selected... In a sudden panic I stopped the whole thing, but the following programmes were uninstalled: the GNOME desktop environment, Gimp and Acrobat Reader (and possibly more stuff that I'm not aware of yet). It was easy enough to reinstall Gimp and Acrobat Reader and I don't mind having lost GNOME (I have a Dell Inspiron 1420n that came with preinstalled Ubuntu and on which I've installed KDE) but I'd just like to know how to avoid similar issues in the future. This time I was lucky, but maybe next time I bugger the whole system... Obviously this has to do with dependencies. Is there any way to find out what dependencies there are and whether it is safe to remove a certain package or not? Also, is there something like "undo" to reverse a process once you've unintentionally uninstalled certain programmes?

Thanks for any hints on that matter!

---

### Post by Damanther on 2007-08-06
I am not aware of an "undo" for package removal.

I generally either use the synaptic package manager, or the command line 'apt-get' series of commands. When you select packages for either update/installation/removal sometimes it needs to add/remove other packages based on some dependecies. Both of the utilities I mentioned will actually give you a warning and ask for confirmation if it needs to add or remove additional packages because of dependencies of the packages you have selected. You might use those in the future.

I've never used the adept manager, but I'm kind of surprised it did not throw up some sort of warning that it was going to remove packages other than what you selected.

---

### Post by p_quarles on 2007-08-06
While I'm not completely sure why this uninstalled these other programs, I'm guessing it has to do with the fact that they were modified by the language support packages. The vast majority of applications won't do anything like this.

Meanwhile, whenever you are about to install or uninstall something through a package manager, you can click on the "show details" button (not sure exactly what it is in KDE), and you will get a list of everything that is about to be changed.

---

### Post by tobleron on 2007-08-06
Thanks! I've found the "details" button both in adept and synaptic. In the future I might just use synaptic as I also think adept should have warned me - or maybe I just need to adjust the settings...

---

