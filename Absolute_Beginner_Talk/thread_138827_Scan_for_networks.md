---
title: "Scan for networks"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by reldruH on 2006-03-02
I just installed Ubuntu for the first time and and I'm trying to get my wireless card working. I've gotten ndiswrapper working just fine, recognizes my driver and card, but when I put in my network infromation to try and actually connect, Ubuntu just smiles at me and does nothing. So my question is: Is there any way to scan for available networks so I can make sure that I'm using the right one? I'm almost sure I am, but I'd like to be able to scan and see what's available. I know that there are quite a few networks in range of my computer; I'd like to be able to see them all.

Thanks in advance,
reldruH

---

### Post by dickohead on 2006-03-02
done this?
sudo ifdown wlan0
sudo ifup wlan0

I need to do that everytime I start, you also need to open up the networking gui and configure the wireless connection to use the SSID of your network, it may find it automatically not sure.

---

### Post by reldruH on 2006-03-02
[QUOTE=dickohead]done this?
sudo ifdown wlan0
sudo ifup wlan0

I need to do that everytime I start, you also need to open up the networking gui and configure the wireless connection to use the SSID of your network, it may find it automatically not sure.[/QUOTE]

I've tried doing those, and sudo ifdown wlan0 goes just fine, but sudo ifup wlan0 gives me an error message. I think I have it set to right SSID, but that's why I want it to scan for me, so that I can see the SSID's of all the available networks.

---

### Post by reldruH on 2006-03-05
If you were curious, I found the answer. To scan for networks you have to use ```
sudo iwlist scan
```
That will give you a ton of information about every wireless network you can pick up. Now that I've got my adapter working, I just have to figure out how to make it execute what it needs to on startup so I don't have to do it everytime.

Thanks for your help :-)

---

### Post by patrick295767 on 2006-03-05
would you mean : xsmbrowser ?

Greetz

---

