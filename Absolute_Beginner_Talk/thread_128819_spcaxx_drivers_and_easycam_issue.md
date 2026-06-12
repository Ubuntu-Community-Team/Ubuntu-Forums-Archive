---
title: "spcaxx drivers and easycam issue"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-02-12
hi all.

was just wondering, it`s no biggie this but i thought i`d ask anyway, after installing the spcaxx drivers with easycam (which after some compiler issues i managed to fathom) for some reason the driver wont remain installed and i have to run the easycam package every time i reboot and need to use my webcam. is there a way i can get this to 'stick' if u will...thanks


DK

---

### Post by Kimm on 2006-02-12
I take it you ran 'make install' after you compiled the module, and didnt just load it at once?

I am using the same driver you are, and even though it was a while ago that I compiled it, I think I had to do a 'sudo modprobe videodev' before I compiled and installed spca5xx.

The driver is also quite unstable, but I feel that it works better with the 2.6.15.1 kernel (what I am using), if your kernel crashes when using the driver consider changing to this kernel (eighter compile it yourself or PM me to get my build (i686) :) )

---

### Post by DiscoKiller on 2006-02-12
erm not much of that made sense to me. installed a package called easycam from synaptic which installs the driver for me. i tried a while ago to install the driver manuyally but got into all sorts of difficulties so i`ve opted for this method which is as simple as clicking a button. everything works fine once the package has run but once i reboot the driver is no longer installed so i have to re run easycam.

---

### Post by zebzeb on 2006-12-26
I know nothing at all! But I had the same problem with ov511 driver.

Seemed to have installed correct driver manually (following idiot proof instructions very slowly)but all devices said can't connect (dev/video0) or didn't start ect.

Easycam2 installed it and it worked (slight problem on some software but all recognised it)

When I reboot I'm back to square 1. 

I understand this is no help I just thought you'd like to know probably not driver specific.

My chipset is ov518+. Driver is ov511 v2.32, it's definately still dmesg says

[17179599.992000] /home/paul/Desktop/ov511-2.32/ov511_core.c: USB OV518+ video device found
[17179599.992000] /home/paul/Desktop/ov511-2.32/ov511_core.c: Device revision 2
[17179600.004000] /home/paul/Desktop/ov511-2.32/ov511_core.c: Compression required with OV518...enabling
[17179600.064000] /home/paul/Desktop/ov511-2.32/ov511_core.c: Device at usb-0000:00:04.2-2 registered to minor 0
[17179600.064000] usbcore: registered new driver ov511
[17179600.064000] /home/paul/Desktop/ov511-2.32/ov511_core.c: v2.32 : ov511 USB Camera Driver (V4L2 disabled)

but won't work till I run easycam2! After I run easycam I note this is added when I do dmesg:

[17180706.760000] /home/paul/Desktop/ov511-2.32/ov511_core.c: No sensor is detected yet
[17180706.764000] /home/paul/Desktop/ov511-2.32/ov511_core.c: No sensor is detected yet
[17180706.764000] /home/paul/Desktop/ov511-2.32/ov511_core.c: No sensor is detected yet
[17180706.768000] /home/paul/Desktop/ov511-2.32/ov511_core.c: No sensor is detected yet
[17180812.936000] ovcamchip: no version for "struct_module" found: kernel tainted.
[17180812.936000] ovcamchip: no version magic, tainting kernel.
[17180812.948000] /home/paul/Desktop/ov511-2.32/ovcamchip_core.c: v2.32 : OV camera chip I2C driver
[17180813.212000] /home/paul/Desktop/ov511-2.32/ovcamchip_core.c: Camera chip is an OV7620
[17180838.800000] ovcamchip: no version magic, tainting kernel.
[17180838.808000] /home/paul/Desktop/ov511-2.32/ovcamchip_core.c: v2.32 : OV camera chip I2C driver
[17180838.984000] /home/paul/Desktop/ov511-2.32/ovcamchip_core.c: Camera chip is an OV7620

Easycam is certainly doing something I couldn't. Good luck!

---

### Post by Stardust85 on 2008-04-05
I had the same problem and this helped to me:

# rmmod ov511
# modprobe ov511 forceblock=1
# modprobe ovcamchip

( I use Fedora 7)

for *buntu people is is maybe this:
$ sudo  rmmod ov511
$ sudo modprobe ov511 forceblock=1
$ sudo modprobe ovcamchip

But you have to do it EACH TIME you (re)start pc and wanna use webcam, so consider putting it somewere to startup scripts in /etc/...

---

