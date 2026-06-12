---
title: "eye candy?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by dmichaels on 2006-09-19
hi. im trying to get that eye candy i see everywhere...you know with the cubed desktop and cool wavy windows...trying to pimp out my destop. i looked in the forum elswhere for xgl help but couldnt make sense of it all ](*,) 

i have an nvidia 5700 and have the latest update. i would appreciate any help. also any suggestions on wicked awesome customizations?

---

### Post by bodhi.zazen on 2006-09-19
[XGL and Compiz eyecandy](http://ubuntuforums.org/showthread.php?t=148351)

[How to set up eye candy](http://ubuntuforums.org/showthread.php?t=77694&highlight=eye+candy)

---

### Post by divague on 2006-09-19
Ths guide worked for me [http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351)

---

### Post by dmichaels on 2006-09-19
so yeah followed instructions and reboot my system....now ubuntu wont start and says xserver is not found or gdm needs to be re confifured. ok i dont want to re install everything how do i fix this...im running ubuntu off the cd now

---

### Post by rocknrolf77 on 2006-09-19
boot into the terminal and type 

sudo dpkg-reconfigure xserver-xorg

:)

---

### Post by dmichaels on 2006-09-19
thankyou i will try this now and see how it works out.

---

### Post by Dinerty on 2006-09-19
I used the official guide for xgl/compiz, tried several ones but did not work for me.

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

---

### Post by dmichaels on 2006-09-19
i tried several times to

sudo dpkg-reconfigure xserver-xorg 

and everytime i restart i get the same message 

> FAILED TO START THE XSERVER 

what is the command to get back into ubuntu after u configure the xserver?

---

### Post by UltraMathMan on 2006-09-19
This will start GNOME from the command line:

```
sudo /etc/init.d/gdm start
```

-Hope this helps :)

---

### Post by smartalecks on 2006-09-19
The guide in the forum definetly did not work for me. It turns out that it is slightly outdated :(, because now Compiz uses CSM, not gcompiz or whatever it used to be.

I used this tutorial, and it worked.

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

Only note that when you get to the compiz-start script, I use the one that is described in the "discussion" tab. The one in the tutorial did not work well for me.

---

