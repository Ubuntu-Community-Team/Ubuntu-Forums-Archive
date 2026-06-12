---
title: "Ubuntu 10.04,MacBook Air,USB install"
date: 2010-04-29
forum: Apple Hardware Users
---

### Post by nightfever on 2010-04-29
I've been waiting for the latest Ubuntu so I can try installing it on my MacBook Air. And I have some questions:

1. Can I install it from USB?
2. What version should I download? (Netbook, PPC)
3. Will it work? (touchpad, video acceleration)
4. I also have a Huawei E160E internet USB stick, as I know it was supported in Linux

---

### Post by linuxopjemac on 2010-04-30
Keep an eye on [this site]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages"), for updates regarding your machine.

---

### Post by jmcfarlane on 2010-05-01
I've tried installing an earlier version of Ubuntu to a MacBook Air 2,1 from a USB stick without any luck. If you have a SuperDrive you have more chance of success. (No other USB drive will allow you to boot a MacBook Air.) But even then, I've had little success with the 10.04 beta. [This page]("http://bloggis.se/atte/99928") claims to have got a recent model working with 9.10. 

As for the CD version, despite its size, the Air isn't really a netbook and all MacBook Airs are Intel and not PPC. You should choose 32-bit - or 64-bit if you're feeling adventurous. The alternate CD might be a little safer than the desktop version. 

Good luck!

---

### Post by kosumi68 on 2010-05-01
Booting using grub-efi might be your best option - although also somewhat adventurous: [http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704). There are reports of successful booting from USB.

---

### Post by linuxopjemac on 2010-05-02
I can only give you some links to USB booting, without any guarantee that it works
[http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick](http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick)
[http://mac.linux.be/content/how-create-ubuntu-live-usb-both-mac-and-pc](http://mac.linux.be/content/how-create-ubuntu-live-usb-both-mac-and-pc)

---

### Post by cyberco on 2010-05-03
> **nightfever said:**
> I've been waiting for the latest Ubuntu so I can try installing it on my MacBook Air. And I have some questions:

1. Can I install it from USB?
2. What version should I download? (Netbook, PPC)
3. Will it work? (touchpad, video acceleration)
4. I also have a Huawei E160E internet USB stick, as I know it was supported in Linux

I have 10.04 running on my MacBook Air 2,1 and it runs very smooth. I am actually typing this in 10.04. :) It runs much better than 9.10, it boots faster and feels much snappier. I've written about installing it from CD or USB here:

[https://help.ubuntu.com/community/MacBookAir2-1/Karmic#preview](https://help.ubuntu.com/community/MacBookAir2-1/Karmic#preview)

I got close with the USB route but never finished since the Superdrive route is much easier. I installed the 9.10 alternate and upgraded to 10.04. This broke grub in the MBR so I had to boot a live CD to fix Grub. Turns out that the 10.04 live CD boots prefectly fine without any options (compared to 9.10 which did need specific options).

- Video acceleration works best if you install the latest driver from the nvidia site.
- Native resolution works (1280x800)
- touchpad & wifi work
- Screen brightness and keyboard lights don't out of the box. I got them working on 9.10 with pommed (>=1.30), but although that version is included in 10.04 it doesn't work. Still investigating.
- Sound (speakers and line out) still don't work. I had line out working in 9.10

---

### Post by splendidus on 2010-05-06
Hrrrrm...I'm having a problem with the superdrive version. After about a few minutes of booting from the Live-CD (both Ubuntu 10.04 and an old version of Gparted) the superdrive goes dead and the usb port will not work again without a COPS reset. When booted into OS X the superdrive works fine copying whole data DVD's onto the harddrive... any thoughts?

Edit: Just read the blog post from above...thanks

---

### Post by rileyporter on 2010-05-14
Yes this is fixable by doing a smc reset.  This should fix your USB ports:

Note: Portable computers that have a battery you should not remove on your own include MacBook Pro (Early 2009) and later, all models of MacBook Air, and MacBook (Late 2009).

   1. Shut down the computer.
   2. Plug in the MagSafe power adapter to a power source, connecting it to the Mac if its not already connected.
   3. On the built-in keyboard, press the (left side) Shift-Control-Option keys and the power button at the same time.
   4. Release all the keys and the power button at the same time.
   5. Press the power button to turn on the computer.  Note: The LED on the MagSafe power adapter does not change states or temporarily turn-off when you reset the SMC.



Source:

[http://support.apple.com/kb/HT3964](http://support.apple.com/kb/HT3964)


Hope that helps.... I too am going to try to install 10.04 on my macbook air 2,1

Ril3y

---

