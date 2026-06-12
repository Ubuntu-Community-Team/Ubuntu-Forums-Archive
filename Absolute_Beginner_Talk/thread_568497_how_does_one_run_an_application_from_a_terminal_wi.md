---
title: "how does one run an application from a terminal windwo"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by gidrdunv11 on 2007-10-05
I have installed a vector tool with the synaptic package manager. The application does not show up in any menu so I can run the program. From what I have read about others with similar issues, I understand that I should open the app. from a terminal window. I would love to know how to do that. Can get to the terminal but just have no clue what commands to use.

Thanks for any info you might have for me.

---

### Post by avik on 2007-10-05
What's the tool?

---

### Post by Lacrimstein on 2007-10-05
first of all, how did you install the program? if you installed it from synaptic, chances are that the command is the same as the package name, with the info about version removed.

---

### Post by gidrdunv11 on 2007-10-05
I'ts called Cenon. An application to convert file formats.

---

### Post by Lacrimstein on 2007-10-05
so yeah, the command is most likely cenon

---

### Post by gidrdunv11 on 2007-10-05
I reinstalled it to see if I could find out where it would be installed. All I got was that it is cenon.app.

---

### Post by Lacrimstein on 2007-10-05
also, try this: press ALT-F2, type in xkill, when the cursor turns to skull click on the gnome panel, and wait for it to restart. Then check the menus again. If the panel doesn't reappear, press ALT-F2 again and type in gnome-panel

---

### Post by gidrdunv11 on 2007-10-05
Whats the gnome-pannel?

---

### Post by Lacrimstein on 2007-10-05
gnome-panel is basically your taskbar and the main menu. restarting it causes the menu to refresh.

---

### Post by gidrdunv11 on 2007-10-05
Tried xkill, didn't work. Thought I would have to launch it from the terminal, just have never done that before.

---

### Post by evets on 2007-10-05
Have you tried opening your terminal and typing the name of the app, and hitting enter?

---

### Post by Dark Hornet on 2007-10-05
Sometimes, a program will require you to navigate to the directory in which in is located, and you will type a "./ <program name>"....just a thought...good luck.

---

### Post by solo1181 on 2007-10-05
If you go into synaptic and right click on the app.  Choose properties, and then the installed files tab.   look for for usr/bin/nameofprogram.  You can usually just type the name of the program in a terminal and it will run or show errors, or type in usr/bin/nameofprogram.  Also some programs don't have the same command as the program name.

---

### Post by Tyke91 on 2007-10-06
try hitting ALT+F2 and just typing the name of your application...

---

### Post by Frak on 2007-10-06
Did you type the name of the program in the terminal?

---

### Post by yoni_m on 2008-02-18
> **gidrdunv11 said:**
> I have installed a vector tool with the synaptic package manager. The application does not show up in any menu so I can run the program. From what I have read about others with similar issues, I understand that I should open the app. from a terminal window. I would love to know how to do that. Can get to the terminal but just have no clue what commands to use.

Thanks for any info you might have for me.

Hi,
I just had the same problem the "solution" is that it is called Cenon not cenon (not the capital 'C').
You can run it via Alt+F2 or command line.

On my system it promptly crashes so ... :(

---

