---
title: "Reducing a picture to 16 colours"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-04-20
I want to change my bootsplash image ,in order to do that I need a png file in 16 colours. I played with the Gimp but couldn't find how to convert a picture to 16 colours. Finally I found [_this _]("http://www.troubleshooters.com/linux/scrshot.htm#gimp") ,a script that supposed to do the trick (on the bottom of the page) ,but my question is : how do I apply the script to the pic?

---

### Post by meborc on 2006-04-20
i'm not sure, but i would make this script a nautilus script... umm... that means make the text file with this code into executable file (right-click -> permissions)... then copy the file to .gnome2/nautilus-scripts/ (i might be mistaken of the path as i'm away from my ubuntu) ... now you just need to right-click on the picture file in nautilus, chose script (or smth) and chose the script file you created...

ok.. was just thinking how i would go about it... it might not work at all... :wink:

for more help on scripting in nautilus [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

---

### Post by htinn on 2006-04-20
Actually, you should reduce it to 14 colors.

EDIT: To do that in GIMP, you need to go to the Image/Mode menu and select "Indexed". Fill in the number of colors with 14 and choose your dithering method.

---

### Post by seshomaru samma on 2006-04-20
It worked like magic!
Thanks
(btw- anyone knows how to do it in the Gimp?)

---

