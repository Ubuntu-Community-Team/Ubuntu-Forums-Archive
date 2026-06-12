---
title: "dual monitor setup"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by siion on 2007-12-12
how do you setup dual monitors, im using nvidia, i've installed it using envy. 

When I go onto control panel, its kinda all weird, because it doesnt show my resolution (1440x900) it shows some close, the only way I can get it to detect my resolution is auto.

Then i turn on my monitor as seperate X Screen, 

but whenever i try apply it says errors, then i hit try whats possible n it loads the other screen but then my primary stays black.

I can't get it to span dual.

---

### Post by overdrank on 2007-12-12
> **siion said:**
> how do you setup dual monitors, im using nvidia, i've installed it using envy. 

When I go onto control panel, its kinda all weird, because it doesnt show my resolution (1440x900) it shows some close, the only way I can get it to detect my resolution is auto.

Then i turn on my monitor as seperate X Screen, 

but whenever i try apply it says errors, then i hit try whats possible n it loads the other screen but then my primary stays black.

I can't get it to span dual.

Hi and have you tried twin view?

---

### Post by siion on 2007-12-13
yeah, it doesnt do anything when i try that.

It worked on the live CD, it was clone view.

---

### Post by PartisanEntity on 2007-12-13
You can also launch the terminal and type:

```
nvidia-settings
```

unless that's what you meant.

---

### Post by Havilland on 2007-12-13
I had the same problem, just save the changes to the config and restart your pc, in my case that helped. Iam running on xinerama. Twinview is as far as i know just a stretched Desktop that runs across both screens.

---

### Post by MrSpiffdifilous on 2007-12-13
I had seperate x-views working on my computer up until this morning. I just turned it on and all of a sudden the sudo nvidia-settings command doesnt work. It will work for you , its just a matter of getting the right config. try this

```
sudo nvidia-settings
```
The "sudo" part is very important in this case as you must have root privileges to save the xorg.conf file!

then in the control panel set to seperate x-views and leave the second monitor on auto for now. Hit "Apply" then "Apply what is possible". Now this is where I'm not 100% sure what the button says but its something to the effect of "Save X-configuration" hit that button. it should bring up a dialog box asking where to save it. It should save to /etc/X11/xorg.conf, if  thats where it says hit save or ok or whatever the box says. Quit Nvidia-settings, log out all users and it should apply the settings and you should have dual monitors running.

I hope this helps! Let us know how it turns out!

---

