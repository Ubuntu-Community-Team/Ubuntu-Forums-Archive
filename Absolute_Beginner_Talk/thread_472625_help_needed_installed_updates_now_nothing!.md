---
title: "help needed installed updates now nothing!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Glennjamin on 2007-06-13
Hey, I installed Ubuntu yesterday and i connected it to the Internet and installed all the updates- all 176. After installing the updates the softeware installed itself- and then the screen flashed and I lost all the objects on the panel- including the off button- so i can't reboot! I've also lost the boot button :::

any idea?:p

---

### Post by taurus on 2007-06-13
Which release are you running right now (Dapper, Edgy, or Feisty)?

---

### Post by starcraft.man on 2007-06-13
> **Glennjamin said:**
> Hey, I installed Ubuntu yesterday and i connected it to the Internet and installed all the updates- all 176. After installing the updates the softeware installed itself- and then the screen flashed and I lost all the objects on the panel- including the off button- so i can't reboot! I've also lost the boot button :::

any idea?:p

Uh, so all the buttons everywhere are gone? Ok... push Alt + F2 and then type in gnome-terminal. In that type in "sudo reboot". That will restart your PC. If you can't see anything at all in the screen i.e. its black... restart the machine manually I guess, can't just sit there waiting for it to come back.

 I don't know what happened... updates shouldn't blank your screen..... if the desktop doesn't show right after reboot I guess its serious problem.

Edit: Hi there taurus :D.

Edit 2: Now that I think about it, why didn't I just recommend gdm restart... try pushing ctrl + alt + backspace (thats it right? I always use the command in terminal...)

---

### Post by HereInOz on 2007-06-13
if you want to reboot, just press CTRL-ALT-F1 and that will open a full screen terminal where you can log on, with your normal username and password, and then enter:

sudo shutdown -r now

You will be asked for your password, so enter that, and the system should reboot. 

If you still have no decent desktop when you re-boot, then something has gone terribly wrong with the updates, and you may have to have another install.

Perhaps someone else can give you a more hopeful answer.

---

### Post by Glennjamin on 2007-06-13
oky dokey thanks starcraft- i manually restrarted the system and everything in back and in business-:p apart from my internet connection :confused:. Using the exact same settings as before the update and it will not join the network- It just shows the signal strenght to be zero and  disconnected. However I know this to be untrue as I have XP on the same laptop and the internet is fine- any ideas? I have a Intel PRO/Wirless 3945ABG network connection

sorry- I'm running edgy

---

### Post by starcraft.man on 2007-06-13
> **Glennjamin said:**
> oky dokey thanks starcraft- i manually restrarted the system and everything in back and in business-:p apart from my internet connection :confused:. Using the exact same settings as before the update and it will not join the network- It just shows the signal strenght to be zero and  disconnected. However I know this to be untrue as I have XP on the same laptop and the internet is fine- any ideas? I have a Intel PRO/Wirless 3945ABG network connection

sorry- I'm running edgy

Sorry, I never used any intel cards with wireless on Ubuntu so I dunno. I'm gonna assume that one of the updates applied was a networking one and changed the way you connect/settings you already made. Thus, you have to redo them/find new ways of getting it working (search forums or wait for a networking person. I use an ethernet line for my Ubuntu PCs.

You may want to post the output of "iwconfig" and "ifconfig" to help whoever is trying to help you...

---

### Post by Glennjamin on 2007-06-13
ok, thanks starcraft- i'll check out that forum cheers
:KS

---

