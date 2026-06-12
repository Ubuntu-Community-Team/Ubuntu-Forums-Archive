---
title: "Hardware Driver Updates"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by aaron_summer on 2007-05-16
Good Day,

I must say I am very impressed with the manner in which my questions are being answered. So much so that I have one more.

I recently bought a budget PC to act as a file / print / LAMP server. 

Here are the specs:
Intel Dual Core 3.0Ghz
1 GB RAM
80 GB HDD
S3 Unichrome Integrated Video
Integrated VIA Gigabit Ethernet Adapter
VIA Integrated RAID 0,1,JBOD Controller

Ok, my question is related to the hardware drivers.

My video is incredibly slow in KDE and I want to know if installing the vendor Linux drivers will correct the performance issue.

Or am I better to just suffer the slow video performance and leave at the default drivers in place?

---

### Post by Happy_Man on 2007-05-16
What video? Like, in Kaffeine? Or do you mean YouTube?

---

### Post by starcraft.man on 2007-05-16
Uh, in almost all cases its advisable to install your video card drivers... I know nothing about S3 though... if they give you drivers install them, I don't see how it could hurt. If you get shunted back to the console for some reason, just log in and run the following command and pick the "vesa" driver when you get to your card.

```
sudo dpkg-reconfigure xserver-xorg
```

That should be it, best of luck to you :).

Edit: happy, I think hes referring to overall sluggishness in moving things around like windows in the GUI. I could be wrong though >.>.

---

### Post by aaron_summer on 2007-05-16
> **Happy_Man said:**
> What video? Like, in Kaffeine? Or do you mean YouTube?

The 3D acceleration appears to be very slow when viewing the OpenGL screensavers or Tux cart etc.

Sorry I hope that helps.

---

### Post by aaron_summer on 2007-05-16
> **starcraft.man said:**
> Uh, in almost all cases its advisable to install your video card drivers... I know nothing about S3 though... if they give you drivers install them, I don't see how it could hurt. If you get shunted back to the console for some reason, just log in and run the following command and pick the "vesa" driver when you get to your card.

```
sudo dpkg-reconfigure xserver-xorg
```

That should be it, best of luck to you :).

Edit: happy, I think hes referring to overall sluggishness in moving things around like windows in the GUI. I could be wrong though >.>.

After I install the drivers, will X automatically detect my card? Or will I need to make some type of change to take advantage of the driver?

Thanks

---

### Post by aaron_summer on 2007-05-16
> **aaron_summer said:**
> After I install the drivers, will X automatically detect my card? Or will I need to make some type of change to take advantage of the driver?

Thanks

Oops forgot the link of the motherboard [http://ca.asus.com/products.aspx?l1=3&l2=11&l3=310&l4=0&model=1575&modelmenu=2](http://ca.asus.com/products.aspx?l1=3&l2=11&l3=310&l4=0&model=1575&modelmenu=2)

ASUS has the video, lan, & raid drivers.

---

### Post by starcraft.man on 2007-05-16
> **aaron_summer said:**
> After I install the drivers, will X automatically detect my card? Or will I need to make some type of change to take advantage of the driver?

Thanks

Ok if its with 3d stuff your having trouble, then installing drivers definitely will fix it. As for will x automatically detect your card, i suppose it depends on the installer. Ubuntu likely has already detected your card and set it in your xorg, the only thing you might have to do is change the drivers manually but I don't know anything about S3 so you will probably just have to try and see how it goes. If you get to a screen your not sure about, screenshot(printscreen) it and post here and we can tell ya what to do likely >.>.

---

### Post by Happy_Man on 2007-05-16
After you install your drivers, hit ctrl+alt+backspace. That will take you back to the login screen, yes it's normal. Go ahead, login, and see if your screensavers and such run faster. If not, run that command starcraft mentioned and when you get to the driver select screen, look for your driver and use spacebar to choose it. Then log out and log back in. Hopefully, one of these two solutions will work.

---

### Post by aaron_summer on 2007-05-16
> **Happy_Man said:**
> After you install your drivers, hit ctrl+alt+backspace. That will take you back to the login screen, yes it's normal. Go ahead, login, and see if your screensavers and such run faster. If not, run that command starcraft mentioned and when you get to the driver select screen, look for your driver and use spacebar to choose it. Then log out and log back in. Hopefully, one of these two solutions will work.


Should I install the video drivers through KDE or before I login?

Thanks again for your help

---

### Post by Happy_Man on 2007-05-16
Through KDE.

---

### Post by aaron_summer on 2007-05-16
Will do.

I will update you on the progress. Thanks for all your help.

---

