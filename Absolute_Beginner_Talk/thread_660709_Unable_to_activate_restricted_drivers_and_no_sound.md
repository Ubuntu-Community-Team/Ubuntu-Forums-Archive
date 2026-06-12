---
title: "Unable to activate restricted drivers and no sound"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Thyzer on 2008-01-07
I just installed Ubuntu 7.10, and the installation went smoothly,but some of the hardware is having problems. My graphics card and wireless card both have restricted drivers that won't activate, and I have no sound. My computer is a Dell Inspiron 1521 laptop.

I have an ATI Radeon Xpress1270 graphics card, and when I attempt to enable the restricted driver, it gives me this message:

[INDENT]The software source for the package

   xorg-driver-fglrx

 is not enabled.[/INDENT]

I have a Dell Wireless 1390 wirelss card, and when I try to enable its driver it gives me a similar message:

[INDENT]The software source for the package

   bcm43xx-fwcutter

 is not enabled.[/INDENT]

As for the sound, I don't even think it's picking up my sound card. The little speaker icon next to the clock has a mute sign over it, and when I click on it, it gives me this error message:

[INDENT]The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.[/INDENT]

I tried to check to see if Ubuntu was detecting my sound card, but I couldn't find the device manager. the Help application told me it was in System -> Administration, but it is not there. I am completely knew to linux in all forms, so I don't know what a GStreamer is, if that's the problem. I also don't know what kind of sound card I have,

Anybody know how to fix these problems? Because if I can get these things to work, I can already tell I like this more than Windows.

---

### Post by Kingsley on 2008-01-07
Open up your sources list.
```
sudo gedit /etc/apt/sources.list
```

Uncomment the URLs.

---

### Post by Thyzer on 2008-01-07
Well, I did that, and it worked on allowing me to be able to activate my graphics card, but not my wireless card, or my sound. What is a GStreamer? Cuz that's what it said about my sound card. And even though it didn't completely fix my problems, uncommenting those urls allowed me to get 149 updates, so it was definitely useful, thanks.

---

### Post by OldGrey on 2008-01-07
Gstreamer can be found in add remove and synaptic. However if you sound card is not recognised I am not sure it will help you.

---

### Post by rkd on 2008-01-07
Here is how to get a list of information about the devices in your computer. Post it here so we can see what your sound and wireless devices are. Then we can search for instructions about getting them to work.

From the Applications menu, choose Accessories, then Terminal.

In the window that opens, type lspci and push Enter.

Use the mouse to select and copy all the output the lspci command produced. Paste that text into a post here.

---

### Post by soslug on 2008-01-07
I would like to say I have everything sorted out concerning sound and graphics on the Dell Inspiron 1521, this however is not the case, this laptop has a really crap Graphics card either that or the the drivers are just not suitable and in addition to this the sound was really very hard to get working and even then I am very dissatisfied with both the quality and lack of control. 

We have document in sum detail the full installation process for both graphics and sound and a few other things of interest, all the prescribed methods detailed work to the best of our knowledge as it is rather long we will just provide you with a link, we hope this will provide you with the necessary information to get your Inspiron 1521 working or as best as can be achieved.

[http://wiki.soslug.org/wiki/dell_inspiron_1521]("http://wiki.soslug.org/wiki/dell_inspiron_1521") 

This is a rather nice Laptop it is rather a shame everything doesn't work straight out the box, metaphorically speaking that is.

> **Thyzer said:**
> I just installed Ubuntu 7.10, and the installation went smoothly,but some of the hardware is having problems. My graphics card and wireless card both have restricted drivers that won't activate, and I have no sound. My computer is a Dell Inspiron 1521 laptop.

I have an ATI Radeon Xpress1270 graphics card, and when I attempt to enable the restricted driver, it gives me this message:

[INDENT]The software source for the package

   xorg-driver-fglrx

 is not enabled.[/INDENT]

I have a Dell Wireless 1390 wirelss card, and when I try to enable its driver it gives me a similar message:

[INDENT]The software source for the package

   bcm43xx-fwcutter

 is not enabled.[/INDENT]

As for the sound, I don't even think it's picking up my sound card. The little speaker icon next to the clock has a mute sign over it, and when I click on it, it gives me this error message:

[INDENT]The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.[/INDENT]

I tried to check to see if Ubuntu was detecting my sound card, but I couldn't find the device manager. the Help application told me it was in System -> Administration, but it is not there. I am completely knew to linux in all forms, so I don't know what a GStreamer is, if that's the problem. I also don't know what kind of sound card I have,

Anybody know how to fix these problems? Because if I can get these things to work, I can already tell I like this more than Windows.

---

### Post by Thyzer on 2008-01-07
So I got the wireless working (turns out that I missed a couple urls in the source list), but I'm still having trouble with the sound. I used the terminal to view the list of hardware (the lspci command), and it does list the audio device. I'll paste a copy of the list below (it's number 14.2). I tried the steps given on the link provided by soslug (directly above), but not all the commands worked. The commands that it gave were:

[INDENT]You need to blacklist the "snd-hda-intel" kernel module from being loaded automatically by appending it to /etc/hotplug/blacklist

From a clean boot, make sure the universe repository is enabled, then:

#> sudo apt-get install build-essential gcc-3.4 linux-headers-$(uname -r) module-assistant
#> wget [http://archive.ubuntu.com/ubuntu/pool/universe/a/alsa-driver/alsa-source_1.0.15-3ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/alsa-driver/alsa-source_1.0.15-3ubuntu1_all.deb) && sudo dpkg -i alsa-source_1.0.15-3ubuntu1_all.deb; sudo apt-get -f install
#> sudo dpkg-reconfigure alsa-source

Choose "Yes" for both Plug n' play support and debugging symbols, then deselect "all" cards and select only "hda-intel". Then:

#> sudo module-assistant a-i alsa-source

At this point you'll need to remove "snd-hda-intel" from /etc/hotplug/blacklist , and reboot.[/INDENT]

I blacklisted snd-hda-intel, and then started entering the commands. The first one, however, did not work, it said that one thing was already installed, and then said that a cd was missing, or something was missing. I can't exactly remember. I was going to just copy it in, but I had unblacklisted snd-hda-intel, and it didn't give me the same message, and i didn't want to complete whatever process I'd started without it being blacklisted, since i don't know what it would do. The second command and the one following it worked, regrading the alsa-source, but the last, regarding the command module-assistant didn't work because it said it was an unknown command. I think that is a command referring to the first command. But I'm not really sure. Then I unblacklisted snd-hda-intel, and I'm still in the same place I'd started, as far as I can tell.

Could it be that I just don't have the correct GStreamer installed? When I click the volume controller in the system tray, it gives me a message saying, " No volume control GStreamer plugins and/or devices found." I went to the Synaptic Package Manager and there was a huge list of GStreamers.

Anyways, thanks for the help so far,if I could get some more to pull through on this that would be awesome.

And here is the output of the lspci command:

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by rkd on 2008-01-07
Something, probably that apt-get error you mentioned, prevented installation of module-assistant. 

Maybe it would be good to run all the steps again (including the blacklist stuff), and this time copy the text of the whole sequence of commands and output from the Terminal window and post it here. It probably is best to copy after each command rather than waiting until the end. Open an editor and paste the command results there as you go.  I guess you know how to copy the results from Terminal. I assume that's what you did to post the lspci output.

Some of the packages probably got installed when you did it earlier, and it will just say they already are installed.

---

### Post by soslug on 2008-01-08
Gstreamer concerns the video output to packages such as mplayer xine and so on.


> **Thyzer said:**
> Well, I did that, and it worked on allowing me to be able to activate my graphics card, but not my wireless card, or my sound. What is a GStreamer? Cuz that's what it said about my sound card. And even though it didn't completely fix my problems, uncommenting those urls allowed me to get 149 updates, so it was definitely useful, thanks.

---

### Post by soslug on 2008-01-08
Sent a message to your email hope it helps


> **Thyzer said:**
> So I got the wireless working (turns out that I missed a couple urls in the source list), but I'm still having trouble with the sound. I used the terminal to view the list of hardware (the lspci command), and it does list the audio device. I'll paste a copy of the list below (it's number 14.2). I tried the steps given on the link provided by soslug (directly above), but not all the commands worked. The commands that it gave were:

[INDENT]You need to blacklist the "snd-hda-intel" kernel module from being loaded automatically by appending it to /etc/hotplug/blacklist

From a clean boot, make sure the universe repository is enabled, then:

#> sudo apt-get install build-essential gcc-3.4 linux-headers-$(uname -r) module-assistant
#> wget [http://archive.ubuntu.com/ubuntu/pool/universe/a/alsa-driver/alsa-source_1.0.15-3ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/alsa-driver/alsa-source_1.0.15-3ubuntu1_all.deb) && sudo dpkg -i alsa-source_1.0.15-3ubuntu1_all.deb; sudo apt-get -f install
#> sudo dpkg-reconfigure alsa-source

Choose "Yes" for both Plug n' play support and debugging symbols, then deselect "all" cards and select only "hda-intel". Then:

#> sudo module-assistant a-i alsa-source

At this point you'll need to remove "snd-hda-intel" from /etc/hotplug/blacklist , and reboot.[/INDENT]

I blacklisted snd-hda-intel, and then started entering the commands. The first one, however, did not work,

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Sorry this is needed
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 it said that one thing was already installed, and then said that a cd was missing,

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Edit and REMARK out first line of /etc/apt/sources.list
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 or something was missing. I can't exactly remember. I was going to just copy it in, but I had unblacklisted snd-hda-intel, and it didn't give me the same message, and i didn't want to complete whatever process I'd started without it being blacklisted, since i don't know what it would 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The file blacklist needs to be created you can use the following command

sudo vim /etc/hotplug/blacklist if it doesn't exist create it and make the entry "snd-hda-intel" without the quotes

 second command and the one following it worked, regrading the alsa-source,

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This downloads and installs the alsa driver not much more
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 but the last, regarding the command module-assistant didn't work

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
It doesn't work because it is not installed
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 because it said it was an unknown command. I think that is a command referring to the first command. But I'm not really sure. Then I unblacklisted snd-hda-intel, and I'm still in the same place I'd started, as far as I can tell.

Could it be that I just don't have the correct GStreamer installed? When I click the volume controller in the system tray, it gives me a message saying, " No volume control GStreamer plugins and/or devices found." I went to the Synaptic Package Manager and there was a huge list of GStreamers.

The procedure posted was submitted due to problems I myself have encountered and only for 64bit_x86 7.10 Gutsy Gibbon distro not any other

Anyways, thanks for the help so far,if I could get some more to pull through on this that would be awesome.

And here is the output of the lspci command:

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

