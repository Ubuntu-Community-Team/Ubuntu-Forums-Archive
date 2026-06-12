---
title: "Just got Ubuntu installed, where do I start?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by chunkylover21 on 2007-10-26
I just got the OS installed. Naturally I want video drivers first. So I downloaded them from ATi, but when I try to run the driver installation it says...

Could not open the file /home/zach/Desktop/ati-d…-8.42.3-x86.x86_64(2).run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Character Coding: Current Locale (UTF-8)

---

### Post by TidusBlade on 2007-10-26
[This](http://ubuntuguide.org/wiki/Ubuntu:Gutsy) helped me alot when I first started.
Try out [this](http://ubuntuguide.org/wiki/Ubuntu:Feisty) one if your using Feisty.
I found instruction on it on how to install my ATi and nVidia so hope it works for you too ;)

---

### Post by llamakc on 2007-10-26
Beside searching here for instructions (and I think there's a stickied thread already in this forum), and searching on google for something like "ubuntu ati howto" or whatever is specific to your issue, you can always look at [http://wiki.ubuntu.com](http://wiki.ubuntu.com) and use the search feature there.

---

### Post by Dr Small on 2007-10-26
Give it executable permissions:
```
chmod +x *filename.run*
```

Then run it:
```
./*filename.run*
```

---

### Post by Crandom on 2007-10-26
in GG restricted drivers are already enabled. Anyway, use flxdev rather than the ati driver

---

### Post by chunkylover21 on 2007-10-26
Remember this is the Absolute beginners forum. I have no idea what to do. I have no idea what flxdev is. Nor do I know where to type in those lines of code (cmd line?)

---

### Post by chunkylover21 on 2007-10-26
Yeah so I just went under the Admin menu and went to like display or graphical drivers. and it said my ati thing wasnt activated or whatnot. So i clicked to enable it, it installed 4 drivers and made me reboot. Now just ******* awesome it doesnt display anything, it says input not supported. I even put a different monitor on and same thing.

---

### Post by llamakc on 2007-10-26
What card do you have?

---

### Post by chunkylover21 on 2007-10-29
Ok well I got a differnet card for a few days, its an 8400 GS and did the same process but now its working. I still need to install the drivers from nVidia though. And they still wont open. Same error. How do I give it permission? Where do I enter the code?

---

