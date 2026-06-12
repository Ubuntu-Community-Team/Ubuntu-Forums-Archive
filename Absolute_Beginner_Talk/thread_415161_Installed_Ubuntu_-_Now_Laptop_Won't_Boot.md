---
title: "Installed Ubuntu - Now Laptop Won't Boot"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by idahogie on 2007-04-20
It won't boot from either the new install or from a Live CD.  The normal startup things happen - the display goes blank after 'Checking NVRAM...'  I've reset the BIOS to default - no good.

I was using a CD I got from Ubuntu Linux Bible, but I've also downloaded 7.04.  Nothing works.

It's a brand new computer with no other OS or partition, and the Live CD worked great before I installed.

---

### Post by LaRoza on 2007-04-20
What OS did it have on it before

What are the laptops specifications?

It sounds like a BIOS problem.

---

### Post by Terl on 2007-04-20
> **idahogie said:**
> It won't boot from either the new install or from a Live CD.  The normal startup things happen - the display goes blank after 'Checking NVRAM...'  I've reset the BIOS to default - no good.

What does "reset to default mean"?  To run the live cd you need to have it set the cd first in the boot order.

> I was using a CD I got from Ubuntu Linux Bible, but I've also downloaded 7.04.  Nothing works.

It's a brand new computer with no other OS or partition, and the Live CD worked great before I installed.

When you did the install you did install grub (the bootloader), right?  Also, do you have the specs of the computer?  That is helpful too.

---

### Post by idahogie on 2007-04-20
Here are the specs:

MSI MS-1042 (171772) Turion&#8482; 64 X2 Performance Notebook, 17" WXGA/WSXGA+ Glossy LCD, NVIDIA® GeForce&#8482; Go 7600 256MB GraphicsAMD, Turion&#8482; 64 X2 TL-60 2.0GHz, Socket S1, 2x128KB L1 + 2x512KB L2 cache, 35W, 90nm, OEM 
CRUCIAL, 2GB (2 x 1GB) PC2-5300 DDR2 667MHz SDRAM SODIMM, CL5, Non-ECC 
HITACHI, 80GB Travelstar 7K100, 7200-RPM, 8MB cache, 9.5mm, SATA, OEM 
OPTICAL DRIVE, Super-Multi DVD±RW Optical Drive (Included) 
NOTEBOOK ACCESSORIES, Built-in 4-in-1 MMC/SD/MS/MS Pro Media Card Reader (Included) 
MICROSTAR, MP54GBT2 Combo Wireless-G + Bluetooth Adapter, IEEE 802.11b/g 11/54Mbps, MiniPCI (for MSI n/b only) 
LOGITECH, LX5 Cordless Optical Mouse, USB, PS2, Black 
SOFTWARE, No Operating System (Choose or subject to Limited Support) 
SOFTWARE, Pre-Installed OpenOffice.org 2.0 Suite (Purchase of operating system is required) 
MICROSTAR, Extended 2-Year Warranty for MSI Notebook Barebones

It's brand new - no OS installed.

The BIOS reset is an option in the BIOS menu to reset all options to default.  The CD drive is the first in the boot order.  I had only played with a couple as I tried to troubleshoot this problem.

The Live CD worked great.  I had mouse, sound, wireless, all the applications worked great.  Then I ran the desktop install, then rebooted - and nothing.  Now I can't start it up.

---

