---
title: "Macbook Pro 7,1 No video out"
date: 2011-10-16
forum: Apple Hardware Users
---

### Post by Sileem on 2011-10-16
According to the Ubuntu Macbook wiki, the mini display port should work out of the box, but for me, it does not. It doesn't recognize and external monitor (in this case being my TV connected through HDMI).
I am using Ubuntu 11.10, gnome-shell, nvidia 285.05.09, and the Monitor Status Indicator shell extension.

---

### Post by Harp on 2012-04-05
I have the exact same problem. Does anyone have a solution for this yet? Or at least know a place to start?

---

### Post by Caltac on 2012-04-06
I recommend opening NVIDIA X Server Settings from system settings and taking a look around there.

---

### Post by Damo42 on 2012-04-08
> **Caltac said:**
> I recommend opening NVIDIA X Server Settings from system settings and taking a look around there.

I just installed Ubuntu 11.10 along side OS X 10.6 on MBP 7,1. To get my mini-display port working I did what Caltac suggested. This might help too.

Go to NVIDIA X Server setting > X Server Display Configuration.

Click Detect Displays.

When the second monitor shows up select it in the 'Layout' panel (It will have a red boarder around it) then select 'TwinView' from the Configuration menu then click Apply (Make sure your external monitor is connected and on).

Change the position as desired and click apply when finished.

You can also run this in clamshell mode by selecting 'Make this the primary display for the X screen' on external monitor, and unselecting this option for the Apple (laptop) monitor. While still in the Apple monitor menu select 'Disabled' from the Configuration menu. Then click Apply. Then change the power settings so that the laptop doesn't go to sleep when the lid is closed.

---

