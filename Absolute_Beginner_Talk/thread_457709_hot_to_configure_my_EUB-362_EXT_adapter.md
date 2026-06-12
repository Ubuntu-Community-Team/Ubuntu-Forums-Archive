---
title: "hot to configure my EUB-362 EXT adapter"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by abrand888 on 2007-05-28
Hi,

Since I was never able to get Ubuntu working on my DELL GX 110, I borrowed a AMD 900 MHZ computer with 512mb of ram a nvidia graphics card 5200, a usb 7-port external adapter self powered and a USB 2.0 card and a DVD/cd writer and a SCSI DVD-Rom player and a dial up modem but since I am located right near a hot spot in my neighborhood, using Windows I can get three different hot spots.

My setup is different in that I am using a yagi 16 dbi antenna and a Engenius EUB-362 EXT Wireless Lan 
USB 2.0 adapter going right into my USB card. The EUB-362 EXT device is using a Atheros AR5005 chipset 
(RoC AR2112 / Baseband AR5523) Engenius heard that Ndiswrapper and Madwifi have a linux driver for their EUB-362 EXT unit.

At the present time I am running the live CD and will appreciate help in getting Ubuntu 7.04 working to go on line. Once I can get UBuntu going on line, then I will partition my drive and use Ubuntu and Windows, or install Ubuntu on a new drive. Haven't decided yet what I will do.

According to Keenansystems.com/nub_362_eub362_linux_ndiswrapper_driver it suggest doing the following :
You must install the kernal source.   Does this mean I must install Ubuntu or can I test Ubuntu in live 
cd ?

By using the ndiswrapper v1.6 driver in linux you can load the windows driver and bootloader.

These steps worked for us with FC4 i386 on a Compaq M2000 laptop with  A64 cpu they will be different 

for other distributions and hardware.

 

You must install the kernel source.

Download build and and install version 1.6 or later of the ndiswrapper  here 

You will need the eub-362 drivers and bootloader files here

install the eub driver with the command

        ndiswrapper -i net5523.inf

plug in your eub-362

        modprobe ndiswrapper

cat /proc/bus/usb/devices  note the vendor id and product id

tell ndiswrapper to use the driver on the eub-362

                                 vendorid

                                               serial number

        ndiswrapper -d 0cf3:0001:0.01

 

load the bootloader (put this step into your startup it must be issued each time the eub is inserted)

                                                    vendor id

                                                               prodid

        load_fw_ar5523 ar5523.bin 0cf3 0002

 

bind the eub362 to wlan0

        ndiswrapper -d wlan0 net5523

 

Issue iwconfig command you should now see the eub362 as wlan0 and can configure in the usual way.


How can I do the above ? 

Thanks


Arthur

---

