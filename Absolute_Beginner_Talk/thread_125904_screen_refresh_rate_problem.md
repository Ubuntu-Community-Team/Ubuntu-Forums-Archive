---
title: "screen refresh rate problem"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by laptin on 2006-02-05
when i set my resolution at 1024x768, the refresh rate is at 60hz. 
But i know my monitor can go up to 75hz. (in winxp, it's that refresh rate)

How can I change the refresh rate? 
I tried System/Preferences/Screen Resolution. but only has 60hz.

my system is 32bit. ati radeon9600. do you think installing the ati driver helps?

Is there a way to change refresh rate ?

---

### Post by Greyice on 2006-02-05
I run an ATI9600 and I'm just grateful that it's recognised. Don't use the ATI drivers and jsut settle for the 60Mhz refresh rate.

ATI hasn't got great drivers for linux. Go through the forums and search, you'll see there's quite a lot of conflict with the ATI chipsets.

I've personally had to redo my installation a few times to learn the hard way.

Sorry for the news.

---

### Post by Perfect Storm on 2006-02-05
Try this:

Find your monitor manual
open the terminal

```
sudo gedit /etc/X11/xorg.conf
```

Change **HorizSync ** and **VertRefresh** as it says in the manual, reboot.

---

### Post by laptin on 2006-02-05
[QUOTE=Artificial Intelligence]Try this:

Find your monitor manual
open the terminal

```
sudo gedit /etc/X11/xorg.conf
```

Change **HorizSync ** and **VertRefresh** as it says in the manual, reboot.[/QUOTE]


thank you!! this worked.  My VertRefresh was set to 43-60.  I changed it 43-75 and i got it set back up to 75hz.

Give it a try, Greyice. 

thank you all. Now one problem solved with linux, onto my next one....

---

