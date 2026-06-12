---
title: "Change the look of the start menu button"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-06-10
I want to change the look of the start menu button. I have downloaded the .png file/picture from gnome look.

 To change it I have followed a guide that tells me to;
1. start gconf-editor
2. Go to; /apps/panel/objects/object_0
Under object_0 there should stand «object_type = menu-object»
Here I must change the path to my custom icon. 

The problem is that I cant find "menu-object", and I have also looked at the other folders under "objects". Do you know what I am doing wrong?

Thanks for any help

---

### Post by mcduck on 2007-06-10
Do you actually have the Main Menu applet in your panel (instead of the default Menu Bar applet that has Applications, Places and System)?

You can only set the image for Main Menu applet that way.

---

### Post by _sAm_ on 2007-06-10
Hmm, no I had not added that one to the panel... I thought I could change the “default Menu Bar applet” with it. But after adding the Main Menu applet I found it, and have now changed the look. 

Thank you for your help:-)

---

