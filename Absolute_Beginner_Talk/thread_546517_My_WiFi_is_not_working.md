---
title: "My WiFi is not working"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by imalumberjak on 2007-09-08
I have a D-Link DWL-G510 Wireless G PCI Adapter, and Ubuntu can detect a few wireless networks, but when I try to connect to my network it looks like it's running for a few minutes and then it prompts me for my password again. Does this mean I have to install the driver (if so, please explain how), or is there another problem?

Any help would be greatly appreciated.

edit: I'm using 7.04 .

---

### Post by chrome307 on 2007-09-09
Why do you feel that you need to enter your login details again?

This is not anything to do with the driver installatiaon - more likely how you configure your access details.

---

### Post by imalumberjak on 2007-09-10
I'm not sure why I would need to. I'm connecting to a WPA network and I'm using the correct password. I can connect when using XP, but it doesn't work when I use Ubuntu.

---

### Post by imalumberjak on 2007-09-15
Sorry to bump this, but that computer is still unable to connect to my WiFi connection. It is, however, able to connect to an unprotected WEP connection, so I don't think it's a problem with the drivers.

 Is it possible that there could be a problem exclusive to WPA connections? I know that this network is functional, since this computer connected to it using Windows before. Again, any help would be greatly appreciated.

---

### Post by Crafty Kisses on 2007-09-16
> **imalumberjak said:**
> I have a D-Link DWL-G510 Wireless G PCI Adapter, and Ubuntu can detect a few wireless networks, but when I try to connect to my network it looks like it's running for a few minutes and then it prompts me for my password again. Does this mean I have to install the driver (if so, please explain how), or is there another problem?

Any help would be greatly appreciated.

edit: I'm using 7.04 .

The bad news is, your probably going to have to use a ndiswrapper, but the good news is after that it should work. :)

```
sudo apt-get install ndiswrapper
```

---

### Post by GuitarRocker2562 on 2007-09-16
How sure are you that it is not asking you to put in a human friendly password for your keyring?

---

### Post by thefoolisme on 2007-09-16
Since it's picking up other networks, you probably don't need to adjust the drivers.  There are actually third party linux drivers for most d-links (usually by Prism), which are usually installed.  I'm working with an older d-link, and never needed to use NDIS wrapper.  What I did notice though is when you input the SSID from the network, in windows it shows up in capital letters.  If you typed it in in caps, delete it, and try typing it in in lower case.  That was my issue.

---

