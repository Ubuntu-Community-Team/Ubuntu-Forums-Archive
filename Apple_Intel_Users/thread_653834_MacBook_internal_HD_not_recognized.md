---
title: "MacBook internal HD not recognized"
date: 2007-12-30
forum: Apple Intel Users
---

### Post by juliabel on 2007-12-30
First of all I must apoligize if this question has already benn posted but I searched for it or similars and couldn't find an answer.
I'm trying to install KUbuntu 7.10 (which I believe shouldn't substantially differ from Ubuntu 7.10) from the DVD installer (holdin 'C' while booting). Everything works fine and I'm able to launch the installer from the desktop but when I get to the partition window all my EXTERNAL disks are listed, USBs and FWs but the INTERNAL HD (a 160 Gbyte Samsung) is not recognized.
I then:
- disconnected all peripherals and retried: same result
- partioned the internal HD from Tiger's Disk Utility as Leopard's doesnt permit to create Unix partitions. Retried installation with no results, the internal HD is still not visible regardless it has now Linux partitions - no matter if they should have been erased again...
- installed rEFIt, since the beginning: nothing changed. Choosing the partitioning progrm fromm the startup screen doesn't give much freedom of partitioning.

From Parted, also, the internal HD is not recognized.

What am I doing wrong? On the Mac side, with or without BootCamp everything is a charm.

Many thanks in advance for any advice or solution.

Simon

---

### Post by juliabel on 2007-12-31
And the (partial) answer is...? It doesn't work with 'third parties' Samsung HM160HI but it does work with the OEM 60 Gbyte Fujitsu. So, where is the problem? Samsung's firmware?
Help!

---

### Post by xeth_delta on 2008-01-01
Try starting with the live CD and then run the following commands:
```
sudo fdisk -l
```
post the output here in the thread.
Be **very** careful with the following command, as you could potentially damage your partition table if you do something wrong and save the changes. We'll assume your harddisk is sda:
```
sudo parted /dev/sda
```
You will be presented with a parted prompt:
```
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)
```
Press "p" followed by ENTER. A list with the partitions of the hard disk will be shown. Please post them here. Quit pressing "q" followed by ENTER.

Are any of the partitions you are looking for present in any of the lists?

Xeth

---

### Post by cyberdork33 on 2008-01-02
or just do this command:
```
sudo parted /dev/sda print
```

This will likely not help though as the hardware is not even recognized. There are others with this problem. There is a bug report.
[http://ubuntuforums.org/showthread.php?t=544626](http://ubuntuforums.org/showthread.php?t=544626)

---

### Post by juliabel on 2008-01-02
(sudo fdisk -l):
-> shows prompt command, no results.

(sudo fdisk /dev/hda):
Unable to open 7dev/hda

(sudo parted /dev/sda  - with or wirhout following 'print' option):
Error: Could not stat device /dev/sda - No such file or directory.
Retry/Cancel?

Launching QTParted also shows no partition and asks if maybe I didn't log in as root but I don't think the problem is here as, I've already said, with the OEM 60 Gbyte Fujitsu everything works well.

If other devices are connected (I also have an external 60Gbyte Fujitsu on FW, a 160 Gbyte Maxtor on FW and a WD 250 GByte on USB) thery are ALL recognized and all partitions can be viewed/modified. Pmu reset and multiple PRAM resets have been done. I believe there are some functionalities in these recent hard disk that make Ubuntu incompatible with them (or viceversa) so I finally believe that the bug reported at [http://ubuntuforums.org/showthread.php?t=544626](http://ubuntuforums.org/showthread.php?t=544626), is the same problem I have.

And I'm now afraid as I'm almost surely going to buy a Santa Rosa MB (after January 8th announcements) and report of Ubuntu on that machine are even worst than those on mine. As we do say here in Italy, you can't have a drunk wife together with an empty barrel.

I like a lot Ubuntu but I also don't want to live back Mac OS X buying a PC machine. I think I'll be using it for a while with VMWare.

Thank you for your interesting on my problem. 
Simon

---

