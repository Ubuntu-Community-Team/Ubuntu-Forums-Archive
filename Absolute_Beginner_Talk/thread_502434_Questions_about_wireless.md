---
title: "Questions about wireless"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-07-16
OK I have an intel wireless card. Here is the proof, from "sudo lshw":
```
   *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                driver=ipw2200 driverversion=1.2.0k

```

I have a lot of problems with it working under Ubuntu.

I read somewhere about someone switching to ipw2100 driver. But I am not sure if he had the same card as me. I only know that it was intel.

Should I switch?

If yes, how would I go about it?

Thanks a lot.

---

### Post by Fitzy_oz on 2007-07-16
> **Majorix said:**
> OK I have an intel wireless card. Here is the proof, from "sudo lshw":
```
   *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                driver=ipw2200 driverversion=1.2.0k

```

I have a lot of problems with it working under Ubuntu.

I read somewhere about someone switching to ipw2100 driver. But I am not sure if he had the same card as me. I only know that it was intel.

Should I switch?

If yes, how would I go about it?

Thanks a lot.

Not Necessarily.  Linux as a rule generally enjoys good driver support from Intel, If you could be a little more specific as to what problems you are having, We might be ablet o give you a hand, the beauty of these foums is no matter what you've gone through it's a safe bet that someone has gone through it as well or something very similar.

Have you tried the NDISWRAPPER, this nifty little piece of software allows to you to use you're windows drivers to run you're wireless hardware (I have  a Belkin wireless card with which I had to use this otion due to the lack of native driver support), it works like a charm and is very easy to setup.

---

### Post by Majorix on 2007-07-17
OK I installed NDISWRAPPER and the gui tool for it. Then I found the drivers for my wireless and installed them. But it didn't show that they were installed. I thought maybe it was installed anyway, so I restarted. But when I was back and tried to run that gui tool again, it crashed, complaining about some NoneType having no property called something.

Is there a way to run NDISWRAPPER without having to launch a gui tool? Or is there something completely different that comes up to your mind?

Thanks a lot.

---

### Post by vbabiy on 2007-07-17
> **Majorix said:**
> OK I installed NDISWRAPPER and the gui tool for it. Then I found the drivers for my wireless and installed them. But it didn't show that they were installed. I thought maybe it was installed anyway, so I restarted. But when I was back and tried to run that gui tool again, it crashed, complaining about some NoneType having no property called something.

Is there a way to run NDISWRAPPER without having to launch a gui tool? Or is there something completely different that comes up to your mind?

Thanks a lot.

You can also ways use ndiswrapper in the terminal, also the original driver will have to be blacklisted. But first you should let us know how the wireless is  not working..

---

### Post by Majorix on 2007-07-17
Wireless sometimes works sometimes doesn't. Thats all I know about it.

Sometimes when I boot the pc up, it would go and connect to wireless. Sometimes it doesn't, then I have to use the wired connection.

Q: How do you blacklist the driver the computer is currently using?

Q: Where can I find the correct drivers for Intel 2200BG Wireless Card that will work under NDisWrapper? I looked but the download link didn't work so I am in desperate need.

---

### Post by Majorix on 2007-07-17
Any one? Where can I find the driver? Please help.

---

### Post by Fitzy_oz on 2007-07-17
> **Majorix said:**
> Any one? Where can I find the driver? Please help.

Seems as you have already installed the ndiswrapper, I think you should just blacklist the default driver - 

Drop to a terminal and type gksudo gedit /etc/modprobe.d/blacklist

add the following line to it somewhere near the bottom
blacklist ipw2200
blacklist ipw2100

save the file and then reboot, after the reboot the device should be using you're windows drivers and you should be able to use the network manager on the taskbar to connect to the wireless network

---

### Post by Majorix on 2007-07-18
The problem is that ndiswrapper has no drivers of its own to work with. Disabling the current drivers would leave me without a connection, no?

Thanks a lot.

---

### Post by Fitzy_oz on 2007-07-18
> **Majorix said:**
> The problem is that ndiswrapper has no drivers of its own to work with. Disabling the current drivers would leave me without a connection, no?

Thanks a lot.

My apologies i thought you'd already installed the drivers, you just need to jump on the Intel site and download the windows xp or windows 98 drivers for that card, ndiswrapper will then ask you for the inf file.
\

---

### Post by Majorix on 2007-07-19
I did exactly so, but when I installed it, the driver didn't associate itself with the network card. I don't know why :confused:

Thanks.

---

### Post by Fitzy_oz on 2007-07-19
> **Majorix said:**
> I did exactly so, but when I installed it, the driver didn't associate itself with the network card. I don't know why :confused:

Thanks.

It won't because the native drivers are still running and have control of the hardware, once they are blacklisted you should be fine.

---

### Post by Majorix on 2007-07-20
Ok thanks I will try that and let you know :)

EDIT: Nope, still the same problem.

---

