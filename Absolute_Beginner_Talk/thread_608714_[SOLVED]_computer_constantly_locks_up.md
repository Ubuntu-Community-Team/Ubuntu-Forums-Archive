---
title: "[SOLVED] computer constantly locks up"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by POWERVICE on 2007-11-10
Hello,
      Please can some one tell me the definitive answer as to why my pc. keeps randomly locking every 20-30 mins when I try to use UBUNTU with the internet connected. It seems to be ok if I am not connected to the internet. I can sometimes clear it and return to the user/password screen after randomly hitting keys such as ctrl/alt/del and everything else - but this has no effect until I have spent several minutes bashing the keyboard (of course if I switch the pc off then this also cures the problem)

My pc is 6 months old and has a win xp installation on one hard drive which has never ever locked up.
I installed 7.04 on a brand new second seagate hard drive and lock ups occurred.
I updated to 7.1 and lock ups occurred.
I installed a complete fresh installation of 7.1 and lock ups occurred.
I returned to a fresh installation of 7.04 and lock ups occurred.
I downloaded all the updates and lock ups still occur. 
I have changed from a speedtouch to sagem modem and lock up still occur!

The only extra software installed is 'usbadslmanager' which automatically sets up my speedtouch modem and 'ENVY' which automatically collects and installs updated drivers for my Radeon Xpress 200 graphics card. Lock ups occurred before ENVY was installed.

My basic pc spec is: Pentium 4 3.2ghz with 1 gb ram.

I am an absolute begiiner with UBUNTU and have no computer expertise other than wanting it to simply keep working. I would like to use UBUNTU because I have come this far (ie installation and modem set up) and feel it has a lot to offer. However the system is unusable and this is my last chance before I have to return to windows after 6 weeks of lock ups. I have read lots of forum answers and it looks as if no one has the answer (do you just live with the lock ups?) but I thought I would give it a go anyway.
  Thank you in anticipation

---

### Post by jba6511 on 2007-11-10
did this problem occur in any other OS, like WIndows? It could be a hardware related issue. What are your temps in the case? Have you ran memtest to check the RAM?

---

### Post by POWERVICE on 2007-11-10
Sorry for the delay but computer has just locked up again. As I said, it has never  ever locked up in windows. Can you tell me what you mean by 'your temps in the case?'. I will have a look at memtest but will have to find out what memtest is first. I am afraid I am a total beginner  with computers.

---

### Post by russnash37 on 2007-11-10
If the lockups seem to be occurring during internet usage, then I would be fairly sure that it's something in that area that is causing it.  From your message, it seems that you are connecting a DSL modem via USB?  Is that correct?

If you have ethernet available to you, and if your DSL modem supports it (most do), it would probably be worth switching your internet over to that to see if it makes a difference.

Russ.

---

### Post by POWERVICE on 2007-11-10
Thanks Russ.  Sorry for delay again (another lock up). My modem is simply the one I get with Tiscali. It has a usb wire coming from it so I guess I can only plug it into the usb unless I need an adaptor to convert usb to ethernet.

---

### Post by jba6511 on 2007-11-10
sorry did not realize it only happens with internet usage.

---

### Post by Harpoon on 2007-11-10
It is possible you are experiencing a problem related to network-kanager,  Take a look at
[https://bugs.launchpad.net/bugs/93360](https://bugs.launchpad.net/bugs/93360)

---

### Post by POWERVICE on 2007-11-10
Thanks for the information. It does not mean much to me though. It looks like I will have to accept it just locks up.

---

### Post by russnash37 on 2007-11-10
Don't give up yet!! :)

The next time it freezes and you are able to eventually unlock it, open up a terminal and type 'dmesg', paste the last couple of screens of it's output here.  There may be some information we can glean from that.

---

### Post by Abild on 2007-11-10
No, dont give up. Ubuntu should definitely not behave like that and what you are experiencing is completely unacceptable.

Could the keys you are hitting when you are able to unlock your computer by any chance be Ctrl+Alt+Backspace? Thats the combination for restarting the graphical user interface.

---

### Post by POWERVICE on 2007-11-10
Thanks for the info. I have been running memtest for the last 1.5 hours and no errors have been found.  There has been absolutely no pattern to the keys I have used to reset. I have used ctrl alt 
backspace and it has worked sometimes but usually nothing works unless I wait. Sometimes I have to wait 5 or 10 or 15 mins and eventually after hitting lots of keys I m away again.
 None of the key sequences suggeested in the forums seem to work immediately like ctrl alt del in windows so I simply switch off. I will send the info you require at next lock up. Thanks

---

### Post by POWERVICE on 2007-11-10
Here are the last pages of output from dmesg. Hope this means something to you!
Thanks for your help


[   21.584857] sd 5:0:0:1: Attached scsi removable disk sdc
[   21.590475] atiixp: codec read timeout (reg 0)
[   21.594784] sd 5:0:0:2: Attached scsi removable disk sdd
[   21.595241] atiixp: codec read timeout (reg 1c)
[   21.602430] atiixp: codec read timeout (reg 0)
[   21.604801] sd 5:0:0:3: Attached scsi removable disk sde
[   21.615878] atiixp: codec read timeout (reg 1c)
[   21.623464] atiixp: codec read timeout (reg 0)
[   21.628518] sd 4:0:0:0: Attached scsi generic sg0 type 0
[   21.628564] sd 5:0:0:0: Attached scsi generic sg1 type 0
[   21.628606] sd 5:0:0:1: Attached scsi generic sg2 type 0
[   21.628648] sd 5:0:0:2: Attached scsi generic sg3 type 0
[   21.628690] sd 5:0:0:3: Attached scsi generic sg4 type 0
[   21.631113] atiixp: codec read timeout (reg 1c)
[   21.639589] atiixp: codec read timeout (reg 0)
[   21.646718] atiixp: codec read timeout (reg 1c)
[   21.651477] atiixp: codec read timeout (reg 0)
[   21.659171] atiixp: codec read timeout (reg 1c)
[   21.667584] atiixp: codec read timeout (reg 0)
[   21.672442] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   21.675704] atiixp: codec read timeout (reg 1c)
[   21.704530] atiixp: codec read timeout (reg 0)
[   21.712008] atiixp: codec read timeout (reg 1c)
[   21.719440] atiixp: codec read timeout (reg 0)
[   21.726938] atiixp: codec read timeout (reg 1c)
[   21.735453] atiixp: codec read timeout (reg 0)
[   21.742981] atiixp: codec read timeout (reg 1c)
[   21.751882] atiixp: codec read timeout (reg 0)
[   21.756973] usb 1-2: reset full speed USB device using ohci_hcd and address 3
[   21.757689] atiixp: codec read timeout (reg 1c)
[   21.763622] atiixp: codec read timeout (reg 0)
[   21.771508] atiixp: codec read timeout (reg 1c)
[   21.779579] atiixp: codec read timeout (reg 0)
[   21.787537] atiixp: codec read timeout (reg 1c)
[   21.794602] atiixp: codec read timeout (reg 0)
[   21.799251] atiixp: codec read timeout (reg 1c)
[   21.806490] atiixp: codec read timeout (reg 0)
[   21.811078] atiixp: codec read timeout (reg 1c)
[   21.818503] atiixp: codec read timeout (reg 0)
[   21.823109] atiixp: codec read timeout (reg 1c)
[   21.830492] atiixp: codec read timeout (reg 0)
[   21.835127] atiixp: codec read timeout (reg 1c)
[   21.842490] atiixp: codec read timeout (reg 0)
[   21.847041] atiixp: codec read timeout (reg 1c)
[   21.854488] atiixp: codec read timeout (reg 0)
[   21.859077] atiixp: codec read timeout (reg 1c)
[   21.866523] atiixp: codec read timeout (reg 0)
[   21.871061] atiixp: codec read timeout (reg 1c)
[   21.878526] atiixp: codec read timeout (reg 0)
[   21.883059] atiixp: codec read timeout (reg 1c)
[   21.890550] atiixp: codec read timeout (reg 0)
[   21.895108] atiixp: codec read timeout (reg 1c)
[   21.902585] atiixp: codec read timeout (reg 0)
[   21.907250] atiixp: codec read timeout (reg 1c)
[   21.914582] atiixp: codec read timeout (reg 0)
[   21.919181] atiixp: codec read timeout (reg 1c)
[   21.926578] atiixp: codec read timeout (reg 0)
[   21.931180] atiixp: codec read timeout (reg 1c)
[   21.938593] atiixp: codec read timeout (reg 0)
[   21.943197] atiixp: codec read timeout (reg 1c)
[   21.950594] atiixp: codec read timeout (reg 0)
[   21.955215] atiixp: codec read timeout (reg 3c)
[   21.956810] atiixp: codec read timeout (reg 1c)
[   21.963680] atiixp: codec read timeout (reg 0)
[   21.971429] atiixp: codec read timeout (reg 3c)
[   21.974660] atiixp: codec read timeout (reg 1c)
[   21.975071] usbcore: registered new interface driver speedtch
[   21.975200] usbcore: registered new interface driver usblp
[   21.975204] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   21.979868] atiixp: codec read timeout (reg 0)
[   21.987542] atiixp: codec read timeout (reg 3c)
[   21.990305] atiixp: codec read timeout (reg 1c)
[   21.996420] atiixp: codec read timeout (reg 0)
[   22.004014] atiixp: codec read timeout (reg 3c)
[   22.006565] atiixp: codec read timeout (reg 1c)
[   22.011659] atiixp: codec read timeout (reg 0)
[   22.019259] atiixp: codec read timeout (reg 3c)
[   22.022220] atiixp: codec read timeout (reg 1c)
[   22.027774] atiixp: codec read timeout (reg 0)
[   22.034889] atiixp: codec read timeout (reg 3c)
[   22.037582] atiixp: codec read timeout (reg 1c)
[   22.042621] atiixp: codec read timeout (reg 0)
[   22.047468] atiixp: codec read timeout (reg 3c)
[   22.048981] atiixp: codec read timeout (reg 1c)
[   22.055503] atiixp: codec read timeout (reg 0)
[   22.059937] atiixp: codec read timeout (reg 3c)
[   22.061515] atiixp: codec read timeout (reg 1c)
[   22.063688] speedtch 1-2:1.0: found stage 1 firmware speedtch-1.bin
[   22.066907] atiixp: codec read timeout (reg 0)
[   22.071397] atiixp: codec read timeout (reg 3c)
[   22.072912] atiixp: codec read timeout (reg 1c)
[   22.079135] atiixp: codec read timeout (reg 0)
[   22.083599] atiixp: codec read timeout (reg 3c)
[   22.085206] atiixp: codec read timeout (reg 1c)
[   22.090833] atiixp: codec read timeout (reg 0)
[   22.096618] atiixp: codec read timeout (reg 3c)
[   22.098782] atiixp: codec read timeout (reg 1c)
[   22.107021] atiixp: codec read timeout (reg 0)
[   22.113469] atiixp: codec read timeout (reg 3c)
[   22.115345] atiixp: codec read timeout (reg 1c)
[   22.123517] atiixp: codec read timeout (reg 0)
[   22.130151] atiixp: codec read timeout (reg 3c)
[   22.132455] atiixp: codec read timeout (reg 1c)
[   22.135607] speedtch 1-2:1.0: found stage 2 firmware speedtch-2.bin
[   22.138683] atiixp: codec read timeout (reg 0)
[   22.143255] atiixp: codec read timeout (reg 3c)
[   22.144807] atiixp: codec read timeout (reg 1c)
[   22.150986] atiixp: codec read timeout (reg 0)
[   22.155565] atiixp: codec read timeout (reg 3c)
[   22.157175] atiixp: codec read timeout (reg 1c)
[   22.162671] atiixp: codec read timeout (reg 0)
[   22.167234] atiixp: codec read timeout (reg 3c)
[   22.168810] atiixp: codec read timeout (reg 1c)
[   22.174690] atiixp: codec read timeout (reg 0)
[   22.179287] atiixp: codec read timeout (reg 3c)
[   22.180850] atiixp: codec read timeout (reg 1c)
[   22.186684] atiixp: codec read timeout (reg 0)
[   22.191289] atiixp: codec read timeout (reg 3c)
[   22.192841] atiixp: codec read timeout (reg 1c)
[   22.198704] atiixp: codec read timeout (reg 0)
[   22.203264] atiixp: codec read timeout (reg 3c)
[   22.204823] atiixp: codec read timeout (reg 1c)
[   22.210722] atiixp: codec read timeout (reg 0)
[   22.215297] atiixp: codec read timeout (reg 3c)
[   22.216859] atiixp: codec read timeout (reg 1c)
[   22.222719] atiixp: codec read timeout (reg 0)
[   22.227300] atiixp: codec read timeout (reg 3c)
[   22.228857] atiixp: codec read timeout (reg 1c)
[   22.234713] atiixp: codec read timeout (reg 0)
[   22.239278] atiixp: codec read timeout (reg 3c)
[   22.240855] atiixp: codec read timeout (reg 1c)
[   22.246738] atiixp: codec read timeout (reg 0)
[   22.251337] atiixp: codec read timeout (reg 3c)
[   22.252915] atiixp: codec read timeout (reg 1c)
[   22.258734] atiixp: codec read timeout (reg 0)
[   22.263309] atiixp: codec read timeout (reg 3c)
[   22.264865] atiixp: codec read timeout (reg 1c)
[   22.270752] atiixp: codec read timeout (reg 0)
[   22.275322] atiixp: codec read timeout (reg 3c)
[   22.276886] atiixp: codec read timeout (reg 1c)
[   22.282746] atiixp: codec read timeout (reg 0)
[   22.287327] atiixp: codec read timeout (reg 3c)
[   22.288990] atiixp: codec read timeout (reg 1c)
[   22.294768] atiixp: codec read timeout (reg 0)
[   22.299361] atiixp: codec read timeout (reg 3c)
[   22.300926] atiixp: codec read timeout (reg 1c)
[   22.306765] atiixp: codec read timeout (reg 0)
[   22.311338] atiixp: codec read timeout (reg 3c)
[   22.312894] atiixp: codec read timeout (reg 1c)
[   22.318752] atiixp: codec read timeout (reg 0)
[   22.323254] atiixp: codec read timeout (reg 3c)
[   22.324792] atiixp: codec read timeout (reg 1c)
[   22.330776] atiixp: codec read timeout (reg 0)
[   22.335276] atiixp: codec read timeout (reg 3c)
[   22.336836] atiixp: codec read timeout (reg 1c)
[   22.342772] atiixp: codec read timeout (reg 0)
[   22.347287] atiixp: codec read timeout (reg 3c)
[   22.348828] atiixp: codec read timeout (reg 1c)
[   22.354785] atiixp: codec read timeout (reg 0)
[   22.359286] atiixp: codec read timeout (reg 3c)
[   22.360821] atiixp: codec read timeout (reg 1c)
[   22.366790] atiixp: codec read timeout (reg 0)
[   22.371304] atiixp: codec read timeout (reg 3c)
[   22.372835] atiixp: codec read timeout (reg 1c)
[   22.378784] atiixp: codec read timeout (reg 0)
[   22.383299] atiixp: codec read timeout (reg 3c)
[   22.384835] atiixp: codec read timeout (reg 1c)
[   22.390807] atiixp: codec read timeout (reg 0)
[   22.395316] atiixp: codec read timeout (reg 3c)
[   22.396856] atiixp: codec read timeout (reg 1c)
[   22.402800] atiixp: codec read timeout (reg 0)
[   22.407311] atiixp: codec read timeout (reg 3c)
[   22.408851] atiixp: codec read timeout (reg 1c)
[   22.414817] atiixp: codec read timeout (reg 0)
[   22.419331] atiixp: codec read timeout (reg 3c)
[   22.420858] atiixp: codec read timeout (reg 1c)
[   22.426812] atiixp: codec read timeout (reg 0)
[   22.431308] atiixp: codec read timeout (reg 3c)
[   22.432845] atiixp: codec read timeout (reg 1c)
[   22.438843] atiixp: codec read timeout (reg 0)
[   22.443350] atiixp: codec read timeout (reg 3c)
[   22.444903] atiixp: codec read timeout (reg 1c)
[   22.450848] atiixp: codec read timeout (reg 0)
[   22.455349] atiixp: codec read timeout (reg 3c)
[   22.456913] atiixp: codec read timeout (reg 1c)
[   22.461328] AC'97 2 does not respond - RESET
[   22.464334] AC'97 2 access is not valid [0xffffffff], removing mixer.
[   22.464341] atiixp: no codec available
[   22.464380] ACPI: PCI interrupt for device 0000:00:14.5 disabled
[   22.547110] lp0: using parport0 (interrupt-driven).
[   22.575018] Adding 2835432k swap on /dev/disk/by-uuid/325efe69-7f5c-471c-ab62-89cfc61998c5.  Priority:-1 extents:1 across:2835432k
[   22.691513] EXT3 FS on hda1, internal journal
[   23.119188] input: Power Button (FF) as /class/input/input4
[   23.119224] ACPI: Power Button (FF) [PWRF]
[   23.119283] input: Power Button (CM) as /class/input/input5
[   23.119309] ACPI: Power Button (CM) [PWRB]
[   23.308288] Using specific hotkey driver
[   23.344709] No dock devices found.
[   23.355604] ibm_acpi: ec object not found
[   23.413579] pcc_acpi: loading...
[   27.113755] eth0: link down
[   27.582909] ATM dev 0: ADSL line is synchronising
[   29.975145] ppdev: user-space parallel port driver
[   30.643106] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   30.643113] apm: disabled - APM is not SMP safe.
[   30.864293] Bluetooth: Core ver 2.11
[   30.864374] NET: Registered protocol family 31
[   30.864378] Bluetooth: HCI device and connection manager initialized
[   30.864382] Bluetooth: HCI socket layer initialized
[   30.890328] Bluetooth: L2CAP ver 2.8
[   30.890335] Bluetooth: L2CAP socket layer initialized
[   30.894699] Bluetooth: RFCOMM socket layer initialized
[   30.894717] Bluetooth: RFCOMM TTY layer initialized
[   30.894720] Bluetooth: RFCOMM ver 1.8
[   31.296381] PPP generic driver version 2.4.2
[   41.444229] NET: Registered protocol family 10
[   41.444394] lo: Disabled Privacy Extensions
[   41.444499] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.579368] ATM dev 0: ADSL line is up (1152 kb/s down | 288 kb/s up)
[   46.971042] PPP BSD Compression module registered
[   47.069069] PPP Deflate Compression module registered
karl@ubuntu:~$

---

### Post by POWERVICE on 2007-11-10
Here is the output from the lockup that occurred 5 mins after the previous one. This one reset to the log in screen after approx 2-3 mins of striking random keys on keyboard. ''ctrl alt prt screen backspace L''    etc.etc  




22.282746] atiixp: codec read timeout (reg 0)
[   22.287327] atiixp: codec read timeout (reg 3c)
[   22.288990] atiixp: codec read timeout (reg 1c)
[   22.294768] atiixp: codec read timeout (reg 0)
[   22.299361] atiixp: codec read timeout (reg 3c)
[   22.300926] atiixp: codec read timeout (reg 1c)
[   22.306765] atiixp: codec read timeout (reg 0)
[   22.311338] atiixp: codec read timeout (reg 3c)
[   22.312894] atiixp: codec read timeout (reg 1c)
[   22.318752] atiixp: codec read timeout (reg 0)
[   22.323254] atiixp: codec read timeout (reg 3c)
[   22.324792] atiixp: codec read timeout (reg 1c)
[   22.330776] atiixp: codec read timeout (reg 0)
[   22.335276] atiixp: codec read timeout (reg 3c)
[   22.336836] atiixp: codec read timeout (reg 1c)
[   22.342772] atiixp: codec read timeout (reg 0)
[   22.347287] atiixp: codec read timeout (reg 3c)
[   22.348828] atiixp: codec read timeout (reg 1c)
[   22.354785] atiixp: codec read timeout (reg 0)
[   22.359286] atiixp: codec read timeout (reg 3c)
[   22.360821] atiixp: codec read timeout (reg 1c)
[   22.366790] atiixp: codec read timeout (reg 0)
[   22.371304] atiixp: codec read timeout (reg 3c)
[   22.372835] atiixp: codec read timeout (reg 1c)
[   22.378784] atiixp: codec read timeout (reg 0)
[   22.383299] atiixp: codec read timeout (reg 3c)
[   22.384835] atiixp: codec read timeout (reg 1c)
[   22.390807] atiixp: codec read timeout (reg 0)
[   22.395316] atiixp: codec read timeout (reg 3c)
[   22.396856] atiixp: codec read timeout (reg 1c)
[   22.402800] atiixp: codec read timeout (reg 0)
[   22.407311] atiixp: codec read timeout (reg 3c)
[   22.408851] atiixp: codec read timeout (reg 1c)
[   22.414817] atiixp: codec read timeout (reg 0)
[   22.419331] atiixp: codec read timeout (reg 3c)
[   22.420858] atiixp: codec read timeout (reg 1c)
[   22.426812] atiixp: codec read timeout (reg 0)
[   22.431308] atiixp: codec read timeout (reg 3c)
[   22.432845] atiixp: codec read timeout (reg 1c)
[   22.438843] atiixp: codec read timeout (reg 0)
[   22.443350] atiixp: codec read timeout (reg 3c)
[   22.444903] atiixp: codec read timeout (reg 1c)
[   22.450848] atiixp: codec read timeout (reg 0)
[   22.455349] atiixp: codec read timeout (reg 3c)
[   22.456913] atiixp: codec read timeout (reg 1c)
[   22.461328] AC'97 2 does not respond - RESET
[   22.464334] AC'97 2 access is not valid [0xffffffff], removing mixer.
[   22.464341] atiixp: no codec available
[   22.464380] ACPI: PCI interrupt for device 0000:00:14.5 disabled
[   22.547110] lp0: using parport0 (interrupt-driven).
[   22.575018] Adding 2835432k swap on /dev/disk/by-uuid/325efe69-7f5c-471c-ab62-89cfc61998c5.  Priority:-1 extents:1 across:2835432k
[   22.691513] EXT3 FS on hda1, internal journal
[   23.119188] input: Power Button (FF) as /class/input/input4
[   23.119224] ACPI: Power Button (FF) [PWRF]
[   23.119283] input: Power Button (CM) as /class/input/input5
[   23.119309] ACPI: Power Button (CM) [PWRB]
[   23.308288] Using specific hotkey driver
[   23.344709] No dock devices found.
[   23.355604] ibm_acpi: ec object not found
[   23.413579] pcc_acpi: loading...
[   27.113755] eth0: link down
[   27.582909] ATM dev 0: ADSL line is synchronising
[   29.975145] ppdev: user-space parallel port driver
[   30.643106] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   30.643113] apm: disabled - APM is not SMP safe.
[   30.864293] Bluetooth: Core ver 2.11
[   30.864374] NET: Registered protocol family 31
[   30.864378] Bluetooth: HCI device and connection manager initialized
[   30.864382] Bluetooth: HCI socket layer initialized
[   30.890328] Bluetooth: L2CAP ver 2.8
[   30.890335] Bluetooth: L2CAP socket layer initialized
[   30.894699] Bluetooth: RFCOMM socket layer initialized
[   30.894717] Bluetooth: RFCOMM TTY layer initialized
[   30.894720] Bluetooth: RFCOMM ver 1.8
[   31.296381] PPP generic driver version 2.4.2
[   41.444229] NET: Registered protocol family 10
[   41.444394] lo: Disabled Privacy Extensions
[   41.444499] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.579368] ATM dev 0: ADSL line is up (1152 kb/s down | 288 kb/s up)
[   46.971042] PPP BSD Compression module registered
[   47.069069] PPP Deflate Compression module registered
[19350.833052] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK showMem Nice powerOff showPc unRaw Sync showTasks Unmount shoW-blocked-tasks 
karl@ubuntu:~$

---

### Post by russnash37 on 2007-11-10
Ok, dmesg didn't turn up much, however, it's not the only place we can look.

This time, when the lockup is over, please open a terminal again and paste the output of the following command:

          tail --lines 100 /var/log/messages

Hopefully, this will give us some more insight.

Russ.

---

### Post by POWERVICE on 2007-11-11
Russ, Here are the outputs from my last 2 lockups. Both times, the mouse jammed so I did nothing except try and move the mouse. After 2-3 min the lock up freed itself and I could continue. Karl.

karl@ubuntu:~$ tail --lines 100 /var/log/messages
Nov 11 09:01:48 ubuntu syslogd 1.4.1#20ubuntu4: restart.
Nov 11 09:32:43 ubuntu pppd[5354]: Connect time 40.7 minutes.
Nov 11 09:32:43 ubuntu pppd[5354]: Sent 1413058 bytes, received 9538392 bytes.
Nov 11 09:32:44 ubuntu pppd[5354]: CHAP authentication succeeded
Nov 11 09:32:44 ubuntu pppd[5354]: CHAP authentication succeeded
Nov 11 09:32:44 ubuntu pppd[5354]: local  IP address 80.42.125.192
Nov 11 09:32:44 ubuntu pppd[5354]: remote IP address 212.74.111.224
Nov 11 09:32:44 ubuntu pppd[5354]: primary   DNS address 212.139.132.10
Nov 11 09:32:44 ubuntu pppd[5354]: secondary DNS address 212.139.132.11
Nov 11 10:01:14 ubuntu -- MARK --
Nov 11 10:22:13 ubuntu -- MARK --
Nov 11 10:32:42 ubuntu pppd[5354]: Connect time 60.0 minutes.
Nov 11 10:32:42 ubuntu pppd[5354]: Sent 1131272 bytes, received 5423773 bytes.
Nov 11 10:32:42 ubuntu pppd[5354]: CHAP authentication succeeded
Nov 11 10:32:42 ubuntu pppd[5354]: CHAP authentication succeeded
Nov 11 10:32:42 ubuntu pppd[5354]: local  IP address 80.42.69.181
Nov 11 10:32:42 ubuntu pppd[5354]: remote IP address 212.74.111.224
Nov 11 10:32:42 ubuntu pppd[5354]: primary   DNS address 212.139.132.10
Nov 11 10:32:42 ubuntu pppd[5354]: secondary DNS address 212.139.132.11
karl@ubuntu:~$

---

### Post by POWERVICE on 2007-11-11
Russ, I have just carried out the mod as below. So far so good but I really need to run it for 2-3 
hours before too much happiness exists. I will let you know if this fixes the problem. I did not want you to waste any time unnecessarily. Thanks for your help so far. Karl




[http://ubuntuforums.org/showthread.php?t=588510&highlight=INTERNET+STALLS](http://ubuntuforums.org/showthread.php?t=588510&highlight=INTERNET+STALLS)

---

### Post by POWERVICE on 2007-11-11
Russ, Unfortunately this mod has not worked and the internet still locks up for a few  minutes so I am back to square one. Karl

---

### Post by philinux on 2007-11-11
If its firefox try the ipv6 fix

[http://kb.mozillazine.org/Network.dns.disableIPv6](http://kb.mozillazine.org/Network.dns.disableIPv6)

---

### Post by russnash37 on 2007-11-11
Ok, I've been thinking on this for a while this morning and am not coming up with anything concrete, although looking at your logs it seems that there are some interesting time intervals for the stalls, such as exactly 60 minutes, which makes me suspect that there's a small chance that LCP could be the culprit?

Turning off LCP link checking is definately worth a try, but first we need to ascertain where your configuration files are, so, get yourself to a terminal session:

1) cd /etc/ppp/peers

2) ls

  See how many files show up in the above list, there should be only one.  If there is only one, use the command 'cat' to show it's contents and paste it back here, i.e. 'cat filename'.  If there is more than one, go ahead and paste each one here in the same way and be sure to identify each by name when you paste them.

Once we have nailed down your ppp peer configuration file, we can look at what changes we need to make.

On a sidenote, I know we've already been over switching you to ethernet but I do think that it's worth looking further to see if we still can achieve this, I am 99.99999% sure that this switch would solve your problems if we could do it.  Have a good look all over your current DSL modem and your old one (the speedtouch?) for a port that says 'Ethernet' or 'LAN'.  I can see from your dmesg that your system already has an ethernet card, although we may need you to get hold of a cable (dont worry, they're cheap).  Lets look at both this and what I mentioned above at the same time.

Russ.

---

### Post by POWERVICE on 2007-11-11
Hi Russ, I have done everything you say.   Sometimes the lock ups can be within minutes of each other if that helps - maybe the 60min interval was just luck. On the ethernet subject all the ports on my modems are labelled up usb and there is only one port per modem - remember they are only the ones given out by tiscali. It would be no problem for me to buy an ethernet modem (I believe UBUNTU supports ALL ethernet modems) if you are that sure the problem lies there. Do you have a recommendation or are they all OK?
 I really do appreciate your help. Karl



karl@ubuntu:~$ cd /etc/ppp/peers
karl@ubuntu:/etc/ppp/peers$ cat provider  ueagle-atm  usbadslmodem  wvdial  wvdial-pipe
# example configuration for a dialup connection authenticated with PAP or CHAP
#
# This is the default configuration used by pon(1) and poff(1).
# See the manual page pppd(8) for information on all the options.

# MUST CHANGE: replace myusername@realm with the PPP login name given to
# your by your provider.
# There should be a matching entry with the password in /etc/ppp/pap-secrets
# and/or /etc/ppp/chap-secrets.
user "myusername@realm"

# MUST CHANGE: replace ******** with the phone number of your provider.
# The /etc/chatscripts/pap chat script may be modified to change the
# modem initialization string.
connect "/usr/sbin/chat -v -f /etc/chatscripts/pap -T ********"

# Serial device to which the modem is connected.
/dev/modem

# Speed of the serial line.
115200

# Assumes that your IP address is allocated dynamically by the ISP.
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
defaultroute

# Makes pppd "dial again" when the connection is lost.
persist

# Do not ask the remote to authenticate.
noauth

user '**deleted**@tiscali.co.uk'
password '**deleted**'
plugin pppoatm.so 0.38
noipdefault
usepeerdns
defaultroute
persist
noauth
cat: usbadslmodem: Permission denied
noauth
name wvdial
usepeerdns
noauth
name wvdial

plugin passwordfd.so

defaultroute
replacedefaultroute
karl@ubuntu:/etc/ppp/peers$

---

### Post by jaybombalous on 2007-11-11
I'll back russ on this one and say go Ethernet. USB is sketchy, maybe u could check for a bios update that would solve certain usb issues. Don't just update the bios firmware for the hell of it, u can cause some serious dmg.

Remember just because the PC is new to you doesn't mean the hardware inside was made yesterday...

---

### Post by POWERVICE on 2007-11-11
Hello philinux,
                           i have followed your link but I must admit I have not done anything a I did not understand what to do if anything.  I have changed alias net-pf-10 ipv6 to alias net-pf-10 off as recommended at [http://ubuntuforums.org/showthread.php?t=588510&highlight=INTERNET+STALLS](http://ubuntuforums.org/showthread.php?t=588510&highlight=INTERNET+STALLS)

However system still locks!

---

### Post by philinux on 2007-11-11
It may be a long shot but it is reversable easilty.

Just type 

```
about:config
```

into the address bar press enter

then for the filter type network.dns

you should see the ipv6 line just double click it to toggle between false to true.

---

### Post by POWERVICE on 2007-11-11
Ok Phil,
              I am giving it a go. Thanks

---

### Post by Supergoo on 2007-11-11
This sounds like a hardware problem,  or there is a driver issue, so this lock up only occurs when you connect to the internet ? Run a memory test from the boot menu, also check that all your fans are working in the computer, could be a temp issue. But this is very strange,let us know any other symptoms.




Supergoo

---

### Post by POWERVICE on 2007-11-11
Phil,
         Changing the ipv6 line has made no difference I am afraid.
 
Supergoo, I have already ran the memory test and no errors were reported. All the fans are ok.
The processor fan is only 2 months old and still perfectly clean. The pc is out of it's cupboard and running just fine. Windows has no problems at all and I run firefox on xp as well. I am going to buy a new router to try an ethernet connection. I do not know of any other symptoms but all I really use the pc for is internet and the UBUNTU spreadsheet which I spent a while trying to jam up yesterday and it kept working perfectly.

---

### Post by russnash37 on 2007-11-11
Karl,

If you are more than happy to move to an ethernet based DSL modem then I would certainly recommend that route, you will find that the DSL performance should improve also.

Going back to the other route, the files you pasted earlier, I recommend you make the following change to the one with the 'tiscali.co.uk' lines in it (this is obviously the one being used as it contains your ISP!).

You should open this file with a text editor, you may need to use sudo for this, and add the following two lines to the end of the file:

lcp-echo-failure 0
lcp-echo-interval 0

You will then need to restart the DSL connection to pick up the changes, or you can just reboot if unsure.

Russ.

---

### Post by POWERVICE on 2007-11-12
Hi Russ,
                 I am afraid this has not worked either. I am going to sort out  an ethernet modem as you advise and give that a go. Thanks for all your time and help.  Karl

---

### Post by POWERVICE on 2007-11-20
I have just installed a new ethernet modem sent FOC by TISCALI - a speedtouch510 (I know there are much more advanced ones) but it takes about 1 minute to set up (simply plug in an attempt to visit any website (eg [www.tiscali.co.uk](www.tiscali.co.uk)). This opens up the THOMSON wizard which asks you for your name and password. Unfortunately this has not worked as the system is still locking up. Please can someone advise if it is possible to use UBUNTU without any lock ups or whether UBUNTU just does keep locking up. If you can solve the problem for me then let me know.

Thanks

---

