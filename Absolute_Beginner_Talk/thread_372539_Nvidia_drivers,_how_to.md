---
title: "Nvidia drivers, how to"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by MurphysLaww on 2007-02-28
**RESOLVED**

I read a few of the nvidia how to's but can't seem to make heads or tails of them. I downloaded the proprietary nvidia driver but cant figure out how to install it, or should I use the Ubuntu nvidia drivers, which I also don't know how to install

the system specs are:

shuttle XPC 41G(has on board video, but I have it disabled in bios)
AMD xp2000
1GB mushkin 2100 Ram
64mb nvidia mx440 agp 8 vid card
40gb western dig harddrive


Thanks for any help.

---

### Post by Maestro23 on 2007-02-28
Having trouble, try using the Envy script.

Envy: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

---

### Post by MurphysLaww on 2007-02-28
everything was looking good, when I was running envy, but then at the end it said Installation failed and now my xwindows is hosed. I am guessing the attempt to install the most recent driver killed the old one.


any help?

---

### Post by arochester on 2007-02-28
Where are you now? Is your Xserver working?

---

### Post by Maestro23 on 2007-02-28
> **MurphysLaww said:**
> everything was looking good, when I was running envy, but then at the end it said Installation failed and now my xwindows is hosed. I am guessing the attempt to install the most recent driver killed the old one.


any help?

Just as with Windows, it is best to uninstall the old driver before installing the new.  You can reconfigure X to get back to the basic driver.

> dpkg-reconfigure xserver-xorg

After you do this, either using the How-To or trying the Envy script again, install your driver.

Good luck.

---

### Post by MurphysLaww on 2007-02-28
I am wondering if there was envy already installed with 6.10? probably I should have run the two lines to purge an existing instance of envy?

---

### Post by bodhi.zazen on 2007-02-28
First the envy script works well with the generic kernel ...

Second, what is the error message when teh envy script fails ???

---

### Post by MurphysLaww on 2007-02-28
Thanks for the help, looks like I was able to back it out and remove the prev instance of envy and reinstall. 

All is good in noob linux land. :)

---

### Post by Maestro23 on 2007-02-28
Good deal man, glad we could help you.  And thanks for marking the post "Resolved".:)

---

### Post by masteryurez on 2007-02-28
> **MurphysLaww said:**
> **RESOLVED**

I read a few of the nvidia how to's but can't seem to make heads or tails of them. I downloaded the proprietary nvidia driver but cant figure out how to install it, or should I use the Ubuntu nvidia drivers, which I also don't know how to install

the system specs are:

shuttle XPC 41G(has on board video, but I have it disabled in bios)
AMD xp2000
1GB mushkin 2100 Ram
64mb nvidia mx440 agp 8 vid card
40gb western dig harddrive


Thanks for any help.

This can solve your problem.. (nVidia driver)
```
sudo apt-get install nvidia-glx nvidia-glx-dev
```

---------------------

Another way to install the correct nVidia driver is to do this guide.. (works for me very well)

1. Get a program called Automatix. You can find it here [http://www.getautomatix.com](http://www.getautomatix.com) and goto the installation tab. 
If you have "Edgy" just follow the installationguide for "Edgy" and if you have "Dapper" just follow the "Dapper"-installationguide.

2. When you have installed Automatix you can goto "Application > System Tools > Automatix and start the program. 

3. Go to Graphic Card i Automatix. You will no see Nvidia Driver. This will automatically install the nVidia Driver for you.. 
This might not be the best way to install the driver but this works for the most users.

4. Install the driver and restart X server. You can simply restart you X server with just 3 keys; ctrl+alt+backspace, but remember to close all programs first :)

5. Log in again and test your new nVidia-driver. If you want to test your driver start a new terminal (Console in KDE) and write
```
glxgears
```
This will start an animation with some gears. If the gears is spinning around fluid your nVidia driver are successfully installed. 

-------------------

I hope this guide will work all nVidia User very well.

Have a nice day :)

---

