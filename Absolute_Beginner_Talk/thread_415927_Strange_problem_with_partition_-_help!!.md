---
title: "Strange problem with partition - help!!"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2007-04-20
Hello

I want to install Ubuntu 7.04 on my desktop computer.

Computer specs:
Dell Dimension XPS 
Intel Pentium 4 3.20 GHz
1042 MB RAM
nVidia Geforce 6800

I want to have Windows XP and Ubuntu - dual boot. When I boot up the live cd it works well, but when I open Gparted strange things happen ... I can't see my partition with Windows on! It is unmounted. I got a harddrive with 300 GB (I have used about 100 GB with Windows). But in Gparted I can only see two 150 discs and it says "Unallocated" **(see the first screenshot)**.

Why is that? Why can't I see my partitons?

I have tried the Gparted live cd - same thing happens. I got a partition manager program in Windows (Paragon Partition Manager) and it shows me my harddrive with NFTS Windows XP partition. The problem is that I can't resize or make new partition in the demo version of the program ...

 I have talked with some other Linux users. They thinks it might be something RAID releated - RAID 01 mirror. I don't know exactly what it is, but I found a interessting thing in "Intel Storage Utility" **(see the second screenshot)**.
I have not changed anything since I got the computer some years ago.

I found this in the Intel help menu:

> Intel(R) Application Accelerator Help
Introduction

Overview. The Intel(R) Application Accelerator is designed to enhance performance on Intel(R) Pentium(R) 4 processor-based systems using the following storage controller(s): Intel(R) 6300ESB Serial ATA RAID Controller (ESB), Intel(R) 82801FR Serial ATA RAID Controller (ICH6R), Intel(R) 82801FR Serial ATA AHCI Controller (ICH6R), and Intel(R) 82801ER Serial ATA RAID Controller (ICH5R). A storage controller is a hardware device that controls all functionality associated with the hard drives connected to it. The Intel Application Accelerator software package is comprised of the following components:



· Intel Application Accelerator Driver

· Intel(R) Storage Utility

· Event Monitor

The Intel Application Accelerator RAID option ROM is packaged separately and is not present on mobile systems. This software module is typically integrated into the system BIOS of the motherboard and allows for the configuration of RAID volumes prior to OS boot.

On systems using ICH5R, this version of the Intel Application Accelerator may be installed. However, ICH6R features that require newer hardware will be disabled within the Intel Storage Utility.

Software installation is fully automated for all supported chipsets and operating systems. Please refer to the 'System Requirements' page of this help file for a list of supported operating systems.

Desktop Features. On systems using ICH6R, this version of the Intel Application Accelerator supports the following features:


· Intel(R) Matrix RAID Technology. The ability to create, manage, and use two independent RAID volumes within a single array.

· Multiple Arrays. The ability to create two independent, two hard-drive RAID arrays on any of the four Serial ATA ports.

· RAID Spare. The ability to mark one or more hard drives as the destination drive(s) for any needed automatic rebuilds.

· Advanced Host Controller Interface (AHCI). An interface specification that allows the storage driver to enable advanced Serial ATA features such as Native Command Queuing and Native Hot Plug.

The Scope of This Help File. The purpose of this help file is to provide a basic overview of the Intel Application Accelerator software package and its use. Below is a list of the topics included in this help file with a brief description of each topic:



· Introduction. Provides a component and feature overview of the software package.

· System Requirements. Lists the minimum hardware and software requirements for running this software successfully.

· Intel Application Accelerator Driver. Provides a basic description of the driver and how it interacts with the other components of the software package.

· Intel Storage Utility. Describes the features of this component and provides basic instructions for its use.

· RAID Overview. Provides an introduction to RAID technology and how it applies to the Intel Application Accelerator software package.

· Event Monitor. Describes the functions of this component and use of the Intel Application Accelerator tray icon.

· RAID Volume Restoration. Provides step-by-step procedures for recovering RAID volumes for typical scenarios.

· Glossary. Defines the terminology associated with this software package.


For a complete user's manual, visit [http://support.intel.com/support/go/iaa/kb_r.htm](http://support.intel.com/support/go/iaa/kb_r.htm).


* Other brands and names may be claimed as the property of others.

Please. I need help to resize my Windows partition and make a new one for Ubuntu! :confused:

---

### Post by Wikzo on 2007-04-21
Bump!

---

### Post by Wikzo on 2007-04-27
:'(

---

### Post by easyease on 2007-04-27
Are you using the alternative install disc to try and install 7.04? if not i think you may find it easier.

---

### Post by Wikzo on 2007-05-12
No, 'cause my problem is not Ubuntu ... it is to make a partition for Linux (ext3)! :\

---

### Post by psusi on 2007-05-12
You have two hard drives, not one.  They are configured in a fake hardware raid.  You can get this working but it will not be easy.  Start by reading [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).

---

