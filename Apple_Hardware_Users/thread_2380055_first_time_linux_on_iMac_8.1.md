---
title: "first time linux on iMac 8.1"
date: 2017-12-12
forum: Apple Hardware Users
---

### Post by dmitry96 on 2017-12-12
Hello, I Installed Xubuntu 16.04 (64 bit) just yesterday on my Intel core 2 duo iMac 8.1 (2GB RAM). and it is my first time seriously trying Linux. Months ago I tried Ubuntu and it was a miserable experience, many things didn't work it was laggy af, I scrapped it instantly. This time I wanted to try xcfe because I heard it is lightweight and so far it seems to work overall, but I still have a lot of issues. I want something that just werks until I am more familiar with Linux, using the terminal etc. Having to research problems I didn't even know could exist gives me a headache tbh, but whatever. I am going to list some problems I am having and I would really appreciate some help.

problems so far:

>slow wireless connection
Wifi works, but it is really slow and browsing is barely possible. It is possible that I caused it myself. I did the firmware-b43-installer thing for broadcom wifi cards since I thought there weren't any drivers preinstalled, but I have a feeling that the drivers were installed with the updates I did through the software center after I plugged in the ethernet cable. So could the issue be caused by me unnecessarily installing an additional driver? Or got any ideas what could cause the slow connection?

>black screen while booting
Xubuntu boots every time, but it takes a couple minutes to boot and the screen is black while booting, after that it gets to the blue booting screen with the xcfe mouse logo. Could it be the dead drive inside the Mac (see further down for more info) that is causing the long boot time? I hear it trying to spin when it boots.

>overall clunky gui feel and quite laggy
It's hard to describe but the overall feel is off in comparison to macOS, I am unsure if it is just not as refined (surely customizable) or something is broke. What I mean is that the feel when navigating through the browser with the mouse is clunky/unprecise for example. The OS is quite laggy overall too, opening several applications almost freezes it. I can't really describe it tho since I don't know anything about computers yet and all I can say is that it feels really laggy sometimes.

Just so you know, I used a dvd to install Xubuntu, the first reboot after the install didn't work (stuck in black screen, had to press button to shut down, booted after that) and also what should be mentioned is that I'm using an external drive for everything (internal drive died recently, didn't change it yet).

Is it hopeless in my situation? I am getting a thinkpad t400 soon anyways, but like I said I wanted to familiarize myself with Linux first.

---

### Post by DuckHook on 2017-12-12
Welcome to the forums, dmitry96.

Just a few pieces of general advice:

[LIST]
[*]You will increase your chances of getting answers if you split your multiple problems down into individual threads: one thread per problem.
[*]I do not own an iMac, so cannot give you technical advice, but Xubuntu should work well on a computer with your specs.
[*]It is very possible that the system is attempting to access your failed drive and causing long boot times as a result. Can you unplug the internal drive completely? Or disable it in BIOS (repeat: I know nothing about Macs)? You can get some idea of which service is slowing down your boot with:```
systemd-analyze blame
```
[*]Running any OS from an external drive is going to slow things down. Especially if your HW is older, then the USB port is usually 2.x or less, which has poor throughput. You can't fairly compare MacOS running on an internal HDD to anything running from an external drive.
[*]GUIs are matters of personal taste. However, it is probably true that most Linux DEs emphasize substance over style. This is in contrast to many commercial products that emphasize style over substance. The ugliest environment of all might be the command line, but it is also the most powerful by far.
[/LIST]
Detailed help may have to wait for someone more familiar with Apple equipment.

---

