---
title: "Updates will not in stall"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by sundance2007 on 2008-03-21
When i try to install the updates I am told are needed (by the icon in the upper tool bar) I get the error below. I tried up checking the 6 that are there one at a time but I still get the error even when it's only installing a zip update??????:confused:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thanks

---

### Post by Tatty on 2008-03-21
Have you tried running 'dpkg --configure -a'... ?

If you are not sure how, open a terminal (Applications->Accessories->Terminal) and type that code in...  or simply copy and paste.

---

### Post by sundance2007 on 2008-03-21
cut and paste what, the line in your email or from the error message. Also I never use terminal and know little of how to use it. I am one that is trying to get away from bill's windows so I know little of how to type in commands and stuff so please be specific or I won't know what you mean.

Thanks,

Steve

---

### Post by brandonclyon on 2008-03-21
Just open terminal and copy paste the command that it says you need to run, 'dpkg --configure -a' without the ' of course

---

### Post by Tatty on 2008-03-21
Ok basically it sounds like some updates were interrupted for some reason at some point,  so you need to force the package manager to finish what it was doing before...

The command: 'dpkg --configure -a'  should do that for you.  But i assume you will probably need root privilages to do this so you should type the following into a terminal  (or simply copy and paste it)

```
sudo dpkg --configure -a
```



The terminal can be found in Applications->Accessories->Terminal

---

### Post by sundance2007 on 2008-03-21
I didn't say anything about trying to run a command, I don't know how. When I click on the icon at the top to install updates I get this error, no commands just click and it  doesn't work as it has in the past.

Thanks

---

### Post by Tatty on 2008-03-21
Sorry, i may have confused you with how i wrote that.

The command i wrote above is what you type into a terminal to fix what has gone wrong.

---

