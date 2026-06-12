---
title: "cat /proc/pci"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by troughton on 2006-09-15
I am wanting to know where to get the data i would get with the cat /proc/pci i have tryed lspci and cat /proc/pci/data and nether give me the information that is givin with the cat /proc/pci i am trying to learn linux and the refrence materal i am using gives the comand as cat /proc/pci can some one tell me what the comand is on ubuntu please

---

### Post by Brunellus on 2006-09-15
what's wrong with 

cat /proc/pci

?

all you're doing is conCATenating the data from that part of the filesystem (/proc/pci) to standard output.

Since you're likely to get much more data than you'll want to deal with, you should pipe the result to less:

cat /proc/pci | less

which will allow you to page through the data one screen at a time.  when you're done, just hit q.

---

### Post by troughton on 2006-09-16
I am looking at the lpi traing corse to increase my knowlage of ubuntu and in there it says to get the qualifcation you must youse cat /proc/pci but when i do cat /proc/pci ubuntu says /proc/pci is a folder and wont give me any data. so all i want to know is where i can get the data from that cat /proc/pci would give you on red hat or mandrake on the ubuntu distro so i can study lpi

---

### Post by Brunellus on 2006-09-16
> **troughton said:**
> I am looking at the lpi traing corse to increase my knowlage of ubuntu and in there it says to get the qualifcation you must youse cat /proc/pci but when i do cat /proc/pci ubuntu says /proc/pci is a folder and wont give me any data. so all i want to know is where i can get the data from that cat /proc/pci would give you on red hat or mandrake on the ubuntu distro so i can study lpi
I believe the bit of the filesystem you want is /proc/bus/pci/devices

so try 

cat /proc/bus/pci/devices | less

---

### Post by troughton on 2006-09-16
what i am looking for is in the web tutorial i am working on and it says :


We'll learn more about the Linux file system in later tutorials in this series, but right now we'll introduce you the /proc filesystem. This is not a real filesystem on disk, but a "pseudo file system" which provides information about the running system. Within this file system, the file /proc/pci contains information about the devices on the system's PCI bus. There has been some discussion about discontinuing this particular file, as the lspci command gives similar information. Run the command cat /proc/pci to see output which will look something like Listing 1.

Listing 1
                    
PCI devices found:
  Bus  0, device   0, function  0:
    Host bridge: Intel Corp. 82845G/GL [Brookdale-G] Chipset Host Bridge 
         (rev 1).
      Prefetchable 32 bit memory at 0xd0000000 [0xdfffffff].
  Bus  0, device   2, function  0:
    VGA compatible controller: Intel Corp. 82845G/GL [Brookdale-G] Chipset 
         Integrated Graphics Device (rev 1).
      IRQ 11.
      Prefetchable 32 bit memory at 0x88000000 [0x8fffffff].
      Non-prefetchable 32 bit memory at 0x80000000 [0x8007ffff].
  Bus  0, device  29, function  0:
    USB Controller: Intel Corp. 82801DB USB (Hub #1) (rev 1).
      IRQ 11.
      I/O at 0x1800 [0x181f].
  Bus  0, device  29, function  1:
    USB Controller: Intel Corp. 82801DB USB (Hub #2) (rev 1).
      IRQ 10.
      I/O at 0x1820 [0x183f].
  Bus  0, device  29, function  2:
    USB Controller: Intel Corp. 82801DB USB (Hub #3) (rev 1).
      IRQ 5.
      I/O at 0x1840 [0x185f].
  Bus  0, device  29, function  7:
    USB Controller: Intel Corp. 82801DB USB2 (rev 1).
      IRQ 9.
      Non-prefetchable 32 bit memory at 0xc0080000 [0xc00803ff].
  Bus  0, device  30, function  0:
    PCI bridge: Intel Corp. 82801BA/CA/DB/EB PCI Bridge (rev 129).
      Master Capable.  No bursts.  Min Gnt=4.
  Bus  0, device  31, function  0:
    ISA bridge: Intel Corp. 82801DB LPC Interface Controller (rev 1).
  Bus  0, device  31, function  1:
    IDE interface: Intel Corp. 82801DB Ultra ATA Storage Controller 
         (rev 1).
      IRQ 5.
      I/O at 0x1860 [0x186f].
      Non-prefetchable 32 bit memory at 0x60000000 [0x600003ff].
  Bus  0, device  31, function  3:
    SMBus: Intel Corp. 82801DB/DBM SMBus Controller (rev 1).
      IRQ 9.
      I/O at 0x1880 [0x189f].
  Bus  0, device  31, function  5:
    Multimedia audio controller: Intel Corp. 82801DB AC'97 Audio 
         Controller (rev 1).
      IRQ 9.
      I/O at 0x1c00 [0x1cff].
      I/O at 0x18c0 [0x18ff].
      Non-prefetchable 32 bit memory at 0xc0080c00 [0xc0080dff].
      Non-prefetchable 32 bit memory at 0xc0080800 [0xc00808ff].
  Bus  2, device   8, function  0:
    Ethernet controller: Intel Corp. 82801BD PRO/100 VE (LOM) Ethernet 
         Controller (rev 129).
      IRQ 9.
      Master Capable.  Latency=66.  Min Gnt=8.Max Lat=56.
      Non-prefetchable 32 bit memory at 0xc0100000 [0xc0100fff].
      I/O at 0x2000 [0x203f].

as this comand dose not work on linx but is part of the lpi 101 exam for the much talked about ubuntu certificate i am asking for your help to get this data in unubntu as cat /proc/bus/pci/data will just give a serise of numbers not the data above

---

### Post by confy on 2008-05-14
Same problem here...
IBM says i can look at PCI carts at /proc/pci but there is not such a file...
/proc/bus/pci/devices gives something else as /proc/pci ...
I guess it's the kernel that choices where to put those files so with upgrading kernel you are upgrading the way of showing /proc/

btw, what you got at LPI exam? Was it hard?

---

