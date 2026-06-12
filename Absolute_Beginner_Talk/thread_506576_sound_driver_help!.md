---
title: "sound driver help!"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by p3ngu1n on 2007-07-21
i have an ASUS socket a A7M266 motherboard and ubuntu didnt automatically detect the sound. i went to asus's website and got the linux driver, but it is REALLY confuzing on how you are supposed to go about installing it. earlier in my experience with the forums, someone showed me how to get the driver for my graphics card through a GUI based thing that did everything for me. is there anything like that for sound drivers?

---

### Post by p3ngu1n on 2007-07-21
anyone?

---

### Post by overdrank on 2007-07-22
> **p3ngu1n said:**
> anyone?

Hi I did a search on the web and can you confirm that you have the C-Media CMI-8738 PCI Audio Controller on your system. You can use the command 
```
lspci
```
In the terminal located under applications,accessories,terminal.

---

### Post by p3ngu1n on 2007-07-22
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller (rev 13)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:04.4 Non-VGA unclassified device: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
01:05.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by p3ngu1n on 2007-07-22
wow um i dont see that listed there, but i have a soundjack and everything!

---

### Post by SPQQKY on 2007-07-22
Your multimedia audio controller doesn't seem to be listed. Is it enabled in BIOS? Do you have windows installed on this system as well? Does it work under windows?

---

### Post by overdrank on 2007-07-22
> **p3ngu1n said:**
> wow um i dont see that listed there, but i have a soundjack and everything!

Ok are you on a dual boot system mean that it works with windows? If it does then I don't know what else to look for. If it doesn't work in windows or you don't have windows on the system then it might be disabled in bios.

Edit: To late lol

---

### Post by p3ngu1n on 2007-07-22
hmn, you know, that inspires me to check bios. and no i dont have dual-boot. i hate windowze with a passion :)

---

### Post by p3ngu1n on 2007-07-22
i didnt do anything. if i get a soundcard, will it auto-detect it?

---

### Post by uzikan on 2007-07-22
MSCExec 1.0 for Linux
MSCExec allows you to call OS command or launch an application right from your script. You can set parameters for the call and check results. the link ~~~> [http://www.softwarevault.com/Internet/Mscexec-10-For-Linux.xml](http://www.softwarevault.com/Internet/Mscexec-10-For-Linux.xml)  well i hope i'm on target coz i'll try to help with a realtek linux ubuntu sound drivers but see if time been u can acces this download to just use it once to get in the bios and reverse your sound problem from within your bios ok i got a break here take this link go to quick links in it see if it maches your sound drivers ad download to your desk top than compare fully to mach yours its all abour drivers i feel for you coz it happened to me the other day on my comp it fixt mine but remember i have windows xp pro and i can use both ubuntu  &&&&& so thats the link try the fix what can u loose ~~~> [http://www.realtek.com.tw/default.aspx](http://www.realtek.com.tw/default.aspx)

---

### Post by kvonb on 2007-07-22
This thread will have the answers I'm sure:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

It does sound like your sound is disabled in your BIOS, have a look in the mainboard's manual for instructions on how to enable it.

Your sound card IS supported by Ubuntu.

You could go and buy another sound card if you feel like spending money, just make sure that it is supported first, there is an Ubuntu hardware guide here somewhere.

---

