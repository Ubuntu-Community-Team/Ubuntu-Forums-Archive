---
title: "ubuntu usb dual boot"
date: 2021-02-19
forum: Apple Hardware Users
---

### Post by secondarymouse on 2021-02-19
[COLOR=#000000][FONT=Arial]Hi, I’m quite new to ubuntu and am undergoing issues. I tried to dual boot ubuntu on my 2013 Macbook air by using a usb. I followed the instructions that the ubuntu site has provided in order to do so (via [https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview;](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview;) [https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)), however I’m now having trouble accessing macos. When I enter the boot screen whenever I restart my laptop and hold the option/alt key the macos disk is no longer there and all disks(3 disks) simply read as EFI Boot. When I select the the disk that was originally macos it reads a message on the screen and then redirects me to ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The message reads as following: [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]*Failed to set MokListRT: Invalid Parameter*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*Could not create MokListRt: Invalid Parameter*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*Importing MOK states has failed: import_mok_state() failed*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*: Invalid Parameter*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*Continuing boot since secure mode is disabledSystem BootOrder  not found. Intia*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*Lizing defaults.*[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]*Failed to set MokListRT: Invalid Parameter*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*Could not create MokListRt: Invalid Parameter*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*Importing MOK states has failed: import_mok_state() failed*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*: Invalid Parameter*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*Continuing boot since secure mode is disabledSystem BootOrder  not found. Intia*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*Lizing defaults.*[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]According to what I have read online it seems I have overwritten my mac os operating system, which I interpret as macos no longer exists on my laptop and I have likely lost any data that is connected to it. I’m fine with the lost data however if there’s any way that I can retrieve it that would be great, however my main concern is getting macos back on my laptop. I apologize for the hassle but i'm rather unfamiliar with linux and general programming terminology and concepts so if a basic rundown with simplified terms can be provided that would be greatly appreciated. Thanks.[/FONT][/COLOR]

---

### Post by yancek on 2021-02-19
The first link you posted simply shows how to create a bootable usb of Ubuntu.  In the 2nd link it explains how to install.  In step 7 of the tutorial, did you select the Something Else option shown or did you leave it as the default "Erase disk and install Ubuntu?  If you used the Erase disk option, you've overwritten your Mac system.  If you can boot Ubuntu, open a terminal and run the following command and post the output here to list drive/partition information:

```
sudo fdisk -l
```

---

### Post by howefield on 2021-02-19
Thread moved to the "*Apple Hardware Users*" forum.

---

