---
title: "I get a blank screen when I Log Out..."
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-20
Hi,
I just reinstalled Feisty today after a disaster with Gutsy. (Long story...;)) Most everything is working well, except when I try to log out. I get a blank screen with no GDM Log On page at all. Just a black screen.
 
I have a Gateway M675x laptop, with an ATI Raedeon RV350 card. It's a Pent 4 with 1.25 GB of ram.

Does anyone have any idea what could be causing this?

I appreciate any suggestions or ideas.

Many Thanks, ....Frank B.

---

### Post by Golyadkin on 2007-06-20
When it happens, try pressing Ctrl-Alt-Backspace to restart GDM.

Also, you can tell Gnome to restart GDM everytime you logout.

---

### Post by Brightbelt on 2007-06-20
Thanks Golyadkin !! Ctr-Alt-Backspace does the trick. It'd be nice Not to have to do it every time I log out, but this is certainly better than a reinstall. So you're saying I can do ctr-alt-backspace every time I log out.

Thanks again,...Frank B.

---

### Post by Golyadkin on 2007-06-21
You are welcome :) 


There is a setting that will do it automatically for you every time you log out. 
**System > Administration > Login Window > Restart X server everytime I logout.**

---

### Post by Brightbelt on 2007-06-21
Thanks Golyadkin!! That works....and just to clarify, what gets checked is a function called, "Restart Xserver with each login".  

But it works. Thanks, Frank B.

---

### Post by Golyadkin on 2007-06-21
Ah, I did it from memory :D glad it worked.

---

### Post by zackf on 2007-06-22
Interesting, I am having the exact same problem, but neither trick worked for me. I wouldn't think there is an error with my x config since it works the first time after I boot up...

Any other suggestions?

Thank you!

---

### Post by Brightbelt on 2007-06-22
Yes Zack, that was my situation as well. I could boot to my Log On screen just fine - it would appear every time. It was only when I logged out after being on my desktop that the Log On Screen would not appear.

If I come across something else that could help you, I'll let you know. Otherwise, I'm just lucky that these tricks worked for me. Otherwise, I'm clueless as well.

Thanks, Frank B.

---

