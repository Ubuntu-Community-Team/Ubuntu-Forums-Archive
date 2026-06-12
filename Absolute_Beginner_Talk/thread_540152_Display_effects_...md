---
title: "Display effects .."
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Lifes Victim on 2007-09-01
I go enable it and everything I should, but then the screen goes white and all I see is my cursor, which is still able to move. Do I just need to wait for it to load or something (been impatient and just rebooted and didn't try again)? My computer is listed on a site that it should be able to do the effects and has the hardware to do so... Is there a program I need to install first?:confused:

---

### Post by Perfect Storm on 2007-09-01
Is the 3D driver install and working? If it's working you might check here: [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by Lifes Victim on 2007-09-01
New thing now:
I boot Ubuntu (using XP atm), and as soon as I log on now the screen is white again and stays that way. If I click around randomly, the items will open up, but then go back to white, so I can't go back and disable the effects. Also on one of my random clicks it moved around a little in the cube effect, then went back to all white again. Help?:confused:

---

### Post by ramjet_1953 on 2007-09-01
What brand of video card / chipset and model do you have.

It sounds like you need to enable aiglx and load the driver for your video card.

Regards,
Roger :cool:

---

### Post by Lifes Victim on 2007-09-01
What can I do for the moment though when all I am getting is a white screen?

---

### Post by Perfect Storm on 2007-09-01
Which card do you have?

---

### Post by Lifes Victim on 2007-09-01
Where would I find this out?

---

### Post by Lifes Victim on 2007-09-01
Really needing some help. Even in recover mode the screen is just white. This is killing me.

---

### Post by Perfect Storm on 2007-09-01
Try

<ctrl>+<alt>+<F1>

can you get to CLI (commandline interface?)

---

### Post by Lifes Victim on 2007-09-01
I can do the <ctrl><alt><f1> thing, what do i type in there? I just need to disable display effects.

---

### Post by Perfect Storm on 2007-09-01
```
sudo apt-get remove compiz beryl
sudo apt-get autoremove
```

Then you should be able to login in X

You can always install them again if you want (when installing the restrictive driver for your card)

```
sudo apt-get install compiz beryl
```

---

### Post by Lifes Victim on 2007-09-01
I'm not even using Beryl though, it's just the basic display effects I need to disable.

---

