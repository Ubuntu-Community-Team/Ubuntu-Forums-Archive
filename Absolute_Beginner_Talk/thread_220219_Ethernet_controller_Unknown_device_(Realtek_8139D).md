---
title: "Ethernet controller: Unknown device (Realtek 8139D)"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by jagannath on 2006-07-21
Have been trying to get Breezy detect my ethernet card to no avail.

Following are the results of my attempts:

lspci gives me:

 0000:00:08.0 Ethernet controller:Unknown device 1904:2031(rev 01)

modprobe -a 8139too gives me:
Error inserting mii (/lib/modules/2.6.12-9.386/kernel/drivers/net/8139too.ko: operation not permitted.

The driver software I got with the ethernet card (Realtek 8139D) a zipped archive consisting of the following files:

1.8139too.c
2.Makefile
3.readme.txt

The readme files is as follows:

8139too.c release note
2001/10/31 by ShuChen Shao

1.This driver was originally based on 8139too.c version "0.9.15".
	
2.It has been enhanced to support RTL8139C+ PCI ethernet controller.

3.RTL8139C+ PCI ethernet chips is set to support C+ mode by default.
  If FORCE_C_Mode below is enabled, the RTL8139C+ chip will be forced to support C mode 
  after reboot.


4.This program can be compiled using the attached Makefile.
  Please remember to SPECIFY "NEW_INCLUDE_PATH" in Makefile according to your linux environment.
  The object file named 8139too.o should be moved to the directory 
  /lib/modules/<linux-version>/kernel/drivers/net/
  The driver could be brought up by the following steps:
	'insmod 8139too'
	'ifconfig eth0 up'

5.It can support Auto-Negotiation ability,that is
	10-half	 0x01
	10-full	 0x02
	100-half 0x04
	100-full 0x08
  If 10-half mode is expected, it can be achieved by the following steps:
	#ifconfig eth0 down
	#rmmod 8139too
	#insmod 8139too media=0x01

6.If the "Install Type", selected during the Linux install procedure, is "laptop",
  this driver can work normally for CardBus application without any modification.
  Otherwise, reinstall Linux and select "Install Type" as "laptop". 
  Then this driver can also work.

---------------------------------------------------------------------------------------
8139too.c version 1.5.0 release note
2003/3/4 by ShuChen  Shao

1.Add flag in Makefile to specify access type to operation register on PCI
ethernet chips.

--

As a windows user all this is a bit too baffling.

Would appreciate some help in installing the driver so that I could have my Breezy up and running and connected to the internet.

I am now online through the same ethernet card and XP.

Thanks,

Jaggu

---

### Post by Balvinder on 2006-10-07
hi buddy,
          i just read your notes the other day and it has been a long time since you posted them.i am surrounded by the same prob tht you are facing right now..i also downloaded the same drivers tht u have mentioned below but being  complete newbie i know nothing than just installing a few apps on linux and installing and removing of the complete os..so if you have found the solutio n to ur prob please please..let me knw..

any help  would be great,,

thanxz,,already

balvinder..

---

