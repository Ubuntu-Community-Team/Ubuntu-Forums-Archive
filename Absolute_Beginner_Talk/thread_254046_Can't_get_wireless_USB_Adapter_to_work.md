---
title: "Can't get wireless USB Adapter to work"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Taskr36 on 2006-09-09
After scouring the web like mad I found what I think are the right drivers for my wireless usb adapter. The model isan ABS NW-200-USB and it is 802.11b/g. I used the terminal to get the chipset number which is 07b8:6001. 

I searched high and low with that number and eventually came to the zd1211 wireless driver module. I then installed the kernel package, module assistant, and then double clicked and seemingly installed the zd1211 driver. I rebooted the computer and nothing seems to have changed. Did I miss a step somewhere? Does anyone have any advice on how to get this thing to work?

The wireless adapter does not show up in the connections window and I did have it plugged in when I originally installed Ubuntu. The device manager sees it as USB WLAN but I can't find any options there to update, install, or change drivers. Was I supposed to do something other than double click the driver to install it?

---

### Post by furiousV on 2006-09-10
Type in

```
lsmod | grep zd1211 
```

If you see a line like "zd1211       XXXXX X" X being some numbers, then the kernel module has loaded.

Type in ```

sudo ifconfig wlan0 up

if successful (sometimes it returns no message) then do:

sudo iwconfig wlan0

and finally

sudo dhclient wlan0

```

That should hopefully get you connected to your router's wireless.



If from above, the kernel module was not loaded, type in
```

sudo modprobe zd1211

```
Then continue with ifconfig and the rest.

If modprobe fails, then you most likely haven't compiled the kernel module properly. If that is the case, let us know and we'll help you out.

I gathered this from [here](http://zd1211.ath.cx/#Installation) - the zx1211 driver site.

Hope that helps

---

### Post by Taskr36 on 2006-09-10
Thanks, I actually got the drivers functional earlier today. Then it was just a fight to get the wireless assistant working. Now I have it connected to the internet so I'm pretty much good to go. Now I'm just installing plugins so I can watch DVDs and browse different webpages. Thanks again.

---

