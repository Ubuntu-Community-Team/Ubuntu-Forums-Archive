---
title: "Macbook 7,1 Brightness Controls Help"
date: 2010-07-23
forum: Apple Hardware Users
---

### Post by labaom on 2010-07-23
I looked through the wiki and for some reason I cannot get my brightness controls to work. Help would be appreciated. Has anyone else ran into this issue?

Thanks

---

### Post by enryf89 on 2010-10-22
I have the same problem on a freshly installed ubuntu 10.10.
Any suggestion?

---

### Post by fergie7 on 2010-10-24
> **labaom said:**
> I looked through the wiki and for some reason I cannot get my brightness controls to work. Help would be appreciated. Has anyone else ran into this issue?

Thanks 

i have this problem too after i installed the grapics driver.

---

### Post by lael on 2010-10-24
I had an issue with my Macbook Pro 6,1 which was recently fixed in a kernel update (LCD brightness control)

Any outstanding updates?

---

### Post by Macbook on 2010-10-24
I experienced the same after updating to 10.10 on MacBookPro 5-4. When updating to 10.10 the mactel ppa packages that provide Apple-specific packages were disabled. 

Reinstalling the mactel ppa packages solved to problem. You can give it a try and follow these instructions:

[https://help.ubuntu.com/community/MacBookPro5-4/Lucid](https://help.ubuntu.com/community/MacBookPro5-4/Lucid)

READ: "Additional Package Support for Intel Macs"

Please be aware that informations and drivers at 
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA) 
seem to be more up to date than some info-pages of the Community documentation.

Hope it works.

---

### Post by mayurdange on 2010-11-29
run this....

```
echo 100> /sys/devices/virtual/backlight/nvidia_backlight/brightness
```

if your brightness lowers.. then my fix should for you..
[I found that default max brightness sets it to 44000 but for MB 7,1 it was 1000]

so just changed the value 44000 to 1000 line #548 in /var/lib/dkms/nvidia_bl/0.17.3/source/nvidia_bl.c

```
static const struct machine_quirks apple_quirks_320m __initdata = {
	.dev_id		= PCI_ANY_ID,
	.max_level	= 1000
};
```

and recompile the kernel module .. it worked!!

for the rest of us..... (who don't want to compile..)
i have attached my /var/lib/dkms/nvidia_bl/0.17.3 folder contents
just find the nvidia_bl.ko and replace or insmod it as,
```
$ sudo insmod nvidia_bl.ko
```
you may need to remove old module first..
```
sudo rmmod nvidia_bl
```
:popcorn:

---

### Post by mac user on 2010-12-16
The same problem with my macbook 7.1 , has anybody solved this problem with the brightness control? :(

---

### Post by caith_sit on 2010-12-23
Mayurdange you are a genius!!! I changed manually the value to 100 and it did worked, now... can I ask you how I recompile the module??

---

### Post by vickoxy on 2011-03-21
Hi,
i still have brightness adjustment problems (F1-F2). I have MacBook Pro 7.1 and Ubuntu 10.04 64bit. I installed Ubuntu following this guide:
[https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)
After i made for the first time: 
```
sudo apt-get remove pommed
sudo apt-get install git-core libdbus-1-dev libconfuse-dev libaudiofile-dev libasound-dev libpci-dev libdbus-glib-1-dev libglade2-dev libgtk2.0-dev libx11-dev libxext-dev libxpm-dev
git clone git://git.debian.org/git/pommed/pommed.git
cd pommed
make 
```

I had keyboard and screen light working. But after few restarts, and - i think - after i activated nvidia drivers, i can´t set up brightness any more-it stays always on the 100%.

I followed instructions on this forum, but nothing helps me. Anyone knows how to fix this?

---

