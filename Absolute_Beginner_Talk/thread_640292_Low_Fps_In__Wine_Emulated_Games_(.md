---
title: "Low Fps In  Wine Emulated Games :("
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by B34ST1Y on 2007-12-14
whenever I run a wine emulated game, I get about 10-30 fps..... vs when I used to run suse 10.2 I would get 90fps which is normal for when I used to run windows.  Is there some plugin I'm missing with wine? 

I have an Everex XT5000T laptop, with an nvidia go 7600



what am I missing here?

---

### Post by Origin415 on 2007-12-14
Make sure you are using the restricted drivers
System -> Preferences -> Restricted Drivers Manager
They aren't open source, but they will give you the full speed of your card.

---

### Post by B34ST1Y on 2007-12-14
is there some wine libraries that I'm missing? maybe something with directX?

---

### Post by B34ST1Y on 2007-12-14
origin that definitely didnt solve my problems...


I have a friend who's using a custom built PC running gutsy as well.........and he gets the SAME problem -_-      


come on SOMEBODY knows the secret here, please help a noob out :(

---

### Post by shae on 2007-12-14
What version of wine are you using?  What version of wine were you using in OpenSUSE 10.2?

---

### Post by skymera on 2007-12-14
ooook,

i fouind the new versions  of wine 0.9.47+..are kinda suckish.

im running 0.9.46 and perfect!

---

### Post by B34ST1Y on 2007-12-15
> **skymera said:**
> ooook,

i fouind the new versions  of wine 0.9.47+..are kinda suckish.

im running 0.9.46 and perfect!

define perfect? And using what programs? have you done a comparison running 3d games using .46 and some other ver and got comparable difference?



EDIT:   I was using 0.9.50, obviously that gave me my original problems....so I heard .41 was good and i downgraded....but nothing changed! dlfkjdfkfj


would running compiz affect this THAT drastically? I turned it off but it really didnt change much

---

### Post by skymera on 2007-12-16
the fact is my 3D games wouldnt even run with 0.9.47+

i get good FPS aswell

---

### Post by B34ST1Y on 2007-12-16
> **skymera said:**
> the fact is my 3D games wouldnt even run with 0.9.47+

i get good FPS aswell

so which version of wine are you using? and do you by chance, use compiz-fusion ? ?

---

### Post by peitschie on 2007-12-16
Hi,

It is HIGHLY recommended that you disable compiz before attempting to run 3D games.  Compiz draws on the 3D card (rather than the CPU), which means it will in fact take some power away from your games.  To disable it, see this thread here: [http://www.uluga.ubuntuforums.org/showthread.php?t=605429]("http://www.uluga.ubuntuforums.org/showthread.php?t=605429")

I get the same issue as you if I attempt to run compiz as well as a 3d game under wine.

---

