---
title: "Turning Off Macbook Keyboard Backlight"
date: 2010-05-30
forum: Apple Hardware Users
---

### Post by Cerin on 2010-05-30
Just upgraded to 10.04. Everything seems to still work on my Macbook, with a bonus being the buttons to modify the keyboard backlight brightness seem to work now.

However, the only caveat is that I can't seem to turn off the backlight. Pressing the dim button all the way to off just seems to reset to full brightness. Even if I set the brightness to 1 (almost off), the backlight seems to reset itself to full brightness at seemingly random times.

Running this command used to turn it off, but now doesn't work:
```
echo 0 | sudo tee -a /sys/class/leds/smc::kbd_backlight/brightness
```

Is this a bug? How do I turn off the keyboard backlight?

---

### Post by linux-hack on 2010-05-31
did you install the ```
sudo apt-get install nvidia-bl-dkms pommed
``` ?
I installed this and you can change the config in the /etc/pommed.conf file
[https://help.ubuntu.com/community/MacBookPro5-3/Lucid](https://help.ubuntu.com/community/MacBookPro5-3/Lucid)

Mine is a macbook pro but may be it will work for you to.

Hope this helps.

---

### Post by Cerin on 2010-06-02
Thanks. Worked perfectly. Glad it was so simple.

---

### Post by erlendoos on 2011-06-14
This works for me only one split second. Almost instantly it switches on again.

i have a macbook pro 6.2

What more tricks are there to manage the backlight status?

---

