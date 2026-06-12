---
title: "Is changing the size of the mouse icon/pointer possible ?"
date: 2013-04-22
forum: Assistive Technology &amp; Accessibility
---

### Post by grey1beard on 2013-04-22
My wife suffers from Age Related Macular Degeneration (AMD), and her main problem using her laptop is not being able to see the mouse icon easily.
Other issues, like the contrast and general brightness have been sorted, and she's now happy with the appearance of the screen, but for this one detail.

I've noticed that while 'skating' her finger over the touchpad while trying to find it, she is very prone to click on something, and is frustrated by the sudden appearance of new windows/actions she didn't intend. Part of this might be oversensitivity of the touchpad, but I'm not sure about that.

If it were possible to just make the mouse pointer bigger, without altering anything else, we would have solved the problem.

Can it be done, and if so how ?

John

---

### Post by slickymaster on 2013-04-22
You can change your cursor size using **dconf-editor**
In a terminal window, run to install it if you don't have it:
```
sudo apt-get install dconf-tools
``` navigate to **org.gnome.desktop.interface** and change the cursor size value.

---

### Post by grey1beard on 2013-04-22
Thanks slickymaster.
I'm doing a trial run on my own laptop and I've now installed dconf-tools.

Navigation without a compass is a bit tricky for this old newby, so could you give me some directions on how I get to the interface ?

Regards
John
EDIT
Doing a search for the interface, I've found an xml file, but I don't know if this is where I should be, nor if I can alter the icon size here.

---

### Post by grey1beard on 2013-04-22
Noticed the name of the xml file, so I went there in my file system.
Guess that I can edit it via terminal/ gedit ?

Regards
John

---

### Post by slickymaster on 2013-04-22
It's under System, just select dconf editor. Then it will open the GUI for the dconf and in the left panel just click on org -> gnome -> desktop and then select interface. When you select interface, on the panel on the right the tenth line is the one you'll have to change the value. Just double click on the value (it should be 24, by default) and correct it to the value you desire.

---

### Post by grey1beard on 2013-04-22
Perhaps I should have asked for glasses ! Went right past it .

Many thanks for your fulsome guidance.

Regards
John

---

### Post by slickymaster on 2013-04-22
Glad you got it fixed.

---

