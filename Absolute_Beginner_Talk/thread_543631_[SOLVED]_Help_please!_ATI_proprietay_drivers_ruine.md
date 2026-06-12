---
title: "[SOLVED] Help please! ATI proprietay drivers ruined my X-server!!!"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by msangil on 2007-09-05
Dear friends,

I am in a bit of a problem here. I just finished installing the proprietary drivers from ATI to be able to use composite and to make use of the 3d acceleration. As you might guess It turned out a complete disaster.

I restarted to test the new drivers (perspiration ran through my forehead) and I couldn't start the X-server... (my fears came true. I was in deep trouble).

I performed that little trick most ATI users are obliged to use... hoping It might save me again... Nothing!

editing /etc/X11/xorg.conf      :( this file no longer exists - I ran the live cd and checked
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial           says there is nothing to configure
etc.

Could someone provide me with a set of commands to go back to the xorg drivers?
It was a pain to install the ATI proprietary drivers, and I don't think I will ever try it again *EVER*.

Thank you all for your help! :KS

---

### Post by Hobo Joe on 2007-09-05
You need to use Envy to install those drivers.

First, you need to get back to the GUI, to do so, follow this command:
```

sudo dpkg-reconfigure xserver-xorg

```
When it's on the the part about drivers, select 'vesa', and leave everthing else how it is.

Reboot into the GUI, and install Envy, there is a link in my sig. When you install the drivers, make sure to let Envy configure X for you.

---

### Post by msangil on 2007-09-05
Thank you for your reply Joe.

I just tried your suggestion and it says it doesn't find xserver-xorg
This seems worse than I imagined... any alternative ways to solve this?

Thanks again 

PS: should I start making the backups by now?

---

### Post by Hobo Joe on 2007-09-05
Oh my, it is worse then I thought.

You will probably have to reinstall, unless someone else has a fix for that. But when you do, install Envy first thing and get your drivers working.

A *possible* alternative is installing Envy from text based mode, but I have no idea how things will work if you are missing xserver-xorg.

---

### Post by Zootropo on 2007-09-05
Try to reinstall it:
sudo aptitude reinstall xserver-xorg

---

### Post by msangil on 2007-09-05
I deserve this for messing around with things I don't yet understand. :) LOL

I'll install Envy as soon as I get the Xserver runing again. Don't worry. Thanks for your advice Joe!

---

### Post by msangil on 2007-09-05
Thank you Zootropo, but I couldn't stantd myself and I already started re-formating and installing Feisty. I think it might be the healthiest solution since -otherwise- there might be some loose ends remaining.

I am learning the hard way. :KS

---

