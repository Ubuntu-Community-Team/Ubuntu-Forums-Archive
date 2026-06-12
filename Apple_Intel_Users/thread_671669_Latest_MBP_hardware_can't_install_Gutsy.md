---
title: "Latest MBP hardware can't install Gutsy?"
date: 2008-01-18
forum: Apple Intel Users
---

### Post by ssnape on 2008-01-18
I have a brand new MacBookPro.  I downloaded the AMD64 alternate disk as per normal for Core 2 Duo apple boxes.  After spinning a long time on install it says it can figure out what my graphics configuration is.  It is a ..
GeForce 8600M GT:

  Chipset Model:	GeForce 8600M GT
  Type:	Display
  Bus:	PCIe
  PCIe Lane Width:	x16
  VRAM (Total):	256 MB
  Vendor:	NVIDIA (0x10de)
  Device ID:	0x0407
  Revision ID:	0x00a1
  ROM Revision:	3175
  Displays:
Color LCD:
  Display Type:	LCD
  Resolution:	1440 x 900
  Depth:	32-bit Color
  Built-In:	Yes
  Core Image:	Hardware Accelerated
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
Display Connector:
  Status:	No display connected

I tell it to continue with low graphics and it freezes and never continues.  I try again and tell it is NVIDIA and it freezes.   Has anyone got the latest and greatest MBP to install gutsy?  If so, how hid you do it?

Here is my top level sys description:

  Model Name:	MacBook Pro
  Model Identifier:	MacBookPro3,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2.4 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	4 MB
  Memory:	2 GB
  Bus Speed:	800 MHz
  Boot ROM Version:	MBP31.0070.B05
  SMC Version:	1.16f10
  Sudden Motion Sensor:
  State:	Enabled



  Vendor:	Intel
  Product:	ICH8-M AHCI
  Speed:	1.5 Gigabit
  Description:	AHCI Version 1.10 Supported

Hitachi HTS722020K9SA00:

  Capacity:	186.31 GB
  Model:	Hitachi HTS722020K9SA00
  Revision:	DC4AC77A
  Serial Number:	071122DP0410DTG6ZMKP
  Native Command Queuing:	Yes
  Queue Depth:	32
  Removable Media:	No
  Detachable Drive:	No
  BSD Name:	disk0
  Mac OS 9 Drivers:	No
  Partition Map Type:	GPT (GUID Partition Table)
  S.M.A.R.T. status:	Verified
  Volumes:
Macintosh HD:
  Capacity:	34.88 GB
  Available:	17.64 GB
  Writable:	Yes
  File System:	Journaled HFS+
  BSD Name:	disk0s2
  Mount Point:	/
Una:
  Capacity:	104.49 GB
  Available:	56.9 GB
  Writable:	Yes
  File System:	Journaled HFS+
  BSD Name:	disk0s3
  Mount Point:	/Volumes/Una

---

### Post by ssnape on 2008-01-19
Got the install to work by setting VGA options to 1440x900 on first screen before hitting install.

---

