---
title: "screen resoultion"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by fire_storm on 2006-08-27
hi

i tryed the live cd but part of my screen wasnt used (it seemed like it was draged ) and the resultion was too low and cant be changed is that fixable??
my screen is LG flatron ez t730s  and my graphics card is ATI radeon xpress 200 series 

and i have a router but it seems that it cant conect to the internet when i use linux can some one help
D-LINK dsl-524T

thank you

---

### Post by Philber on 2006-08-27
Hi, yep same problem! In fact I want to install to HD and the resolution is preventing me from clicking an 'ok' or similar button that I presume should be visible once I've selected my installation language! Help please someone.

---

### Post by Russty of Oz on 2006-08-27
> **fire_storm said:**
> hi

i tryed the live cd but part of my screen wasnt used (it seemed like it was draged ) and the resultion was too low and cant be changed is that fixable??
my screen is LG flatron ez t730s  and my graphics card is ATI radeon xpress 200 series 

and i have a router but it seems that it cant conect to the internet when i use linux can some one help
D-LINK dsl-524T

thank you

I have had the same problems in the past.  For the resolution click System > Preferences > Screen Resolution and select one from there.

As for the other problem, if you mean it is off center and have a black bit on the side, then on my screen I press the auto tune button (mine isn't an LG so I don't know if you have one)  My screen always goes off center when I switch between Ubuntu and Windows.

---

### Post by Jerome36 on 2006-08-27
> **Russty of Oz said:**
> As for the other problem, if you mean it is off center and have a black bit on the side, then on my screen I press the auto tune button (mine isn't an LG so I don't know if you have one)  My screen always goes off center when I switch between Ubuntu and Windows.

Yup, look for the Auto, or Auto Tune button.  Or it could be hidden in one of the menus on the monitor.  This usually happens if you go between Ubuntu and Windows, at least in my experience.

As far as the screen resolution goes, Russty of Oz mentions where you change it.  However, if for some reason the other resolution options aren't available, you'll have to add them.  I never had to, and don't know how, but I've seen them discussed before... in this section of the forum as a matter of fact.  Just do a quick search for "resolution," or "screen resolution," and I'm sure something will pop up.

---

### Post by Philber on 2006-08-27
Hi, I tried changing the screen resolution as you suggest but the only option available is the one already set. 480 by something I think. It will not allow itself to be changed, though my screen is easily able to go far higher.

---

### Post by Jerome36 on 2006-08-27
Here's [one of the topics](http://www.ubuntuforums.org/showthread.php?t=244380&highlight=screen+resolution) I had seen.

---

### Post by derred on 2006-08-27
Try pressing Ctrl+Alt+F1(you can also use F2..F6), now don't be scared, this will put you in a text based console. Log in normally (username, password).
Next type in "sudo dpkg-reconfigure xserver-xorg" and type in your password again. This will help you reconfigure your graphical interface.
After the wizard finishes press Ctrl+Alt+F7 and then Ctrl+Alt+BkSp to restart your Xserver. The display should now work normally. You can also change your resolution if it's still too low to the highest setting you choose in the setup.

---

### Post by rlreich on 2006-08-27
I've got the resolutions set but it won't let me select it when I exit out and get back to the GUI.

---

### Post by Perfect Storm on 2006-08-27
Do you have the monitor manual? Does it show what which Horizontal scan range and Vertical scan range it have?

---

### Post by rlreich on 2006-08-27
Yes but it's all in Chinese! Actually it gives the ranges when I press Auto/Set. The default xorg is set to be a little larger range. Does it have to be exact?

---

### Post by Perfect Storm on 2006-08-27
may I see your xorg.conf?
```
cat /etc/X11/xorg.conf
```

---

### Post by fire_storm on 2006-08-27
thank you about the router can i make it work it is d-link dsl-524t

---

### Post by rlreich on 2006-08-27
It's working now but I had to reboot a couple of times. Might be something more serious going on inside. Crossing fingers, making burnt offerings to the Dell computer gods.

---

