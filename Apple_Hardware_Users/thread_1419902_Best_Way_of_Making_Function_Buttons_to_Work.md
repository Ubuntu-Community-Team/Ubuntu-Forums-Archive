---
title: "Best Way of Making Function Buttons to Work"
date: 2010-03-02
forum: Apple Hardware Users
---

### Post by gcndavidmn on 2010-03-02
I'm not sure if function button is the correct term, I meant the screen brightness, volume etc. buttons on a Macbook Pro 5.4

I currently have them "working" using the tutorial here [https://help.ubuntu.com/community/MacBookPro5-5/Karmic](https://help.ubuntu.com/community/MacBookPro5-5/Karmic) I was wondering if this was the most elegant or functional way. I ask this because ubuntu never seems to remember the brightness I have my screen at the last time I shut down.

Regards
Dave

---

### Post by linuxopjemac on 2010-03-02
It will not remember your last setting. I don't know a way how to do it.

---

### Post by gcndavidmn on 2010-03-02
Ah ok. Ill just have to remember to turn it down every time I boot it up.

---

### Post by dennis123123 on 2010-03-03
just add

```
echo 512 >/sys/class/backlight/nvidia_backlight/brightness
```

to /etc/rc.local and it will change every boot. the range on my 5,5 is 0-1023, so I opt for 50% brightness on AC power, which is the value 512.

---

### Post by gcndavidmn on 2010-03-03
```

#!/bin/sh -e
# echo 512 >/sys/class/backlight/nvidia_backlight/brightness
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```

Is that correct?

---

### Post by linuxopjemac on 2010-03-03
```
#!/bin/sh -e
# 
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 512 >/sys/class/backlight/nvidia_backlight/brightness

exit 0
```

I don't have the exit 0 code, but I guess this will work.

---

### Post by gcndavidmn on 2010-03-03
Brilliant thank you. I will fiddle around with the intensity. Thank you.

---

### Post by linuxopjemac on 2010-03-03
Does anyone know how to set the initial backlight level for a MacBook 2,1 (Intel 945) in pommed? If I set it in /etc/pommed.conf, my settings are completely ignored, except the increase/decrease step. That I lowered because I liked more control.

---

