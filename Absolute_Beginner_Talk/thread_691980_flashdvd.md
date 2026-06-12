---
title: "flash/dvd"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by wobbiebobbie on 2008-02-09
HI yaw First I like to say great job on everything  here.   I love  ( ubuntu 7.10)  just one thing Im still haveing trouble doing, the flash player and DVD I have done everything I know to do and read I think all the threads. I really want to make this thing work, here is my specks Dell dimension 8200 2.60. 256mb  of ram, nvida Geforce fx 5500 with 256mb of ddr on the card. The install went great and I am real happy with everything but I just cant get the flash working good I do know when I turned off the desktop graphic flash work better. ( Im new to this ) thanks

---

### Post by spiderbatdad on 2008-02-09
so your total ram is 512? that would be enough to run 7.10 effectively, 256 would not. 
this is a pretty comprehensive guide for basic media.[http://ubuntuforums.org/showthread.php?t=664242](http://ubuntuforums.org/showthread.php?t=664242)

---

### Post by cybertron3000 on 2008-02-09
For good playback on dvd's, trying searching for "Quickstart 6.0" that someone has made for Ubuntu in the forums.  Also, the flash can be downloaded from the adobe site for linux (ubuntu too) systems.  I didn't get it to work at first, but I realized I had to meticulously follow the instructions (download it to desktop, then next step, etc.)

Hope this helps.

---

### Post by euler_fan on 2008-02-09
[Gusty Startup Programs]("http://ubuntuforums.org/showthread.php?t=619226")

Turning even a few of these off will save you lots of RAM usage. May help if that's an issue in your case.

---

### Post by cybertron3000 on 2008-02-09
[http://ubuntuforums.org/showthread.php?p=3774207#post3774207](http://ubuntuforums.org/showthread.php?p=3774207#post3774207)

this should take you to the thread about installing "quickstart 6.0" for your issues, that I mentioned.

---

### Post by jan quark on 2008-02-09
for installing flash you can use this code
```

sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

