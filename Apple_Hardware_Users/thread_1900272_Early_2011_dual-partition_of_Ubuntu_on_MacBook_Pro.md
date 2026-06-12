---
title: "Early 2011 dual-partition of Ubuntu on MacBook Pro"
date: 2011-12-25
forum: Apple Hardware Users
---

### Post by adamboettiger on 2011-12-25
I've been reading and trying a variety of things to get this to work without success. 

First problem I came across is that some folks say that 64-bit will work and others say not to mess with it, so would help to get a straight answer.

Here are my specs:


Hardware Overview:

  Model Name:	MacBook Pro
  Model Identifier:	MacBookPro8,1
  Processor Name:	Intel Core i7
  Processor Speed:	2.7 GHz
  Number of Processors:	1
  Total Number of Cores:	2
  L2 Cache (per Core):	256 KB
  L3 Cache:	4 MB
  Memory:	8 GB
  Boot ROM Version:	MBP81.0047.B24
  SMC Version (system):	1.68f98
  Serial Number (system):	C02FR724DH2H
  Hardware UUID:	1220DD0A-290F-5FA2-A908-8EB1A77F16E4
  Sudden Motion Sensor:
  State:	Enabled

Early 2011

Second, I followed the instructions to create a bootable USB flash drive with Ubuntu on it and even with Reit it is not recognizing it.

I've uninstalled Reit and am starting over.

Here's what I want to do:

1. I have a 500GB HD with over 250 GB of free space on it. I'd like to ultimately put Ubuntu on it and have the option to dual boot to OS X Lion or Ubuntu. Will the 64-bit version of Ubuntu work?

2. I seem to be having trouble when I download the ISO file and convert it to IMG and move it to the USB drive. In terminal it appears as if it has all worked correctly, which leads me to believe that I am not properly formatting the USB drive such that it is bootable or recognized. What file format should it be in, and one single partition?

I'd like to boot from the flash drive before I decide to permanently partition the rest of my drive to Ubuntu.

I can't understand why this is so complicated with so many steps involved. Is it an intentional obfuscation to keep out Windows users? I'm a Mac user and am having problems...

Thanks

---

### Post by 2F4U on 2011-12-26
These pages are dedicated to installing Ubuntu on a Mac:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

On the Ubuntu download page, it is recommended to use a CD on a Mac:

> We would encourage Mac users to download Ubuntu Desktop Edition by  burning a CD for the time being. But if you would prefer to use a USB,  please follow the instructions below.

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I had trouble booting from a usb stick on my MacBook and therefore used a CD, which booted without problems. The CD is a liveCD and will allow you to try without installing anything.

---

