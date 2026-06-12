---
title: "Acer Aspire 14.1&quot; 3050-1594 Laptop with Acer Mobile AMD Sempron 3400+, 1.8GHz"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by oldone on 2007-01-08
Acer Aspire 14.1" 3050-1594 Laptop with Acer Mobile AMD Sempron 3400+, 1.8GHz


Has anyone got Ubuntu to work with this model of laptop?

I NEED TO Know.

I am thinkiong of getting it - the price is right and it has 802.11g card too.

thankyou

---

### Post by tchoklat on 2007-01-08
r u able to test it with the Live CD?

---

### Post by oldone on 2007-01-08
as I stated - I have not boughten it yet. I would have to order it. not testable

---

### Post by gingerj on 2007-01-08
I've got the Aspire Aspire 5602wlmi, Ubuntu 6.06 installed fine on it, just be careful with your partitions if you're going to dual boot as there's a hidden partition which has a recovery image on it for your WinXP system. 

Erm, I haven't tried all the gizmo's on it like bluetooth, or wireless or even the card reader. But I can confirm the actual O/S installs fine, I'll probably try to get the ATI drivers working this weekend. So I can use it at a half decent resolution.

---

### Post by oldone on 2007-01-08
Ginger - what is the problem with the resolution. I also need to have the wireless working to.

thank you for the response.

---

### Post by The Joe on 2007-01-08
I have had it working on the model, the same type. 3050 Sempron dadadadada... So you should be ok, I don't know about SignalUp and Bluetooth. Give it a small partition and keep Windows on though! Things like Arcade are irreplaceable!

---

### Post by gingerj on 2007-01-08
> **oldone said:**
> Ginger - what is the problem with the resolution. I also need to have the wireless working to.

thank you for the response.

The resolution problem isn't really a problem, it's just when you install Ubuntu on it with the **default** drivers installed you'll only be able to select 1024x768.

But I'm pretty sure the second the ATI drivers are installed I should be able to get the resolution up to something half decent.

Although I haven't researched this at all and I'm just going on a hunch here :D

If I cant get the resolution up to my XP partition I'll be most-displeased.

---

### Post by oasill on 2007-01-25
Hi,

I just yesterday got an Aspire 3050 and used the LXFDVD88 with ubuntu 6.10 to install everything on the machine. It works well but I am still missing the WLAN and I cannot get the speakers on. I would assume that both can be configured but I have yet not had time to look into it.

The rest of the sytem works well. Installed first the Windows system, then boot linux and resized the bigger windows partition and in the spare space put in a swap and an ext3 partition. Off it went and the result is a nice well working system. The price for the device (special offer) was 550€.

                                   Good luck OA

---

### Post by oldone on 2007-01-26
Ok - thank you for the reponse.  Did anyone get the resolution sorted out since this a widescreen?  and also anyone get the wireless working. I have an airport extreme station.

thank you.

---

### Post by tiger015 on 2007-05-09
I have Acer aspire 3004, 15.4 inch with SiS video card and Sempron 3100+. I have perfect widescreen resolution and I can connect to wireless using nm-applet. Getting widescreen resolution is tricky. You may have to modify screen and monitor settings in /etc/X11/xorg.conf Here is mine. Let me know if it helps

Section "Monitor"
identifier "Generic Monitor"
vendorname "Generic"
modelname "Flat Panel 1280x800"
HorizSync 31.5-90
VertRefresh 60
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1280x800_60.00" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
modeline "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
modeline "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
modeline "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
modeline "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
depth 24
modes "1280x800@60" "640x480@60" "800x600@60" "1024x768@60" "1280x1024@60" "1600x1200@60" "1792x1344@60" "1856x1392@60" "1920x1440@60"
EndSubSection
EndSection

---

### Post by black_ice on 2007-05-09
i have got an acer aspire 5601 and ubuntu works fine but the resulotion 1024*768 i cannot adjust it to have more resolution 

and wireless ... the card is already detected but i donot  know which program is suitable  for wireless on feisty

---

### Post by tofaffy on 2007-11-21
I have the same laptop with sempron mobile and ati graphics. I'm in Ubuntu Gutsy and experience Crackling audio? Does anyone have any ideas what could be causing this?

---

