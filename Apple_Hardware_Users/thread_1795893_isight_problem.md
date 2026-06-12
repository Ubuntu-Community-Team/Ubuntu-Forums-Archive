---
title: "isight problem"
date: 2011-07-03
forum: Apple Hardware Users
---

### Post by paren8esis on 2011-07-03
Hello everybody!
I'm running Ubuntu 11.04 on a Macbook 4.1, and I'm trying to load the isight firmware. I followed the instructions [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight"), and now there is an isight.fw in /lib/firmware/ folder. The problem is that still cheese cannot find my camera. 

Also, gstreamer says that there is no /dev/video0 device.

And by putting *lsusb* in the terminal, I get this :
```
Bus 002 Device 002: ID 05ac:8300 Apple, Inc. Built-in iSight (no firmware loaded)
```

Well, probably it's a quite stupid question, but I'm pretty new to Ubuntu, and after searching for two days on the internet for a solution, I got more confused... :confused:

Any suggestions greatly appreciated! :mrgreen:

---

### Post by tucun on 2011-07-04
Hi
Don't know if this will help, but I solved a similar problem just now. I found out the NVIDIA driver was the culprit, at  least on my MacBook Pro 5,1 running Ubuntu 10.04.

After activating this driver, I noticed that my /dev/video0 simply disappeared. So I then went back and deactivated the NVIDIA driver. Not only I got  /dev/video0 back, but now my iSight came back to life as well.

How I did it on 10.04 (may be different for your 11.04, I don't know):

- Go to System > Administration > Hardware Drivers
- Select the NVIDIA driver you may have installed and choose "Remove"
- Shut down the computer. Turn it back on.
- See if it worked: go to a terminal, type gstreamer-properties, hit enter, a dialog opens, go to  the Video tab, see if your iSight is listed under "Devices", hit the  "Test" button and... your cam should work now.

I don't really use a lot of fancy graphical things so at least until now I didn't feel I'm missing anything for not having the NVIDIA driver active. I'd rather have the webcam working.

---

### Post by tucun on 2011-07-04
PS. I didn't have to do anything of the whole firmware stuff. In fact, I was suspicious that it wasn't really necessary when I first got the built-in iSight to work out of the box with Ubuntu running from the Live CD, even before installing it.

---

### Post by paren8esis on 2011-07-04
Thank you very much for your reply!

I tried what you said. I uninstalled the nvidia packages, turned off and on again the computer, but the problem still remains. My camera isn't working and /dev/video0 is nowhere to be found....  :(

---

### Post by paren8esis on 2011-07-04
There is some progress.

I went to start-up programs, and added the following : 
```
xterm -e gconftool-2 --set /system/gstreamer/0.10/default/videosrc --type=string -s 'v4l2src device="/dev/video0" ! videoscale' 
```

Then turned off and on my computer.

now, the output of *lsusb* is :
```
Bus 002 Device 005: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]

```

Anyway, gstreamer has "found" my camera since now there is a new option : "Built-in Sight", which wasn't there before, but still no output.
On the other hand, my camera now works perfectly with cheese! :)

---

### Post by tucun on 2011-07-04
After a day of experiments, sometimes I still get this same error you describe: my iSight is listed in gstreamer-properties, but it doesn't work. Usually after a reboot it comes back to work.
I still haven't figured out what happens on each boot that seems to "randomly" break something (either /dev/video0 disappears altogether, or it is there but still iSight doesn't work). Luckily so far most of the time it works now...

---

