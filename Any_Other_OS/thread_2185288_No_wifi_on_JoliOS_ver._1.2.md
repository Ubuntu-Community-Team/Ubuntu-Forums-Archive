---
title: "No wifi on JoliOS ver. 1.2"
date: 2013-11-01
forum: Any Other OS
---

### Post by love4shadow on 2013-11-01
My wired works fine, but my wireless does not. I searched to see if it was blocked, my switch is set to enables. The device also shows up when I put lspci into a terminal. When I click the network icon though, it only shows a wired connection. And the wifi light it orange, meaning it's disabled. It also doesn't show up again when I put ifconfig into a terminal. Just shows Eth0 and Loopback. 

I've tried reinstalling JoliOS but it didn't fix anything. Here's all my information: 

JoliOS ver 1.2 ( No windows installed at all )
HP Pavillion dv6000
WLAN card: Broadcom Corporation BCM4311 802.11b/g WLAN 

I've been working on this for hours .. I hope one of you guys know how to fix this^^

---

### Post by cariboo on 2013-11-02
No an Ubuntu or official flavour question. Moved.

---

### Post by westie457 on 2013-11-07
Hi love4shadow

Assuming that in your attempts to get your wifi working you have installed the recommended driver (bcmwl-kernel-source) and not tried anything else, this is what I suggest you try.

With a ethernet cable plugged in open a terminal and ```
sudo apt-get purge bcmwl-kernel-source
```
Do not reboot because occasionally this removes the wired driver as well.

Now in the terminal ```
sudo apt-get install b43-fwcutter firmware-b43-installer
``` When that has finished ```
sudo modprobe b43
``` should bring the wifi to life. If it works a reboot will make the changes permanent.

If it does not work we shall try something else.

---

