---
title: "asus k53tA"
date: 2012-01-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by spantch101 on 2012-01-01
ok so i have been using ubuntu on my toshiba satellite and asus k50id for the past few years now, with a lot of trial and error learning with this amazing OS, but i just went and bought a new k53TA from asus and i cannot run 64 bit as soon as the loading screen comes up asking to install the os no matter my choice my screen goes black, i have tried using directly from live cd and i know its running and i can hear the system sounds but no visual at all its like zero power going to my lcd ... any ideas ? my specs are as follows :

ASUS K53TA:
amd A6 3400m Quad Core 1.4/2.3ghz
4gb ram ddr3
Radeon HD6720G2 1GB
500GB 
Win7 Premium 64 bit

Any Ideas? i can run 32 bit ubuntu for now i guess, but i want to take advantage of my full 4 gb plus i have another 4gb to put in so i'd like to get 64 bit working. thanks in advance.

---

### Post by adrien214 on 2012-01-16
Install the PAE for the 32bit version, you will get full memory support but the speed sucks ball. As for the black screen on the 64bit, did you try to run it from a CD/USB?

---

### Post by odu dan on 2012-01-25
I also have the problem with the black screen on 64-bit Ubuntu 11.10.  I have tried installing off of a USB as well as the wubi installer, with the same result.

---

### Post by odu dan on 2012-01-27
I believe the black screen is a result of the Ubuntu installation lacking the proper display driver for the A6-3400 integrated GPU.  I will try to confirm this by looking up whether or not users of other laptops with AMD APUs also have trouble.

Otherwise, how could this proprietary driver [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx) , released a few days ago, be included in the installation if the CD or USB method is used?

---

### Post by xenon53 on 2012-01-28
Guys i have the same laptop and the same problem.The gpu sends the graphics to the HDMI port and not to the display of the laptop.You can see the graphics if you connect the laptop to an external monitor via HDMI cable.
Does anyone know how can i make the laptop display the default display?

---

### Post by odu dan on 2012-01-28
Thanks for pointing out that HDMI works.

After installing Ubuntu using a separate HDMI display, simply use the "Additional Drivers" tool and download the ATI proprietary driver that is available.  Restart the computer, and then Ubuntu will use the laptop's display.  Unplug your HDMI and you're good to go!

---

### Post by xenon53 on 2012-01-28
> **odu dan said:**
> Thanks for pointing out that HDMI works.

After installing Ubuntu using a separate HDMI display, simply use the "Additional Drivers" tool and download the ATI proprietary driver that is available.  Restart the computer, and then Ubuntu will use the laptop's display.  Unplug your HDMI and you're good to go!

Have you tried this?Can i install these drivers into my live persistent USB drive?I dont want to install ubuntu in my hard drive yet,maybe later.

---

### Post by odu dan on 2012-01-28
It works fine.  I am a noob and have no clue how to include the driver on a USB installation.  I had to use a separate monitor.

Make sure its just the regular proprietary driver, and not the one that says "(post-release updates)" as that one does not work.

---

### Post by odu dan on 2012-01-31
Beware, there appears to be a bad update distributed through Update Manager.  Browsing through the 324 available updates, I'm not sure which one it is.  This bad update breaks the computer's ability to boot up into Ubuntu.  The error given is 

"Stopping crash report"                                                                [fail]

...or something along those lines.


You are still able to boot into recovery mode, however.

---

### Post by sandy8925 on 2012-02-14
Hello everyone. I have this laptop as well. There was a bug in Linux kernel 3.0 because of which the display doesn't work on this laptop (and some others as well). However this has been fixed in Linux kernel 3.2. Apparently, Ubuntu kernel 3.0.0-16 works, so please try installing it. If you need to install Ubuntu 11.10, I suggest installing Ubuntu 11.04 and upgrading to ubuntu 11.10 (but make sure that you install either the 3.0.0-16 kernel or compile and install Linux 3.2 kernel before rebooting after upgrading - preferably install before doing the upgrade).

---

### Post by Linuxisfast on 2012-03-23
I had no luck installing Ubuntu on this laptop, I have tried the alternate edition as well. Also added nomodeset to kernel but all I get is blank screen on boot. Only beta 12.04 works but after installing Catalyst, playing any movies blanks the screen and logs the machine out.

Same results with Fedora, PCLOS, LMDE and SUSE, only arch based Chakra with latest open source video stack came to the rescue. It installs fine but has issues with the wireless, after a dist-upgrade, everything works fine and fast, Catalyst installs and runs without hitches, full HDMI videos with VLC consume around 12% average CPU. So for anyone using this laptop, Chakra is the answer for Linux world. Chakra also uses latest kernel so all features of CPU and dual GPU in this laptop gets supported better.

---

### Post by Linuxisfast on 2012-04-06
Ubuntu 12.04 beta will run this laptop but installing AMD post release crashes Jockey although after reboot AMD driver seems to be working. xvba-video driver is old and I can't tell if its working with VLC with GPU acceleration enabled.

---

### Post by sandy8925 on 2012-04-23
Ubuntu 12.04 should work fine. unfortunately, the proprietary AMD drivers have been getting steadily worse for the asus k53ta. i'd advise you to stick with catalyst 11.8 if possible.

Edit: I just tested 12.3 and it works perfectly for me. 2D is fast, suspend works and 3D is amazingly good! It's a huge jump in performance from 11.8 to 12.3. I ran the Unigine Sanctuary benchmark with 11.8 FPS and it was crawling at around 10 FPS with all settings low but with Catalyst 12.3, I got around 80-100 FPS in the same settings! Everything is smooth and works properly (including video acceleration through XVBA)

---

### Post by nidhindas33 on 2012-04-27
[QUOTE=spantch101;11580150]ok so i have been using ubuntu on my toshiba satellite and asus k50id for the past few years now, with a lot of trial and error learning with this amazing OS, but i just went and bought a new k53TA from asus and i cannot run 64 bit as soon as the loading screen comes up asking to install the os no matter my choice my screen goes black, i have tried using directly from live cd and i know its running and i can hear the system sounds but no visual at all its like zero power going to my lcd ... any ideas ? my specs are as follows :

ASUS K53TA:
amd A6 3400m Quad Core 1.4/2.3ghz
4gb ram ddr3
Radeon HD6720G2 1GB
500GB 
Win7 Premium 64 bit

Any Ideas? i can run 32 bit ubuntu for now i guess, but i want to take advantage of my full 4 gb plus i have another 4gb to put in so i'd like to get 64 bit working. thanks in advance.[/QUOTE

there is alternate download for amd laptop. the problem is related with the kernal ver 3.. try ubuntu 12.04 using kernal 3.2. which is fixed this bug. 

i provide the link here...
[http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

download this file from the list...
ubuntu-12.04-alternate-amd64.iso.torrent


read the ubuntu 12.04 release carefully...


especially about kernal

note this line
On systems with an ATI Radeon 9200 graphics card the system will boot to a black screen. As a work around edit the kernel command line in the boot loader and add "nomodeset". (725580) 

after installation press e for edit the grub menu... here add nomodeset at the end....
now reboot...
the problem will solved

---

