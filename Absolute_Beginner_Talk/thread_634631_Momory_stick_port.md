---
title: "Momory stick port"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by ziplinedown on 2007-12-07
I have a dell inspiron laptop, and it has a port that i can put a memory stick in, in order to view the pictures on it from my digital camera.  I cannot figure out how to do this with ubuntu.  Any help would be appreciated.

-Zip

---

### Post by scxtt on 2007-12-07
post the output of **sudo lspci** to be sure the device is recognized by the OS ...
then once you put the memory stick in, post **sudo fdisk -l**.

---

### Post by ziplinedown on 2007-12-07
I am not able to do anything using those cammands.  When i enter sudo lspci, it shows a list of devices ( one of which i think is the device im looking for)  Then i enter the stick into the port, and enter the command sudo fdisk-l which gets me here;


Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6817    54757521   83  Linux
/dev/sda2            6818        7113     2377620    5  Extended
/dev/sda5            6818        7113     2377588+  82  Linux swap / Solaris


What do i do to view my pics?

---

### Post by tom957 on 2007-12-08
I had a similar problem with my SD card until I tried this:

```
sudo modprobe -r ehci_hcd
```

---

### Post by ziplinedown on 2007-12-08
This still doesnt work.  Did you find the card in Places, or did it pop up automatically like a cd does?  Maybe there is a package i need to download?
I would really like to view my pics.

---

### Post by scxtt on 2007-12-08
the commands i gave were to give anyone viewing this thread some background on your hardware - since your opening post doesn't help someone who doesn't have that laptop and is already familiar w/ it ...

i'd still post **sudo lspci** ... and post **sudo fdisk -l** again after you've done the **modprobe**  ...

---

### Post by ziplinedown on 2007-12-08
Man,
Im a total n00b, could you maybe explain it to me like you would to a kindergardener?  I just am having a hard time following your posts,  Whats the modprobe?  I still dont know how to view my pictures.
Thanks for the patience
Zip

---

### Post by scxtt on 2007-12-09
Mr. Kernel is the brains of the OS, so you need to tell Mr. Kernel to use a certain module, a tool if you will (think of a hammer, or a saw), in order to use your "memory stick port" ... chances are the piece of hardware that allows you to use the "memory stick port", if even recognized (the **lspci** will inform us of such), doesn't have to proper tool (module) loaded into Mr. Kernel (your helpy-helper) in order to get the job done ... doing the **modprobe** will essentially hand the hammer/saw/screwdriver to Mr. Kernel so that when you put the "memory stick" in the "memory stick port" Mr. Kernel understands what's going on ...

my laptop (a gateway) has a built-in card-reader, but i have Fedora 7 on it (i generally just use Vista on it) -- honestly, i'm not sure if i can read my 2Gb mini card (w/ songs,pics,video) w/o any issue - never really needed to.

---

### Post by ziplinedown on 2007-12-09
I didnt ask for you to be condasending, that little explanation still didnt help at all.  i really dont  care how it works, i just want to know if anyone can tell me what to do, step by step, in order to use my built in card reader.

---

### Post by scxtt on 2007-12-10
that was hardly condescending, you asked to have it explained as if you were a kindergartner ... i've asked you at least twice to post the output of **sudo lspci**, but you appear to refuse to do it ... at this point, no one who owns a"dell inspiron laptop" and has gotten the "momory stick port" working has posted, what do you expect when you're short on details after you've been asked questions to which you don't provide what was asked?

---

### Post by rockinlinux on 2007-12-10
i have been waiting a very long time for MS support in linux and it has still not arrived. I have a toshiba witha card reader and there is no way to get the MS to work...i have tried everything. My best advice to you is either get a USB reader or if it is for your camera just plug the camera into the USB port. I hope someday we can use our MS with linux. I am aware of some driver for the TIFW but i have not heard of anyone getting them to work. Also i have read the 7.04 had these drivers built into the kernel but gusty does not. I gave up a couple months ago trying to get my MS to work in gusty.  good luck!  :)

---

### Post by ziplinedown on 2007-12-10
here is the sudo lspci output

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)



and the fdisk-l

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6817    54757521   83  Linux
/dev/sda2            6818        7113     2377620    5  Extended
/dev/sda5            6818        7113     2377588+  82  Linux swap / Solaris

Im not trying to start an argument, and i do appreciate your help.  This process has been rather frustrating, and its seems that sometimes people on here speak in terms that i cannot even comprehend.

---

### Post by short3000y on 2007-12-10
scxtt; well played, well played!

---

### Post by rockinlinux on 2007-12-10
if it is for your camera (you siad it was) the best thing to do is to plug your camera into the USB port on your computer. Chances are you will not be able to get the memory stick to work with linux, few ever have and it is going to be sometime before there is memory stick support in linux. 

Is the fdisk with the stick in? if so your computer does not even see that the memory stick is there. 

here are your best options, you can still try to fix the memory stick port but i dont think you can becasue the only drivers i know of are texas instrument drvers and you dont have the right hardware.

1)buy a USB card reader.
2)best option- just plug in your camera and get pictures that way.

---

### Post by ziplinedown on 2007-12-10
Yeah, i figured so.  
Ive done it that way before, the thing that i liked about my laptop was that i could get pics from anyones camera, cuz it fits many kinds of cards.  
I hope a future version will supprt this.
Thanks for the help.
-Zip

---

### Post by rockinlinux on 2007-12-10
yeah i liked that about my card reader too but ms does not work. The SD card do though, so you should still be able to use the SD cards in your reader.

---

### Post by scxtt on 2007-12-10
i have a Texas Instruments 5-in-1 card reader in my laptop and i plugged my 2gb mini card into it - didn't work in a plug-n-play sense ... looks like Fedora pulls in the right modules (tif*.ko) but it looks like the reader really doesn't like the card itself ... dmesg has MANY "I/O error" related messages ... but the reader senses the card and seems to react fine to whatever i do ...

i have to use an adapter and maybe my phone does some weird sort of formatting to the card (it's a WinCE-based smartphone) -- so i feel it's the card itself more than anything else -- if i had an actual normal-size SD card it may work (or i'm just wrong on what i said above :p) ...

---

