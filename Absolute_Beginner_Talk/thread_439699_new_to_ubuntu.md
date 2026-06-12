---
title: "new to ubuntu"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by nepaliman on 2007-05-10
hey anyone help me ,, i am new in ubuntu.. i cant find synaptic package manager in my system- administrator-- dude ,anyone ...
help me ! and there is also a sound problem ...can anyone refer me anywhere .. 
it says

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
help me ...



:( thanks

---

### Post by Mateo on 2007-05-10
right click on the Systems menu and press "Edit Menus".  Make sure synaptic is listed there and that it's checked.  Assuming it is and it's still not listed, go to the terminal (applications - accessories - terminal) and type "killall gnome-panel". hope it helps.

---

### Post by TheMono on 2007-05-10
When he says killall gnome-terminal, I think Mateo means killall gnome-panel

Otherwise it will just close the terminal that you opened...

---

### Post by TheMono on 2007-05-10
To respond to your questions directly though, firstly, if Synaptic isn't in your menus you can launch it from a terminal with 

gksudo synaptic

But adding it to your menus is a more long term solution, and requires no command line stuff.

Secondly with the sound, do you know what sound card you have? You can check in the device manager, or from a terminal with the command 

lspci

And then find the one that is your sound card.

---

### Post by DoctorMO on 2007-05-10
You need help, should this post be moved into the support area?

---

### Post by Mateo on 2007-05-10
> **TheMono said:**
> When he says killall gnome-terminal, I think Mateo means killall gnome-panel

Otherwise it will just close the terminal that you opened...

yes i did, sorry.

---

