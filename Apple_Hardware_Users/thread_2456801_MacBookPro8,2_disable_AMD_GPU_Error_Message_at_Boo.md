---
title: "MacBookPro8,2 disable AMD GPU Error Message at Boot"
date: 2021-01-20
forum: Apple Hardware Users
---

### Post by keamas2 on 2021-01-20
Hello.
I have a old MacBookPro8,2 and I didn't want to recycle it so I installed Linux.
This MacBookPro8,2  (Apple MacBook Pro 15-Inch "Core i7" 2.2 Late 2011) Uses a dual graphics processors an AMD Radeon HD 6750M with 512 MB of dedicated GDDR5 memory and an Intel HD Graphics 3000 graphics processor. The AMD Radeon HD 6750M is broken and after a while the system crashes.
So I deactivated the AMD GPU that the system only uses the Intel HD Graphics 3000.


To do this I changed this two files, for more details see below. 



[LIST]
[*] /etc/default/grub
[*] /etc/grub.d/10_linux
[/LIST]




Everything workes fine and it seems the sestem uses the Intel GPU like it should.


The only thing is, when I boot up the System I get this messages:
Is there any way to get rid of this messages?
Or is there any better way to deactivate the AMD GPU?
[ATTACH=CONFIG]287773[/ATTACH]



```
sudo nano /etc/default/grub


#Search:
GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash“
#Replace
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0"


sudo nano /etc/grub.d/10_linux


#insert before: echo "	insmod gzio" | sed "s/^/$submenu_indentation/"
echo "	outb 0x728 1" | sed "s/^/$submenu_indentation/"
echo "	outb 0x710 2" | sed "s/^/$submenu_indentation/"
echo "	outb 0x740 2" | sed "s/^/$submenu_indentation/"
echo "	outb 0x750 0" | sed "s/^/$submenu_indentation/"


sudo update-grub

```


[https://orville.thebennettproject.com/articles/installing-ubuntu-14-04-lts-on-a-2011-macbook-pro/](https://orville.thebennettproject.com/articles/installing-ubuntu-14-04-lts-on-a-2011-macbook-pro/)


```
admin@MacBookPro:~$ inxi -G
Graphics:
  Device-1: Intel 2nd Generation Core Processor Family Integrated Graphics 
  driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1440x900~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 3000 (SNB GT2) 
  v: 3.3 Mesa 20.2.6 
  
admin@MacBookPro:~$ sudo dmidecode -s system-product-name         
MacBookPro8,2





```

---

### Post by yancek on 2021-01-20
The thread at the link below to a Mac user forum discusses the issue so I'd suggest reading it.  Don't use Macs myself so...?

I don't think have 2 lines in /etc/default/grub is correct although I don't know that is related to your problem.  Comment one of the:   GRUB_CMDLINE_LINUX_DEFAULT= lines out and test.

---

### Post by howefield on 2021-01-20
Thread moved to the "*Apple Hardware Users*" forum.

---

