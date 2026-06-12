---
title: "Can't get iSight working on 11.04"
date: 2011-05-06
forum: Apple Hardware Users
---

### Post by regebro on 2011-05-06
I can't get the iSight working on 11.04.

I've extracted the driver and put it in /lib/firmware, shutdown and restarted as per instructions. I even tried downloading the latest version (1.6) of isight-firmware-tools from source but that didn't make a difference.

lsusb still says:

Bus 002 Device 003: ID 05ac:8300 Apple, Inc. Built-in iSight (no firmware loaded)

and ls -l /lib/firmware/isight.fw says:
-rw-r--r-- 1 root root 10871 2011-05-06 11:43 /lib/firmware/isight.fw

I can't see any relevant messages in dmesg. 

Bug report: [https://bugs.launchpad.net/ubuntu/+source/isight-firmware-tools/+bug/762128](https://bugs.launchpad.net/ubuntu/+source/isight-firmware-tools/+bug/762128)


Any ideas?

---

### Post by ispmarin on 2011-05-08
Exactly the same problem here.

---

### Post by Silmathoron on 2011-05-08
When you have a problem like that, please don't forget to give us details about your hardware : model of mac, and hardware details
```
sudo dmidecode -s system-product-name
sudo lspci -k
```

When you'll give us that much, we may be able to help you. And by the way, there are lots of informations here : [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by ispmarin on 2011-05-08
The firmware is extracted, and the file is in /lib/firmware. isight-firmware-tools is installed, and it correctly extracted the firmware. The model is a MacBook 2,1, and I already followed all the steps in the guide that you provided. The problem is that it seems that ift-load is not available on 11.04, and even with a complete shutdown the firmware is not loaded and dmesg doesn't show anything. There's a bug report about this exact behavior:

[https://bugs.launchpad.net/ubuntu/+source/isight-firmware-tools/+bug/762128](https://bugs.launchpad.net/ubuntu/+source/isight-firmware-tools/+bug/762128)

Thanks for your help.

---

### Post by samuaz on 2011-05-08
I have installed my isight, the problem I have is that the gstreamer propierties not save the settings, I need to put in

add: custom
and pipeline: v4l2src device = "/ dev/video0"! videoscale

the test works perfectly, but on leaving, gstreamer properties does not save changes!

anyone know how to save the settings properly?

---

### Post by tucun on 2011-07-04
I'm using Ubuntu 10.04 on a MacBook Pro, so I don't know if my solution will help you guys, but here it is just in case (in short, I deactivated the proprietary NVIDIA driver and iSight magically came back to life) -- see my second post on this thread:

[http://ubuntuforums.org/showthread.php?t=1781721&highlight=isight+macbook](http://ubuntuforums.org/showthread.php?t=1781721&highlight=isight+macbook)

---

### Post by paren8esis on 2011-07-04
> I have installed my isight, the problem I have is that the gstreamer propierties not save the settings, I need to put in

add: custom
and pipeline: v4l2src device = "/ dev/video0"! videoscale

the test works perfectly, but on leaving, gstreamer properties does not save changes!

anyone know how to save the settings properly?

Maybe the following will help you :

Go to system->preferences->start-up applications (or something like that) and press *add*. Enter a *name* (eg. isight) and then write into the *command* box : 
```
xterm -e gconftool-2 --set /system/gstreamer/0.10/default/videosrc --type=string -s 'v4l2src device="/dev/video0" ! videoscale'
```

Now, theoretically, every time you boot, the following command line will be executed, and those gstreamer settings will be modified. (I'm pretty new to this, but anyway it worked for me...)

---

### Post by earlf on 2011-12-28
I'm a bit late to the party, but this solution does not work for me on Xubuntu 11.04 running on a Macbook 1,1.

Manually entering ```
v4l2src device="/dev/video0" ! videoscale
``` for the gstreamer-properties video option makes the iSight work.

The setting does not persist, even with a startup application as paren8esis kindly provided. 

Even manually changing the default of this setting in gconf-editor does not change the settings for cheese to use. 

I'll keep trying and post a solution once I find one.

---

### Post by tanzantj on 2012-03-11
I have the same problem.  I can get my cam to work while in gstreamer-properties but the settings don't save.  I am able to have skype recognize my cam if I run this command:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
```

but the cam is very, very dark.

This is getting frustrating.  Thanks to [this guy]("http://blog.pucp.edu.pe/item/66219/how-to-fix-the-skype-video") for that command.

---

### Post by whiskers751 on 2012-03-15
Code to run
```
 sudo nano /etc/init.d/isightconfig
```
Inside that file put
```
 #!/bin/bash
[that long command the other guy mentioned]
exit
```
Then run
```
cd /etc/init.d/
sudo update-rc.d isightconfig defaults
sudo bash /etc/init.d/isightconfig

```

---

