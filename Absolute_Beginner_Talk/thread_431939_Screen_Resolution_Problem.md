---
title: "Screen Resolution Problem"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by bprof on 2007-05-03
Hi,

I was using Ubuntu Live CD (7.04) my screen resolution was perfect and if I want to change it I have this list to choose from. But after I installed it, I have 640x480 and there is no other resolution in the list to select from. Could you please help me know why this happened and how to solve it?

Thank you!

---

### Post by starcraft.man on 2007-05-03
Easy fix for that... run this in terminal. (Applications > Accessories > Terminal)

```
sudo dpkg-reconfigure xserver-xorg
```

Just keep selecting ok if you don't know what an option means, then when you get to the monitor section make sure your screens maximum resolution is ticked off in the circle box. :)

Just a note, but you should likely install your video drivers as well, always makes things run better (I assume you have a 3rd party card ati/nvidia).

[Envy]("http://www.albertomilone.com/nvidia_scripts1.html"), just read instructions, download the 0.9.2 debian and double click it on the desktop to install. Then go Applications > System Tools > Envy and pick your driver (automatically install nvidia/ati). If there are any prompts, say yes. 

Installing the drivers of course is at your discretion, you only need to run the command in terminal to get your resolutions back :).

Have a nice time.

---

### Post by bprof on 2007-05-03
Thanks a lot m8 that solved it. :)

---

### Post by starcraft.man on 2007-05-03
> **bprof said:**
> Thanks a lot m8 that solved it. :)

Your welcome, have fun with Ubuntu.

---

### Post by bokorpop on 2007-05-03
I have the same problem, but I cannot solve it because when I type in the code, it asks for my password, and when i start to type in my password my keyboard suddenly goes dead. It won't let me type anything. The only key it responds to is "enter" at which point it tells me my password is invalid, but won't let me type in the proper one.

Also, I tried installing some program from add/remove called "resolution changer" or something to that effect(I typed in 'resolution" in add/remove and it came up), but the program doesn't run at all when i click the icon.


I am new to Linux/Ubuntu btw. Somebody please help!

---

### Post by starcraft.man on 2007-05-03
> **bokorpop said:**
> I have the same problem, but I cannot solve it because when I type in the code, it asks for my password, and when i start to type in my password my keyboard suddenly goes dead. It won't let me type anything. The only key it responds to is "enter" at which point it tells me my password is invalid, but won't let me type in the proper one.

Also, I tried installing some program from add/remove called "resolution changer" or something to that effect(I typed in 'resolution" in add/remove and it came up), but the program doesn't run at all when i click the icon.


I am new to Linux/Ubuntu btw. Somebody please help!

THREAD HIJACKER!!! :p

Hehe, ummm well I can tell you that your keyboard certainly shouldn't stop working in the middle of typing the password, thats not anything Ubuntu does. Can you try a different keyboard?

I have no advice for the resolution program, its best to go right to the source with the xorg file. Try a different keyboard and if that works, you may need a new one >.>.

---

### Post by bokorpop on 2007-05-03
Well it does seem to be Ubuntu and not my keyboard because it only won't let me type when it asks for the password in terminal, in all other instances I can type just fine. if I open a web browser and type, its fine, if I try to type a command in terminal, its fine, only when it asks for the password does it not allow me to type anything.

---

### Post by RKCole on 2007-05-03
bokorpop,

As for your password issue, the terminal usually (to my knowledge) never gives visual feedback when a password is entered.  This was something that threw me off my first time using Linux.  But now...I like it.  Just type in your password as normal and hit ENTER; hopefully things should then work just fine.

Take care.

---

### Post by bprof on 2007-05-03
> **starcraft.man said:**
> Your welcome, have fun with Ubuntu.

I'm having a lot already, now I find myself just want to work with Ubuntu and not any other OS.

---

### Post by starcraft.man on 2007-05-03
OH! Hehe, ya, I thought you knew that. Unlike in windows or any other place, you won't see the stars (*****) across the password place. Just an Ubuntu thing, your key board still works :)

---

### Post by starcraft.man on 2007-05-03
> **bprof said:**
> I'm having a lot already, now I find myself just want to work with Ubuntu and not any other OS.

YAY!:p  Thats what I love to hear :D

---

### Post by bokorpop on 2007-05-03
Thanks for solving 2 problems of mine! This is my first post at the Ubuntu forums and I'm really impressed with the general activity and spirit of helping. 

One strange thing though which  can't put my finger on, is that the resolution still seems "stretched" lengthwise like a rubberband in 1440X900. I use 1440X900 in Windows(I am dual booting) and it does not look stretched there. I tried to switch to 1440X1050 in xorg but it wouldnt let me as perhaps 1440X 900 is my maximum. Its not unbearable or anything, but just strange. Any idea why this is?

---

