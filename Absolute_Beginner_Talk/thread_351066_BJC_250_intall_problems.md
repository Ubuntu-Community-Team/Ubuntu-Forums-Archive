---
title: "BJC 250 intall problems"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-02-01
I tried to get my Canon BJC 259 up and running by chekcing the forums.

i tired turboprint.de

followed the instructions there and get this

robi@robi:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
robi@robi:~$ sudo dpkg -i turboprint_1.95-2_i386.deb
dpkg: error processing turboprint_1.95-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 turboprint_1.95-2_i386.deb


maybe obvious to all of you but I do not understand what is going on and I would like to print some stuff.

thanks for any help

---

### Post by Jussi Kukkonen on 2007-02-01
You need to be in the same directory as the file (turboprint_1.95-2_i386.deb), or you need to add the path to your command (*sudo dpkg -i /path/to/turboprint_1.95-2_i386.deb*)...

---

### Post by beanco on 2007-02-01
Jussi, Kiitos!

But I need more help.... I understan dthe words but I am still lost.. kind of like not seeing the forest for the trees.

so paht and to.... what do i have to write inplace of these? so or such newbie questions...

robi

---

### Post by Jussi Kukkonen on 2007-02-01
Ah, I see. No problem

When you download the file, make note of where it is downloaded (select Desktop if you want to follow my example below). Then open the terminal and use the cd-command to move to the right directory. Here is an example ('~' is a short hand for your own home directory, bold text is your commands):
```

jku@loki:~$ **cd ~/Desktop**
jku@loki:~/Desktop$ **ls**
turboprint_1.95-2_i386.deb
jku@loki:~/Desktop$ **sudo dpkg -i turboprint_1.95-2_i386.deb**

```

---

### Post by beanco on 2007-02-02
kiitos kiitos very very kiitos..

(you are finnish right?)

robi

---

### Post by Jussi Kukkonen on 2007-02-02
Olepa hyvä.

(yes, I am)

---

