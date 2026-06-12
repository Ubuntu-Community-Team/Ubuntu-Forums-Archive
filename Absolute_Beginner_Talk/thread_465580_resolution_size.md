---
title: "resolution size"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by sneeker on 2007-06-05
hey ok, i installed ubuntu studio, now one problem is that the resolution size is not right, it is 1024x768, i got an extra inch on ether side (4 1/2 or so cm) and prob 1 cm lef on top and bottom of actual working screen how do i fix this one?

---

### Post by Pragmatist on 2007-06-05
Do you want to increase the resolution (for example, to 1600x1200)?  Or, do you want to keep 1024x768, but want it to take up the whole screen?  If it is the latter, you can use your monitor's controls to get it to fit the screen.

---

### Post by steveneddy on 2007-06-05
Is this a laptop or desktop?

---

### Post by sneeker on 2007-06-05
Pragmatist: > Do you want to increase the resolution (for example, to 1600x1200)? Or, do you want to keep 1024x768, but want it to take up the whole screen? If it is the latter, you can use your monitor's controls to get it to fit the screen. Yes, i woul like increase the resolution
and i have already chaged the settings to take up the whole scree, it jsut gets really really blurry then!

Steveneddy: > Is this a laptop or desktop? Laptop

---

### Post by Pragmatist on 2007-06-05
In GNOME, go to the System-->Preferences menu and select "Screen Resolution"

---

### Post by sneeker on 2007-06-05
ive done that, but the highest i installed was 1024x768, and i need bigger, thats my question, how do i install more resolution sizes?

---

### Post by Wim Sturkenboom on 2007-06-05
Which videocard is in the system? Did you install videocard drivers?

If so, in a terminal, try ```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.mybackup.conf
sudo dpkg-reconfigure xserver-xorg
```
The first command makes a backup of the existing x-server configuration and the second command should allow you to reconfigure it.

If above solution does not work, please post the sections device, monitor and screen of your /etc/X11/xorg.conf.

---

### Post by Pragmatist on 2007-06-05
Please attach a copy of this file on your next post:
**/etc/X11/xorg.conf**

---

### Post by sneeker on 2007-06-05
> **Pragmatist said:**
> Please attach a copy of this file on your next post:
**/etc/X11/xorg.conf**

ok one problem i dont know how to attach files to this OH nvm i c it

ok i did it, not sure what happend the box went away:)

---

### Post by sneeker on 2007-06-05
> **Wim Sturkenboom said:**
> Which videocard is in the system? Did you install videocard drivers?

If so, in a terminal, try ```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.mybackup.conf
sudo dpkg-reconfigure xserver-xorg
```
The first command makes a backup of the existing x-server configuration and the second command should allow you to reconfigure it.

If above solution does not work, please post the sections device, monitor and screen of your /etc/X11/xorg.conf.

na, doesnt work, right now this is just the ubuntu trial for me.. im gettin a new comp. so i'll have windows on one hd and ubuntu on another, and when i install that i'll make sure i install everthing perfectly, no matter how long it takes me to install it lol

---

### Post by Wim Sturkenboom on 2007-06-06
OK, so you did install the videocard driver.

Edit /etc/X11/xorg.conf. At the end there will be a number of subsections that look like the one below
```
SubSection "Display"
Viewport   0 0
Depth     24
**modes     "1280x960" "1024x768"**
EndSubSection

```Add the mode that is supported by your screen at the beginning of the bold line (after the word modes).

---

### Post by tkrisz on 2007-06-06
I have installed a 32-bit Feisty Fawn on an old computer. So far it works as a wonder, except for one thing: the resolution size. I want 1024x768. If i boot the system, sometimes (randomly, about 1/2 of the cases) it starts in 800x600 (login screen as well) and if i log in only 800x600 and 640x480 are available to choose. Then in other cases the log in screen starts in 1024x768, but if i log in it starts in 800x600, however in this case i can change to 1024x768, apply the change, but next time it starts in 800x600 again. Sounds too mysterious to me...

---

### Post by Wim Sturkenboom on 2007-06-06
Please start your own thread. This can get frustrating for topicstarter. He/she sees a reply but it's for somebody else.

For now
Did you try
```

sudo dpkg-reconfigure xserver-xorg

```

Which videocard (make/model)?
Did you install videocard drivers (if applicable)?
Which monitor (make/model)?

When you start your own thread, please supply the info as well

---

### Post by sneeker on 2007-06-06
> **Wim Sturkenboom said:**
> OK, so you did install the videocard driver.

Edit /etc/X11/xorg.conf. At the end there will be a number of subsections that look like the one below
```
SubSection "Display"
Viewport   0 0
Depth     24
**modes     "1280x960" "1024x768"**
EndSubSection

```Add the mode that is supported by your screen at the beginning of the bold line (after the word modes).

ok i understand where this is, but there are A LOT of subsection "Display"'s

which one do i edit?

---

### Post by Wim Sturkenboom on 2007-06-07
You can do all

In the beginning of the *screen* section is a *DefaultDepth*. Just change the subsection that the defaultdepth refers to; it's usually 24.

---

### Post by tkrisz on 2007-06-07
I'm sorry from everyone,  i thought it's a general topic about resolution size problems and thought not to open a new topic.  Thx for the help btw.

---

