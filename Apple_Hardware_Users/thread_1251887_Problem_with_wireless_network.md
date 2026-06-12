---
title: "Problem with wireless network"
date: 2009-08-28
forum: Apple Hardware Users
---

### Post by Conspiracy88 on 2009-08-28
Hi everybody im new to Ubuntu and this forum!

I just finished setting up Ubuntu 9.04 on my MacBook 2,1.

Everything is working fine exept the wireless network. Sometimes it work great with no problems but often I can't connect to wireless network. The signal strenght is great but I can't connect. I see the two blue dots in the right upper corner end blue circle around it when it tries to connect. It often takes few minutes until it fails and disconnects.
When I was using Mac OS X 10.4 I had not problem connecting to wireless network.

I was wondering if anybody knows how to fix this problem?8

Thanks,
Conspiracy88

---

### Post by Conspiracy88 on 2009-08-28
Can anyone help me solving this problem?

Its very annoying to spend 10 minutes just trying too connect to the wireless network.

---

### Post by Rog-Mahal on 2009-08-30
Are you trying to connect to a secured network? In my experience with the same Macbook I know that the driver doesn't load correctly from suspend, and I can't connect to encrypted networks until I modprobe the ath9k module. To give that a try, use the following commands:

```
:~$sudo modprobe -r ath9k
```
This will unload the wireless module. Immediately afterwards, you can reload it using:
```
:~$sudo modprobe ath9k
```
Hopefully that will work. It solves the majority of my connectivity problems, and you don't even have to reboot!

---

