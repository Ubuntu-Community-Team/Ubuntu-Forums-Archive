---
title: "HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72"
date: 2012-09-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by redpiersystems on 2012-09-15
Before doing *anything* to your new Asus G75VW notebook, REMEMBER TO LOG IN TO YOU WINDOWS INSTALL AND CREATE A RECOVERY DISK. You will NOT be able to run the Recovery software after modifying the bootloader. (I tried setting up dual-booting, and found this out the hard way. If anyone could be so kind as to make a recovery disk for me, I'd appreciate it. I have my own Win7 key)

HOW TO install Ubuntu on your Asus G75VW (no dual boot)

STEP 1:

 - Make a bootable DVD of the latest and greatest Ubuntu Desktop (32-bit) distribution.

STEP 2:
 - Insert the bootable DVD into your bluray/DVD drive. Restart your machine. REMEMBER to press the ESC key as soon as the machine boots up in order to get the boot menu.

STEP 3:

 - As soon as you see the color purple (that screen with the keyboard symbol and a human outline), hit any arrow key. You should be presented with a list of actions, including the option to simply run the live CD, and install. DO NOT simply hit enter. You will need to do the following...

STEP 4:
 - Select Install, but modify the entry by pressing F6 before hitting enter. You will need to set "acpi=off" ...otherwise, your machine will hang and you won't get to the install process. After selecting the "acpi=off" option, hit ENTER to continue.

STEP 5:
 - When the installer presents you with the options to "download updates" and "install 3rd party" stuff, MAKE SURE BOTH CHECKBOXES ARE CHECKED. You WILL need internet connectivity. Wireless should work, just click the networking icon in the top right, and connect to your wireless network as usual, ...or simply plug in an ethernet cable to your network. In fact, go ahead and PLUG IN VIA ETHERNET cable. It's safer that way. Go through the entire installation set up. I simply selected the entirety of SDA (the SSD drive) and completely overwrote it with the Ubuntu install.

STEP 6:

 - After the installation routines complete, you will be asked to restart your machine. Go ahead and follow the instructions to restart, remove the DVD from your drive and restart.

STEP 7:
 - When you restart, and are presented with the GRUB bootloader screen, do *NOT* simply hit enter for the first option. Use the second option, the one that says "Ubuntu (recovery)" or something to that effect.

STEP 8:
 - When the Ubuntu Recovery menu appears, you will need to enable networking by selecting the "Enable Networking" option and hitting enter. If you encounter issues with no wireless networks showing up, you may need to manually add your wireless network's ESSID via a Terminal. Open up a Terminal window and see the following help info to accomplish this ```
iwconfig --help
```

STEP 9
 - You will be presented with the Ubuntu Recovery menu again, this time, select the "Root shell" (or whatever that option is for the root prompt is), and hit enter.

STEP 10
 - You will need to install the NVIDIA DRIVERS. Do this by typing ```
apt-get install nvidia-current
``` ...Press ENTER.

STEP 11
 - When the nvidia driver installation completes, type ```
exit
``` and press enter. This will send you back to the Ubuntu Recovery menu.

STEP 12
 - Select the "RESUME" option, and press enter. You will now see the Ubuntu Desktop log in screen.

STEP 13
 - After logging in, you will need to open up a Terminal window, and run the nvidia-xconfig utility by typing the following: ```
nvidia-xconfig
``` ...and then pressing ENTER. You may be asked for your password, as this action requires sudo/root privileges.

STEP 14
 - That's all for now. Disconnect your ethernet cable and restart. You can now select the default GRUB boot option when you restart. Enjoy!

:popcorn:

---

### Post by mudien on 2012-09-17
Thank you sooooo much for this!

---

### Post by mhoude on 2012-11-16
Hi,

I've made the same mistake as you did.

Did you found the recovery disks ?

Looks like I need them too...

Thanks in advance

Mike

---

### Post by willkzhang on 2012-11-29
> **redpiersystems said:**
> Before doing *anything* to your new Asus G75VW notebook, REMEMBER TO LOG IN TO YOU WINDOWS INSTALL AND CREATE A RECOVERY DISK. You will NOT be able to run the Recovery software after modifying the bootloader. (I tried setting up dual-booting, and found this out the hard way. If anyone could be so kind as to make a recovery disk for me, I'd appreciate it. I have my own Win7 key)

HOW TO install Ubuntu on your Asus G75VW (no dual boot)

STEP 1:

 - Make a bootable DVD of the latest and greatest Ubuntu Desktop (32-bit) distribution.

STEP 2:
 - Insert the bootable DVD into your bluray/DVD drive. Restart your machine. REMEMBER to press the ESC key as soon as the machine boots up in order to get the boot menu.

STEP 3:

 - As soon as you see the color purple (that screen with the keyboard symbol and a human outline), hit any arrow key. You should be presented with a list of actions, including the option to simply run the live CD, and install. DO NOT simply hit enter. You will need to do the following...

STEP 4:
 - Select Install, but modify the entry by pressing F6 before hitting enter. You will need to set "acpi=off" ...otherwise, your machine will hang and you won't get to the install process. After selecting the "acpi=off" option, hit ENTER to continue.

STEP 5:
 - When the installer presents you with the options to "download updates" and "install 3rd party" stuff, MAKE SURE BOTH CHECKBOXES ARE CHECKED. You WILL need internet connectivity. Wireless should work, just click the networking icon in the top right, and connect to your wireless network as usual, ...or simply plug in an ethernet cable to your network. In fact, go ahead and PLUG IN VIA ETHERNET cable. It's safer that way. Go through the entire installation set up. I simply selected the entirety of SDA (the SSD drive) and completely overwrote it with the Ubuntu install.

STEP 6:

 - After the installation routines complete, you will be asked to restart your machine. Go ahead and follow the instructions to restart, remove the DVD from your drive and restart.

STEP 7:
 - When you restart, and are presented with the GRUB bootloader screen, do *NOT* simply hit enter for the first option. Use the second option, the one that says "Ubuntu (recovery)" or something to that effect.

STEP 8:
 - When the Ubuntu Recovery menu appears, you will need to enable networking by selecting the "Enable Networking" option and hitting enter. If you encounter issues with no wireless networks showing up, you may need to manually add your wireless network's ESSID via a Terminal. Open up a Terminal window and see the following help info to accomplish this ```
iwconfig --help
```STEP 9
 - You will be presented with the Ubuntu Recovery menu again, this time, select the "Root shell" (or whatever that option is for the root prompt is), and hit enter.

STEP 10
 - You will need to install the NVIDIA DRIVERS. Do this by typing ```
apt-get install nvidia-current
``` ...Press ENTER.

STEP 11
 - When the nvidia driver installation completes, type ```
exit
``` and press enter. This will send you back to the Ubuntu Recovery menu.

STEP 12
 - Select the "RESUME" option, and press enter. You will now see the Ubuntu Desktop log in screen.

STEP 13
 - After logging in, you will need to open up a Terminal window, and run the nvidia-xconfig utility by typing the following: ```
nvidia-xconfig
``` ...and then pressing ENTER. You may be asked for your password, as this action requires sudo/root privileges.

STEP 14
 - That's all for now. Disconnect your ethernet cable and restart. You can now select the default GRUB boot option when you restart. Enjoy!

:popcorn:

I got stuck on step 8 and step 10.
for step 8 my laoptop freezes at a long piece commandline text,which seems to be unable to mount a partition.
then i skipped 8 and go to 9 ->10
but after executing installation command from 10,i got error message:
W: Not using locking for read only lock file /var/lib/dpkg/lock E: Unable to write to /var/cache/apt/ E: The package lists or status file could not be parsed or opened.

can you give me some help please?:(

---

### Post by rDwyP44y on 2012-12-04
Thank you sooooo much, this just savd my life!

---

### Post by cjhoward on 2013-02-14
I was able to successfully make a Windows 8 recovery disc after dual-booting with the Asus G75VW.  Try changing the boot order in the BIOS (F2 during startup).  I set Windows as the default boot option and there was no issue in making a recovery disc after installing Ubuntu.

Everything on the Ubuntu side seems to be working **aside from the wireless driver**.  There is no proprietary wireless driver listed in Software Sources.  Wireless networks show up but none will connect (given correct password, SSID, security protocol, etc).  Step 8 in the original post does not solve the issue.  The Unity wireless icon keeps fading in and out like it's trying to connect, however, using the ethernet jack on the machine works just fine.  After hard-wiring my internet connection, I was able to download and install updates but still no proprietary wireless driver.  I've installed Ubuntu twice-over with the same result.

Anyone else getting this same issue?  I'm running Ubuntu 12.10 64-bit with the default graphics driver (non-Nvidia).

---

### Post by wongda on 2013-07-11
Here are some quick notes regarding my own battle with getting Ubuntu 12.04.1 on Asus G75vx:

1. Need to disable secure boot and book with UEFI on the CD

2. No need to set acpi=off if you boot UEFI 

3. If things get stuck, run ubiquity with debug (ubiquity --debug) and look at /var/log/installer/debug and see what is happening.

4. I got stuck at the "Preparing Installation ..." because:

    a. I selected "3rd party / Internet download" ... deselect those get me pass this
    b. modprobe wl   - the wireless card is not working, and it got stuck there forever ... ps axuww  | grep modprobe and kill -9 the process will get you going again.

Other than that, so far so good...

---

### Post by wongda on 2013-07-11
Here is my little report for installing on ASUS G75VX

1. Turn secure boot off, press F2 when powering up, and change and save setting, only then you can enable CSM

2. Boot DVD, at purple screen, please arrow keys, press F6 to put acpi=off, this is important, otherwise, it will hang.

3. My touchpad is not working, you can plug a mouse if this bother you during install (it will work after install). If not, TAB/Space/Enter are your friends.

4. Process until you see "Preparing Ubuntu install or something like that" ... check download / 3party ...

5. Ubuntu hangs here forever because it is doing a modprobe wl  and the broadcom driver doesn't work.

6. Switch to the terminal CTRL-ALT-F1 and sudo bash, do a ps awux | grep modprobe wl    find the pid and kill -9 it.  

7. This will happen again in about 70% of the installation, when ubuntu trying to activate wireless again.  Repeat #6.

8. I upgrade the NVIDIA driver, I use experimental ... blender recognize it out-of-box. I can use the GPU through CUDA

9. apt-get install build-essential   

10. Download ndiswrapper here (apt-get install ndiswrapper-dkms doesn't work, compile fail!!) 

[http://sourceforge.net/projects/ndiswrapper/files/stable/](http://sourceforge.net/projects/ndiswrapper/files/stable/)

11. I used ndiswrapper-1.58 and it compiles out-of-box.

12. Download Broadcom window driver: 

[http://www.asus.com/Networking/PCEAC66/#support_Download_17](http://www.asus.com/Networking/PCEAC66/#support_Download_17)
[URL="http://www.stchman.com/install_ndis_broadcom.html"]
13. apt-get install ndiswrapper-utils-1.9

14. ndiswrapper -i bcmwl5.inf

after that, you should be able to do:

# ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:43B1) present

15. modprobe ndiswrapper 

16. vi /etc/modprobe.d/ndiswrapper.conf   empty the file

17. ndiswrapper -m

18. echo ndiswrapper >> /etc/modules

http://www.stchman.com/install_ndis_broadcom.html[/URL]


my wireless is working with encryption after reboot without any modifications... 

BTW, if your G75vx doesn't use broadcom chip, the above will obviously not work ... check here:

# lspci -vvnn | grep Broadcom
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:**43b1**] (rev 03)


SOund is working, Fn keys are working, keyboard light is working, I am a happy man!!

You should be too ...

---

