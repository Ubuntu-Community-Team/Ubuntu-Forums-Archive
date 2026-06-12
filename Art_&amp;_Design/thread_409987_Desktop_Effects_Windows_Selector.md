---
title: "Desktop Effects Windows Selector"
date: 2007-04-15
forum: Art &amp; Design
---

### Post by kolslorr on 2007-04-15
Hello,

I am able to have desktop effects running on my Ubuntu Fesity, and it looks really good.

However, my machine specs are too low, and enabling this cause performance degradation.

Then I am thinking of disabling it, since it doesnt really affects my workflow. But I really like the windows selector feature that comes with compiz, whereby I just need to click on the top right corner to bring up all the windows arranged in a grid, and I can select the one I want to activate.

Any method of only enabling this feature somehow without using any other compiz feature?

Thanks.

---

### Post by aidanr on 2007-04-15
haven't tried it, but this might be worth trying out
[http://kompose.berlios.de/](http://kompose.berlios.de/)

or try turning off all the other plugins bar scale in gconf-editor

---

### Post by lanchongzi on 2007-04-15
if your comp specs are too low AND you are running GNOME I wouldnt really recommend kompose
I use it under KDE and I like it a lot 

BUT under GNOME it becomes SUPER slow

kinda takes the fun and useability out of it

plus when you clik on one application ( under GNOME that is ) it will put them in the same desktop as you were before
resulting in an chaos desktop ( windows like )

---

### Post by kolslorr on 2007-04-18
Thanks for all your input, appreciate it... 

I tried to enable desktop effects WITHOUT ticking both checkboxes, and I get the windows selector function without all the extras... sweet.

But i realised enabling this brings me some other issues which I am really tired of trying to resolve... namely, my video playback at Totem breaks, showing only black screen.

I tried to download kompose to try, but couldnt find the download link... lol.. I am noob.

Thanks guys.

---

### Post by Spin Doctor on 2007-04-23
> **kolslorr said:**
> ...But i realised enabling this brings me some other issues which I am really tired of trying to resolve... namely, my video playback at Totem breaks, showing only black screen.
.....

Try this to solve your problem with Totem:
[LIST]
[*]Press ALT+F2
[*]Enter ,"gstreamer-properties"
[*]choose the video tab
[*]At the output line. choose "X Window System (no Xv)[/LIST]Let me know if that works for ya! =)

---

### Post by jan. on 2007-04-28
Worked for me :)

---

