---
title: "Transparency in xubuntu"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by linux phreak on 2008-02-01
Hi friends,I installed Xubuntu yesterday and it is running well.I have  the'Display compositing turned on and it looks nice.The problem is that the terminal window is horribly sluggish when moved about in the screen.Other windows are ok and firefox is also quick.Why is the terminal window so sluggish when moved.Can i solve this?

---

### Post by mali2297 on 2008-02-01
Have you tried other terminals such as xterm? (Press alt+f2 and type xterm.)

---

### Post by linux phreak on 2008-02-01
xterm does not lag.Great.What is the difference between xterm and normal terminal?

---

### Post by mali2297 on 2008-02-01
> **linux phreak said:**
> xterm does not lag.Great.What is the difference between xterm and normal terminal?

The default terminal in Xubuntu is xfce4-terminal. I think it is somewhat buggy. There might be a fix for your problem, but there are many other terminals to choose from. Besides xterm, you can install aterm, rxvt-unicode, gnome-terminal etc. They all have the same basic functionality. 

As for the difference between xfce4-terminal and xterm, the first is probably easier to customize. For example, if you want to change the background color in xterm, you will have to edit the file ~/.Xdefaults.

---

### Post by linux phreak on 2008-02-01
Thank you for you reply.So how can i make x-tem to open when i choose terminal in accessories?

---

### Post by mali2297 on 2008-02-01
> **linux phreak said:**
> Thank you for you reply.So how can i make x-tem to open when i choose terminal in accessories?

Go through the menus **Applications > Settings > Preferred Applications**, and then the **Utilities** tab.

If that doesn't work, you can add an entry in the menu for xterm with the menu editor.

---

### Post by linux phreak on 2008-02-01
The preferred applications did not work.The terminal stays the same here.Could you please guide me regarding menu editor,I am a  relative new comer to linux

---

### Post by mali2297 on 2008-02-01
> **linux phreak said:**
> The preferred applications did not work.The terminal stays the same here.Could you please guide me regarding menu editor,I am a  relative new comer to linux

Press alt+f2 and type **xfce4-menueditor**. (It is also available through the menus but I can't give you the directions.)

From the menu editor, choose to **create a new menu** and then **add an item**. The command should be **xterm**, type it. Then just **save** your menu and you are done.

---

