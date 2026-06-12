---
title: "installind Nvidia driver"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Skull Kid on 2007-02-11
Hi, I am currently trying to install the Nvidia Linux driver from here: [http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html)

I log in as root user and run the .bin file and it tells me 'You appear to be running an X server; please exit X before installing.' What the heck is an X server and how do I exit it? I've read the README on their site but it doesn't seem to help. Thanks in advance for any help

---

### Post by taurus on 2007-02-11
Here is an easier way to install nVidia driver for your graphic card.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Pollywoggy on 2007-02-11
> **Skull Kid said:**
> Hi, I am currently trying to install the Nvidia Linux driver from here: [http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html)

I log in as root user and run the .bin file and it tells me 'You appear to be running an X server; please exit X before installing.' What the heck is an X server and how do I exit it? I've read the README on their site but it doesn't seem to help. Thanks in advance for any help

Before I answer your question...
I installed Edgy only yesterday and all I had to do was 'sudo apt-get install nvidia-glx' and that got all the dependencies as well.

Then I went to /etc/modules file and added "nvidia" to that list (no quotes).  Then I did
cd /etc/X11 and edited xorg.conf, changing the driver line from "nv" to "nvidia" and also removing the line that says "load    dri"

Then you have to RESTART the X server.  If you are using kdm, the command to stop the X server is  'sudo /etc/init.d/kdm stop'  "stop" can be replaced with "restart" or "start" as needed.  If you use xdm or gdm, just put those in that command instead of kdm.

Stopping the X server will take you to a console.

BTW before you restart the X server, do a 'sudo modprobe nvidia' which you won't need to do after a reboot if you modify /etc/modules as I suggested above.

---

### Post by Skull Kid on 2007-02-11
Hey that worked, thanks!!

I just ditched the official nvidia page and followed taurus' link.

---

