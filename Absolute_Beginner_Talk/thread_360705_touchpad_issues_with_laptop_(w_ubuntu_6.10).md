---
title: "touchpad issues with laptop (w/ ubuntu 6.10)"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by alwiap on 2007-02-13
I had XP pro previously installed on this laptop and I guess the drivers for it were different or something.  When I was running XP I couldn't tap twice on the pad to open anything up.  I liked that.  Now going to Ubuntu, I keep dragging stuff around the place because with Ubuntu it will double click anything if I double tap.  I was just wondering if it was possible to change the driver or something so it wouldn't double tap to double click.  If i am being unclear I apologize, it's kind of a weird thing. 

thanks ~

---

### Post by wh0rd on 2007-02-14
Try installing gsynaptics. 

```
sudo apt-get install gsynaptics
```

It's a GUI that will let you adjust the touchpad.

---

### Post by Bachstelze on 2007-02-14
You'll also need to configure your X server to correctly use the touchpad :

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by alwiap on 2007-02-15
ok thanks, just getting back to the laptop now and will investigate 

:]

---

### Post by alwiap on 2007-02-15
how do i run synaptics? sorry for the noob question i'm a complete beginner.

---

### Post by alwiap on 2007-02-15
i found synaptics but when i click on it in system ---> preferences ---> touchpad, it displays the following message:

GSynaptics couldn't initialize.
You should have to set 'SHMConfig' 'true' in xorg.conf of XF86Config to use Synaptics

I am opening xorg.conf and seeing if I can set it to true atm.

---

### Post by SnowPunk98 on 2007-02-15
open the config file by doing

```
sudo gedit /etc/X11/xorg.conf
```

Under the Section "Input Device" for the synaptic touchpad put the following

 ```
Option         "SHMconfig" "true"
```

Restart X, you can do CTRL+ALT+BACKSPACE

---

