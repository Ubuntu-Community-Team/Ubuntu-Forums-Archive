---
title: "Executing a script"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by venik212 on 2007-02-08
In Gnome there was a nice feature that allowed me to determine (behavior) what happens when I click a text file.  I have a one line script file that I wnat to be able to click on and run the script.  How do I do that in KDE?

---

### Post by etank on 2007-02-08
At the top click Places->Home Folder. Now click Edit->Preferences and go to the Behavior tab. That will change it for all files though.

---

### Post by venik212 on 2007-02-09
I obviously failed to explain my problem.  I am NOT in gnome, but in KDE.   What you described works for gnome, but I am looking for the equivalent option in KDE.

---

### Post by RomeReactor on 2007-02-09
Open Konsole, cd to the folder containing the file and write

```
sudo chmod +x NAME_OF_FILE
```

That will make the file executable.

---

### Post by venik212 on 2007-02-09
I also thought that was the way to do it, so I tried it, but it did not work.  I cannot try it again now since I have not been able to discover how to revive the VINO server (or some other way to log on the macihne from a remote computer.  I am at home now, and the machine is in the office.  In fact, remote log in is my biggest problem with KDE-- it workd fine under Gnome, but I do not know how to do it in KUBUNTU.

---

### Post by lamego on 2007-02-09
For non graphical operations you can install the openssh server, login using an ssh client (putty for windows) and just run the script from the command line after setting the +x on it.

---

### Post by venik212 on 2007-02-09
I already know how to run it from a command line.  I wanted to click on it to launch it, as I did in gnome.

---

