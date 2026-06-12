---
title: "Windows not booting after ubuntu installation"
date: 2012-11-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by altoman on 2012-11-25
Hi Guys,

I finally managed to installed ubuntu. But now I cannot boot win8.
I searched on the forum and tried everything without any luck.
Here is the log from boot-repair: [http://paste.ubuntu.com/1384576/]("http://paste.ubuntu.com/1384576/")

Please assist.

Altoman

---

### Post by YannBuntu on 2012-11-26
Hello

You have some .bckp files.
Did you try another repair procedure or tool before using Boot-Repair?

Please run the "Recommended Repair" and indicate the new URL that will appear.

---

### Post by altoman on 2012-11-26
> **YannBuntu said:**
> Hello

You have some .bckp files.
Did you try another repair procedure or tool before using Boot-Repair?

Please run the "Recommended Repair" and indicate the new URL that will appear.

Hi,

Thank you for your reply.
No I didn't use any other tool.
Please find below the new URL:
[http://paste.ubuntu.com/1389617/](http://paste.ubuntu.com/1389617/)

BR,

altoman

---

### Post by YannBuntu on 2012-11-26
1. Boot on your installed Ubuntu, connect internet
2. Open a terminal and type the following commands:
```
sudo apt-get update
sudo apt-get install -y boot-repair boot-sav
sudo rm /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
sudo rm /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi.grb
sudo cp /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi.bckp /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
boot-repair
```

3. then run Boot-Repair's Recommended Repair, and tell me the new URL that will appear.
4. reboot the PC and tell me what you observe when selecting the "Windows UEFI loader" entry

---

### Post by altoman on 2012-11-26
> **YannBuntu said:**
> 1. Boot on your installed Ubuntu, connect internet
2. Open a terminal and type the following commands:
```
sudo apt-get update
sudo apt-get install -y boot-repair boot-sav
sudo rm /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
sudo rm /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi.grb
sudo cp /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi.bckp /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
boot-repair
```

3. then run Boot-Repair's Recommended Repair, and tell me the new URL that will appear.
4. reboot the PC and tell me what you observe when selecting the "Windows UEFI loader" entry

Thank you.
I just did as you recommended, if I try to boot on Win UEFI the screen blinks black then the grub menu is displayed.
here is the new URL: [http://paste.ubuntu.com/1389746/](http://paste.ubuntu.com/1389746/).

Altoman

---

### Post by Shuudoushi on 2012-11-26
Your MBR seems to be jacked up a bit. Windows 8 also doesn't like to be dual-booted. As I have yet to try to dual-boot win8 and Ubuntu; all I can tell you is to fix your MBR. It's what i had to do with win7 and had to do to many other peoples computers when they tryed to dual-boot Ubuntu and windows. [https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows) This link should help you get back on track.

---

### Post by altoman on 2012-11-26
Thank you.
I think I will need to re-install everything. Only issue is the Win8 is OEM version, not shipped with CD and I messed up the recovery partition :(

---

### Post by altoman on 2012-11-26
Thank you.
I think I will have to re-install everything. Only issue is my win8 is an OEM version (no CD shipped) and I messed up with the recovery partition :(

---

### Post by Shuudoushi on 2012-11-26
> **altoman said:**
> Thank you.
I think I will need to re-install everything. Only issue is the Win8 is OEM version, not shipped with CD and I messed up the recovery partition :(

Ouch! Well luckly if you do it right you can fix your MBR without having to wipe and try all over again. However if it does come down to that you can go to some web-sites and get a copy of win8 (Make sure it doesn't auto-enter the serial numbers for you) and use the serial number off of your case.

---

### Post by oldfred on 2012-11-26
Your Windows 8 looks ok, but somehow you have the efi partition as sda7. The efi partition is normally first per UEFI spec and with Windows sometimes second. And even thought it is sda7 it still is first on drive?

Both Ubuntu & Windows need to be either UEFI/gpt partitioned or BIOS/MBR partitioned. And how you boot installer (UEFI or BIOS/legacy)  is how it will install.

If you go into UEFI and select efi boot, does it show both ubuntu and windows?

---

### Post by Shuudoushi on 2012-11-26
> **oldfred said:**
> Your Windows 8 looks ok, but somehow you have the efi partition as sda7. The efi partition is normally first per UEFI spec and with Windows sometimes second. And even thought it is sda7 it still is first on drive?

Both Ubuntu & Windows need to be either UEFI/gpt partitioned or BIOS/MBR partitioned. And how you boot installer (UEFI or BIOS/legacy)  is how it will install.

If you go into UEFI and select efi boot, does it show both ubuntu and windows?

Holy crap good catch! I just thought of the most common problem of the MBR getting messed up.

---

### Post by altoman on 2012-11-26
Yes sda7 is the first partition.
Finaly my recovery (external) disk worked fine.
Now i need to reinstall ubuntu but with custom partitioning: I already have 3 unused partition which i want to use as /root, /tmp and /home.

the EFI partition is also still there. Do I need to specify efi partition during the re-installation?

---

### Post by oldfred on 2012-11-26
You need to boot in UEFI mode. I believe grub then just installs with grub-efi correctly into the efi partition if it already exists. 
You do not install grub to the MBR or any place else. Does it still give the old choices which then is a bug?

---

