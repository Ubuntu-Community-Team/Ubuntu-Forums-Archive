---
title: "Resolution, Mysql problems"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Ranganaths on 2007-01-27
HI guys,

       With your great support i am getting use to ubuntu now.  Again i need to seek  all your help.  
  1) how to know if the display drivers are installed or not?
  2) how to install the mysql, I use it for every thing like java,jsp,struts,spring,hibernate,swings,python

Thank you
Regards

---

### Post by an.echte.trilingue on 2007-01-27
You open up synaptic (desktop --> administration --> synaptic)  and hit the reload button (while connected to the internet).

Then search for your driver.    If it is not installed, you check the box and hit the apply changes button and synaptic will download and install it for you.

To set it up you video (select new resolutions, select a new driver, etc), run this command from the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

And then reboot.

As for mysql, simply open synaptic, search for mysql, and install the packages you want.

Take care,
-mat

---

### Post by nullmind on 2007-01-27
To check if your display drivers are accelerating properly you should try:

```

glxinfo | grep direct

```

If **Direct Rendering** is enabled you are likely being accelerated. On my i180 graphics adapter (for my laptop) I had to change my display mode to have 16-bit or 32-bit colour; but the default 24-bit colour did not work even though direct rendering reported Yes. I would also try going into the screen savers and trying a few (MatrixView seems to be a good example).

If things aren't accelerated, you'll notice.

---

