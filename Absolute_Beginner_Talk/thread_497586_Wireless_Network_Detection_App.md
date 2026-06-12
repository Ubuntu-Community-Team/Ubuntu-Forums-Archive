---
title: "Wireless Network Detection App?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-07-10
What is the best app for searching and connecting to wireless networks from Ubuntu

---

### Post by Inxsible on 2007-07-10
> **kc5hwb said:**
> What is the best app for searching and connecting to wireless networks from Ubuntu
The one which comes pre-installed with Ubuntu. its called nm-applet
 
People have also found madwifi to be useful.

---

### Post by black_ice on 2007-07-10
SWS scanner form synaptic  is great and feisty has itis default manager and itis great also

---

### Post by kc5hwb on 2007-07-10
I don't find any of those pre-installed ones in my Applications menu.

---

### Post by Inxsible on 2007-07-10
> **kc5hwb said:**
> I don't find any of those pre-installed ones in my Applications menu.
Its not in your Applications menu. When you try to use a wireless connection, it is being used. It doesnt have a frontend GUI i think, its simply a backend process.

---

### Post by kc5hwb on 2007-07-10
Well then how does it know which network I want to detect to when i am in range of multiple routers, and how do I setup encryption?

I want one with a GUI.  Which one is best with a GUI?

---

### Post by Inxsible on 2007-07-10
> **kc5hwb said:**
> Well then how does it know which network I want to detect to when i am in range of multiple routers, and how do I setup encryption?
 
I want one with a GUI. Which one is best with a GUI?
 
If you click on the network icon near the system clock, it will show you all the networks nearby. You can select anyone you want to connect to. You can also easily set up encryption, by selecting 'Manually Configure Network' and then setting up the parameters within

---

### Post by WieboJJ on 2007-07-10
If your wireless card is set up correctly, i.e proper drivers and such are installed and set to scan, when you left click on the nm applet (in the top right corner of your screen by default) it will give you a list of availible networks. Select one, tell it what kind of encription your network uses and enter your password.  WEP works no problem for me, but for WPA or WPA2 encription you will probably need wpasupplicant. Info on how to set that up is a sticky on the wireless forum.

---

### Post by kc5hwb on 2007-07-10
Perfect, thanks for the help.

---

### Post by Skidpad on 2007-07-10
I use RutilT WLAN Manager.  I think its a great application.  It was written primarily for the Ralink RTxx series wireless chipsets, but the web page says it works on anything.  I have a Ralink chipset in my wireless adapter, so I can't personally comment on compatibility with other chipsets.

Check it out here: [RutilT WLAN Manager]("http://cbbk.free.fr/bonrom/")

Screenshots [here]("http://alexit.wordpress.com/2007/04/10/rutilt-utility-grafica-per-driver-wireless-ralink-rt73/")

---

### Post by walkerk on 2007-07-10
+1 for [wicd]("http://wicd.sourceforge.net")

---

### Post by kc5hwb on 2007-07-10
SWS Scanner seemed cool, but it kept crashing on me.  The one in Nautilus seems to work ok though.

---

### Post by gigaferz on 2007-07-10
wifi-radar ?

---

### Post by kc5hwb on 2007-07-10
> **gigaferz said:**
> wifi-radar ?

So far so good, I will test it out tonight.  Thanks!

---

### Post by gigaferz on 2007-07-10
i had it running and i like the way it works.

But i decided to wep my network, and dist upgrade and it stopped working, but it was kinda like windows,click and connect

---

### Post by ugm6hr on 2007-07-10
> **walkerk said:**
> +1 for [wicd]("http://wicd.sourceforge.net")

Agreed. 

Pros:
System-tray applet with live connection strength display;
Roaming facility (including wired);
Compatible with essentially any chipset or ndiswrapper, and does WPA using wpa-supplicant;
Can be setup to auto-connect to preferred networks;
Doesn't harrass you for a "keyring password" every time it connects.

Cons:
Struggles with WPA if your chipset doesn't use wpa-supplicant.

---

### Post by imdano on 2007-07-10
> **ugm6hr said:**
> Cons:
Struggles with WPA if your chipset doesn't use wpa-supplicant.We're actually working on fixing that right now.  We're testing support for using iwpriv instead of wpasupplicant to connect with the enhanced ralink legacy drivers that serialmonkey puts out (not the rt2x00 drivers) to use WPA.  Is there a list around of what chipsets aside from all the rt* drivers don't support wpasupplicant?

---

### Post by kc5hwb on 2007-07-10
none of mine are WPA, just WEP.  So hopefully I won't have an issue.

---

### Post by Inxsible on 2007-07-10
> **ugm6hr said:**
> Agreed. 
 
Pros:
System-tray applet with live connection strength display;
Roaming facility (including wired);
Compatible with essentially any chipset or ndiswrapper, and does WPA using wpa-supplicant;
Can be setup to auto-connect to preferred networks;
Doesn't harrass you for a "keyring password" every time it connects.
 
Cons:
Struggles with WPA if your chipset doesn't use wpa-supplicant.
 
How would I find out if my chipset supports/uses wpa-supplicant ?
 
My wireless works flawlessly as of now. But I might just install wicd if it can rid me of the keyring password question on every boot.

---

### Post by linux_kid on 2007-07-10
Feisty Fawn comes with gnome-network applet as default, and the applet works on Dapper, too (not Edgy).  I advise using it, works great for me.

EDIT:
About the question thing at boot, there is nothing you can do about it, I've tried many times.  If it disappears as you are typing your pass, right click it at the bottom and select "On Top".

---

### Post by imdano on 2007-07-10
> **Inxsible said:**
> How would I find out if my chipset supports/uses wpa-supplicant ?
 
My wireless works flawlessly as of now. But I might just install wicd if it can rid me of the keyring password question on every boot.If you got WPA working without any trouble then you're probably fine.  What chipset are you using.

---

### Post by Inxsible on 2007-07-10
> **imdano said:**
> If you got WPA working without any trouble then you're probably fine. What chipset are you using.
Yes, I have WPA working fine. I use Intel 3945A/B/G

---

### Post by imdano on 2007-07-10
I'm pretty sure that chipset works fine with wpasupplicant.  That's actually the same card I have (haven't tried it with WPA though, obviously).

edit: I just set it up on my home network with no problem at all, except that I initially was using a "$" in my key which wpa_passphrase wouldn't convert into a psk.  So make sure you only use a-z and 0-9 in your key and you should be alright.

---

### Post by compwiz18 on 2007-07-11
> **Inxsible said:**
> How would I find out if my chipset supports/uses wpa-supplicant ?
 
My wireless works flawlessly as of now.** But I might just install wicd if it can rid me of the keyring password question on every boot.**

It connects at boot, automatically, with no very irritating password prompt :D (one of the reasons it was created)

---

