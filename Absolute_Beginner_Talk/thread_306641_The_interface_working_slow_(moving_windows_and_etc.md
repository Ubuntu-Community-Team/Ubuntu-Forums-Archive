---
title: "The interface working slow (moving windows and etc)"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by tiptip on 2006-11-25
hello,

* I'm a newbie to linux & ubuntu and still fighting to set everything up. ](*,) 

At first the the max resolution i could choose was 1024x768 ,and ofc i wanted to use the recommended resolution of my screen (1280x1024) , at the /etc/X11/xorg.conf file they wrote to run :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
for setting it and it worked , i can use 1280x1024 now but every action is kinna slow :/ moving windows, scrolling and etc are soooo sllooooow .

How can i fix it ? in win xp everything works very fast at  that resolution.

my computer :
p4c 2.4Ghz
asus p4p800d
geil 2x256mb
GF4 Ti4200 64mb

---

### Post by taurus on 2006-11-25
Sounds to me like you need to install a driver for your graphic card!!!  

[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

p.s.  You still need to install a driver for your graphic card even when you use XP so don't tell me that it just works!!!  That's why you get the CD-ROM with the driver on it when you purchase the graphic card/monitor...

---

### Post by tiptip on 2006-11-25
thx 
worked like a charm

but now my refresh rate is 75hz and the recommended for my screen is 60hz
how i can fix it ? 
it doesnt let me change in the "Screen Resolution"

---

### Post by taurus on 2006-11-25
You can edit your /etc/X11/xorg.conf.  

Applications -> Accessories -> Terminal:
```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by tiptip on 2006-11-25
thx again for the quick answer

but when i look in the file i see :
```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection
```
how my screen show 75hz after all ?

---

### Post by taurus on 2006-11-25
Are those the right refreshing rates for your monitor?  What about the rest of it?

---

### Post by tiptip on 2006-11-25
My monitor refresh rates are :

Horizontal Refresh Rate	30 to 83 kHz
Vertical Refresh Rate	56 to 76 Hz
(HP L1906)

While the recommended is 60hz.
Shouldnt i work at the recommended rates ?

---

### Post by taurus on 2006-11-25
> **tiptip said:**
> My monitor refresh rates are :

Horizontal Refresh Rate	30 to 83 kHz
Vertical Refresh Rate	56 to 76 Hz
(HP L1906)

While the recommended is 60hz.
Shouldnt i work at the recommended rates ?
Please replace the values in /etc/X11/xorg.conf with the actual values for your monitor, from above!  

```

Section "Monitor"
    Identifier     "HP L1906"
    HorizSync       30 - 83
    VertRefresh     56 - 76
    Option         "DPMS"
EndSection

```

---

### Post by tiptip on 2006-11-25
I couldnt load ubuntu in windows mode when the line 
```
Identifier     "HP L1906"
```
was in /etc/X11/xorg.conf, the system reported on an error and i could use only command line mode.
but i could change the HorizSync, VertRefresh.
```
    HorizSync       30 - 83
VertRefresh     56 - 76
```
the current setting is still 75hz :/

---

### Post by taurus on 2006-11-25
Actually, just change it back to "Generic Monitor" because it has to match with "Monitor" section later on...

---

### Post by tiptip on 2006-11-25
i did, but i still cannot change it to 60hz
with the 
```
HorizSync       30 - 83
VertRefresh     56 - 76
```
setting ofc or any other settings.

---

### Post by taurus on 2006-11-25
If it's running at 75Hz and everything is working fine, I would just leave it alone...

---

### Post by tiptip on 2006-11-25
ok :D
thx for the help, boss

---

### Post by 23meg on 2006-11-25
[http://www.ubuntuforums.org/showpost.php?p=1114025&postcount=31](http://www.ubuntuforums.org/showpost.php?p=1114025&postcount=31)

---

