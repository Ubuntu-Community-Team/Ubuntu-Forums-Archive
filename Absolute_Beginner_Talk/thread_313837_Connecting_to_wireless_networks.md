---
title: "Connecting to wireless networks"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by manishk on 2006-12-06
I just installed a Win driver for my **Broadcom wireless** card using **NDISwrapper**. 

I dont have **Network Manager**. How do I search and connect to wireless networks??

I dont have net access till then, so no apt-get.

---

### Post by GreenHawkIA on 2006-12-06
Use the included networking dialog.  Go to System-Administration-Networking.  If your wireless card is recognized, it should be in the list.  Another way to make sure that the wireless is working is to open a terminal and type iwconfig.  If your wireless card is recognized it should appear in the list somewhere.  Back to the GUI - in the networking dialog, highlight the wireless conneciton, hit Properties, and fill in the information on the network you wish to connect to.  Hit apply, and that should connect you without Network-Manger.
When you do install network-manager...go back to the networking dialog, and disable the devices, otherwise network manager won't be able to manage them.  Let me know if this helps.


> **manishk said:**
> I just installed a Win driver for my **Broadcom wireless** card using **NDISwrapper**. 

I dont have **Network Manager**. How do I search and connect to wireless networks??

I dont have net access till then, so no apt-get.

---

### Post by manishk on 2006-12-07
Thanks for that.

I connected to the network succesfully, but Firefox is not throwing up any webpages. Actually I wouldn't have even known that I was connected if not for the 'Updates available' dialog that poped up.

I even installed network-manager and network-manager-gnome, but Firefox is not displaying any webpages. 

Any solutions?

I had to reconnect using Win post this...I'll try next connecting using network manager and will let you know

Thanks again

---

