---
title: "MacbookPro running hazardously hot under Oneiric"
date: 2011-11-03
forum: Apple Hardware Users
---

### Post by Lars Noodén on 2011-11-03
I have a MacBookPro8,2 which runs way too hot under Oneiric.  A second problem is that the fans don't run even when the machine does get hot.  A third problem is that the output from /usr/bin/sensors doesn't seem to be reliable.

Are there any known fixes or work-arounds?  What is the cause of it running too hot?  OS X runs cool on the same hardware.

---

### Post by LinuxFan999 on 2011-11-03
> **Lars Noodén said:**
> I have a MacBookPro8,2 which **runs way too hot under Oneiric.**  A second problem is that **the fans don't run** even when the machine does get hot.  A third problem is that the output from /usr/bin/sensors doesn't seem to be reliable.

Are there any known fixes or work-arounds?  **What is the cause of it running too hot?**  OS X runs cool on the same hardware.
1. Oneiric consumes more power than earlier versions of Ubuntu.
2. The fans are actually always on, but they usually run at a low speed, which is why you can't hear them.
3. Macs, in general, do tend to run hotter then regular PCs, especially the iMac and the 17 inch macbook pro. They both get incredibly hot, even when idle. Two good solutions would be:

1. Install LXDE, and use that instead of Unity, since LXDE uses less resources.
2. Prop up the rear of the laptop using a small objects under the rear feet of the laptop.

Which  size Macbook pro do you have? 13inch, 15inch, or 17inch?

Remember, do not put your Laptop on your lap.

---

### Post by luckylud on 2011-11-03
Have a look on ubuntu mac pages :  
[https://help.ubuntu.com/community/CategoryMac#List_of_pages_in_CategoryMac](https://help.ubuntu.com/community/CategoryMac#List_of_pages_in_CategoryMac)

Several points to check, in particular the modules coretemp, applesmc
lsmod|grep coretemp
coretemp

The macfanctld package is needed to control the 2 fans, you can install it from mactel ppa depot.
The 11.10 mactel ppa is not out, add the natty ppa with this :
sudo [COLOR=#000000]apt-add-repository 'deb [http://ppa.launchpad.net/mactel-support/ppa/ubuntu](http://ppa.launchpad.net/mactel-support/ppa/ubuntu) natty main'

[/COLOR]

---

### Post by Lars Noodén on 2011-11-04
> **LinuxFan999 said:**
> 1. Oneiric consumes more power than earlier versions of Ubuntu.
2. The fans are actually always on, but they usually run at a low speed, which is why you can't hear them.
3. Macs, in general, do tend to run hotter then regular PCs, especially the iMac and the 17 inch macbook pro. They both get incredibly hot, even when idle. Two good solutions would be:

1. Install LXDE, and use that instead of Unity, since LXDE uses less resources.
2. Prop up the rear of the laptop using a small objects under the rear feet of the laptop.

Which  size Macbook pro do you have? 13inch, 15inch, or 17inch?

Remember, do not put your Laptop on your lap.

It's a 15"

#3 above it the problem I have.  Ubuntu runs hot but the same machine runs cool under OS X.

---

### Post by Hatsune Miku on 2011-11-04
> **Lars Noodén said:**
> It's a 15"

#3 above it the problem I have.  Ubuntu runs hot but the same machine runs cool under OS X.

Oh Hai,

Are you booting with the EFI boot loader or the BIOS bootloader?

Also, do you have Macfanctld running on the system?

---

### Post by Lars Noodén on 2011-11-05
I'm booting from the EFI bootloader via rEFIt.

Macfanctld is not installed.

Edit: I'm not finding macfanctld in the repositories, but I can control the fan speed manually.

---

### Post by Hatsune Miku on 2011-11-05
> **Lars Noodén said:**
> I'm booting from the EFI bootloader via rEFIt.

Macfanctld is not installed.

Edit: I'm not finding macfanctld in the repositories, but I can control the fan speed manually.

The operating system is supposed to control the fan speeds, through SMC commands. OS X does this automatically, and Linux obviously doesn't control systems fans... so yeah, its basically the EFI Firmware

---

### Post by majortom67 on 2011-11-18
If I was in you I would add the Mactel PPA repository and then the macfacltd package. Adding "coretemp" in /etc/modules shoul be useless as from 11.10.
I had a 6,2 MacBook Pro (i5/2,4 Ghz 1st gen) and worked very welle. Now I have a 8,2 MacBook Pro (Late 2011I and I'm in trouble.

---

### Post by alexmurray on 2011-11-19
> **Hatsune Miku said:**
> The operating system is supposed to control the fan speeds, through SMC commands. OS X does this automatically, and Linux obviously doesn't control systems fans... so yeah, its basically the EFI Firmware
This is wrong - the SMC on MacBook's is a dedicated piece of hardware which controls the fans automatically without the intervention of the OS - so either under OSX or Ubuntu or even Windows the SMC should spin up the fans once the temperature gets high all by itself without the OS getting involved - for me (on my MBP5,1) it doesn't happen until CPU temp is over about 80C - but note there is some hysteresis and averaging across the different temperatures from what I have observed so it doesn't spin up straight away.

Yes in general both Ubuntu and Windows seem to run a bit hotter, but the SMC should still eventually spin the fans up to cool it down. If your CPU temp is getting to say 85C or more and the fans still aren't automatically spinning up, it could the the SMC needs a reset (this can even happen under OSX so its not a Ubuntu problem) - see here for more info [http://support.apple.com/kb/ht3964](http://support.apple.com/kb/ht3964)

---

