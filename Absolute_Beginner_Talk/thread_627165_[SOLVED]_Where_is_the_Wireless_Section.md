---
title: "[SOLVED] Where is the Wireless Section??"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-29
I just installed Ubuntu 7.10 offline, did nsdiswrapper, and have wireless enabled under restricted hardware. However at the top right there is no wireless section when I click on it. I did restart my computer. Help? Thanks.

---

### Post by NotTheMessiah on 2007-11-29
Did you left-mouse click on the network icon(top right) and then manual conf?

---

### Post by 449 on 2007-11-29
> **NotTheMessiah said:**
> Did you left-mouse click on the network icon(top right) and then manual conf?

Yes, and there's wired connection and modem. :confused:

---

### Post by XVII on 2007-11-29
Is your internet functioning wirelessly?

---

### Post by 449 on 2007-11-29
> **XVII said:**
> Is your internet functioning wirelessly?

No, right now it's wired.

---

### Post by jimrz on 2007-11-29
might help if you posted the make/model/chipset of the wireless device you want to use. that way, others with the same setup will be able to assist.

---

### Post by anewguy on 2007-11-29
Try posting the output of  lspci  back here - it may give us more to go on.  

Another thought as well:

If you are using ndiswrapper you (at least in the past) had to blacklist the included driver.

Also:

If you look under Network Settings (system/network), does it show the wireless there?  If so, does it say roaming?


Any of the above information will help.:)

---

### Post by 449 on 2007-11-29
The problem was something with nswrapper. I installed some stuff in the package manager and now it's working. :)

---

### Post by ace007 on 2007-11-29
EDIT: Just Realized you cant even find the Wireless Connection in Network Manager, whoops

I had a confusing experience as well.  If you are referring to the Network Monitor you added to the top panel. I also had a problem. If you are using gnome here is how I solved it:

1).  System-->Administration-->Network

2).  Choose Wireless Connection and then properties. Enable roaming. And then close.

3).  Right click the gnome panel: "Add to Panel..."

4).  Add the Notification Area utility. I already had the Network Monitor utility on the panel, but its not the same as the one that is in the Notification Area.

5).  Click the new network icon in the notification area, and there should be a menu of all the available wireless network connections. You should be able to select yours and then enter the key, or if your SSID isn't broadcast, you can choose "Connect to other network" and enter the credentials.


I don't know if that was what you were asking but, I thought i'd try

---

