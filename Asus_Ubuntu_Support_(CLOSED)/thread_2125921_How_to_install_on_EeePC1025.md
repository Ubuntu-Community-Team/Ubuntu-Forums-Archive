---
title: "How to install on EeePC1025?"
date: 2013-03-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dmtparker on 2013-03-15
I just got an Asus EeePC1025 and am having a terrible time trying to replace Windows 7 with Ubuntu. I soecifically wanted the netbook remix (or edition), but I have tried several varieties up to 12.10 desktop. I have tried both booting from a thumbdrive (I get the message, "kernel not found") and an external DVD player (the drive flashes and makes a bit of noise and then shuts down and boots into Windows). I have installed Ubuntu and several devices and used it for years, so I am not a real newbie, but I'm beginning to feel like one. Any ideas on what I am doing wrong? (I created the thumb drive with the UUI program downloaded from Ubuntu), the DVD was burned using Windows 7. Do I need to do something special to make the DVD bootable? If the iso was for a CD and I burned it on a DVD would that be a problem?
Any help appreciated!!

---

### Post by JRV on 2013-03-15
You will be best installing 12.04 LTS from the netboot CD because in supports the non-Pae kernel which is not supported in12.10.
Download "mini.iso" here:

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

I don't know what program to use in Windows to create a bootable disk form an .iso.

Use unetbootin to copy the .iso to the thumb drive.
It is available for both Linux and Windows.

Burning an iso for a CD to a DVD is not a problem.

---

### Post by dmtparker on 2013-03-16
> **JRV said:**
> You will be best installing 12.04 LTS from the netboot CD because in supports the non-Pae kernel which is not supported in12.10.
Download "mini.iso" here:

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

I don't know what program to use in Windows to create a bootable disk form an .iso.

Use unetbootin to copy the .iso to the thumb drive.
It is available for both Linux and Windows.

Burning an iso for a CD to a DVD is not a problem.

This looks great! I will try it and post results.

---

### Post by dmtparker on 2013-03-18
> **JRV said:**
> You will be best installing 12.04 LTS from the netboot CD because in supports the non-Pae kernel which is not supported in12.10.
Download "mini.iso" here:

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

I don't know what program to use in Windows to create a bootable disk form an .iso.

Use unetbootin to copy the .iso to the thumb drive.
It is available for both Linux and Windows.

Burning an iso for a CD to a DVD is not a problem.

I downloaded 'mini' no problem and 'burned' it to USB no problem, booted into USB no problem and ran installer no problem. When I went to actually download Ubuntu - PROBLEM. Just after choosing download mirror (US) I got the dreaded purple screen of death. No activity from either hard drive or WiFi. After 5 min or so, I did Cntl-C which obviously ended the hung program because the sreen went from purple to black (big improvement). Eventually Cntl-Alt-Del got me out. I tried again in 'Expert' mode and it hangs at "Download installer components". If I use http, I get purple screen, if I use ftp, I get an error message that it cannot find the mirror (I just used defaults for everything). I have tried this several times using both WiFi and ethernet connections and even tried the Canadian mirror all with the same results, now What ???!
FWIW, I have a 32G thumb drive. Is there an iso with everything on it that I could burn and maybe avoid this problem?

---

### Post by dmtparker on 2013-03-19
> **dmtparker said:**
> I downloaded 'mini' no problem and 'burned' it to USB no problem, booted into USB no problem and ran installer no problem. When I went to actually download Ubuntu - PROBLEM. Just after choosing download mirror (US) I got the dreaded purple screen of death. No activity from either hard drive or WiFi. After 5 min or so, I did Cntl-C which obviously ended the hung program because the sreen went from purple to black (big improvement). Eventually Cntl-Alt-Del got me out. I tried again in 'Expert' mode and it hangs at "Download installer components". If I use http, I get purple screen, if I use ftp, I get an error message that it cannot find the mirror (I just used defaults for everything). I have tried this several times using both WiFi and ethernet connections and even tried the Canadian mirror all with the same results, now What ???!
FWIW, I have a 32G thumb drive. Is there an iso with everything on it that I could burn and maybe avoid this problem?

The plot thickens. I have managed to download and install Lubuntu 12.04, Xubuntu 12.04 and Ubuntu 12.04. In each case, they worked until I tried to update hardware drivers with the Cedar drm drivers at which point the system freezes and even a reboot is unsuccessful and the system must be re-installed. What now? Are there other sources of graphics drivers? Would 11.04 or even 10.04 be likely to work better? Without the drivers I am stuck with 800 x 600 which is pretty lousy. I even found an Eeebuntu designed for the EeePC's, but it appears to be pretty out of date. Anyone know about it? ?Worth trying?

---

### Post by dmtparker on 2013-03-20
Problem solved! For the benefit of those searching and finding this thread, you need to go here: [http://linuxeeepc.blogspot.com/2012/08/lubuntu-on-eeepc-1025c-with-correct.html](http://linuxeeepc.blogspot.com/2012/08/lubuntu-on-eeepc-1025c-with-correct.html).
Do NOT add the additional drivers via the Lubuntu interface, instead follow the commandline instructions above. Worked like a charm

---

