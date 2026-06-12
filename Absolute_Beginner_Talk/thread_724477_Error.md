---
title: "Error"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by ENigma885 on 2008-03-14
i had a post before about Firestarter that suddenly disappears from the bar ..but no one could tell me anything useful. Anyways,
NOW i think the problem is starting to have some visible features.
1st I installed Avast Antivirus for Linux (because i'm using flash memories from and to  Windows PCs )and it makes the same thing Firestarter does;_ it disappears_ whenever i run a scan after 1 or 2 minutes 
i tried to run them (Avast and Firestarter) from the terminal and after 2 or 3 minutes i got the expected errors 
*_**for Firestarter _*
melancholia@Melancholia:~$ sudo firestarter
Firewall started
Segmentation fault (core dumped)

*_**and for Avast _*
melancholia@Melancholia:~$ /usr/bin/avastgui

(process:11893): Gdk-WARNING **: locale not supported by Xlib

(process:11893): Gdk-WARNING **: can not set locale modifiers
Bus error (core dumped)

***so could someone help me to figure out wat those errors mean and how to fix them ?***

---

### Post by gobbles414 on 2008-03-15
> **ENigma885 said:**
> i had a post before about Firestarter that suddenly disappears from the bar ..but no one could tell me anything useful. Anyways,
NOW i think the problem is starting to have some visible features.
1st I installed Avast Antivirus for Linux (because i'm using flash memories from and to  Windows PCs )and it makes the same thing Firestarter does;_ it disappears_ whenever i run a scan after 1 or 2 minutes 
i tried to run them (Avast and Firestarter) from the terminal and after 2 or 3 minutes i got the expected errors 
*_**for Firestarter _*
melancholia@Melancholia:~$ sudo firestarter
Firewall started
Segmentation fault (core dumped)

*_**and for Avast _*
melancholia@Melancholia:~$ /usr/bin/avastgui

(process:11893): Gdk-WARNING **: locale not supported by Xlib

(process:11893): Gdk-WARNING **: can not set locale modifiers
Bus error (core dumped)

***so could someone help me to figure out wat those errors mean and how to fix them ?***

I recommend that you remove Firestarter. Then restart your computer. Then install a firewall program called gnome-lokkit. You can install gnome-lokkit using Synaptic. Also, you should be able to get Avast working correctly by following directions from [here]("http://ubuntuforums.org/showthread.php?t=510010") (posts 4 and 5).

Does this help?

---

### Post by ENigma885 on 2008-03-15
Thanx* gobbles414* for ur reply..
i tried the instructions stated in this[ post]("http://ubuntuforums.org/showthread.php?t=510010") ..but apparently it only solved a GDK related problem and ***still the core dumped problem exists*** while scanning .

melancholia@Melancholia:~$ avastgui
Bus error (core dumped)

and btw i forgot another thing ; when i launch Avast after that error i get a pop up window saying " Avast Information.... Deleted stale lock file '/home/melancholia/.avast/lockfile-melancholia'"

any ideas?

---

### Post by gobbles414 on 2008-03-21
> **ENigma885 said:**
> Thanx* gobbles414* for ur reply..
i tried the instructions stated in this[ post]("http://ubuntuforums.org/showthread.php?t=510010") ..but apparently it only solved a GDK related problem and ***still the core dumped problem exists*** while scanning .

melancholia@Melancholia:~$ avastgui
Bus error (core dumped)

and btw i forgot another thing ; when i launch Avast after that error i get a pop up window saying " Avast Information.... Deleted stale lock file '/home/melancholia/.avast/lockfile-melancholia'"

any ideas?

Sorry... I haven't been able to think of anything useful.

---

