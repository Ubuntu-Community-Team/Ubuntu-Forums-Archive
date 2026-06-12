---
title: "resolution"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by smellycorpse on 2007-11-21
can someone give me a link to a tutorial or anything info on changing the resolution in ubuntu? i am just running the live cd right now but its funny cuz the highest res is 800x600, and when i go to "install ubuntu" the window is too big and i can't go to the bottom of the page to continue hehe. ive read posts about "xorg" but i am clueless to what that is or how to use it =P thanks!

edit: ok nvm about the whole installation part, i figured that out lol. but i would still like to know how to change the res.

---

### Post by olivero1 on 2007-11-21
You should be able to change the resolution by going to 

System>Preferences>Screen Resolution

the xorg is a command you run in the terminal, I am not sure if it will work under LiveCD. Simply run the code below in the terminal:

Applications>Accessories>Terminal

```
sudo dpkg-reconfigure xserver-xorg
```

I would go for the Screen Resolution first. If you are not able to set the resolution you like check your graphics card for and make sure it is not blacklisted.

---

### Post by banewman on 2007-11-21
The resolution problem is because you don't have the right video card driver installed.
While installing ubuntu if you press the ALT key then hold the left mouse button down and then drag the cursor upwards you will move the window up and can make selections and continue installing.
Once installed you can then find the way to install the right driver for your card - lots of howto's for doing that. :)

---

### Post by smellycorpse on 2007-11-21
right, i'm just trying to get ubuntu installed first because some of my drivers are on discs and i cant open my drive with the live cd in. but thanks for the quick replies i really appreciate it.

---

### Post by olivero1 on 2007-11-21
No problem - good luck and have fun!

---

### Post by banewman on 2007-11-21
Let us know how it goes. :)

---

### Post by smellycorpse on 2007-11-21
Thanks again, its installing now. I'm so glad to be a part of this, it feels so revolutionary and communal, lmao in a good way!

---

