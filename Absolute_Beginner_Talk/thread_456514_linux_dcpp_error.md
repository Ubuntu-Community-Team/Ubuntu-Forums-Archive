---
title: "linux dcpp error"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by finer recliner on 2007-05-27
i installed linuxdcpp form automatix on my feisty fawn computer

when i run it all i get is an empty window that says DC++ at the top. when i click the X in the corner to exit. i get an error window but it is also blank. there isnt even a button to click OK or Cancel. i have to go to tty1 and kill the process from there. something is obviously not rendering correctly. Maybe i'm missing a GTK package or something?

i've run the application many times, and it has only worked once. but it crashed about a minute later and closed itself without an error message.

i've tried uninstalling and then reinstalling from automatix

then i tried installing it from cvs as recommended by this tutorial:
[http://ubuntuforums.org/showthread.php?t=193984](http://ubuntuforums.org/showthread.php?t=193984)

at first i still had the blank windows. i decided to remove my .dc++ directory, and then it worked. unfortunatly it soon crashed, and the next time i ran it it gave me blank windows again :(

in one instance of dc++ working, and then crashing, my shell said a core was dumped. but i dont know where that file is. it may be helpful.

anyone else having this problem?
any suggestions?

---

### Post by finer recliner on 2007-05-29
bumpy

---

### Post by stevensheehy on 2007-06-01
Read the debug section of the [wiki]("http://openfacts.berlios.de/index-en.phtml?title=Ldcpp_Manual") and post a backtrace here. Also post what you or it was doing when it crashed and any other useful output from the terminal (especially if the terminal says something about gailtreeview).

---

