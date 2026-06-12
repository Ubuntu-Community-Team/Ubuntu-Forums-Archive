---
title: "can not connect to a netwrok w/ WEP. suggestions?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2007-03-04
i am having issues connecting to my home network. I use wep and i am able to connect to it in windows no prob.

i am able to connect to unsecured networks but can not connect to a wep network at all. i have ran the following command and it does not help.

sudo iwconfig rausb0 essid home key 1234567890.

i have also used the network applet located under admin and network. i have verifed that the info is being added to /etc/network/interfaces.

what else can i try? if i can get this to work i can abandon windoze all together on my laptop.

---

### Post by Songwind on 2007-03-04
Try issuing the same command only with "open" after key.

```
sudo iwconfig rausb0 essid home key **open** 1234567890
```

I had this same issue with a new Netgear adapter that I received.

---

