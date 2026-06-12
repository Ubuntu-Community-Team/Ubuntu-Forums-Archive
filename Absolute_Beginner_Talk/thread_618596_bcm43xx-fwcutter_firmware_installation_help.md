---
title: "bcm43xx-fwcutter firmware installation help"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by linux4life88 on 2007-11-20
I downloaded this file from packeges.ubuntu.com. I needed this driver for my Broadcom chip to work although after I installed it I went to the Restricted Drivers window and it was still there listed. So I checked enable and it brought up a window that says Specify Firmware location. Where would the firmware be located? I'm using Ubuntu 7.10. I've looked in /lib/firmware and my choices are 2.6.22-14 generic folder and bcm43xx_microcode11.fw. The bcm files says when opened "this is just a fake file to prevent postinst scripts." I open the folder and there is nothing even close to what the file name is. So when I'm trying to enable my card where will the file for the driver be located on my computer? I need to know to enable my wireless card in the Restricted Drives area. Please help.

---

### Post by Pumalite on 2007-11-20
I'm not much of a wireless guy, but see if this helps:(this recipe is for Suse)

    * On an HP Pavilion zv6000 laptop the driver configures automatically on a fresh install but is not funcional; the BIOS still reads that the card is enabled but if you watch the boot messages you'll see a line saying radio is disabled. The 1-touch-button for enable/disable wireless is off and pushing the button or using KWifiManager does not remedy the problem. Installing bcm43xx-fwcutter firmware will fix this problem. 

1. You need to check if the bcm43xx-fwcutter package is installed through: Yast > Software > Software Installation and search for bcm43xx-fwcutter

2. Find the windows driver for your wireless chip. An example windows driver was titled bcmwl5.sys Also note if you can't find yours try doing a google search for wl_apsta.o (SUSE worked with both the orginal windows driver and the wl_apsta.o at the time of this WIKI post). Put the driver file on your desktop in SUSE.

3. Start the shell console (Kmenu >System > Terminal Program > Terminal) and login as root with the command:

sux -

and type in the root password

Extract your firmware files from your wireless chip and store them in the firmware file by typing in the following. (Note: Swap out the name of your driver accordingly...in this example it is wl_apsta.o):

 bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o

4. Another way to install the firmware is using the install script included in the bcm43xx-fwcutter package. You need to have a working internet connection for this as it is attempted to download wl_apsta.o, next the firmware is extracted and stored in /lib/firmware.

 install_bcm43xx_firmware 

5. Now that the firmware is ready for the driver to use, load the module by typing the following:

 modprobe bcm43xx

6. Reboot and now you can configure your WLAN card through YAST > Network devices > Network card

---

### Post by arochester on 2007-11-20
I have found this very helpful, right down to Problem 1: [http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+wireless+feisty](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+wireless+feisty)

---

### Post by CCNA_student on 2007-11-20
I also had a wireless NIC from Broadcom(BCM 9413) and could not get it to work either. I went on Broadcom's website and it seems that no Linux driver exists for any of Broadcom's recently manufactured wireless NIC's. They have not released the source code for the Firmware(software stored in hardware basically). So what I did was buy a wireless NIC from Intel, the Intel 2915ABG for about $25. And this works very well.

---

### Post by duruttye on 2007-11-20
I just installed it.
In the restricted driver manager, when it asks you where the driver is, it should provide an internet location too, and thats the source where I installed from. No big deal.

Hope it helps.

---

### Post by brn on 2007-11-20
Here are some links you can check for starters.  Some may not apply to Gutsy but the information and links are worth studying.
```
http://ubuntuforums.org/showthread.php?t=405990
https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff
https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)
https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx
```
I struggled for months trying to make the Broadcom 4311 work with Feisty on a Compaq laptop. Finally got it to work with ndiswrapper but also had to install wifi-radar (from the repository) to run at startup (System > Preferences > Sessions).  Occasionally I have to run wifi-radar from a command line, sometimes repeatedly, to connect the wireless.  

**Note:**  If you download the driver (a source should be listed in one of the referenced guides) get the XP version.  The Vista driver doesn't seem to work with anything.

---

### Post by linux4life88 on 2007-11-20
Durutty, I couldn't get your idea to work, but I'm trying arochester and Pumalite help. I've use Ubuntu since version 5.04 but this is the first time I've tried to use a wireless card. Thanks for the help.

---

### Post by linux4life88 on 2007-11-20
Also, I'm thinking about taking CCNA_student advice and just get a new wireless card. It says that my broadcom card is a wlan mini-PC card, so any suggestions on a wireless card that plays nice with Ubuntu would be nice.

---

### Post by duruttye on 2007-11-20
Sorry to hear that, I just shared with you, what I did.
Maybe someone will have a better idea.

Take care.

---

### Post by linux4life88 on 2007-11-20
Thanks for the help duruttye, if someone could help me with what the name of the file would be after I install the .deb driver that I need to choose in the Restricted Hardware area then I think I could get it up and running. Or like I said, name some good wireless cards that play nice with Ubuntu 7.10.

---

### Post by CCNA_student on 2007-11-20
I use the Intel 2915ABG wireless NIC. I use Xubuntu 7.10 and the wireless NIC runs very well. Just go to intel.com or look on amazon.com, which is where I got my wireless NIC from.

---

### Post by linux4life88 on 2007-11-20
I finally got it to work. I downloaded this file [http://home.nc.rr.com/thehinnants/stuff/drivers/64_bit_drivers.zip]("http://home.nc.rr.com/thehinnants/stuff/drivers/64_bit_drivers.zip") and used it as my file and it worked. Thanks again for all the help.

---

### Post by anewguy on 2007-11-20
For others reading this forum who have similar problems with a BCm43xx series wireless card, I personally would recommend using ndiswrapper and the Windows driver.  It installs quite easily and has always worked for me.  Some will tell you to download the latest source for ndiswrapper and compile it, but I have never found that needed for the 43xx series - just use ndiswrapper.

If you can get your card working with the firmware cutter method that is good too, although I have read some threads on this forum about problems with that (randomly dropping, etc.).

Just thought I'd relay another option for the newbies reading this,:)

---

### Post by linux4life88 on 2007-11-21
I'm thought I was making headway but I finally figured out (really stupid on my part) that my card is a Broadcom BCM94311MCG wlan mini-PCI card. I'm guessing that the bcm43xx file will not work for my card? It ended up that it only worked once then crashed. I need to find the Windows driver for this file, I know but I was also wondering if the bcm43xx file will work with my card at all.

---

### Post by brn on 2007-11-23
Try a Google search for BCM94311.  Perhaps one or more of the links there can point you to the correct driver.

---

