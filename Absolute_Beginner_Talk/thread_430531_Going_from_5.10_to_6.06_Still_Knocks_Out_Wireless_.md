---
title: "Going from 5.10 to 6.06 Still Knocks Out Wireless Connection"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by IronMac on 2007-05-02
Hi all, I tried once again to update going from 5.10 to 6.06 and am still encountering this problem where the system seems (from what I can tell) to recognize that I have the wireless card (an old 3COM XJack which worked fantastically well under 5.10) but I can't seem to connect out.

Any suggestions would be greatly appreciated. Thanks!

---

### Post by urukrama on 2007-05-02
You could try a clean install of Feisty (7.04), Ubuntu's latest release. The wireless support has improved a lot.

---

### Post by IronMac on 2007-05-02
I don't want to do that (long story) but I don't understand why 5.10 was excellent with wireless (better than XP!) and 6.06 breaks it?

---

### Post by chili555 on 2007-05-02
I believe this is actually an Atheros chipset which is supported if you install linux-restricted-modules. If you have already done that and your wireless won't connect, please let us see *iwconfig* and *sudo iwlist ath0 scan*. Thanks.

---

### Post by IronMac on 2007-05-02
> **chili555 said:**
> I believe this is actually an Atheros chipset which is supported if you install linux-restricted-modules. If you have already done that and your wireless won't connect, please let us see *iwconfig* and *sudo iwlist ath0 scan*. Thanks.

Ok...that went well over my head! LOL!

First, I don't know what you mean by "install linux-restricted-modules". It simply worked under 5.10.
Second, I would do the iwconfig and sudo iwlist ath0 scan but how? :confused:

---

### Post by chili555 on 2007-05-02
Please go to Applications -> Accessories -> Terminal. In the terminal, type ```
iwconfig
```Press 'Enter' Post the result here. Type, in the same terminal, ```
sudo iwlist ath0 scan
```Press 'Enter' Please post the result here. Thanks.

---

### Post by IronMac on 2007-05-03
Thank you for the instructions! Ok, here is what I get after iwconfig, please bear with me, I have to type this all out by hand from another computer.

lo     no wireless extensions.

irda0 no wireless extensions.

eth0 whole bunch of stuff here specific to the card and network

sit0 no wireless extensions.

And, after typing in sudo iwlist ath0 scan, I get:

ath0  interface doesn't support scanning.


Does the above help? Thanks!

---

### Post by IronMac on 2007-05-03
Just a quick little bump.   :)

---

### Post by IronMac on 2007-05-05
Another bump.  :)

---

### Post by IronMac on 2007-05-06
No one knows?  :(

---

### Post by IronMac on 2007-05-07
Patiently bumping...

---

### Post by chili555 on 2007-05-07
I think we need to be sure linux-restricted-modules is installed or install it if it's not. Open a terminal and do:```
 dpkg -l | grep linux-restricted
``` That vertical line is the 'pipe' symbol; it's over on the right on your keyboard above \.

If you see linux-restricted-modules listed, then it's installed. If not, we can install it from your install CD. In the terminal, do:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install linux-restricted-modules
```Now, your wireless interface should appear, but let's give it a kick in the pants first:```
sudo ifconfig ath0 up
``` Then do:```
ifconfig
```Please post the result here.

---

### Post by IronMac on 2007-07-20
Coming back to this after a long long time away from Linux but still determined to get this working!  :)

I followed the above instructions and got four linux-restricted modules listed.

So, I then typed in :

sudo ifconfig ath0 up

and got an error of: No such device.

Hrmmm...this is very odd since it was working fine under the earlier install.

---

### Post by IronMac on 2007-07-23
Ok, I have no idea what happened but the wireless is now up and running! I guess that ifconfig really did the trick! :lolflag:

---

### Post by IronMac on 2007-07-24
*sighhhhhhhhhhhhhhh*

Not working again.  :(

---

