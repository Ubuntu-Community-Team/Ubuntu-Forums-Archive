---
title: "Ubuntu 6.06 no power light on wireless card"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by tomg35 on 2006-10-21
Hi
Just installed 6.06. I have a belkin F5D7010 wireless card installed, the power light is no on, I've checked in device manager and the card has been detected. I've tried both card slots - no luck.

Any suggestions please?

---

### Post by Kateikyoushi on 2006-10-21
I think the drivers might not be loaded.
On my pcmcia wireless card both the power and the net led blink simultaneously so not really as it was meant to be.

---

### Post by .t. on 2006-10-21
I have an ipw2200, which needs to be customised for the LED to work. I suggest you post the output of the following code:```
find /sys | grep led
```

---

### Post by ntetreau on 2006-10-23
Hi .t., I have the same card as you, here's my output:

/sys/module/ipw2200/parameters/led
/sys/class/input/input1/capabilities/led
/sys/class/input/input0/capabilities/led
/sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/led

By the way, on another thread you mentionned latop mode and wireless power management as ways to improve the battery life.  Can these two be automoated to be turned on when running on battery?  Thanks for your help.

Nic

---

### Post by mahy on 2006-10-23
Open the file /etc/modprobe.conf and add the following line

options ipw2200 led=1

then reboot

---

### Post by .t. on 2006-10-23
And if that doesn't work add this line to /etc/rc.local:```
echo 1 > /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/led
```

Also, I just replied in that other thread... [http://ubuntuforums.org/showpost.php?p=1651099&postcount=15](http://ubuntuforums.org/showpost.php?p=1651099&postcount=15)

---

### Post by jqk on 2006-10-23
According to Ndiswrapper (Which, by the way, supports your pcmcia card): 

Needs The Driver: [http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE) (use bcmwl5a.inf in directory AR) 

And ofcourse, it needs ndiswrapper itself, and your good to go!

---

### Post by ntetreau on 2006-10-23
Thanks for the two solutions guys, a quick question though, is the LED supposed to come on when the wifi radio is turned on or only when it connects to a network?  The best would be to use the LED to know when the radio is on or off and not when it is connected or not.  That would make it easier to monitor the power burned when running on the battery!

Nic

---

### Post by TrueJk7 on 2006-10-23
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

SAME Exact problem tomg35! I got it resolved with the link above! 

Hope it goes well.

---

