---
title: "Wireless Help"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by kilroy423 on 2007-02-21
When setting up wireless do you have to add everything into /etc/network/interfaces or can i just do this?

```
sudo iwconfig eth1 essid linksys
sudo iwconfig eth1 ap 90-234-242-234243-2
sudo iwconfig eth1 key xxxxxxx
sudo iwconfig eth1 channel 6
```

won't just entering this into the terminal allow for a quick on the fly change over to a network and then when i do a ifdown eth1 and then a ifup eth1 immediately switch back to whatever the default is in the file? one more question is there anyway to allocate the wifi card to use wlan0 or is that more of a pain then it is worth?  Also anyone have a good tutorial on WEP or WPA cause i have been trying to get that to work for a week now with no luck... :(

thx,
dan

---

### Post by charles.g.moore on 2007-02-21
As far as the security issue I used this how-to and it worked for me

[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=WPA](http://www.ubuntuforums.org/showthread.php?t=202834&highlight=WPA)

---

