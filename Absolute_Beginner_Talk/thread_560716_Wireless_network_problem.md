---
title: "Wireless network problem"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Gladjaframpf on 2007-09-26
I just installed Ubuntu 7.04 on another computer (not the one I'm using now), and everything seems to be working fine except I can't connect to my wireless network. I have a D-Link DWL-G122 USB wireless adapter, but I can't seem the computer to recognize it.

At first I thought it was just that the drivers weren't installed, so I looked at [this guide](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) for using ndiswrapper, but it seems to assume that the computer has already recognized the hardware. It doesn't show up when I use the *lspci* command, and the light that means it's properly connected to the computer isn't lit.

I have a feeling I'm probably missing some obvious solution here, so hopefully someone will know what it is.

---

### Post by Linux_Man on 2007-09-26
USB network devices have been a problem for many linux distros, Ubuntu is no exception, if NDIS wrapper can't help you might be better off to install an internal Wi-Fi card they usually work better.

---

### Post by Gladjaframpf on 2007-09-27
The think is, I'm fairly certain that I *will* be able to get it to connect with ndiswrapper if I can just get the computer to recognize it. The wireless adapter I have is on the list of ones that should be compatible with Ubuntu.

---

### Post by Linux_Man on 2007-09-27
Is at a USB 2.0 or 1.1, (Just about any computer made in the last 5 years has 2.0) Could it be that its not fully connected? Try a different port, did it work fine in Windows (or whatever OS you had before Ubuntu?)

---

