---
title: "Ubuntu Install Procedures"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by davidmoore83 on 2006-04-04
Hi,

I'm not that new to ubuntu but one thing i would like to clarify in my head is the best procedure for install and tuning/perfecting the setup.

1. When do you install the most appropriate kernal? Compile during install or once your in the desktop enviroment with the default installed kernal? 

2 .When do you delete the old one....or do you not delete it? 

3. When is it best to install other drivers?.....before or after the optimal kernal? 

4. What happens when you change the kernal do you need to re-install programs and drivers?

I probably have more questions but my head is buzzing from all the coffee right now :-D

---

### Post by taurus on 2006-04-04
[QUOTE=davidmoore83]Hi,

I'm not that new to ubuntu but one thing i would like to clarify in my head is the best procedure for install and tuning/perfecting the setup.

1. When do you install the most appropriate kernal? Compile during install or once your in the desktop enviroment with the default installed kernal? 

2 .When do you delete the old one....or do you not delete it? 

3. When is it best to install other drivers?.....before or after the optimal kernal? 

4. What happens when you change the kernal do you need to re-install programs and drivers?

I probably have more questions but my head is buzzing from all the coffee right now :-D[/QUOTE]

1.  Ubuntu will install the default, i386, kernel for you and if you want to install i686, you can do that after it finishes installing.  Just use synaptic and search for the i686 kernel then.

2.  I would keep the old one, default kernel, around just in case there is something wrong with the new one.  That way, you can still boot your Ubuntu and fix whatever the problem is.

3.  I assume you are talking about driver for your video card.  Install it after you install the new kernel.

4.  You might have to reinstall the driver for your video when you install a new kernel but that is as far as you have to reinstall.  Chances are you may not even have to reinstall the driver for your video.  In other words, no need to reinstall anything unless it doesn't work with the new kernel...

---

### Post by trent dillman on 2006-04-04
Also, be aware that you'll probably just install a new pre-compiled kernel (rather than compile one). Your software should be fine, but some drivers (particularly nvidia) might need reinstalled. I say might only because sometimes, kernel updates are just patches and don't install a whole new kernel.

I hope that made sense.

---

### Post by davidmoore83 on 2006-04-04
great thanks,

What Kernal would you say is best for an AMD Athlon XP 3200+ then? i386?

---

### Post by carlosqueso on 2006-04-04
For Athlon processors, the customized one is a K7 kernel.   I use a custom kernel on my Athlon machine, so I'm not really sure what kind of performance gain you get with that though.

---

