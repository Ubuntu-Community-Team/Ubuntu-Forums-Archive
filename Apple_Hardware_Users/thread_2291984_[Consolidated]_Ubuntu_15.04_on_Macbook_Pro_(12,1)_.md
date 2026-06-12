---
title: "[Consolidated] Ubuntu 15.04 on Macbook Pro (12,1) (early 2015 model)"
date: 2015-08-24
forum: Apple Hardware Users
---

### Post by vishal733 on 2015-08-24
I am consolidating all the steps for running Ubuntu 15.04 on Macbook Pro (12,1). And also listing open issues as of now.

Installation steps:
(1) From OSX, create a separate partition/unpartitioned space where you could install Ubuntu
(2) After installation, in order to be able to launch OSX from grub, do the efiboot fix. And add MacOSX in grub entry
[http://www.makeuseof.com/tag/install-linux-macbook-pro/](http://www.makeuseof.com/tag/install-linux-macbook-pro/) [for both (1) and (2)]

(3) After installation, WiFi fix: 
Just download the correct brcm driver, and place it in /lib/firmware/brcm
[http://askubuntu.com/questions/622988/wifi-issues-with-macbook-pro-retina-early-2015-12-2-on-ubuntu-15-04](http://askubuntu.com/questions/622988/wifi-issues-with-macbook-pro-retina-early-2015-12-2-on-ubuntu-15-04)

(4) Keyboard/touchpad [my personal favourite, thanks SicVolo!]
[https://github.com/SicVolo/hid-apple-3.19](https://github.com/SicVolo/hid-apple-3.19) [Download and follow the instllation steps from Readme]
SicVolo has also listed fixes for other kernel versions.

(5) LCD backlight fix:
Do both these steps
(i) [COLOR=#111111][FONT=Consolas]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video.use_native_backlight=1"
[/FONT][/COLOR](ii) Creation of [COLOR=#111111][FONT=Ubuntu]/usr/share/X11/xorg.conf.d/20-intel.conf
[/FONT][/COLOR]Details on this link: 
[http://askubuntu.com/questions/622988/wifi-issues-with-macbook-pro-retina-early-2015-12-2-on-ubuntu-15-04](http://askubuntu.com/questions/622988/wifi-issues-with-macbook-pro-retina-early-2015-12-2-on-ubuntu-15-04)

(6) Temporary fix for disabling shutdown when 0% battery 
[http://askubuntu.com/questions/210623/modify-actions-when-battery-is-critically-low](http://askubuntu.com/questions/210623/modify-actions-when-battery-is-critically-low)

(7) Power Management
Use [https://help.ubuntu.com/community/MacBookPro11-1/utopic](https://help.ubuntu.com/community/MacBookPro11-1/utopic)
Do not refer to sections like WiFi fix, and many other sections. They do not apply to Ubuntu 15.04 on Macbook Pro (12,1)

(8) Screen resolution:
[http://askubuntu.com/questions/472262/adapt-ubuntu-to-a-high-dpi-resolution-screen](http://askubuntu.com/questions/472262/adapt-ubuntu-to-a-high-dpi-resolution-screen)

Open Issues:
(1) [CRITICAL] If battery goes to 0%, the laptop is unable to resume into linux at all. Even recovery methods don't work, and neither does no_console_suspend=1 flag help 
(2) Bluetooth doesn't work
(3) Sleep/resume doesn't work 
(4) Webcam doesn't work
(5) Battery backup obtained on linux is still much lower than that on OSX

In case there are other fixes you guys find, please refer me to them. I can add them here to make our lives easier.

---

### Post by Felipe_Ortiz on 2015-09-23
Hi! some updates:

(1) Keyboard/touchpad
I use Ubuntu Developer and since kernel 4.2.0-6.6 the SicVolo's driver is included!

(2) Bluetooth
I found this [http://www.spinics.net/lists/linux-bluetooth/msg64111.html](http://www.spinics.net/lists/linux-bluetooth/msg64111.html) and if you want to use it, you must do this:

a) Download your linux-image source:
# apt-get source linux-image-$(uname -r)

b) Create a directory and copy this files inside (in this case I use kernel 4.2.0) from downloaded sources:
linux-4.2.0/drivers/bluetooth/btbcm.c
linux-4.2.0/drivers/bluetooth/btbcm.h
linux-4.2.0/drivers/bluetooth/btintel.c
linux-4.2.0/drivers/bluetooth/btintel.h
linux-4.2.0/drivers/bluetooth/btrtl.c
linux-4.2.0/drivers/bluetooth/btrtl.h
linux-4.2.0/drivers/bluetooth/btusb.c

c) Create a Makefile in the same directory with this content:
obj-m=btusb.o

d) Install your kernel headers
# apt-get install linux-header-$(uname -r)

e) Compile with this command
$ make -C /lib/modules/$(uname -r)/build/ M=$(pwd) modules

Now you should have a btusb.ko in your directory, now test it!!!
# rrmod btusb
# insmod ./btusb

If all is ok, now your bluetooth should work, in this case copy module to your modules directory (for autoload)
# cp btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/

(3) GPU switch
To switch between graphics cards see this [https://github.com/0xbb/gpu-switch](https://github.com/0xbb/gpu-switch) please see the warning about MBP 11,3 and use [https://github.com/0xbb/apple_set_os.efi](https://github.com/0xbb/apple_set_os.efi) if is necessary

All this working for me in a MBP 11,5

**Update: **Tim Sammut have an great (and updated) page for tracking all this issues see [here]("https://teamsammut.com/blog/2015/09/apple-macbook-pro-linux-issue-tracking.html")

---

