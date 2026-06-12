---
title: "ATI accelerated graphics driver"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by sonicborg on 2007-05-13
HI all,

i recently had a go at trying to update to the latest ATI drivers, had to try and do it all manually, but i never got any success on this,

So now to get xorg going, i tried to reset everything, but am stuck with MESA drivers in fglrxinfo, and it no longer lists the "ATI accelerated graphics driver in the restricted drivers manager. 
i have followed all the ATI howto's i can find to get this back, but instead all i have is some rubbish about a linmodem (i dont even have a modem since i am on a broadband network) which was not listed there before.
I have redownloaded and updated through apt-get all the resticted modules and fglrx drivers etc. but i dont seem to be able to get it as my xorg driver.

PLease help :)
:confused:

---

### Post by Kobalt on 2007-05-13
Can you please post your xorg.conf file here so we can have a look at it : ```
cat /etc/X11/xorg.conf
```

---

### Post by Thingymebob on 2007-05-13
Envy works well at installing the correct ATI drivers and configuring xorg.conf
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by sonicborg on 2007-05-13
thanks for quick replies, i infact somehow got it working. i re-ran 3-4 commands to do with module-assistant, updates, build etc,

i never had success with envy, did give it ago a few times though.

---

