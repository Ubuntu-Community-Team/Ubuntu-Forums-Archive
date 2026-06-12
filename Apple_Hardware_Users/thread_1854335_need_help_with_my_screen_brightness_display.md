---
title: "need help with my screen brightness display"
date: 2011-10-04
forum: Apple Hardware Users
---

### Post by trolommonm on 2011-10-04
why doesn't the F1 and F2 buttons work???? the screen brightness is set to 100%. it's killing my eyes and my battery!!! someone help. I'm using macbook pro 7,1 running ubuntu 11.04. i tried editing the edit the xorg.conf file: sudo gedit /etc/X11/xorg.conf
and added Option          "RegistryDwords" "EnableBrightnessControl=1". however, i restarted my macbook pro and the F1 and F2 keys still doesn't work. Help !!!!!

---

### Post by matt_symes on 2011-10-04
Hi

Open a terminal and type

```
sudo bash -c "echo 5 > /sys/class/backlight/*/brightness"
```Does that change your brightness ?

If not or if it errors then type
[FONT=monospace]
[/FONT]```
[FONT=monospace]ls [/FONT]/sys/class/
[FONT=monospace]ls [/FONT]/sys/class/backlight/
```and post the results back here.

Kind regards

---

### Post by trolommonm on 2011-10-04
i tried typing into the terminal window. i got no such file or directory:( sorry im new to ubuntu on my macbook pro.

---

### Post by matt_symes on 2011-10-04
Hi

> **trolommonm said:**
> i tried typing into the terminal window. i got no such file or directory:( sorry im new to ubuntu on my macbook pro.

No problem.

Did you try the last two commands ?

I think your backlight may not have been discovered correctly by Ubuntu. This would make it an ACPI issue and may require a kernel command line switch to fix it.

Open the terminal and type these two command
[FONT=monospace]
[/FONT]```
ls /sys/class/ 
ls /sys/class/backlight/

```Copy and paste the results from them from the terminal into your next post. You can copy and paste them by highlighting them with the mouse, right clicking and selecting copy. You can then paste into your next post. 

Post the results between code tags like this.

[noparse] ```
 results 
``` [/noparse]

As an example, here is mine
```

matthew@matthew-laptop:~$ ls /sys/class/
backlight  bsg  firmware  hwmon        input     mem       net      power_supply  printer    rtc          scsi_generic  spi_master  usbmon       video_output
bdi        dma  gpio      i2c-adapter  leds      misc      pci_bus  ppdev         regulator  scsi_device  scsi_host     thermal     vc           vtconsole
block      dmi  graphics  ieee80211    mdio_bus  mmc_host  pktcdvd  ppp           rfkill     scsi_disk    sound         tty         video4linux
matthew@matthew-laptop:~$ ls /sys/class/backlight/
acpi_video0
matthew@matthew-laptop:~$ 
```Kind regards

---

### Post by trolommonm on 2011-10-04
is this the one you're talking about?

ata_device  dma          input     pktcdvd       scsi_device   usb
ata_link    dmi          leds      power_supply  scsi_disk     usbmon
ata_port    firmware     mdio_bus  ppdev         scsi_generic  vc
backlight   gpio         mem       ppp           scsi_host     video4linux
bdi         graphics     misc      printer       sound         vtconsole
block       hidraw       mmc_host  regulator     spi_master    wmi
bluetooth   hwmon        net       rfkill        thermal
bsg         i2c-adapter  pci_bus   rtc           tty




alvin@alvin-MacBookPro:~$ ls /sys/class/
ata_device  dma          input     pktcdvd       scsi_device   usb
ata_link    dmi          leds      power_supply  scsi_disk     usbmon
ata_port    firmware     mdio_bus  ppdev         scsi_generic  vc
backlight   gpio         mem       ppp           scsi_host     video4linux
bdi         graphics     misc      printer       sound         vtconsole
block       hidraw       mmc_host  regulator     spi_master    wmi
bluetooth   hwmon        net       rfkill        thermal
bsg         i2c-adapter  pci_bus   rtc           tty
alvin@alvin-MacBookPro:~$ ls /sys/class/backlight/

---

### Post by matt_symes on 2011-10-04
[LEFT]Hi
```

alvin@alvin-MacBookPro:~$ ls /sys/class/
ata_device  dma          input     pktcdvd       scsi_device   usb
ata_link    dmi          leds      power_supply  scsi_disk     usbmon
ata_port    firmware     mdio_bus  ppdev         scsi_generic  vc
backlight   gpio         mem       ppp           scsi_host     video4linux
bdi         graphics     misc      printer       sound         vtconsole
block       hidraw       mmc_host  regulator     spi_master    wmi
bluetooth   hwmon        net       rfkill        thermal
bsg         i2c-adapter  pci_bus   rtc           tty
alvin@alvin-MacBookPro:~$ ls /sys/class/backlight/
```

Ubuntu has not recognised you have a backlight by the looks of it.

There is a kernel switch that may help. Give me a little time and i will dig it out for you.

Kind regards
[/LEFT]

---

### Post by matt_symes on 2011-10-04
Hi

Let's put a hold on the fact it may be an ACPI issue and back up for a moment. 

I don't actually own a mac book pro 7-1 so i don't want to try and second guess an issue that may have been fixed or addressed elsewhere.

Have you read through these documents ?

One is for Lucid and one is for Natty.

[https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)
[https://help.ubuntu.com/community/MacBookPro7-1/Natty](https://help.ubuntu.com/community/MacBookPro7-1/Natty)

Kind regards

---

### Post by trolommonm on 2011-10-05
Yes i have read the website on natty. Still no luck.

---

### Post by matt_symes on 2011-10-05
Hi

Just to double check you installed the mactel-support package on your system and the required are files and daemon running ?

From the Natty page.

> sudo add-apt-repository ppa:mactel-support && sudo apt-get update
The  mactel PPA modules needed on Ubuntu on this MBP nvidia-bl-dkms (driver  for the LCD panel backlight) and pommed (daemon to control them all). 
What is the output of these commands ? (A small L after modprobe)

```
modprobe -l nvidia-bl-dkms
lsmod | grep nvidia-bl-dkms
ps aux | grep pommed

```BTW: If anybody owns a macbook pro 7-1 then please feel free it add your input.

Kind regards

---

### Post by trolommonm on 2011-10-06
i have the mactel support package on my system.

---

### Post by matt_symes on 2011-10-07
Hi

You can try each of these switches kernel command lines.

```
acpi_backlight=vendor
```Try the above one first as you have installed the mactel ppa.

If that does not work try the second one.

```
acpi_osi=linux
```To try them you need to reboot your PC and at the grub menu select your kernel.

When you have selected your kernel press e to edit the kernel command line and add the switch to the end of the kernel command line.

You then need to press ctrl + x (i think) to continue the boot process.

Only try one of the switches at a time.

Check the contents of /sys/class/backlight after each attempt.

If either of them work then we need to make then persistent after a reboot.

Kind regards

---

