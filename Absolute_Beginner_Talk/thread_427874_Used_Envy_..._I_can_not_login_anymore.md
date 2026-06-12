---
title: "Used Envy ... I can not login anymore"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Kuoi on 2007-04-29
I had an issue that my computer wont poweroff.

I did searched the forum much and somebody mentioned Envy to install the Nvidia driver  because it seems that is the problem<

I did uninstalled the Nvidia driver and installed it using Envy <

Since then I can not login anymore<

I had  backup files of xorg.conf but these where both overwritten by envy it seems<

I did a dpkg-reconfigure xserver-xorg too but that did not work either<

There is an error about the x-server <

Can somebody help me Kuoi

BTW . it is not easy typing from the live cd  with a Belgian keyboard

---

### Post by earobinson on 2007-04-29
you should be able to press ctrl alt f1 at the log in screen to put you into text mode. from there you should be able to reinstall nvidia

ctrl alt f7 will bring you back to gui mode

---

### Post by zetsumei on 2007-04-29
Envy shouldn't have messed with your xorg.conf.backup or did it make one itself?  Before I used envy I created my own backup of xorg.conf and it's a good thing I did b/c X crashed.  When you get to the X server failed to start just get out of that and it should put you a black screen.  From there hit alt+f1 or something (i forgot which key combo) and it'll ask for your login and password.  Just loging and do your reconfigure, backup, etc...

Hope this helps unless I misunderstood your question.

---

### Post by starcraft.man on 2007-04-29
Ummm, when you reconfigure Xserver, you can't switch it back to the 2D "nv" driver?

If you can't swap in the 2d driver, you might have corrupted more files than just the driver for graphics >.<.

Do you have anything important needing to be saved? Maybe you should just reinstall 7.04.

EDIT: Btw, have you tried just using 

```
sudo cp /location/of/backup /etc/X11/xorg.conf
```

it shouldn't have been deleted whatever you did.

---

### Post by Kuoi on 2007-04-29
Thank you all , I'm logged in again .

Did ctrl alt f1 , ... then typed envy -t , wich was the only option I had to work with Envy.
I've used "Install Nvidia driver manually"
After it was installed , it asked me to configure Xserver automatic , I did not , and configured myself.
Don't ask me what I configured , but I have the feeling everything works a bit quicker.

Thank you all for the quick answers , Kuoi

---

### Post by starcraft.man on 2007-04-29
> **Kuoi said:**
> Thank you all , I'm logged in again .

Did ctrl alt f1 , ... then typed envy -t , wich was the only option I had to work with Envy.
I've used "Install Nvidia driver manually"
After it was installed , it asked me to configure Xserver automatic , I did not , and configured myself.
Don't ask me what I configured , but I have the feeling everything works a bit quicker.

Thank you all for the quick answers , Kuoi

Your welcome, be careful and be sure to back up your files now... if you find any more instabilities it might be worth a clean install.

Good luck.

---

