---
title: "Incredibly Hot in Macbook 5,1!"
date: 2009-06-12
forum: Apple Hardware Users
---

### Post by opensourcelife on 2009-06-12
Hi, I'm running Jaunty on my new aluminum 5,1 Macbook Pro 15.4".  One thing that concerns me is that the machine runs incredibly hot under Ubuntu.  This is probably due to lack of thermal engineering on Apple's side.  However, they treat this in OS X by providing the Battery Life and High Performance modes.  Regardless, even when in high performance mode in OS X, and when booting from Windows it still does not run as hot as it does in Ubuntu.  The heat is almost to the point of rendering it unusable because you cannot use it in your lap without burning yourself.  I'm having to use it like a desktop.

Also, seems like the massive majority of the heat is coming from the left side of the computer.

Does anyone know how I might be able help this?

---

### Post by maflynn on 2009-06-12
I wrote a series of scripts that adjust the minimum speed of the fans
for instance I have a script called fans-35 that looks like the following:
```

echo 3500 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
echo 3500 | sudo tee /sys/devices/platform/applesmc.768/fan2_min

```

I can't claim ownership of creating these, I found something similar here on the board.  If you do a search on fans-up you'll probably find the thread I lifted the code from and the ensuing discussion.

---

### Post by dman777 on 2009-06-12
Was it decided this was due to an aggresive Nvidia driver? Has this been resolved with a new Nvidia driver?

---

### Post by hachaboob on 2009-06-13
NVidia 185 driver does wonders in regards to heat.

---

### Post by cyberdork33 on 2009-06-15
yea, we were pretty sure that it was due to something with the nvidia driver.

---

### Post by alexmurray on 2009-06-15
I've also found the 180.60 driver (current stable NVIDIA driver, unfortunately not in Jaunty - still has 180.44) seems a fair bit cooler too - quoting from the [release notes for 180.60]("http://www.nvnews.net/vbulletin/showthread.php?p=2004770")

> Fixed a bug that caused some performance levels to be disabled on certain GeForce 9 series notebooks


---

### Post by dman777 on 2009-06-15
> **alexmurray said:**
> I've also found the 180.60 driver (current stable NVIDIA driver, unfortunately not in Jaunty - still has 180.44) seems a fair bit cooler too - quoting from the [release notes for 180.60]("http://www.nvnews.net/vbulletin/showthread.php?p=2004770")

would you compare the coolness(using the new nvidia 180.60 driver) of it to a regular laptop?

---

### Post by alexmurray on 2009-06-16
Well given its the first laptop I've owned I can't really say ;) but to me it seems quite cool - idle CPU temp is down to about 47C compared to 55C which it was with the 180.44 Nvidia drivers so it is definitely cooler - to me it is comfortable to have it on my lap.

---

### Post by Engine_number_9 on 2009-06-16
> **alexmurray said:**
> I've also found the 180.60 driver (current stable NVIDIA driver, unfortunately not in Jaunty - still has 180.44) seems a fair bit cooler too

Does anyone know if/when 180.60 will become part af Jaunty?

---

### Post by cyberdork33 on 2009-06-16
> **Engine_number_9 said:**
> Does anyone know if/when 180.60 will become part af Jaunty?
You can file a bug and make the request! I think that it makes sense  since it is a heat issue.

---

### Post by Engine_number_9 on 2009-06-22
> **cyberdork33 said:**
> You can file a bug and make the request! I think that it makes sense  since it is a heat issue.

After finishing my exams I've reported the bug. I'm new to bug reporting but I've done my best at describing the issue. It's reported here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/390665](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/390665)

---

### Post by soderstrom on 2010-07-17
This problem still exist for me and have not found any solution for it yet. Ended up at this thread so would like to know if anyone knows how to fix this heat problem? I don't want my Macbook 5,1 to be used as a frying pan, because seriously thinking about using it for that if this problem can't be solved.

The temperature gets really high just by watching you tube and the fan is on max for a long time. 

I really like Ubuntu 10.04 and wanna use it as my main OS, because Apple is bothering me allot with their dictatorship But it seems they have not made it easy to use any other OS than their own thinking about the hardware compatibility with Linux.

Will also try to apply some Artic Silver 5 to the gpu and cpu to see if that helps. Read it did the trick for heat problem with Macbook Pro.

Don't want the Macbook to turn into a "helicopter frying-pan" so really appreciate any reply to this.

---

### Post by Maletor on 2010-07-29
I could fry an egg where my left palm sits on my MacBook 5,1.

I think it's just an issue with the 5,1 series... could be mistaken though.

---

