---
title: "Fresh Install - now what?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by tekknique on 2007-03-26
Hey Guys and Gals

I finally decided to test out this Linux phenomenon and after about an hour, I think it's installed.   I have XP Pro / Dual Boot going with Ubuntu 6.06 LTS Live CD (The CD is about a year old or so).  I popped in the CD and installed it on the secondary hard drive.  I got some error the first time "Ubuntu kernel panic - not synching:  IO-APIC + Timer doesn't work" but I reinstalled with 'noapic' as suggested by someone in here and it booted up without a problem.   Although I need to read more about Linux and how it works and differs from XP, I had some general questions:

I restarted and I am at the desktop but I cannot get online.  Do I have to install the NIC?  I went into System > Administration > Device Manager > MCP51 Ethernet Controller > Networking Interface shows the Vendor, Device as 'unknown'.    In fact, 90% of the devices are unknown.  

I built this system about a week ago and here are the specs:

Board:  Asus M2NBP-VM CSM
BIOS:  Phoenix Technologies, LTD AUS M2NBP-VM CSM ACPI BIOS Revision 0201 08/21/2006
Processor:  AMD Athlon 64 X2 Dual Core 4200+
Memory:  1GB
Network Adapter:  NVIDIA nForce Networking Controller
Lite-On DVD Burner
LG CD-RW

I got this information by going into XP which is able to get online and works perfectly. 

1:  Do I need to install each device / drivers in Ubuntu?
2:  Is it normal for XP to not see my secondary hard drive now since it has Linux installed on it? (Device Manager sees it but 'My computer' does not allow me to go into anymore)

---

### Post by Bachstelze on 2007-03-26
1. No, at the very worst, you'll need to install only one or two of them but most of the time, nothing will be needed.
2. Yes, Windows cannot natively read Linux partitions but there are tools around to enable it, google for "ext2ifs".

---

### Post by zvacet on 2007-03-26
What kind of modem do you have?Did Ubuntu recogized it?It is normal for Windows not to see linux partition(drive),and that mean you don´t have direct access to it from Windows.Butthere are ways to access Windows from Ubuntu(even without reboot).

---

### Post by tekknique on 2007-03-26
Thanks for help.   I guess I am a little lost on the installation part.  I thought the LiveCD would automatically recognize my devices and install them.   I am assuming it didn't have the proper drivers for the network card.  I have the NVIDIA nForce network card installed on the desktop but how I go about installing it?  I only have Internet Access from my laptop or if I boot up XP from my desktop.   I am very new for Linux so does this require putting in codes in Terminal or is there an easier way?   Thanks again.....

---

### Post by Bachstelze on 2007-03-26
Before you do anything, open a terminal and do

```
sudo ifconfig -a
```

then paste what you get.

---

### Post by arron on 2007-03-26
You have a recent machine with a dual core.  Get a recent CD with newer drivers if you are only going to play with the live cd.  Try the latest 6.10 cd, or in a few weeks 7.04.  You NIC might not be supported on that version of 6.04, and since you cant get to the net to update, it would be a problem to update the drivers (kernel).  You can borow a usb nic or even a pci card to connect to the web, update then it should work.  Or download the recent linux kernel, put it on a usb stick and install with 

$ dpkg -i ubuntupackage.deb

As well some things do not load for some reason with the live CD, but run great after its fully installed.

I assume this is a NIC with a CAT 5 cable or wire (i mean its not wireless)?  The 64 bit ubuntu might be a option as well, but pros and cons with it.  For a newbie stick with the x86 version.

But before this, run the ifconfig... Great idea first!

Welcome to the Ubuntu community!

---

### Post by tekknique on 2007-03-31
Ok - I can try those options.  I did the ifconfig command and it came back with a series of information (kinda like ipconfig in XP).  I saved it onto a document in Ubuntu - plugged in my USB card and dragged it there.   I then plug my USB card into XP and it doesn't find the file.  Without a network connection, how can I get this information to XP (without having to type the whole thing).

Additionally, if I wanted to go with the newer CD, do I download to XP - then burn that to a CD then reinstall from scratch?   Do you think that will do it?    Thanks again for the help.

---

