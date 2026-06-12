---
title: "I lost the wifi icon on the top panel. How to get it back?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Hookheathen on 2008-02-11
I somehow lost the wifi connection (signal strength) icon that also displays available wireless networks that enables me to choose which network to use. After browsing the most helpful posts on this subject, I reinstalled the network-manager-gnome using Synaptic and can now connect wirelessly to one network but I am still unable to choose an alternative network. Additionally panel icon has not reappeared! All i have to show for a connection is the icon with two screens.

Any suggestions how to retrieve the wifi signal strength icon?:confused:
__________________

---

### Post by jan quark on 2008-02-11
i am not sure what you have lost actually but try this

right click on paner 

click add to panel

and under the section system and hardware add network monitor

is it this?

---

### Post by Hookheathen on 2008-02-12
Thanks for this suggestion, it was the first thing I tried but regrettably it did not work. 

The main problem is that I am unable to select or switch from one wireless network to another. Any other ideas?

---

### Post by ibizatunes on 2008-02-12
have u turned your wirless card off bye mistake, if u have a laptop there is a special funiction that can turn it off?!

---

### Post by Hookheathen on 2008-02-12
No I have not turned off the wifi, it is working but I am unable to switch between networks.

I formerly had a panel icon, which, when right clicked, revealed a drop down list of identified networks and I could select the one I wished to connect to. Now I have no icon and accordingly no drop down list. It defaults to probably the strongest signal it picks up, but it is not the network I want. A disaster.

---

### Post by spiderbatdad on 2008-02-12
You need a notification area in the panel...usually where Time and Date reside. If you lost this area, right click on the panel, select add, and add a notification area. If you have a notification area but no network-monitor applet, press** alt-F2** and enter** nm-applet**. The network monitor applet will add itself to your notification area.

---

### Post by kpkeerthi on 2008-02-12
If you have notification area but (still) unable to see wifi icon, you need ```
nm-applet --sm-disable
``` added to System -> Preference -> Session -> Startup.

You may also type that command in a terminal for now.

---

### Post by spiderbatdad on 2008-02-12
> **kpkeerthi said:**
> If you have notification area but (still) unable to see wifi icon, you need ```
nm-applet --sm-disable
``` added to System -> Preference -> Session -> Startup.

You may also type that command in a terminal for now.

That would require the terminal to stay open. If the user closes the terminal, the applet would vanish again. The easiest way is as I posted. **alt-f2** then enter **nm-applet**

---

### Post by cool_penguin on 2008-02-12
Right click the panel. Select Add to Panel and then in the window that opens up, click on Notification area and click on Add. 

Then log out and log in again and you will find that the WiFi logo / icon is back on the panel.

It worked for me. 

Good Luck,

Harry

---

### Post by buntu_Geek on 2008-02-12
The Thing is that you some how stopped the Network Manager Applet.... to start it  use the following code in your terminal...

```

sudo /etc/dbus-1/event.d/25NetworkManager start

```

This should start the Network Manager Applet again...

---

### Post by Hookheathen on 2008-02-12
Thanks for the prompt assistance, no matter how chronically simple it was to solve. You guys are great. You make newbies like me feel reassured that Ubuntu is a welcoming, supportive place. I will continue to spread the gospel!
:):)

---

