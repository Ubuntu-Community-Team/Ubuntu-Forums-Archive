---
title: "A Simple Question From Someone on the Verge of Wireless! Please Help!"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by NavmaN on 2007-07-04
Hi,

I think (or maybe I should say hope) I am on the verge of getting wireless with the WG111v1. I followed the instructions on the Ubuntu Wiki. I'm at the last step where I must actually connect. For some reason, Ubuntu is not detecting wlan0. Here are some outputs:

"lsusb" gives me: Bus 001 Device 002: ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)

note that in reality it is v1 because of its S/N. I was told to go by Netgear's website.

"ndiswrapper -l" gives me: Installed ndis drivers: netwg111      driver present, hardware present

"/etc/iftab/" says at the bottom: wlan0 mac 00:0F:B5:91:56:C4

But when I try to use Network Tools to connect it states that the only device I have is the loopback interface. There is no wlan0.

Thanks,
Van

---

### Post by mig5 on 2007-07-04
Have you restarted since you set it all up?  Try that and maybe it will refresh the network list and give you wlan0

---

### Post by NavmaN on 2007-07-04
I have restarted it multiple times, but I guess I can give it another go.

By the way, thanks for the lightning fast response. It's probably faster than calling your average tech support considering hold times, etc.

Thanks,
Van

---

### Post by NavmaN on 2007-07-04
I restarted it again and no luck.

Van

---

### Post by mig5 on 2007-07-04
Have you tried ```
modprobe ndiswrapper
*or*
modprobe wlan
*or*
modprobe wlan0
```
I think it should be *modprobe ndiswrapper*.

---

### Post by ubuntu.daemon on 2007-07-04
have you tried going to your network settings and seeing whats there??  Or even look under /etc/network/interfaces?? Maybe try another wireless application like wifi radar and see where that gets you

:popcorn:

---

### Post by NavmaN on 2007-07-04
Okay I did all of those modprobe commands. Under /etc/network/interfaces "auto wlan0" along with other interfaces (like ath0 and eth0) are listed. I looked in Network Setting and the only device listed there is a Dial-Up Modem. I then restarted again. It still doesn't work.

Thanks,
Van

---

### Post by lintoon on 2007-07-04
I don't know if it has anything to do with your problem but I had problems getting my wireless to work until I installed knetwork manager.  It was a long time ago though.  Maybe it was the application that enabled me to use WPA encryption, I can't remember now.

It's worth remembering though for when you get it working.

---

