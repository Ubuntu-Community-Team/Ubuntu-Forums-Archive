---
title: "startting over"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by jbrockk13 on 2007-08-27
OK, I've put this off long enough and now I need to try to retry ubuntu! My problem is I can not get my wireless to work on my laptop. I have a Compaq pesario v5000 with a Broadcom built in wifi model bcm4318. I have tried a couple of how to's but had no luck. So like I said I am ready to start over I'm going to reinstall 7.04 (feisty I believe). This will be a dual boot with xp. Does anyone have a suggestions as to which direction I should take to get this Broadcom bcm4318 to work right? The last couple times I've tried I end up loosing a wireless connection all together in network manager. It doesnt even show up as an option. Wired works just fine. Thanks for any help and please stick with me for this is my first venture into the world of linux . Thanks

 Jason

---

### Post by kellemes on 2007-08-27
Is this what you're looking for?

[http://ubuntuforums.org/showthread.php?t=285809]("http://ubuntuforums.org/showthread.php?t=285809")

---

### Post by jbrockk13 on 2007-09-01
ok finally got time to try this. I've downloaded the driver and extracted it to a folder called wifi on the desktop. When i get to the part of entering the location of the driver, what would be the whole line to type out?

---

### Post by jbrockk13 on 2007-09-01
help?

---

### Post by jbrockk13 on 2007-09-01
ok, I get to check to see if hardware found and i get the following error code, invalid driver. Any idea what I did wrong?

---

### Post by jbrockk13 on 2007-09-02
I think I've about had it with this built in wifi!  I must be doing something really wrong cause it just doesnt work for me. can anyone recommend a usb adaptor, or a wifi card that is a express slot card that will work. I understand almost anything will need some work, and I am willing to do what ever I have to to get wireless working. Thanks

---

### Post by jbrockk13 on 2007-09-02
starting to think im talking to myself :(

---

### Post by jbrockk13 on 2007-09-03
help?

---

### Post by bonzodog on 2007-09-03
right, the command path for your system is probably (try looking for the driver first in the terminal):

```
sudo ndiswrapper -i /home/jbrock/Desktop/wifi/bcmw15.inf.
```

Please make sure you have installed ndiswrapper first, like the tutorial pointed to says.

Also, make sure you are using the correct driver!

It sounds like there may be more than one on the install CD, so maybe downloading from the site pointed to in the tutorial ([ftp://ftp.support.acer-euro.com/notebook/aspire_3020/driver/WLan%20Driver%20Broadcom%20802.11g%203.100.46.0.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020/driver/WLan%20Driver%20Broadcom%20802.11g%203.100.46.0.zip))
will work better.

---

