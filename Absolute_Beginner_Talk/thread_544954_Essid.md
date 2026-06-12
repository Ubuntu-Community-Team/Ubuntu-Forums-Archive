---
title: "Essid?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-09-06
[http://ubuntuforums.org/showthread.php?t=529090](http://ubuntuforums.org/showthread.php?t=529090)

What should the 3rd line of this script say? He says "YOUR_ESSID_NAME_SHOWN ABOVE" I don't see anything that has anything to do with a ESSID name. Do you what this guy is talking about?

---

### Post by BrendanM on 2007-09-06
When you enter the command "iwlist scan" it will scan for any wireless networks within range and list information about them. You'll then need to use the ESSID for the wireless network you want to connect to in the following commands. 

Hope that helps.

---

### Post by RomeReactor on 2007-09-06
Hi. That refers to the output of running the command **sudo iwlist wlan0 scan** that was above. Run that command and look for **Essid: XXXXXXX**, where XXXXXXX will be the name of the router you want to connect to.

---

### Post by swoll1980 on 2007-09-06
I can't even get fiesty to recognize my adapter, I thought this was part of the process to get it to recognize it. So this script is for after my adapter is recognized. Correct?

---

### Post by BrendanM on 2007-09-06
Correct. To try to recognize the adapter, you're going to need to try something like **lspci** which will list all the devices connected. Then you'll have to find the right driver and load that module with something line **modprobe**. Other people probably have better specifics on how to do that though.

---

### Post by swoll1980 on 2007-09-07
it's usb will that command work for usb?

---

### Post by BrendanM on 2007-09-07
You might need to use **lsusb** for USB devices. I'm not entirely sure.

---

### Post by hyper_ch on 2007-09-07
yes, it's lsusb :) (list usb devices)

lspci (list pci devices)

---

