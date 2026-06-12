---
title: "Playing mp3."
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-06-24
I am unable to connect to the internet in kubuntu and ia there a mp3 player so that it can play those files in  kubuntu. I tried vlc but it says "dependencies not satisfied" and says to install "liba" . Can someone please tell me where i can download those dependency packages in .deb or is there a vlc installation with all those dependency packages in .deb. I have to download it using XP. If there is any .tar packages please tell me how to install it.Help me please.

Thanks in advance.

---

### Post by shifty_powers on 2007-06-24
why do you have no internet in kubuntu?

And porbably the best kde mp3 player is amarok...

---

### Post by bren on 2007-06-24
here are the names of the packages you need to install

[https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html)

although it says they must be installed via apt you can also search and download the files directly I think

good luck

bren

---

### Post by atria on 2007-06-24
Yep you definitely can. Download the packages and install with
```
sudo dpkg -i <path to package.deb>
```

---

### Post by Rabindranath on 2007-06-24
The reason I cant connect to the internet is that I dont know how to configure kppp.I installed the scan modem tool and the output was,


 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-15-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_June_19


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 06:01.0	134d:2189	134d:1002	Modem: PCTel Inc HSP56 MicroModem 

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 06:01.0 ----
[    3.297174] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 22 (level, low) -> IRQ 20
[    3.297410] 0000:06:01.0: ttyS1 at I/O 0xb808 (irq = 20) is a 16450
[    3.297565] 0000:06:01.0: ttyS2 at I/O 0xb810 (irq = 20) is a 8250
[    3.297718] 0000:06:01.0: ttyS3 at I/O 0xb818 (irq = 20) is a 16450
[    3.297787] Couldn't register serial port 0000:06:01.0: -28

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:2668	8086:e202	Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW 

 Modem interrupt assignment and sharing: 
 16:      69469          0   IO-APIC-fasteoi   uhci_hcd:usb4, HDA Intel, i915@pci:0000:00:02.0

 --- Bootup diagnositcs for card in PCI slot 00:1b.0 ----
[   16.601981] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.602006] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

8086:2668 is a High Definition Audio card, possibly hosting a soft modem.

---

### Post by Rabindranath on 2007-06-24
I am unable to find the one with mp3. Is there a single plugin for playing all the restricted formats?

---

### Post by atria on 2007-06-24
mp3 is contained in gstreamer0.10-ffmpeg if i remember correctly.

---

### Post by Rabindranath on 2007-06-24
Ok thanks. Where shall i find the dependency files for vlc?

---

### Post by atria on 2007-06-24
You can do
```
aptitude -s install vlc
```
or
```
aptitude show vlc
```
or
```
dpkg --info packagename.deb
```
to show the dependencies. Use the third one if you don't have internet access.

---

### Post by Rabindranath on 2007-06-24
Does anyone know how to configure a HSP56 modem in kppp?

---

### Post by Rabindranath on 2007-07-14
I have found a way to play mp3 files in kubuntu. Some people here haven't an internet connection in kubuntu and new comers to kubuntu can use this. It is just very easy. 

I think you can install the files in the following order. (Have to verify). Just google these files and download it from "packages.ubuntu" or "packages.debian"( It has all the packages needed). I have included most of the dependencies but please correct me if there are more.


1.libavutil1d
2.libpostprocld
3.gcc-4.2base(=4.2-20070627-1)
4.libgcc1(>=1:4.2-20070516)
5.slibstdc++6(>=4.2-20070627-1)
6.libasound2(>>1.0.14)
7.libflac8
8.libjack2(>=0.103.0)       ( I haven't installed this library but it still played. Used a lower version of libjack2)
9.libxcb-xv()
10. libxcb-shm()
11.libxcb-shape()
12.libxcb1
13.libxine1(>=1.1.7)


                       ( These files are suitable also for the xine engine in amarok. I think it is preinstalled in kubuntu)

Just download these files from another computer or dual boot in your own computer, download these files
and reboot to kubuntu. Just rightclick those packages ( right click   >kubuntu package manager> install package) Provide your password if necessary. 

i have seen another method of installing mp3 support but it didn't work for me. 

( run "install mp3" from /usr/.../install mp3. Some claim that it works)- Have to check....

I dont know whether this works in ubuntu as well.

 Please post any other method to install mp3 support so that the new ubuntu converts will find it easy.

---

### Post by shifty_powers on 2007-07-14
Seems kind of long winded. I've always found that mp3's play from a fresh installation anyway?

---

