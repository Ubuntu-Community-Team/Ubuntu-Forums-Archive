---
title: "Ubuntu gnome startup problem"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by german st john on 2008-04-16
Hello, my name is german from argentina 
i just bougth a new laptop with Linux ubuntu as the main operation sistem. I have no complains about linux what so ever, but today i left mi my computer updating and my girlfriend restarted in the process whitout canceling the ubuntu update..... when she restart the computer again to acess some files of her, the Gnome dosent work... it post me a message saing that my file home/german>> does not exist. try to run the recovery secion and tell me that the xserver-xorg is not working or not fully install, also tried every thing that would make common sence but still have the same problem. 
Hope someone can gide me in the rigth way to solve this problem as i've got all my personal data inside that computer. thanks hope to hear from sombody soon

---

### Post by terrukallan on 2008-04-16
Assuming you can get to a terminal prompt, try running:
```
sudo apt-get -f upgrade
```
This should hopefully let you complete any upgrades that failed to finish.  If all goes well (and failed upgrades is all that went wrong) restarting once this is done should allow gnome to start properly.

Edit: Sorry, mbadawi23 is correct, it should be "-f" to correct any errors.

---

### Post by spiderbatdad on 2008-04-16
If xserver has failed, run ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mbadawi23 on 2008-04-16
You may also want to try:
```
apt-get -f upgrade
```

so it fixes any broken packages.

---

