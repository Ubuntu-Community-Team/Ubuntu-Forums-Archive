---
title: "Wireless network card drivers problem"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by gnrlove on 2007-02-28
I've recently installed Ubuntu 6.10, and I'm really pleased with it... :)

The only prob I have is that I can't access the internet... I've installed ndiswrapper, and I think I got the driver for my wlancard installed, it at least shows up when I run the command 

```
ndiswrapper -l
```

The thing is that I don't know what to do now... nothing has happened automatically, as I still can't load any pages in firefox... 

Help would be appreciated... :D

---

### Post by Bachstelze on 2007-02-28
If *ndiswrapper -l* says "Driver installed, hardware present", all you need to do is :

```
sudo depmod -a
sudo modprobe ndiswrapper
```

If you get no output but just another prompt, that means all went well. Your interface should appear in *iwconfig* and you can configure it in whichever way you like.

---

### Post by gnrlove on 2007-02-28
When I run ndiswrapper -l, I get the following message:

> Drivers installed:

netwg311         Driver installed


And nothing more... it doesn't mention wether hardware is present... 

hope you can help me.. :D

---

### Post by Bachstelze on 2007-02-28
Are you sure you installed the correct driver for your hardware ?

---

### Post by gnrlove on 2007-02-28
well, the thing is that I don't have them on disc, I had to download them, but they're supposed to be correct... I have a netgear wg311v1, and the drivers were for that card... :)

---

### Post by gnrlove on 2007-03-01
I've tried the commands you said, and I get no output, so everything seems to be working...
I also tried iwconfig and it shows up under wlan0... I don't know what to do now... again, nothing has happened automatically... 
hope you can help me... :)

---

### Post by Bachstelze on 2007-03-01
Then if your interface appears in *iwconfig*, all you need to do is to configure it like any other. I personnally use the command line for this :

```
sudo iwconfig wlan0 essid YOUR_ESSID key YOUR_WEP_KEY
sudo dhclient wlan0
```

---

### Post by gnrlove on 2007-03-01
It worked!!
thanks a lot... you saved my day... :)

---

