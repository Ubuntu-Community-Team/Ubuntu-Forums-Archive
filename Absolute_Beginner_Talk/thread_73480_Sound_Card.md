---
title: "Sound Card"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by Vladimirm on 2005-10-09
How do i install my sound card??
On the drivers disk that comes with it are a set of instructions but a)i cant understnad alot of it and b)i think its meant fo ranother distro

---

### Post by Lord Illidan on 2005-10-09
Perhaps I should ask the obvious question..

What is your soundcard? Specify the make and model. We don't read minds.

---

### Post by Vladimirm on 2005-10-09
Edited for being rude.
It says on the box that its a multi channel PCI cound card CMI8738

---

### Post by Kapre on 2005-10-09
[QUOTE=Vladimirm]What do you mean you dont read minds!!!!! what sort of place is this!!!!
It says on the box that its a multi channel PCI cound card CMI8738[/QUOTE]

Sir/Mam - we are trying to help. LordIllidan is just asking for the make and model of your sound card. I dont see anything bad about asking for it. Please refrain from using exclamation points. You cannot get help by having that kind of attitude.

---

### Post by Vladimirm on 2005-10-09
no offense intended, its the standard cavalier british atidude to awkward situations in which we are placed in a position where we need ot do something that we are completely ignorant to. Very very hard to get it right in text form. Please forgive me

---

### Post by Kapre on 2005-10-09
vlad - you can try this [thread]("http://www.ubuntuforums.org/showthread.php?t=32063&highlight=cmi")

---

### Post by Vladimirm on 2005-10-09
tried that but theres a problem with alsa, i dont htink its installed, or configured correctly

---

### Post by Lord Illidan on 2005-10-09
I have the exact same sound card.. CMI 8738. And it worked in all Linux distros correctly. Did you install using a server install or normal basic install?

---

### Post by Vladimirm on 2005-10-09
you knwo i new somebody would come up and put a pin in it. i do not know how to install the drivers.
It asks me in the read me file to save config.ini i think it is into a directory but the directory doens texist im in way over my head

---

### Post by Vladimirm on 2005-10-09
Audio driver for CM8338/CM8738 chips by Chen-Li Tien





HARDWARE SUPPORTED

================================================================================

C-Media CMI8338

C-Media CMI8738

On-board C-Media chips





WHAT'S NEW

================================================================================



  1. Support modem interface for 8738. (select in kernel configuration)

  2. Enable S/PDIF-in to S/PDIF-out (S/PDIF loop).

  3. Enable 4 channels analog duplicate mode on 3 jack or 4 jack

     configurateion.

  4. Enable joystick support. (joystick driver needed)





STEPS TO BUILD DRIVER

================================================================================



  1. Backup the Config.in and Makefile in the sound driver directory

     (/usr/src/linux/driver/sound).

     The Configure.help provide help when you config driver in step

     4, please backup the original one (/usr/src/linux/Document) and

     copy this file.

     The cmpci is document for the driver in detail, please copy it

     to /usr/src/linux/Document/sound so you can refer it. Backup if

     there is already one.



  2. Extract the tar file by 'tar xvzf cmpci-xx.tar.gz' in the above

     directory.



  3. Change directory to /usr/src/linux



  4. Config cm8338 driver by 'make menuconfig', 'make config' or

     'make xconfig' command.



  5. Please select Sound Card (CONFIG_SOUND=m) support and CMPCI

     driver (CONFIG_SOUND_CMPCI=m) as modules. Resident mode not tested.

     For driver option, please refer 'DRIVER PARAMETER'



  6. Compile the kernel if necessary.



  7. Compile the modules by 'make modules'.



  8. Install the modules by 'make modules_install'





INSTALL DRIVER

================================================================================



  1. Before first time to run the driver, create module dependency by

     'depmod -a'



  2. To install the driver manually, enter 'modprobe cmpci'.



  3. Driver installation for various distributions:



    a. Slackware 4.0

       Add the 'modprobe cmpci' command in your /etc/rc.d/rc.modules

       file.so you can start the driver automatically each time booting.



    b. Caldera OpenLinux 2.2

       Use LISA to load the cmpci module.



    c. RedHat 6.0 and S.u.S.E. 6.1

       Add following command in /etc/conf.modules:



       alias sound cmpci



	also visit [http://www.cmedia.com.tw](http://www.cmedia.com.tw) for installation instruction.



DRIVER PARAMETER

================================================================================



  Some functions for the cm8738 can be configured in Kernel Configuration

  or modules parameters. Set these parameters to 1 to enable.



  spdif_loop:   Enable S/PDIF loop, this route S/PDIF-in to S/PDIF-out

                directly.

  four_ch:      Enable 4 channels mode, rear-out or line-in will output

                the same as line-out.

  rear_out:     Enable this if you have independent rear-out jacket on

                your sound card, otherwise line-in will be used as

                rear-out.

  modem:	You will need to set this parameter if you want to use

		the HSP modem. You need install the pctel.o, the modem

		driver itself.

  joystich:	Enable joystick. You will need to install Linux joystick

		driver.
Is the readme file but im new to linux and i dont knwo what im suppose dto do

---

### Post by RagingOcelot on 2006-01-08
What an appallingly bad translation of a README file.  I'm lost now having read through half that file.  Can anyone make heads or tails on how to install this driver or should I just stop wasting time and find some other cheap sound card with more understandable Linux install instructions?

---

