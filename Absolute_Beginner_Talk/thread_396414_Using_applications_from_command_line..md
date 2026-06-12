---
title: "Using applications from command line."
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by trulyfree on 2007-03-29
Ahoy all. Ubu rocks. I just switched over from the other OS, and linux is way better. I have found most of what I need to get started, and really have nothing to complain about concerning my install or anything. Ubuntu recognized my wireless, my sound card, and all that. Then I proceeded to install programs I thought I would never have at my fingertips. Sorry to brag, but this rocks. I am a total linux noob though, so would someone tell me how to "run" the programs that are not iconified in the pull down menu. I used synaptic to expand my repositories, and installed some really useful tools, but how do I get them to start? Thank you for your help.
Free

---

### Post by Obor on 2007-03-29
Good to hear that everything went well :)
You can make new launchers or shortuts yourself but if you want to run a command to start an application use ALT+F2 and type the name

---

### Post by ceeg on 2007-03-29
> **trulyfree said:**
> Ahoy all. Ubu rocks. I just switched over from the other OS, and linux is way better. I have found most of what I need to get started, and really have nothing to complain about concerning my install or anything. Ubuntu recognized my wireless, my sound card, and all that. Then I proceeded to install programs I thought I would never have at my fingertips. Sorry to brag, but this rocks. I am a total linux noob though, so would someone tell me how to "run" the programs that are not iconified in the pull down menu. I used synaptic to expand my repositories, and installed some really useful tools, but how do I get them to start? Thank you for your help.
Free

If you want to become more familiar with the terminal (which is immediately useful, and immediately reccomended), a great website to add to your bookmarks is [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

It is a well written tutorial that walks you through creating bash scripts and learning the basics of a linux terminal. Once you finish that, you should be able to tackle most intermediate tasks requiring the use of a command line.

Good luck and if you have any questions, the Ubuntu community is the best the linux world has to offer!

---

### Post by sirkism on 2007-03-29
Yes, I just loaded up ubuntu my self and the website posted above helps with the basics. Must read.

again that's.. [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by airtonix on 2007-03-29
open the applications menu, then open the accessories menu, then drag the terminal entry on to your main gnome-panel.

very useful for those extended terminal sessions....gets you there quick.

---

### Post by billmeek on 2007-03-29
To figure out the command to run for applications in the menu, you can start the menu layout editor and look at the properties of the menu items.  To start the menu editor from a terminal window use

```
alacarte &
```

Alacarte is the program and the "&" starts it as a background job so the terminal returns to a prompt without closing Alacarte.  Once in the menu editor click on the correct menu in the left column and then right-click on the program and select "Properties" to see the 'command' that is ran from the menu.

---

### Post by gpiccirilli on 2007-10-24
Works great! Thx

---

