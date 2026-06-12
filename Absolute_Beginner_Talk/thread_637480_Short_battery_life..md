---
title: "Short battery life."
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by luke949 on 2007-12-11
Hi I have a Acer Aspire 3690 laptop. It says the battery life is around 3 hours, however I only get an hour and a half. I running ubuntu 7.10 and compiz. I am mostly just surfing the internet and checking my email. Any suggestions on how to extend my battery life?

---

### Post by Rocket2DMn on 2007-12-11
When using battery, you can dim your screen to about 1/2 it's normal brightness, disable compiz, and if your processor supports it, make sure it's version of speed-stepping is active (drops the clock cycles per second when processor is not in high demand).

---

### Post by luke949 on 2007-12-11
I do dim my screen, but can you elaborate more on this speed-stepping suggestion? Would i need a certain software? please forgive me for not knowing these things :(

---

### Post by Rocket2DMn on 2007-12-11
Try adding the speed-step applet to your tasbar.  Right click and Add to Panel.  Scroll down to System and Hardware and see if there is an option for CPU Frequency Scaling Monitor or something similar.  If so, add it and you can watch if it varies when you use the computer (like opening a new program).
If that doesn't work, can you tell us what kind of processor you are using?

---

### Post by luke949 on 2007-12-11
Ah well when i tried to add it, a messaged popped up saying my cpu does not support it. I guess that out of the picture, thanks for your help though!

---

### Post by chips24 on 2007-12-11
how old is youre computer? if is a shining piece of metal, you can get the battery for free from youre company. otherwise its up to $100  :(

---

### Post by luke949 on 2007-12-11
well these are the specs: Acer Aspire 3690-2970 Notebook specs:
Intel Celeron M Processor 520, 1.6GHz, 512MB RAM, 80GB Hard Drive, 15.4&#8243; WXGA TFT Display, 8X DVD / 24X24X24 CD-RW Combo Drive

---

### Post by Rocket2DMn on 2007-12-11
Check and see if CPU frequency scaling is enabled.  Go to Applications->System Tools->Configuration Editor (it's like windows' registry editor).  Navigate to /apps/gnome-powermanager/cpufreq and see what values are set for each variable.
On my Pentium M 2ghz, I'm set at unchecked (for nice), performance_ac = 85, performance_battery = 25, policy_ac = ondemand, policy_battery = ondemand

---

### Post by luke949 on 2007-12-11
I do not see System Tools under Applications. Would it be somewhere else?

---

### Post by luke949 on 2007-12-11
Nevermind I found out how to put it back in the menu. Lemme do what you suggested earlier.

---

### Post by Rocket2DMn on 2007-12-11
Right click the Applications menu and select Edit Menus.  Under Menus, scroll down to System Tools and select it.  On the right side check the box for Configuration Editor.
If you can't find it there, just run this in a terminal ```
gconf-editor
```

---

### Post by luke949 on 2007-12-11
For me it is:
Consider_Nice unchecked, Performance_ac 85, Performance_battery 25, Policy_ac nothing, policy_battery nothing.

---

### Post by chips24 on 2007-12-11
how do you post a thread?

---

### Post by chips24 on 2007-12-11
how doya post a thread?

---

### Post by chips24 on 2007-12-11
sry didnt mean to repeat

---

### Post by Rocket2DMn on 2007-12-11
> **luke949 said:**
> For me it is:
Consider_Nice unchecked, Performance_ac 85, Performance_battery 25, Policy_ac nothing, policy_battery nothing.

Try setting the policies to "ondemand".  With that, see if you can add the applet again to the taskbar so you can visually see if the processor is scaling.

> **chips24 said:**
> how do you post a thread?

Go to the help forum - [http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)
At the top there is a yellow-ish button titled Make New Post

---

### Post by luke949 on 2007-12-11
Darn, it still says its either misconfigured or my hardware doesnt support it. I thought i read somewhere online that my laptop does support cpu scaling.

---

### Post by Rocket2DMn on 2007-12-11
I suggest searching around google for the correct way to enable that scaling in ubuntu, I can't do all the work for you :)
Use keywords like ubuntu, cpu, frequency, scaling, enable, centrino, pentium m
I'm sure it's out there, I had to enable scaling on my laptop when I setup with Feisty last spring, so it can be done (I just don't remember how and can't find my source).  Good luck!
Post back about your search.  If you really can't find it, we'll have another look.

---

### Post by luke949 on 2007-12-11
Ok thanks a lot for your help, I will continue tomorrow since its late and I have school tomorrow. Thanks again for your help!
Good night.

---

### Post by rkd on 2007-12-11
It looks like the 3 hours battery life is the manufacturer's estimate.  In general, those estimates tend to be very optimistic.  You know how marketeers are.  So you shouldn't realistically expect to get 3 hours run time on a single charge.  I don't know whether Acer is any better on this point than others, or any worse.  

I've read that the power management stuff in notebooks tends to be black magic that the manufacturers don't document well, if at all.  And they only make an effort to make it work well with Windows.  So battery run time for a notebook computer running Linux tends to be less than the run time for the same notebook computer running Windows.  Another reason to lower your expectation of realistic run time on the battery.

But you probably should be able to get more than 1.5 hours, so it probably is worth your effort to try to improve the time.  I don't have any specific suggestions to help with that.  I just wanted to point out that you shouldn't be surprised if you can't get it to run a full 3 hours on the battery.

---

### Post by btlee on 2007-12-11
> **luke949 said:**
> well these are the specs: Acer Aspire 3690-2970 Notebook specs:
Intel Celeron M Processor 520, 1.6GHz, 512MB RAM, 80GB Hard Drive, 15.4&#8243; WXGA TFT Display, 8X DVD / 24X24X24 CD-RW Combo Drive

As far as i know, celeron M processor does not support cpu scaling.
Don't waste your time in hacking it.

---

### Post by luke949 on 2007-12-11
Ok i followed this guide: [http://ubuntuforums.org/showthread.php?p=3334743](http://ubuntuforums.org/showthread.php?p=3334743) 
and it works great. I can now add the cpu scaler on the task bar now. so if anyone else is having these problems with celeron M's take a look at it. I will post back on how much more time i get on my battery later.

---

### Post by luke949 on 2007-12-11
Ok it works fine, but when I set it to ondemand or conservative, the cpu speed goes down to 199 mhz and then after about a minute my laptop just freezes. Is there any ways to make it stop and 399 mhz and not go any lower?

---

### Post by luke949 on 2007-12-11
does anyone know the answer? its getting annoying when it freezes once it gets to 199 mhz XD

---

### Post by Rocket2DMn on 2007-12-11
First, turn off that p4_modclock module, it might not be the correct one.  I think I'm using "powernowd" to scale my processor.

---

### Post by luke949 on 2007-12-11
ok then

---

### Post by luke949 on 2007-12-11
ok i got powernowd

---

### Post by Rocket2DMn on 2007-12-11
> **luke949 said:**
> ok i got powernowd

is it working correctly?

---

### Post by luke949 on 2007-12-11
I just restarted my laptop after i had uninstalled the cpufrequtils package and stopped p4_modclock from loading on startup and now a message popped up saying I cant change the cpu speed. the same message i got before.

---

### Post by Rocket2DMn on 2007-12-11
Can you please post the exact messages it is giving you?

---

### Post by luke949 on 2007-12-11
yea sure it says:

You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

---

### Post by Rocket2DMn on 2007-12-11
I think maybe you should start another thread under the Hardware & Laptops forum at [http://ubuntuforums.org/forumdisplay.php?f=135](http://ubuntuforums.org/forumdisplay.php?f=135)
They will probably have more success in helping you out (though responses may be more delayed).  You should explain your problem in detail, tell them what steps you have taken, and post a link to this thread for their reference.
Sorry I'm not able to help you fix this problem.

---

### Post by luke949 on 2007-12-11
oh no problem, thanks for your help!

---

