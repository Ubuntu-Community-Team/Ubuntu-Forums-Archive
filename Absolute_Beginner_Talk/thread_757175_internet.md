---
title: "internet"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by pixiesnoot on 2008-04-16
I just got ubuntu onto my computer, and the internet isn't really working. I'm connected to the internet, same one as with windows, and I'm unable to load a single page. It'll just keep trying forever, whereas firefox on windows works fine

---

### Post by lbotha on 2008-04-16
Are you connected directly to the internet/through a proxy server?

---

### Post by pixiesnoot on 2008-04-16
I am not quite sure. I clicked on a button at the top left of the screen, hit "Linksys" because that's what my wireless connection is, then later it said connected. Apparently it didn't work

---

### Post by lbotha on 2008-04-16
Look at the settings for "Network settings" for firefox under windows and make sure it is the same.

---

### Post by Tom--d on 2008-04-16
Ah wireless... 

In Terminal, type and paste the outcome:

```
lspci
```
```
lsusb
```

---

### Post by crjackson on 2008-04-16
> **pixiesnoot said:**
> I am not quite sure. I clicked on a button at the top left of the screen, hit "Linksys" because that's what my wireless connection is, then later it said connected. Apparently it didn't work

Do you have wireless encryption activated in the router?

---

### Post by pixiesnoot on 2008-04-16
> **crjackson said:**
> Do you have wireless encryption activated in the router?

no

---

### Post by pixiesnoot on 2008-04-16
> **Tom--d said:**
> Ah wireless... 

In Terminal, type and paste the outcome:

```
lspci
```
```
lsusb
```

i typed in each, now wat? I got a long lsting of words out of each

---

### Post by Roque2 on 2008-04-16
He asked you to paste the output of each command in a reply

---

### Post by pixiesnoot on 2008-04-16
k, but its really long. that'll be a lot of typing copy and paste didn't work. I need to go back into windows to get onto this site

---

### Post by northern lights on 2008-04-16
In the terminal, you can mark with the mouse and either navigate to "Edit > Copy", or use "Shift+Ctrl+V"...

---

### Post by pixiesnoot on 2008-04-16
k, here it is:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

pixiesnoot@pixiesnoot-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
pixiesnoot@pixiesnoot-desktop:~$ lsusb
Bus 002 Device 005: ID 046d:c513 Logitech, Inc. 
Bus 002 Device 004: ID 03f0:5511 Hewlett-Packard 
Bus 002 Device 003: ID 0830:0061 Palm, Inc. 
Bus 002 Device 002: ID 046d:0a0b Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 13b1:000d Linksys 
Bus 001 Device 001: ID 0000:0000  
pixiesnoot@pixiesnoot-desktop:~$ 

Sorry that it took so long

---

### Post by Tom--d on 2008-04-16
I see you have a Linksys Wireless usb thing... ? 

Linksys + Ndiswrapper + Linksys Driver = Wireless (maybe not on all models tho)

Download Ndiswrapper:
[Ndiswrapper-common]("http://ge.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb")
[ndisgtk]("http://ge.archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.6-0ubuntu3_all.deb")
[Ndiswrapper-utils-1.9]("http://packages.ubuntu.com/gutsy/ndiswrapper-utils-1.9")

Install them all and then you will see Windows Wireless Drivers under > System > Admin > Windows WIreless Drivers

Now, you need your driver for your wireless. 
Did you get a disk with the Linksys wireless thingy?

If so, get the CD. On the cd there should be a folder called 'driver' (or something like that) and in there should be a .sys file and a .inf file. Get them both and but them in a folder on your Desktop.

Now in Windows wireless drivers, locate your .inf file and click install.

Then wireless should work :)
In the network settings connect to your access point and any encryption needed and your sorted :)

---

### Post by pixiesnoot on 2008-04-16
great, i don't have the cd. I got the wireless thing from a friend, and I don't have the cd. any other ways to make this work, or will i need that cd?

---

### Post by Tom--d on 2008-04-16
You could download the drivers from Linksys website. 

Find the model of it and find the drivers. (google it ;) )

---

### Post by pixiesnoot on 2008-04-16
> **Tom--d said:**
> I see you have a Linksys Wireless usb thing... ? 

Linksys + Ndiswrapper + Linksys Driver = Wireless (maybe not on all models tho)

Download Ndiswrapper:
[Ndiswrapper-common]("http://ge.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb")
[ndisgtk]("http://ge.archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.6-0ubuntu3_all.deb")
[Ndiswrapper-utils-1.9]("http://packages.ubuntu.com/gutsy/ndiswrapper-utils-1.9")

Install them all and then you will see Windows Wireless Drivers under > System > Admin > Windows WIreless Drivers

Now, you need your driver for your wireless. 
Did you get a disk with the Linksys wireless thingy?

If so, get the CD. On the cd there should be a folder called 'driver' (or something like that) and in there should be a .sys file and a .inf file. Get them both and but them in a folder on your Desktop.

Now in Windows wireless drivers, locate your .inf file and click install.

Then wireless should work :)
In the network settings connect to your access point and any encryption needed and your sorted :)

umm, windows doesn't know what to do with those files. and ubuntu's internet isn't working, so that wouldn't work. Sorry that I'm responding so late, i had to go to taekwondo class. But i got the driver

---

### Post by northern lights on 2008-04-17
Don't you have a USB/flash drive, an external HDD or an empty CD and a burner? All three devices could be used to transfer the driver from your windows to your Ubuntu.

Besides that, you can mount your NTFS partition(s) in Ubuntu. Actually it should do so out of the box. If it doesn't, it's most likely cause of an unclean Windows shutdown. Should that be the case, boot Windows (login screen suffices) and do a clean shutdown. Reboot into Ubuntu, NTFS partition(s) should be mounted...

---

