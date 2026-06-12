---
title: "Update to Feisty, Possible no Wireless?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by reslider on 2007-08-06
So Far I have tried Ubuntu 6.06, 6.10, 7.04. I can't get my wireless to work in 7.04, but it works in both 6.06 and 6.10. I was wondering, If I have my wireless working right now (currently running 6.10) and I do the update to 7.04 will my wireless stop working. Also if it will possibly stop working what is different in feisty that will make it not work.
Thanks Tyler

---

### Post by Ek0nomik on 2007-08-06
What type of wireless card is it?

I will point out that I know your frustration.  It's a shame hardware becomes unsuported with a newer version.  It's something that shouldn't happen as often as it does in my opinion.

If you don't know what kind of card it is, you can run this at the terminal:

```
lspci
```

---

### Post by overdrank on 2007-08-06
> **reslider said:**
> So Far I have tried Ubuntu 6.06, 6.10, 7.04. I can't get my wireless to work in 7.04, but it works in both 6.06 and 6.10. I was wondering, If I have my wireless working right now (currently running 6.10) and I do the update to 7.04 will my wireless stop working. Also if it will possibly stop working what is different in feisty that will make it not work.
Thanks Tyler

Hi there is a good chance that it will stop working. But if you can give us some info on your wireless card we maybe able to help you find a solution.

---

### Post by Sandlst on 2007-08-06
This seems rather odd, could you please post what wireless card you are using?

---

### Post by reslider on 2007-08-06
well its actually a usb adapter.

My wireless adapter is the 2wire 802.11g USB Wireless Adapter
When I type in the command to find out what the usb code is i get this 1630:0005

I use Ndiswrapper or nidskgt to install the driver. In 7.04 I can install the driver but it says that the hardware is not present. Even when I would use the iwlist scan my wireless network would show up but I could not connect, i assumed because it could not detect my hardware, so I just went back to 6.10.

---

### Post by Sandlst on 2007-08-06
Just wondering, are you installing ndiswrapper-utils or ndiswrapper-utils-1.9?  1.9 works for me, whereas the normal one does not!
Also, just want to make sure you know you can test it out on a live-cd instead of reinstalling!

---

### Post by reslider on 2007-08-07
So I installed feisty. I am having the same problems. I tried using ndiswrapper-utils-1.9 and ndisgtk.
When I install through the terminal, it seems as though it is installed

this is what the terminal shows

tyler@ubuntu:~$ ndiswrapper -l
wlanuig : driver installed
             device (1630:0005) present

When I go into Wireless Network Drivers (ndisgtk)  it shows something there, it doesn't have a name, and it states that no hardware is present. When I delete the wlanuig  driver in the terminal and I open it again it is gone, so I believe it is the same driver. 

I remember that for some reason when I was using 6.10 I couldn't get the the driver to work by using the terminal, but for some reason it would work when I would use Wireless Network Drivers. So I installed using Wireless Network Drivers and everything worked fine. When I try to use Wireless Network Drivers in 7.04 my whole computer freezes(can't use the mouse and I tried using ctrl alt backspace and that didn't work either). So I thought maybe if I do a fresh install it might work. Wrong! froze on me again. 

Im not really sure on what to do. Should I just go back to using 6.10?

---

### Post by reslider on 2007-08-07
Any Ideas anyone?

---

