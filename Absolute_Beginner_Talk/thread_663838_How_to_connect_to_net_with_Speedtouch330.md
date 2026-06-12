---
title: "How to connect to net with Speedtouch330 ??"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by JungleBeast on 2008-01-10
Hello there, I'm a newbie - just installed 7.10 Gutsy Gibbon for amd64

And I'm trying to connect to the net. Using a Speedtouch 330 modem (adsl for tiscali)

I've tried to follow the basic How to's:

[USB ADSL modem manager]("http://ubuntuforums.org/showthread.php?t=585647")
where this one just wouldn't run. No idea why!

and this:
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")
[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch")


boh of these are the same method. I understand it fine but come up with the following problems:

1. in the initial grep to see what version firmware I have. I don't actually have any files/folders at ```
/proc/bus/usb/devices
```

but this is ok, cos i did of looking around in device manager or something and found that it's version 4.0 anyway.

2. when I go to run the firmware-extractor on the ZZZL_3.012 file using ```
./firmware-extractor ZZZL_3.012
```    (having chmoded it)   i get ```
bash: ./firmware-extractor No such file or directory
```      and without the ./   i get command not found


So does anyone have any ideas? connecting to the net is pretty vital to me.

Thank you!!!

---

### Post by duruttye on 2008-01-10
Hey!
A while ago I had that same model, the only suggestion I have for you is to change it, as soon as possible!

It is a pain in the a** to make it work and it is unstable... stops and starts at it's own will.

Still, there is a romanian distribution which recognizes the modem and has a gui interface to configure it, you can find it at: [http://kiwilinux.org/download.html](http://kiwilinux.org/download.html)

Good luck!!

---

### Post by plucky on 2008-01-10
JungleBeast,

I see you are using AMD64 bit Ubuntu. Did you download the 64 bit version of **USBADSLMODEMMANAGER**. The 32 bit version won't work on the 64 bit system.
You can get the 64bit version from [here]( http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/64-bit%20i686/)

I use the 32 bit version so I don't know if the 64 bit version works.

Hope this helps

---

### Post by JungleBeast on 2008-01-12
Thank you guys!  I'm now getting along with the 64 bit usbadslmodemmanager.

Which of course worked once and then wouldn't work again! However I'm now 1 step closer to internet!
Which I'm following up on page 9 of this thread [here]("http://ubuntuforums.org/showthread.php?t=585647&page=9")

hopefully it will get seen!!

Still have no idea why i wasn't able to just run the firmware-extractor!?

---

