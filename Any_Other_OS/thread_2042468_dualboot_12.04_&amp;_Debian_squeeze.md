---
title: "dualboot 12.04 &amp; Debian squeeze"
date: 2012-08-14
forum: Any Other OS
---

### Post by boregard on 2012-08-14
Hello, I am wanting to install debian squeeze and dual boot with precise 12.04. Would it be best for someone that has never tried Debian to go with network install or jigdo? Any advice will be appreciated. Regards

---

### Post by ratcheer on 2012-08-14
I tried jigdo once; it worked very well. I don't know about netinstall, though.

Tim

PS - Hey, especially since your avatar appears to be the Zig Zag man.

---

### Post by tartalo on 2012-08-15
Unless things have changed since I last checked, Jigdo is not an installation method, but a method for downloading packages from multiple mirrors and create ISO files with them, like for example the netinst ISO.

It is very efficient if you want to keep an up to date copy of the over 9000 CDs of "Debian testing", for example.

---

The netinst ISO contains only what's needed to boot the computer and start the installation process. All the necessary packages will be downloaded during this installation process. It's often used as an installation method when the internet connection is reliable and has a decent bandwidth.

---

### Post by UltimateCat on 2012-08-15
The Netinstall was a nightmare for me and had to abort the installation.
I realized during the install that my system uses the Linksys ( wusb54gc) and I'm wireless.

I installed Debian Squeeze 6.0.5_amd64 again using the cd/dvd ( not netinstall) and had to go into expert mode to allow 20 GB for the Debian install and 1GB for the swap.  Take your time through the installation and know exactly what partition's are dedicated to your 12.04.
 If you make a mistake you'll get the GRUB Rescue mode like I did.

I'm now enjoying the Debian Squeeze 6.0 on my system dual booted with Windows XP Pro.  It's rock solid and very stable.  If you like Ubuntu you will like Debian Squeeze.

I don't recommend Netinstall if your modem is wireless.

---

### Post by boregard on 2012-08-15
Thanks to all for input, think I'll try jigdo. Best Regards

---

### Post by cortman on 2012-08-15
Standard installation image (CD 1) worked great for me. You should have online access during installation, though.

---

### Post by kumoshk on 2013-05-03
So, how did the dual booting turn out? Did you install Debian after Ubuntu? Are they both the same architecture (32/64)?

I prefer the Debian business card install ISO. It downloads practically everything during the install and gives you lots of options (so everything's up-to-date when you're finished). So, you can install from a USB drive without much space. Just use dd to copy it to your USB (i.e. dd if=debian.iso of=/dev/whereverYourUSB is).

Anyway, I'm looking to dual boot Debian (probably 32-bit) and Xubuntu 13.04 64-bit. Feel free to let me know of anything you think is important before I start. I might just try to resize my current Debian root partition to make room for Xubuntu, instead of starting fresh.

---

