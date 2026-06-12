---
title: "Need advice/help on a few things"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by r5gtt2k3 on 2008-03-07
Right, I'm new to Ubuntu and I have managed to install my driver for my graphics card (8600GT using Twin View setting)) All is working fine, But im using Dual screen, Both of them are coming up just fine and working spot on, But when i maximize a window or app for instance Firefox, It covers both of the monitors, Is there a way to just make it maximize to just either the left or right monitor ? (the fonts have gone really big, actually makes me squint to read it.

Second of all, the security, Everything i do, It wants me  to enter my password, Is there a way to stop this ? I have looked, but as I'm new I'm just getting to grips with it, The login screen needs to go too if thats at all possible, I just want it to boot straight into Ubuntu, not having to enter my username and password each time, thats rather annoying, Anyway, Thanks for any response at all, I've read quite alot on this forum, you all seem helpful enough :) keep up that good stuff you do.



Jay.

---

### Post by r5gtt2k3 on 2008-03-07
Oh an also, Sysinfo is only showing me that i have just only 1 core, Does Ubuntu not support dualcore ?

---

### Post by PurposeOfReason on 2008-03-07
The password thing is really for you're own good. However, if you are dead set to change it, open up a terminal and type: sudo visudo. In this file (press a to be able to tpye, it is using the vim editor), add the following:

YOUR USER NAME HERE    ALL=(ALL) ALL 

Then type :wq to save and close. Restart X.

Login screen. Go to the login screen editor where you change themes and go to the security tab. Simple enough from there.

The dual monitors (I had this before, oh so long ago), are you using compiz?

Ubuntu does support dual cores. Type "cat /proc/cpuinfo' in a terminal for a more reliable read. Also, are use using 32 or 64 bit?

---

### Post by Ecclesia on 2008-03-07
You can allow Ubuntu to boot up without a password by clicking on System -> Administration -> Login Window.

Under the security tab there's a box to click on "Enable Automatic Login".

You won't need to enter passwords as often in Hardy.  Although, asking for a root login isn't entirely arbitrary.

---

### Post by r5gtt2k3 on 2008-03-07
Awesome I will change that then hehe I know it's there to protect me, But I rarely do anything to make me want to protect myself against stupidity, Vista is my main OS, I'm just trying to get the feel for this an understand it more, so then i can use it on my other desktops without no dual boot fuss :)

And no I'm not using Compiz, I'm using just NVIDIA X server settings thingy, Would it work better if i tried Compiz ? I tried to install that before, But even reading the install guides i get lost. Thanks for the reply.

---

### Post by r5gtt2k3 on 2008-03-07
Thanks, It's really weird, As soon as i came onto Ubuntu, i clicked System -> Administration -> Login Window. and nothing came up at all, I've just clicked it again, and all it has asked me to do is enter my password, nothing else.

---

### Post by PurposeOfReason on 2008-03-07
> **r5gtt2k3 said:**
> Awesome I will change that then hehe I know it's there to protect me, But I rarely do anything to make me want to protect myself against stupidity, Vista is my main OS, I'm just trying to get the feel for this an understand it more, so then i can use it on my other desktops without no dual boot fuss :)

And no I'm not using Compiz, I'm using just NVIDIA X server settings thingy, Would it work better if i tried Compiz ? I tried to install that before, But even reading the install guides i get lost. Thanks for the reply.
If you're using 7.10, it's just under one of the tabs you get when you right click the desktop and choose the background. Something like visual effects. But if you don't want it, don't use it. Sometime it makes a difference, sometimes it doesn't.  I'm on a laptop and my nvidia and dual monitor days are 4 months ago but you can try this.
[http://www.zulustips.com/2007/04/01/dual-monitors-howto.html](http://www.zulustips.com/2007/04/01/dual-monitors-howto.html)

---

