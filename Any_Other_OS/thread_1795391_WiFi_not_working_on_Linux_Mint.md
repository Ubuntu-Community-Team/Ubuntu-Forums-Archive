---
title: "WiFi not working on Linux Mint"
date: 2011-07-02
forum: Any Other OS
---

### Post by TimmyK. on 2011-07-02
Hi guys, my brother (my other one, not the one who fixes everything with a hammer ;)) just got a Dell D620 like me, but *unlike* me, he installed Linux Mint instead of Ubuntu and his WiFi says he has missing firmware. He has a DW 1490 PCIe Mini card. I know the card is not the problem, as I used it with no problem for months. I Googled "DW 1490 driver", but all that came up were drivers for Windows. What can I do, and why did wireless work on mine but not his?

---

### Post by in-dust-rial on 2011-07-02
thats kinda cool!

so i think the obvious solution is to install ubuntu on his machine too :D

therefore another solution is to compare what ubuntu is doing to what mint is doing.
most likely it is enough to compare the driver used for the card within the two systems.

and if its too hard, contact these guys:
[http://community.linuxmint.com/hardware/view/559](http://community.linuxmint.com/hardware/view/559)
[http://community.linuxmint.com/hardware/view/557](http://community.linuxmint.com/hardware/view/557)
(the second link might be more useful :P)

good luck

p.s.:
so i dont know how old you are or how much you want to learn:
but it says: install the windows drivers via tool for pro.-drivers

---

### Post by TimmyK. on 2011-07-02
Well, I don't know where the driver would be. And how do I contact those guys? And what is this "tool for pro"?

---

### Post by chili555 on 2011-07-02
Do you have an ethernet connection so we can download things if needed? Please open Applications > Accessories > Terminal (is that what Mint has??) and run and post:```
lspci -nn
```Post the line that relates to your wireless card. Thanks.

---

### Post by nm_geo on 2011-07-02
Wow doc you got me again .. Think I will go drink me some mint julips.. LOL

Strange days indeed..

Wifi: Dell Wireless 1490 Dual Band 802.11a/b/g (Broadcom BCM4312 chip)

I found that on Fedora Forum Archive..

I would fire up the Mint - (drink a julip)

In terminal

```
lspci -nn
```Once you have the pci number you have hope.

```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [**[COLOR=Red]14e4:4312[/COLOR]**] (rev 01)
```When you see [0280] you have the wireless the red numbers give you needed information.

---

### Post by nm_geo on 2011-07-02
Both messages above apply ...
Now I also have a D620 here pretty modified but still a Dell D620. I also
have a live/USB of Linux mint forgot which version, but anyway. If you
 see that the pci number 14e4:4312 or 14e4:4311 I would recommend
the Additional Drivers pick B43.  Mint is so much like Ubuntu you can only imagine, they are not as cutting edge in Mint, but some users appreciate that ideology. 

Let us know how it goes .. Hmmm maybe I will install the Mint just for kicks.. I still have 60GB left on my HD.  Good Luck

---

### Post by Perfect Storm on 2011-07-02
Moved to Other OS/Distro Talk.

---

### Post by TimmyK. on 2011-07-06
I don't know that the move was appropriate, since this really is a WiFi issue (unless every discussion relating to anything other than Ubuntu goes here). So here is what the terminal spat out when I typed in lspci -nn.

---

### Post by knnyzhu on 2011-07-06
Hey I got the same problem when I installed Linux Mint the first time, as well as on ubuntu. The trick is to plug your laptop with an ethernet cable with an internet connection and then proceed to update everything in your software manager (click everything). You should then be able to use wifi after a reboot, if I recall! Hope that helps.

---

### Post by chili555 on 2011-07-06
This device, 14E4:4312, uses the driver b43 and Broadcom's proprietary firmware. In Ubuntu, we'd hook up an ethernet cable and do:```
sudo apt-get install b43-fwcutter
```After the firmware was downloaded, extracted and installed, we'd detach the ethernet connection and reboot.

I don't know much about Mint.

---

### Post by TimmyK. on 2011-07-07
I tried the terminal command and rebooted, but that did not work. AS for the software manager thing, I saw no update thing anywhere. Did you mean the package manager?

---

### Post by chili555 on 2011-07-07
May we see:```
dmesg | grep b43
```Thanks.

---

### Post by TimmyK. on 2011-07-07
Here it is.

---

### Post by chili555 on 2011-07-07
You are still missing firmware. Did you have an internet connection when you ran the command? Please do so and try this:```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Reboot and tell us how it's working.

---

### Post by TimmyK. on 2011-07-07
Thank you guys! He never would have had WiFi without you.

---

