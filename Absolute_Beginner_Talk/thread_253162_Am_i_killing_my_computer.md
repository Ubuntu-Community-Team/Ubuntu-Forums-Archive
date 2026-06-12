---
title: "Am i killing my computer?"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by krazed nun on 2006-09-07
I use the command 'sudo shutdown -h now' to turn off my computer, beacause the shutdown icon disspeared. It also does not appear when i log off. If i leave my computer on the screensaver all day, will that do damage to my computer? I am getting really worried about turning off my computer the terminal way because it takes much longer to boot when i turn it on. It also says: blah blah has been mounted 30 times without being checked. blah blah.

Please help. thanx in advance.:)

---

### Post by reacocard on 2006-09-07
No idea y your shutdown icon would have disappeared like that. the command should be just fine though, its a proper shutdown. leaving it on screensaver won't damage the computer. maybe the monitor if it stays on, but the computer itself will be fine. the mounted XX time without check is normal. ubuntu automatically runs an fsck (linux scandisk) every so many mounts.

---

### Post by halitech on 2006-09-07
I leave my computer on 24/7 and just have it blank the screen so it can run folding@home and I never have any troubles. back in the day, it was recommended to turn the computers off caue of monitor burnin but it's not so much of a problem anymore and new systems use very little power when running all day anymore so might as well leave it on.

---

### Post by taurus on 2006-09-07
You can run that command to shutdown your computer.  It is logical and reasonable way to do it...  Are you sure you can't shut it down after you log out of your window manager.  There is an icon at the bottom left and when you click on it, you have an option to reboot, shutdown, and a few others!  

And you only get the "blah blah has been mounted 30 times without being checked. blah blah" only once 30th time you boot Ubuntu!!!  It's not like it runs every single time you boot into Ubuntu...

---

### Post by akniss on 2006-09-07
> **krazed nun said:**
> I use the command 'sudo shutdown -h now' to turn off my computer, beacause the shutdown icon disspeared. It also does not appear when i log off. If i leave my computer on the screensaver all day, will that do damage to my computer? I am getting really worried about turning off my computer the terminal way because it takes much longer to boot when i turn it on. It also says: blah blah has been mounted 30 times without being checked. blah blah.

Please help. thanx in advance.:)

Right-click on a bare spot on the panel.
  Choose "Add to panel..."
    Choose the "Quit..." applet under 'Desktop & Windows'
and you should get a logout button back on your panel.

---

### Post by krazed nun on 2006-09-07
thanx. i am probably gonna leave my computer on screensaver with the briteness turned all the way down. that way i dont kill my backlight. By the way, it is usefull to leave it on for downloading torrents. now i feel more save turning it off. thanx again

---

### Post by jpkotta on 2006-10-12
This will turn off the monitor (much better than just dimming it).

```
sleep 2; xset dpms force off
```

---

### Post by petri on 2006-10-12
> **jpkotta said:**
> This will turn off the monitor (much better than just dimming it).

```
sleep 2; xset dpms force off
```

... and then? How to wake upp the monitor, moving mouse or something? I'd like to test that but... :-D

---

### Post by petri on 2006-10-12
> **krazed nun said:**
> I use the command 'sudo shutdown -h now' to turn off my computer, beacause the shutdown icon disspeared. It also does not appear when i log off. If i leave my computer on the screensaver all day, will that do damage to my computer? I am getting really worried about turning off my computer the terminal way because it takes much longer to boot when i turn it on. It also says: blah blah has been mounted 30 times without being checked. blah blah.

Please help. thanx in advance.:)

The shutdown icon disappeared question has been asked quite a few times, why not make a Search and find out. There was two or three different ways to get the icons back and I don't remember what they were. :rolleyes:

---

