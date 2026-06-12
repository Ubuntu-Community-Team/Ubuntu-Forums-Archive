---
title: "What drivers do I have?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Chelidon on 2008-04-13
Is there a way of listing what drivers I have installed on my computer? It's something I haven't really thought about, and it's the sort of thing Windows would keep out of sight.
But lately I've become concerned about my system, and I want to know what my graphics/video card and driver are. How do I find out?

---

### Post by dcast on 2008-04-13
the command "lspci" will tell you what hardware is there, also you can go to System > Administration > Device Manager, and that will let you know anything you could possibly want to know. 

Edit: Oops, just saw that you are using Kubuntu, not sure what the process would be for Device manager would be in KDE, but typing in lspci in the terminal should tell you what graphics card you have.

---

### Post by ibutho on 2008-04-13
Commands like lshw and the device manager in Ubuntu should help you figure out the hardware on your system and the modules/drivers being used.

---

### Post by mikewhatever on 2008-04-13
Try running <sudo lshw -C display>. Post the output here if you need more info.

---

