---
title: "installing usb to rs232 adapter in wine"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by tay on 2005-12-13
i am trying to get an audi diagnostic k+l interface cable to work with my wine program vag-com, so i need to copy those driver files to wine so i can then install in wine.   I don't know how to install in wine either.

this is the cd
root@sahaihost:/media/cdrom0/driver# ls
CCPORT.SYS  HIDCOM.INF  HidComInst.exe  HidCom.sys  RS232????.txt  WDMMDMLD.VXD
root@sahaihost:/media/cdrom0/driver#

and this is the text they attached.

"Driver setup:

double click HidCOMInst contained the INF fils and driver derectory.Nothing will 

appear.then plug the usb device,You can setup by the winzard.



Under some circustances,Windows Xp fails to load the HIDCOM driver,and instead loads

the Windows HID driver for the device.In this case,follow the steps below to force

windows to use the HIDCOM driver.

1.Open up the device manager.

2.Find the Human Interface Device Key related to USB to Serial and right chick on it.

3.Select Update Driver

4.Select"Install from list from specific location" and click Next

5.De-select"Search removable media",Then select"Include this location in Search".

6.Click Brower.Find the directory containing the Ccport.sys driver and click OK.

7.Select"Don't search,Iwill choose the driver to install".Then click Next.

8.Select"SemiTech USB-HID->COM device" and click Next.

9.Windows will prompt you for the HIDCOM.sys driver.Click Browse and locate HIDCOM.sys

  and ckick Next   "
 


Sounds easy in windows.  anyays,  i hope somebody can help me.
I really want to hack on my audi's computer.

---

### Post by tay on 2005-12-13
i copied the driver to wine and installed it from wine.  sorry.  that was a dumb question.

---

### Post by tay on 2005-12-13
this is what i am really asking?

after installed..  how do i get this program to recognize my adapter for a com port.

---

