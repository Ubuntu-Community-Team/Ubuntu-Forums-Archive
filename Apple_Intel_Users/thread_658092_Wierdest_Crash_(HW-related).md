---
title: "Wierdest Crash (HW-related?)"
date: 2008-01-04
forum: Apple Intel Users
---

### Post by omax on 2008-01-04
Hi guys, I just had the weirdest crash. And to avoid it happening again, I'd like to find out what happend.

Macbook C2D rev2 - 1gb ram
Macosx 10.4, 2.6.22-14-rt Xubuntu, Windows XP Home (broken, to be deleted)

I was surfing the web, computer running without problems just as usual...
All of a sudden it dies, as if you pulled out the power cord on a workstation.

I pressed the powerbutton again, and it booted up... for 1 second and then it died again.
I pulled out the battery and blew it clean, I also blew all the fan-holes. After reinserting it, the computer didnt respond at all. It didnt boot.

Checking the battery with the button underneath gives full power. The powercord's light is lit.

After a while of desperate trying, it boots, everything back to normal...

What just happend? Is it because the laptop was in my knee?

Happy for response

---

### Post by cyberdork33 on 2008-01-04
Sounds very strange, and yes, likely hw. What OS were you in when the issue occurred?

It almost sounds like you unintentionally reset the SMC controller (which handles much of the power settings.) which got it working again. [http://docs.info.apple.com/article.html?artnum=303319](http://docs.info.apple.com/article.html?artnum=303319)

---

### Post by david_edmundson on 2008-01-04
Sounds like overheating to me. 
Run "lsmod | grep applesmc" and check that it's loaded

---

### Post by omax on 2008-01-04
I was running ubuntu while it happend.

```

$ lsmod|grep applesmc
applesmc               18572  0 
led_class               5380  1 applesmc

$ sudo hddtemp /dev/sda
/dev/sda: FUJITSU MHV2080BHPL: 35°C


```

I know that applesmc is installed, but if its loaded here I'm not sure according to the output...
applesmc 0 ?

---

### Post by cyberdork33 on 2008-01-05
> **omax said:**
> I know that applesmc is installed, but if its loaded here I'm not sure according to the output...
applesmc 0 ?
It wouldn't even come up at all if it wasn't loaded.

---

