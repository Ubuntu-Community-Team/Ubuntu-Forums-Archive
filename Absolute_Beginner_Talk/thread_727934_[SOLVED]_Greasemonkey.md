---
title: "[SOLVED] Greasemonkey"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-03-18
where can i find my grease monkey scripts so i can edit them?

---

### Post by RadiationHazard on 2008-03-18
nevermine i found it

---

### Post by Oldsoldier2003 on 2008-03-18
> **RadiationHazard said:**
> where can i find my grease monkey scripts so i can edit them?

googling greasemonkey ( I don't use it) leads me to think that your scripts are saved in user.js

---

### Post by anantshri on 2008-03-18
[http://userscripts.org/](http://userscripts.org/)

check this particular site it is my one stop solution for all my greasemonkey related requirements.

---

### Post by livelove.breathe on 2008-06-23
:[ 

I came here hoping to find an answer, but I'm still quite clueless. 
To edit greasemonkey scripts, one either needs to find where the actual script files were installed, or through greasemonkey, which asks you to select the executable file for your preferred text editor. Neither of which I can find. 
 A search of user.js lead me only to template.user.js. 

If you could please explain to me where you found them, Radiation, I would be very grateful.

Or even if someone is unaware of greasemonkey script locations, when I am asked to select the exe of my text editor, where *exactly* would I find that? What **exact** file would I be opening to use "Text Editor"??

I am veryvery new to Ubuntu, and any help would be appreciated.

---

### Post by tk03759 on 2008-06-28
> **livelove.breathe said:**
> If you could please explain to me where you found them, Radiation, I would be very grateful.

Scripts are located at /home/user/.mozilla/firefox/****.default/gm_scripts/

"user" should be your username, and the ****s will be a set of letters and numbers.

> **livelove.breathe said:**
> 

Or even if someone is unaware of greasemonkey script locations, when I am asked to select the exe of my text editor, where *exactly* would I find that? What **exact** file would I be opening to use "Text Editor"??


"Text Editor" is actually an application called gedit. It is located at /usr/bin/gedit so you should go there when it asks you for the application. If you've already selected the file, or nothing is happening when you click edit, you can type "about:config" into the firefox address bar, accept the security warning, In the filter box, type "greasemonkey" and hit enter. Right click the line "greasemonkey.editor" and use modify to change it to /bin/usr/gedit. If that doesn't work, right click it and hit reset.

Changes take place immediately. Good luck.

---

