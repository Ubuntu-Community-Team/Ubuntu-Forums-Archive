---
title: "General Compiz Fusion - n00bie at ubuntu"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by suffer1989 on 2008-02-29
Hello peple...

I am running ubuntu 7.10, and i saw this [impressive  video]("http://youtube.com/watch?v=7QyyC4LRoYI")...

I somehow installed Fusion on my PC, and even found out how to open it...

I have the latest [nvidia] drivers and all, but how do I get those effects shown in the above video ???

2 - Also, how can i set up 4 desks, currently I only have 2 ...

[[IMG]http://img405.imageshack.us/img405/8189/screenshot2oz5.th.png[/IMG]](http://img405.imageshack.us/my.php?image=screenshot2oz5.png)

BTW, i am a total n3wb at linux, so please be forgiving...

EDIT : specifically, the fire and Cube effects...

---

### Post by neurostu on 2008-02-29
to setup 4 desktops rightclick on your desktop selector, select preferences then change the columns and rows to what you want

---

### Post by neurostu on 2008-02-29
The cube is easy, just enable desktop cube and cube rotate, then mess around with the settings, like speed, zoom etc...

---

### Post by suffer1989 on 2008-02-29
> **neurostu said:**
> to setup 4 desktops rightclick on your **desktop selector**, select preferences then change the columns and rows to what you want

Whats that ??

---

### Post by forrestcupp on 2008-02-29
If you have Compiz running, you need to install the settings manager to change settings.
```
sudo apt-get install compizconfig-settings-manager
```
Then go to System->Preferences->Advanced Desktop Effects Settings.  In there, check the boxes next to 'Desktop Cube' and 'Rotate Cube'.  It may tell you you have to turn off another effect to use those and that's ok.

Then go back to the top of the main screen and click 'General Options' and click the 'Desktop Size' tab.  Change the 'Horizontal Virtual Size' to 4 and you will have 4 screens in a cube.

---

### Post by neurostu on 2008-02-29
[IMG]https://help.ubuntu.com/6.06/book/book/ubuntubook-ch3-html/3-1.png[/IMG]

In the bottom right corner of the picture there are 4 gray squares, you can use these to select a desktop. Right click on these (they are the desktop selector) (or thats what I call them)

---

### Post by suffer1989 on 2008-02-29
Ok, got the 4 spaces figured out, and the cube effect figured out, but how did the guy in the video make the cool burning windows effect, as well as the water efect...

and how can you zoom out to see the 4 windows in a cube shape, as the video shows ?

Thanks for the help :D....

---

### Post by jryprt on 2008-02-29
Try [Forlong's Guide](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#)

---

### Post by forrestcupp on 2008-02-29
> **suffer1989 said:**
> Ok, got the 4 spaces figured out, and the cube effect figured out, but how did the guy in the video make the cool burning windows effect, as well as the water efect...

and how can you zoom out to see the 4 windows in a cube shape, as the video shows ?

Thanks for the help :D....

Did you install compizconfig-settings-manager?  If so, look through all the effects and find the ones you want.  To find out how to get one working, click that effect to go to its settings and click the Actions tab to find out what the key bindings are.  Some of this stuff you should be able to figure out on your own.

To rotate the cube either press ctrl-alt-right or left, or press ctrl-alt and drag the screen with the left mouse button.

---

### Post by suffer1989 on 2008-02-29
heh, thanx for the help, i figured out, that to get to the options/hotkeys, you only needed to click on the effect...

---

