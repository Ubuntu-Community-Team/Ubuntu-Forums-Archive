---
title: "Asus EeePC 900 Netbook"
date: 2012-04-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by peterqb on 2012-04-07
When trying to install Ubuntu (ubuntu-11.10-desktop-i386.iso) using an external disk or a pen drive, in both cases the BIOS would not alter to allow the computer to boot from the other device. The option appeared greyed out.

It has Windows XP installed, and a solid state disk. I would like a clean install of just Ubuntu.

Could anyone shed any light on this. TIA
--
pqb

---

### Post by Plumtreed on 2012-04-08
I have not installed Ubuntu but I have installed PeppermintOS to my 701SDX. Peppermint is based on Ubuntu and follows a similar install process. I installed from a live CD and followed the suggested steps. I allowed the 'installer' to use the entire disk and did not partion for a swap file.

This should boot directly without reference to the Bios.

---

### Post by peterqb on 2012-04-09
Thanks for the reply. The problem is that the computer does not have an optical drive.

How do I get it to boot from either a USB external disk or a pen drive? The BIOS setting could not be changed, as they were greyed out. I wasn't trying to change BIOS setting beyond the boot order, which is necessary in order to stop the computer booting into Windows XP, which is currently installed.
--
pqb

---

### Post by barrieluv on 2012-04-09
You need to create a bootable stick using Unetbootin under XP.
Download and install Unetbootin from [here](http://unetbootin.sourceforge.net/).
Select the .iso you downloaded, point it to the stick and then reboot. Tapping the Escape button as the machine boots should bring up the option to boot from the stick.

It should be pointed out that if you have the 900 with the 4GB and 16GB drives, you will have to install it to the 16GB drive as the newer Ubuntus won't install to a 4gB drive. If you have the one with a single 20GB drive you will be fine.

---

### Post by Plumtreed on 2012-04-09
I guess the first question is what do you have on the 'pendrive'? If it is the Ubuntu ISO it should boot to a menu which will allow you to install.

---

### Post by peterqb on 2012-04-10
Thanks very much. I'll give this a try.
--
pqb

---

### Post by snowpine on 2012-04-10
On most Asus EEE's you press Esc at boot to choose the device.
If this doesn't work then go into your BIOS options and make sure "boot booster" is disabled.

---

