---
title: "panel transparency issue"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by manutdfan2850 on 2007-01-14
i have one of my panels set to be transparent and set to autohide. . However, when I am on another window, for example, I am currently in Firefox, the if I bring up the panel from autohide, its not transparent to the firefox window  but rather transparent to my desktop.  (see screenshot to see what i mean)

is there a way to make my panel transparent nomatter what I have open? 

I dont want to install beryl, etc because of video card limitations. 

thanks in advance.

---

### Post by blackened on 2007-01-15
Unfortunately this can't be done in default Gnome without compositing enabled (through beryl or compiz). Believe me, I'd love it if it could.

---

### Post by jordanmthomas on 2007-01-15
You can do it without beryl or compiz, but you do still need to enable the composite extension in your xorg.conf

After you do that, you can install xcompmgr and transset
run xcompmgr and then run transset .7 (or however transparent you want it) and click on the panel

It will look better if you tell the panel to be of a solid color instead of transparent first.

---

### Post by blackened on 2007-01-15
Alright, foot in mouth. I tried using xcompmgr, but it locked my machine requiring a hard reset. Might work better for you manutdfan2850.

---

### Post by jordanmthomas on 2007-01-15
xcompmgr does suck but it usually runs ok on my computer, just a little slow sometimes.
Sorry I crashed your computer :(

---

### Post by blackened on 2007-01-15
Heh, no worries. It made me remember how much louder my main machine is compared to my fileserver. It's like I have a hovercraft in the floor next to me.

---

