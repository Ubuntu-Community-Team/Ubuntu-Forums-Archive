---
title: "Wlan client software?"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Shack on 2007-09-02
Hi.

I've installed d-link card to my computer and succesfully connected it to my wlan-ap with wpa. I was just thinking if there is some good wlan client software available which I could use  to connect wlan's at my work and hotels etc.

I'm not so familiar with wlan commands at terminal so I would apriciate some software to my graphical interface.

---

### Post by moore.bryan on 2007-09-02
*i'd suggest [wicd]("http://wicd.sourceforge.net/").*

---

### Post by Shack on 2007-09-03
> **moore.bryan said:**
> *i'd suggest [wicd]("http://wicd.sourceforge.net/").*

I thank thee.

---

### Post by moore.bryan on 2007-09-03
*thou art welcome.*

---

### Post by Shack on 2007-09-04
Just another question friend.

I'm having problems with my encryption. I'm using wpa. My wlan is working fine with the encryption when I start my ra0 device from terminal. I have manually edited my network settings and set up my encryption there.

But which settings  to choose with this program from encryption tab? I hav d-link dwl-g630 card with RT61 driver. I have set my encryption method and key to Wicd, but what choose from prefences wpa supplicant driver? 

Thanks already.

---

### Post by moore.bryan on 2007-09-04
*when you single-left-click on the wicd tray icon to start the gui, you should see white triangles next to your available networks.  when you click one of them, you should see more choices and another white triangle next to "advanced settings."  click that triangle and you'll see "encryption" if you scroll-down.  there you can choose which encryption method you're employing and put-in your key- or pass-phrase.*

---

### Post by Shack on 2007-09-04
I've done like you told, but for some reason this software is displaying that I'm using web altought that isn't true. How come does it show wrong encryption method for my network.

---

### Post by imdano on 2007-09-06
Your wireless card probably uses a ralink chipset, which doesn't properly report (or report at all, in some cases) which type of encryption networks are using.  What is the output of these commands ```
sudo lshw -C network
iwlist scan
iwpriv
```

---

