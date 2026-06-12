---
title: "I have an internet problem..."
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by DarchAengel on 2007-08-08
I have a Dell OptiPlex GX1 computer and I put the newest version of of Ubuntu on it.  I can't seem to get my cable connection to work on it.  I installed an ethernet card on the board and it worked fine but I am trying to get the on-board connection to work instead so as to keep my PCI card slots free.  Any help would be greatly appreciated.

---

### Post by overdrank on 2007-08-08
> **DarchAengel said:**
> I have a Dell OptiPlex GX1 computer and I put the newest version of of Ubuntu on it.  I can't seem to get my cable connection to work on it.  I installed an ethernet card on the board and it worked fine but I am trying to get the on-board connection to work instead so as to keep my PCI card slots free.  Any help would be greatly appreciated.

Hi can you post the out put of the command in the terminal 
```
lspci
```
located under application, accessories, terminal. And tell us what the model of the nic card you just installed is?

---

### Post by DarchAengel on 2007-08-08
This is what came out:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0e.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

As far as the PCI card I have in at the moment it is a generic card I had in a computer that I had laying around.  Not sure how to find out the make/model

---

### Post by overdrank on 2007-08-08
> **DarchAengel said:**
> This is what came out:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
[COLOR="Red"]00:0e.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)[/COLOR]
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

As far as the PCI card I have in at the moment it is a generic card I had in a computer that I had laying around.  Not sure how to find out the make/model

Ok I highlighted the nic card and I believe it is the one you have install (pci) and there is no other nic card showing on the system. If you are familiar with bios on you system you might check and see if the onboard nic is disable. It is not showing up. If you can find it and enable it you might be lucky! :popcorn:

---

### Post by DarchAengel on 2007-08-08
Thanks, it was the BIOS.  You have been a lifesaver.  While we are at it I have few other problems.  First is that I have been playing with the screen resolutions to fit my monitor and all of a sudden I have this small UPC-style bar code that appeared in the upper lefthand corner.  Where did that come from and how do I get rid of them?  Also how do I interface with linux while on my Mac?

---

### Post by overdrank on 2007-08-08
> **DarchAengel said:**
> Thanks, it was the BIOS.  You have been a lifesaver.  While we are at it I have few other problems.  First is that I have been playing with the screen resolutions to fit my monitor and all of a sudden I have this small UPC-style bar code that appeared in the upper lefthand corner.  Where did that come from and how do I get rid of them?  Also how do I interface with linux while on my Mac?

Ok as far as the graphics, I had a similar graphics card in a laptop of mine and they are not real powerful. You can search here and see if you find something that might help
[http://ubuntuforums.org/search.php?searchid=25100278](http://ubuntuforums.org/search.php?searchid=25100278)
As far as interfacing with the Mac I am assuming you are talking about networking and I would assume it would be the same as windows. But I have no experience in that area with Mac.

---

### Post by DarchAengel on 2007-08-08
I will read through the threads and see if I can find some help.  Thanks again.  I have a question that I almost forgot.  I have been trying to install Adobe acrobat.  I am opening the installer using terminal.  The first thing it asks is where to put the installation.  I am not used to the file structure of linux so I am a little lost as to where to install and how to tell it where to install.  Sorry for all the questions.  I really appreciate it.

---

### Post by overdrank on 2007-08-08
> **DarchAengel said:**
> I will read through the threads and see if I can find some help.  Thanks again.  I have a question that I almost forgot.  I have been trying to install Adobe acrobat.  I am opening the installer using terminal.  The first thing it asks is where to put the installation.  I am not used to the file structure of linux so I am a little lost as to where to install and how to tell it where to install.  Sorry for all the questions.  I really appreciate it.

Ok that is enough questions on this thread:lolflag: A quick SEARCH of the forums lead me to this link
[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)
Good luck! :popcorn:

---

