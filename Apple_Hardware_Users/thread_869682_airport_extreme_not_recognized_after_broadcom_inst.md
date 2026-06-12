---
title: "airport extreme not recognized after broadcom install"
date: 2008-07-25
forum: Apple Hardware Users
---

### Post by gaswirth on 2008-07-25
Hi,

I've been trying now for hours to get this to work!

I'm running Ubuntu (64 version) on my iMac, and I'm trying to get my internal Airport Extreme card working.  I've installed (I believe, anyway) the cafuego packages for the broadcom firmware (including the b43-fwcutter utility), and have followed every instruction I can find, but the driver isn't loaded, and my system won't recognize any other interface other than my wired ethernet (eth0).  in lspci, the card is recognized.

Any suggestions?

Thanks!!

---

### Post by cyberdork33 on 2008-07-25
Please read the FAQ before posting:
[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

fwcutter and the open broadcom driver do not work with the cards in Macs. You have to use ndiswrapper.

---

### Post by gaswirth on 2008-07-25
Thanks, sorry about that.

I followed the directions you pointed to, and everything seemed to go OK, but there's STILL no wireless interface detected.  I followed the directions here: [http://ubuntuforums.org/showthread.php?t=735846]("http://ubuntuforums.org/showthread.php?t=735846").

iwconfig and ifconfig only show lo and eth0 interfaces, even though ndiswrapper -l shows that the broadcom driver is now installed.

Ahhhh!!!!

Thanks!

---

### Post by cyberdork33 on 2008-07-25
> **gaswirth said:**
> Thanks, sorry about that.

I followed the directions you pointed to, and everything seemed to go OK, but there's STILL no wireless interface detected.  I followed the directions here: [http://ubuntuforums.org/showthread.php?t=735846](http://ubuntuforums.org/showthread.php?t=735846).

iwconfig and ifconfig only show lo and eth0 interfaces, even though ndiswrapper -l shows that the broadcom driver is now installed.

Ahhhh!!!!

Thanks!
you have to load ndiswrapper:
```
sudo modprobe ndiswrapper
```

Then to make sure it loads by itself in the future, add 'ndiswrapper' to /etc/modules

---

### Post by gaswirth on 2008-07-25
Did that...sorry, should have mentioned it.  But yeah....did modprobe, and when I do modprobe -l, I see ndiswrapper in the list.  I keep reading things about Madwifi...should I try using those instructions?  Or am I on the right track?

Thanks again...really appreciate it!

---

### Post by gaswirth on 2008-07-25
Got it!!! Finally found these great instructions!  Thanks!!

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by cyberdork33 on 2008-07-25
> **gaswirth said:**
>  I keep reading things about Madwifi...should I try using those instructions?  Or am I on the right track?
madwifi is for the other type of Apple WiFi card... based on the Atheros chipset.

Please mark this thread as solved (Thread Tools Menu).

---

