---
title: "[SOLVED] How do I know the command associated to a program?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by coront on 2007-10-23
Hi, how do I know the command to start a program in the "applications" menu? I installed AWN but I want it to be in the start-up programs in the "sessions" menu. The problem is that I need the command to execute it but I dont know it and neither I know how to find it out. So, how I *easily* find out program commands??. THank you in advance

---

### Post by Dr Small on 2007-10-23
System > Preferences > Main Menu
Browse, find the entry in the menu, select Properties.
It will tell you the command right in there ;)

Dr Small

---

### Post by petersjm on 2007-10-23
Not sure what AWN is but if it was installed in one of the usual ways (aptitude, apt-get, synaptic, adept, etc) then it will more-than-likely go in your /usr/bin folder (I think that's the one) and *should* work with the simply command "awn" (try it and see).

---

### Post by Qwerty_ on 2007-10-23
This is probly not the quickest way but it may solve your problem.

Go to your applications menu, right click on the program you want to run and click add this launcher to the desktop.

Go to your desktop were you will now see the launcher for the application.
Right click the application>Properties>Launcher. You will then see the command. I am sure there would ba an easier way but for a one off this will work for you.

---

### Post by Mr. Scott on 2007-10-23
If it's installed in one of the usual locations, try typing "whereis awn" in a terminal. That would give you its full path, but as said above, if it's in a standard location, you only need to specify the command and not the full path to run it.

---

### Post by coront on 2007-10-23
Thanks a lot

---

