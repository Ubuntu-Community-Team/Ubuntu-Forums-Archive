---
title: "mldonkey"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-02-25
Hello, I was installing the packages of mldonkey

and installed the packages

mldonkey-gui
mldonkey-server

and the package that was necessary for those, but there did not appear an entry in the applications menu. How can I run mlonkey? Maybe something in the installation went wrong?

---

### Post by bugmenot on 2006-02-25
The GUI should appear in the Application menus.
Do you have the time to report that bug on Malone?

To your question. You have the fundamental choice between running mldonkey's core (mlnet) as a memory-resident system service or on-and-off from your home-dir. You can switch between the modes by "sudo dpkg-reconfigure mldonkey-server". If you want to run from your home-dir just issue "mlnet" somewhere.
Now that your core is running launch the GUI with "mlgui". Connect to the core (server "localhost" or any other host if you run the core on another box).

---

### Post by tomski on 2007-04-04
you could be really lazy and install the debian menu and use the 3 icons in that after running update-menus

---

