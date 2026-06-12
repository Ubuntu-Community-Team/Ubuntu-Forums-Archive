---
title: "ATI x700 fiesty install Prob"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-04-22
I can't install fiesty because my screen splits up into three horizontal screens. They are small screens and it's getting on my nerves. Does anyone else have this prob?

---

### Post by mikeyphi on 2007-04-22
If you haven't already - look here for possible help! [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by XLiquidIceX on 2007-04-22
That's really odd, because I have a x700 and it is installing fine. I hope it finishes installing fine.

---

### Post by Bagboy23 on 2007-04-24
What I mean is the LIveCD loads up fine but during the actual install, i.e. when I get to see the screen to install it, the screen splits into 3 horizontal screens. I have a widescreen laptop. Could this be a prob? HP DV4000.

---

### Post by LauH on 2007-04-24
Mine did the same, it made the desktop in 800x600 and some part of a copy of the desktop under it, and then a black bar to the right, a picture of it here, [http://aycu34.webshots.com/image/14593/2005308190645354550_rs.jpg](http://aycu34.webshots.com/image/14593/2005308190645354550_rs.jpg)
I couldn't choose 1024 i don't know why, and i could not install it, it was my first time using ubuntu, so my exspirience with it pretty much suck. I have now installed 6.10, where there is no graphical problem, and then updated to 7.04, and the same thing happens. I may go M$ Windows again.:(

---

### Post by nsleiman on 2007-04-24
hey dude i have also ATI X700 and had same problem, the trick was reconfiguring the xserver, just hit enter and you will have it. 
this worked fine for me

---

### Post by Bagboy23 on 2007-04-25
LahH that is exactly the same prob I am having. I just can't find any workarounds.

Nsleiman, can you tell us how you re-configured your Xserver? Did you do it in safe Graphics mode?

---

### Post by kittyhawk63 on 2007-04-25
> **LauH said:**
> Mine did the same, it made the desktop in 800x600 and some part of a copy of the desktop under it, and then a black bar to the right, a picture of it here, [http://aycu34.webshots.com/image/14593/2005308190645354550_rs.jpg](http://aycu34.webshots.com/image/14593/2005308190645354550_rs.jpg)
I couldn't choose 1024 i don't know why, and i could not install it, it was my first time using ubuntu, so my exspirience with it pretty much suck. I have now installed 6.10, where there is no graphical problem, and then updated to 7.04, and the same thing happens. I may go M$ Windows again.:(

If you've got Edgy working, stay with it. Why make Gates richer than he already is? Edgy is a good program. Wait until Feisty has made a number of updates fixing the problems that people are reporting. I would wait several months. Then give Feisty another try if you would want it. BTW, the most stable is probably Dapper 6.06 and is LTS, and that is the reason many people use it. People have even been able to get Beryl to work in Dapper, as well as Edgy.

---

### Post by Bagboy23 on 2007-04-26
Part of the fun of Ubuntu is the 6 month development time, and the time we get to try it out. It just adds to the fun if you don't do anything serious on your computer.

Anyway, does anyone else have any more news on this?

---

### Post by nsleiman on 2007-04-27
> **Bagboy23 said:**
> LahH that is exactly the same prob I am having. I just can't find any workarounds.

Nsleiman, can you tell us how you re-configured your Xserver? Did you do it in safe Graphics mode?
sorry for being late :)
the command is:

sudo dpkg-reconfigure xserver-xorg

---

### Post by kittyhawk63 on 2007-04-27
> **nsleiman said:**
> sorry for being late :)
the command is:
sudo dpkg-reconfigure xserver-xorg

nsleiman,
What exactly does reconfiguring your xserver do?
kh

---

### Post by Bagboy23 on 2007-04-28
I tried this, still doesn't work. It's still giving me the split-screen thing.

---

### Post by Bagboy23 on 2007-04-28
Ok guys I got it to work. Basically do this:

1. If your screen is split up so badly that you can't see what you are doing, then run this command first: sudo dpkg-reconfigure xserver-xorg. Then just answer default to everything.

2. Logout and let it log back in. If it's not fixed go to step 3.

3. Then go to the administrative options and choose to enable the restricted drivers (ATI in this case). It'll download some stuff so you need an internet connection. It will ask to reboot, don't reboot, just logout and log back in and it should be fixed. Then you can install as normal.

---

### Post by nsleiman on 2007-04-28
> **Bagboy23 said:**
> Ok guys I got it to work. Basically do this:

1. If your screen is split up so badly that you can't see what you are doing, then run this command first: sudo dpkg-reconfigure xserver-xorg. Then just answer default to everything.

2. Logout and let it log back in. If it's not fixed go to step 3.

3. Then go to the administrative options and choose to enable the restricted drivers (ATI in this case). It'll download some stuff so you need an internet connection. It will ask to reboot, don't reboot, just logout and log back in and it should be fixed. Then you can install as normal.

1 for Bagboy23 :)

---

