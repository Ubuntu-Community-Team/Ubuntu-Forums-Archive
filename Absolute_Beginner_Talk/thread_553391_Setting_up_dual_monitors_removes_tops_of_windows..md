---
title: "Setting up dual monitors removes tops of windows."
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by SphereX253 on 2007-09-17
Hey everyone.  I recently got all the programs and everything that I've been trying to get working (noob) up a running. My problem is, when I got into my nvidia settings and set up my dual desktop (which works just fine after a reboot) the tops of my windows dissapear like so many others have in other posts.  Again... they only dissapear AFTER i've setup the dual monitors, and the only way to get them back is selecting metacity as my manager.

I can only pray for a response.

---

### Post by burt_57 on 2007-09-17
> **SphereX253 said:**
> Hey everyone.  I recently got all the programs and everything that I've been trying to get working (noob) up a running. My problem is, when I got into my nvidia settings and set up my dual desktop (which works just fine after a reboot) the tops of my windows dissapear like so many others have in other posts.  Again... they only dissapear AFTER i've setup the dual monitors, and the only way to get them back is selecting metacity as my manager.

I can only pray for a response.
I can run dual monitor in Windows Xp
In Ubuntu,,,,,,,,,,,,, no way :confused:

---

### Post by alwiap on 2007-09-17
I had the same problem with my setup, I use Compiz Fusion though, didn't see if you did or not, but putting this is console fixed it:

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

again that might just work if you're using Compiz only, I have no idea (I'm a nub) but this solved my problem.

GL

---

### Post by SphereX253 on 2007-09-17
Yes, I'm using compiz fusion.  Its accually my roomates machine, so i will go try this out and hopefully it works.  Seems like everything I do on my machine works just fine, no problems (exept for random mistypes or other small mistakes I made) but working on my roomates machine is giving me an anurism.  Thanks for the suggestion. Off I go.

---

### Post by SphereX253 on 2007-09-17
Fantastic. That worked, Than you so much for the quick response and useful information.

---

### Post by burt_57 on 2007-09-18
> **alwiap said:**
> I had the same problem with my setup, I use Compiz Fusion though, didn't see if you did or not, but putting this is console fixed it:

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

again that might just work if you're using Compiz only, I have no idea (I'm a nub) but this solved my problem.

GL

How do you install Compiz Fusion?
I have downloaded it and it is in  /home/robert/compiz-0.5.2.....many files in there !  :confused:

---

