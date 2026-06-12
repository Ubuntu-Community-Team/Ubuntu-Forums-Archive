---
title: "New Macbook WLAN"
date: 2008-11-17
forum: Apple Hardware Users
---

### Post by the_29 on 2008-11-17
Hello!
After I installed Ubuntu my WLAN was working fine.

Then i discovered the hardware drivers program, where you can install closed source drivers. 
So i decided to install the NVidia drivers and then the Broadcom drivers.
After i installed the broadcom drivers, my WLAN was not working anymore (it says no wlan found).
So i decieded to deactivate the closed source driver and my old wlan was found (when the wlan modul connected to the net, the wlan icon at the taskbar disappears - is that normal?).

But every reboot, i have to activate the closed source driver and then deactivate it. Then i have to wait 1 minute and the WLAN module is recognized again..

So how can i avoid this problem?! Any solutions out there? 
Or has anyone the same problem?

---

### Post by cyberdork33 on 2008-11-17
Please use the info in the "Before You Post" Link to properly identify your Mac and find the appropriate documentation.

---

### Post by the_29 on 2008-11-18
You mean that site?
[https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

I know that i have the Macbook Alu (Macbook 5,1)

The problem is that the WLAN was 100% working. But after installing the closed source driver the module is not working anymore!
So i have to deactivate the driver (but this every reboot and this sucks!!)

---

### Post by cyberdork33 on 2008-11-18
> **the_29 said:**
> You mean that site?
[https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

I know that i have the Macbook Alu (Macbook 5,1)
You should be sure to post the version information EVERYTIME you post a new thread. This will let everyone know exactly what hardware you are dealing with. (not all airport cards are the same hardware).

> **the_29 said:**
> The problem is that the WLAN was 100% working. But after installing the closed source driver the module is not working anymore!
So i have to deactivate the driver (but this every reboot and this sucks!!)

You should be sure to enable the Broadcom STA driver and only the Broadcom STA driver in the Hardware Drivers dialog. If you continue to have issues, you probably should block the ssb and b43 drivers from trying to load automatically on bootup. You can do this by adding
```
blacklist ssb
blacklist b43
```

at the bottom of your /etc/modprobe.d/blacklist file.

You may also want to add 'wl' to your /etc/modules file to make certain that is loaded at startup.

In the future, if something is working, don't try to fix it ;)

---

### Post by the_29 on 2008-11-19
Yeah!
Thx man, now its working again! (i will not change things that are working :D)

But i am a little bit confused!
In the HowTo is for the trackpad that:

Left-click, basic trackpad and two-finger vertical scrolling work out of the box. Work on right-click, multi-touch etc is progressing.

But two finger vertical scrolling is not working for me :(

---

### Post by cyberdork33 on 2008-11-19
> **the_29 said:**
> Left-click, basic trackpad and two-finger vertical scrolling work out of the box. Work on right-click, multi-touch etc is progressing.

But two finger vertical scrolling is not working for me :(
Did you do the steps in the wiki page? If so, and you still have issues, then please start a new thread as it is a new problem. Please mark this one as solved from the thread tools menu at the top of the page.

---

