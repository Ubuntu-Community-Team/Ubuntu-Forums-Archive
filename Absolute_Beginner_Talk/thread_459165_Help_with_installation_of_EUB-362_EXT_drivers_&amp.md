---
title: "Help with installation of EUB-362 EXT drivers &amp; ndiswrapper"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by abrand888 on 2007-05-30
Please guide me with my questions in brackets with the instructions given by Keenan Systems. Thank you very much. I am new to Linux and appreciate your help.
Arthur

Download build and and install version 1.6 or later of the ndiswrapper  here 

( I am assuming I have to unrar this file using a Linux command using tar - zxvf ndiswrapper-version.tar.gz)

You will need the eub-362 drivers and bootloader files here 

( I unrarred this zip file and made a separate directory on my flash drive. Will the command "ndiswrapper - net5523.inf find the directory on my flash drive or do I have to copy the files to which directory on my hard drive ?)

install the eub driver with the command

        ndiswrapper -i net5523.inf

plug in your eub-362

        modprobe ndiswrapper  

(Does this command create the line below cat ?)


cat /proc/bus/usb/devices  note the vendor id and product id  

( does this command give me the id number and product id ?)

tell ndiswrapper to use the driver on the eub-362 

(Where will this directory of files reside /)

                                 vendorid   ( What does this commend do and mean ?)


                                               serial number

        ndiswrapper -d 0cf3:0001:0.01

 

load the bootloader (put this step into your startup it must be issued each time the eub is inserted)

(Where is the startup to issue this command ? Also if the EUB-362 is always connected I assume that I don't have to issue this command. )

                                                    vendor id

                                                               prodid

        load_fw_ar5523 ar5523.bin 0cf3 0002

 

bind the eub362 to wlan0

        ndiswrapper -d wlan0 net5523

 

Issue iwconfig command you should now see the eub362 as wlan0 and can configure in the usual way.

Where do I issue the command iwconfig ?

 Thank you very much.

Arthur

---

