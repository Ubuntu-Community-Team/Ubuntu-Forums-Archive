---
title: "[SOLVED] Ati Radeon RV100 QY"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Semong on 2008-01-15
Ok Im having horrible results with my graphics card. First off Im running Xubuntu 7.10 & I have an Ati Radeon RV100 QY 128mb graphics card. When I type the 'glxgears' command into the terminal it puts my CPU at 100%, appears to run smoothly for a few seconds then Im only seeing the gears move at about 5 or 6 frames every 5 seconds although my terminal says otherwise:

432 frames in 6.0 seconds = 71.651 FPS
339 frames in 5.3 seconds = 63.986 FPS

I know it couldnt be my monitors refresh rate because I've fixed that already. So, if you would be so kind, please help me troubleshoot this problem.

---

### Post by soulreaver2991 on 2008-01-15
quick question for you i have the same graphics card but my issue is my computer starts up i see the ubuntu loading screen as soon as the bar fill and goes to start up to the desktop i get a no signal display on my monitor the speakers goes through the normal chimes telling me that the computer is actually going to the desktop but killing the graphics card 

did you have any problems when you fist installed linux with your card ??
if so how did you fix them it's driving me crazy !

---

### Post by Semong on 2008-01-15
Sorry but I'm afraid not. Sounds to me like you have a short in your connection somewhere or possibly the card itself has been damaged. Stillyet thats strange. Why would it work up until you login and X is trying to start... Can you run the live CD without problems? I haven't the slightest clue how to go about fixing it whatever the problem may be so maybe you should ask for help with a new post. I'm just a begginner here too. Best of luck too you  :)

---

### Post by soulreaver2991 on 2008-01-15
thanks anyway ya it bugging the hell out of me why it's not working i can't even use the live cd same issue i think i'm going to pull the card and get a new one

---

### Post by nikoPSK on 2008-01-15
maybe xorg got messed up?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

nikoPSK

---

### Post by Semong on 2008-01-17
> **nikoPSK said:**
> maybe xorg got messed up?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

nikoPSK

First you would have to change the session to failsafe mode (if possible), then type the above code, and then press ctrl+alt+backspace to restart X. In theory this will fix your problem.

---

### Post by nikoPSK on 2008-01-17
> **Semong said:**
> First you would have to change the session to failsafe mode (if possible), then type the above code, and then press ctrl+alt+backspace to restart X. In theory this will fix your problem.

hopefully will! :)

nikoPSK

---

### Post by Semong on 2008-01-18
Well I've solved this problem along with quite a few others by simply switching from Xubuntu 7.10 to Ubuntu 7.10.

---

