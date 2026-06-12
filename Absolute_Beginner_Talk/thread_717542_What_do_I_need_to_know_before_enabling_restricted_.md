---
title: "What do I need to know before enabling restricted ATI drivers?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Laughed on 2008-03-07
I am sitting at my desktop and everything seems fine except
1.) everything looks bleached or washed out
2.) I have yet to enable the resticted ATI drivers because the last time I did I needed to reinstall the OS

Is there anything I should do before enabling these drivers???

---

### Post by jan quark on 2008-03-07
you can also try the application envy to install the ati drivers if the restricted ones caused trouble:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by SunnyRabbiera on 2008-03-07
Yeh, ATI sucks :D

---

### Post by rockinlinux on 2008-03-07
well im dealing with this problem right now. I have no 3d and the resrticted drivers just mess everything up. what card do you have?

also i have heard of envy but i have read it might mes other things up....not sure though

---

### Post by rockinlinux on 2008-03-07
im trying envy now so ill post how it works in a bit...

FYI i have a ATI HD2600PRO super PCI-E

---

### Post by Laughed on 2008-03-07
Im running an x850XT Platunim PCI-e. I hate to say this but I am going to wait on you. I do not want to reinstall the OS and I want to have a btter understanding of what I'll need to do.

Can anyone tell me why the picture is so bleached? Grey is almost none existant.

---

### Post by rockinlinux on 2008-03-07
i dont balme you, i would wait too...i dont really mind reinstalls or anything...im trying envy mostly to help you. ;)

as far as the bleached...look in your screens and see of you can mess with the colors...or try to adjust your monitor...not really sure though

---

### Post by rockinlinux on 2008-03-07
well the good thing is that envy is downloading the latest drive from ATI, it will work better than the one in the repos...i hope :)

---

### Post by rockinlinux on 2008-03-07
WORKED GREAT!!! easy to do....i now have all my 3d working!! :)

---

### Post by Laughed on 2008-03-07
Nice, hopefully I'll have the same luck. How do I go about getting Envy from the desktop??? Yep, Im that green?

---

### Post by Laughed on 2008-03-07
I am about to install envy and under status it says: Same version already Installed.

What gives? I do not have 3d rendering. I know that because I can't play chess in 3d. SO do I go ahead and enable the restricted ATI drivers. I really, really, really do not want to have to reinstall this OS.

---

### Post by Laughed on 2008-03-07
How do I enable 3d mode??? 

This is the error I am trying to solve:
Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings.

---

### Post by rockinlinux on 2008-03-08
so if you already have envy got to a terminal (Applications>>Accessories>Terminal) and type in 

```
envy -g
```

This bring up a gui interface. Click on the "install ATI drivers"....thats it..it does the rest from there. When it asks you if you want to automatically write something toa file say "yes" and then it will ask you to reboot, say "yes".

When you reboot you should have 3d!

good luck let me knwo if i can help anymore

---

### Post by Laughed on 2008-03-08
I did that earlier and I still didnt have 3d. I just finished re-installing the OS becuase of conflicts with the video feed. I was being forced to boot up in low graphics mode, and attempts at fixing it just caused the image to be unreadable.

Should I enable the restricted drivers, envy, compfusion, all 3, and in what order.

---

### Post by xc3RnbFO8P on 2008-03-08
Just in case if you have not seen this:

[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu")

---

### Post by rockinlinux on 2008-03-08
make sure that everything you did with the rescrited drivers is totally off the machine. the do the envy and dont do anything else...it worked for me but we have different cards....mine is still working great....

---

