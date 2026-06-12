---
title: "first time installing linux on mac"
date: 2012-11-08
forum: Apple Hardware Users
---

### Post by kokoshmusun on 2012-11-08
My wife has an oldish Mac and is sick of the Apple lockdowns, etc.  Seems like the newer Apple OSs can't even be run on her laptop.  So instead of trying (with possible failure) to update her Mac OS or paying an arm and a leg to get new Mac hardware, she's going to install ubuntu (she already has another smaller netbook with ubuntu on it and she's very happy). 
   But we've never done this and I wanted to check whether this is as simple as installing ubuntu on other hardware (which I find a breeze). 
   So do I just try to boot the Mac from a USB and rest is the same, or what?
   Here are the specs of the laptop. 
   Thanks in advance. 

Model Name:        MacBook
  Model Identifier:        MacBook4,1
  Processor Name:        Intel Core 2 Duo
  Processor Speed:        2.4 GHz
  Number Of Processors:        1
  Total Number Of Cores:        2
  L2 Cache:        3 MB
  Memory:        2 GB
  Bus Speed:        800 MHz

---

### Post by 2F4U on 2012-11-08
I have the same model. Mine doesn't boot from USB, but boots fine from CD. Press the Alt key during boot and you will get to a boot menu and will be able to select the boot medium.
I installed 12.04 and didn't try 12.10. 12.04 runs very good on that model.
You need to decide whether you want EFI or go for MBR. EFI is not easy to get to work on this model, so I choose MBR. I went on to create a msdos partition table, so I deleted the whole OSX installation (no dual boot). From then on, the installation is the same as for anything else.

---

