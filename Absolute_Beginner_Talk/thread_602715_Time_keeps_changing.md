---
title: "Time keeps changing"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Blue Sassley on 2007-11-04
I have a kind of boot boot setup going right now on my production laptop... I have windows xp installed on the HD and ubuntu 7.10 installed on a 4GB express card... but when I boot to ubuntu the time seems to be correct and then when I boot back to Windows the time seems to be forward 6 hours as I'm in CST/CDT. In ubuntu under the prefs options I have the UTC box un-checked, should I have it checked to keep the time correct between both OSes? Or is there something else I need to do?

Thanks,
Blue

---

### Post by schorsch on 2007-11-04
What is the output of
```
less /etc/default/rcS
```
```
man rcS
``` will give you some hints about the variables defined in the mentioned file

---

### Post by katch22 on 2007-11-04
I had the same very annoying problem when I first installed both Fiesty and Gutsy. 

Try this:
Go to System>Administration>Time and Date
Set your proper time zone
Then set "configuration" to "Manual" and click the button "Synchronize Now" 
It should then tell you that you need to install some package and ask if you want to install it. 
After installing that package, I had no more problems with my time! :)

---

### Post by Blue Sassley on 2007-11-04
> **katch22 said:**
> I had the same very annoying problem when I first installed both Fiesty and Gutsy. 

Try this:
Go to System>Administration>Time and Date
Set your proper time zone
Then set "configuration" to "Manual" and click the button "Synchronize Now" 
It should then tell you that you need to install some package and ask if you want to install it. 
After installing that package, I had no more problems with my time! :)

I will double check to make sure the right TZ is selected, but I think it already is.

Get back to you soon,

Thanks,
Blue

---

### Post by katch22 on 2007-11-04
> **blueley said:**
> I will double check to make sure the right TZ is selected, but I think it already is.

Get back to you soon,

Thanks,
Blue

Well, don't forget the rest of what I wrote. :) 
It was when I tried to synchronize my time to the time server that it prompted me to install something.

---

### Post by Blue Sassley on 2007-11-04
You mean when you set it up to sync with a NTP server?

Blue

---

### Post by katch22 on 2007-11-04
Yes, exactly. There is a "synchronize now" button. I believe it was when I hit it that it installed the package that fixed my problem... Maybe it was actually when I tried to put it on the "keep synchronized with internet server" setting. But one of those things brought up a prompt that told me in order to do what I was trying to do I needed to install a package. It asked if I wanted to and then it installed it. Then my time problems when switching between OSs were solved. That is just what worked for me, thought it might help you out too.

---

