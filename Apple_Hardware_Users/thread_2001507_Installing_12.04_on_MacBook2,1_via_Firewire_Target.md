---
title: "Installing 12.04 on MacBook2,1 via Firewire Target or USB?"
date: 2012-06-11
forum: Apple Hardware Users
---

### Post by raintheory on 2012-06-11
Hi there,

I have a MacBook2,1 with no operating system installed.  The CD drive is dead on this unit.  I would like to install 12.04.  

I do have another Mac, so I was wondering if it might be possible to boot into target mode on the *other* mac (with install CD in it) and install via firewire onto the MacBook from there, has anyone tried this?  

Alternately, I have an 8GB USB drive as well as plenty of old external USB drives, is it possible to install via USB?  

I was thinking of installing Ubuntu Studio if that makes a difference...

Thanks in advance!

---

### Post by cochise85 on 2012-06-15
> **raintheory said:**
> Hi there,

I have a MacBook2,1 with no operating system installed.  The CD drive is dead on this unit.  I would like to install 12.04.  

I do have another Mac, so I was wondering if it might be possible to boot into target mode on the *other* mac (with install CD in it) and install via firewire onto the MacBook from there, has anyone tried this?  

Alternately, I have an 8GB USB drive as well as plenty of old external USB drives, is it possible to install via USB?  

I was thinking of installing Ubuntu Studio if that makes a difference...

Thanks in advance!

Hi,
i have a MBP 3,1 (with broken CD unit too) and i made a dual boot OS X/Lubuntu but i think it is quite the same.
it is not easy because Mac's EFI needs a GPT partition table and linux needs a MBR.
To get a working mixed GPT/MBR partition table you have to run the bootcamp utility.
I don't know if your other mac (maybe if it is a newer model) can boot from usb and install into another mac in firewire target mode. You can try this.
Otherwise you have to do:

1 - connect in firewire target mode and format the drive;
2 - install OS X (if you can't, clone your other's mac disk on the firewire disk with CARBON COPY CLONER);
3 - repair permission disk (firewire disk with disk utility);
4 - boot osx from your laptop;
5 - open finder, go in applications, right click on bootcamp utility-->show package content-->contents, copy on desktop info.plist;
6 - click on apple--> info about this mac-->more info-->system-->copy your bootROM version;
7 - open info.plist you have on desktop (unlock it). You have something like this:
<key>DARequiredROMVersions</key>
	<array>
ADD HERE: "<string>YOUR BOOTROM</string>
		<string>IM41.0055.B08</string>
		<string>IM42.0071.B03</string>
		<string>IM51.0090.B03</string>
		<string>IM52.0090.B03</string>
		<string>IM61.0093.B01</string>
		<string>MP11.005C.B04</string>
		<string>MB11.0061.B03</string>
		<string>MBP11.0055.B08</string>
		<string>MBP12.0061.B03</string>
		<string>MM11.0055.B08</string>

<key>USBBootSupportedModels</key>
	<array>
AND HERE ADD "<string>FIRST GROUP OF YOUR BOOT ROM</string>
		<string>IM130</string>
		<string>MM50</string>
		<string>MP60</string>
		<string>MB80</string>
		<string>MBP90</string>
		<string>MBA40</string>

save it and put it in the original folder (before delete the original);

8 - dowload an iso of a windows CD and connect an usb pendrive;
9 - start bootcamp utility and create a win partition, you can first free up some space (it will be your linux+swap space).
10 - download refit and copy the EFI folder in your mac partition (don't install it),
11 - open terminal and type: sudo /efi/refit/enable-always.sh;
12 - reboot in target mode and connect to you other mac or pc;
13 - boot from linux cd or usb and install into the win created space (if your mac can't boot from usb try with ISO-to-USB EFI booted for mac, google it / use a someone's else pc)
14 - boot the macbook and use refit partition tool to update the partition table
15 - Reboot
16 - enjoy your linux on macbook!

---

