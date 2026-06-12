---
title: "F1A75-V Pro with A6 3650 cpu"
date: 2011-11-20
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dabrudda on 2011-11-20
When I install linux I get a black screen, my monitor goes into power saving mode while linux, ubuntu, redhat fedora 16, Mint, Xubuntu is installing.  I've tried 2 different  monitors so it's not a bad monitor.  I am using the onboard graphics card (Integrated AMD Radeon™ HD 6000 Series Graphics in Llano APU).  Flashed the bios with the latest ROM.  But still no joy.  Is this board too new to work with any flavor of linux?
 
I have set the bios to use the onboard graphics card as the primary video card but still nothing.  I can get Fedora to boot up with the live CD when I select the low res option from the boot menu but something crashes and there is no way to install from the live CD.

I am going to try putting my Nvidia GTX480 in the PCI-E slot and see if I get any video while installing Ubuntu.  Funny thing is Asus say Fedora 14 supports this board but Fedora 16 does the same thing as Ubuntu or any other distro.

---

### Post by dabrudda on 2011-11-21
I put my Nvidia GTX 480 in the PCI-E slot and Xubuntu fired right up.  I didn't want to have to buy another video card so I was able to load the Radeon open source drivers from a terminal.

I had to go into the boot menu by holding down the Shift key after the POST test
Then press "E" to edit the boot options and replaced "quiet splash" with "nomodeset" (without the quotes)
The boot up process would hang on "Checking the battery status" in tty7
I pressed Ctrl Alt F1 to go into tty1 and logged in
I downloaded the open source Radeon drivers to my USB thumb drive
I mounted my USB thumb drive and copied the file to my Downloads folder
I ran the Radeon driver installer, selected 1 to do a default install
After the driver said it was successful I ran "sudo aticonfig -initial"
And rebooted

After a reboot my screen is in 1400x1050 resolution.  I changed the resolution to 1280x960 so I could at least see the and text.

Hope this helps.

---

### Post by dabrudda on 2011-11-22
Scratch that.  Maybe it is my 10 year old monitors.  I hooked my board up to my 51" plasma with a HDMI - DVI cable, set the video card options to IGFX for internal graphics card and I set the IGFX option to Force instead of Auto.  

I was able to install Fedora and Xubuntu without my big screen tv going blank.

So I don't know if it was the settings in the bios, the Force, that made it work.  I haven't hooked the board back up to my old monitors yet.

---

### Post by cfr42 on 2011-12-25
> **dabrudda said:**
> Scratch that.  Maybe it is my 10 year old monitors.  I hooked my board up to my 51" plasma with a HDMI - DVI cable, set the video card options to IGFX for internal graphics card and I set the IGFX option to Force instead of Auto.  

I was able to install Fedora and Xubuntu without my big screen tv going blank.

So I don't know if it was the settings in the bios, the Force, that made it work.  I haven't hooked the board back up to my old monitors yet.

Could you possibly say more precisely what you did? If I set the primary output to "IGFX" then I don't get blank but I do get the most hideous output and it is virtually impossible to read anything. (It is eye-blindingly bright even with the monitor's brightness at zero.)

Or did you set the option for "Integrated graphics" to force? I tried that, too, but that didn't seem to make any difference - still the blank.

I would be interested to know if you can output to VGA. I've got a new monitor which should have come with an HDMI cable but I've only got VGA right now. (Somebody built the machine for my mother so he might have been using VGA and just given us that.) I too am getting the monitor continually lacking a signal and switching to power-saving mode.

Linux Mint 10 didn't initially do this. The graphics sucked but they were usable. Installing fglrx etc. resulted in blank screens and now the best I can get is the blinding stuff. Linux Mint 12 boots to blank screen. (Ubuntu 11.10, I believe.) Even booting with xforcevesa on the command line (Mint 12 from the live dvd in compatibility mode doesn't help.)

I'm wondering if the issue is specific to VGA-output. If it is, I might be able to solve it if I can get an HDMI/DVI cable...

---

### Post by bonvivant1x on 2012-02-18
I have the same problem with f1a75-mpro / amd A8 3850
It goes blank every time I try to load Ubuntu 11.10, Kubuntu, Mint12, Fedora...
It only works (poorly) Ubuntu 10.4 Lucid Linx and Mint Debian, then I load the hideous Catalyst drivers and I get no way de right vga screen resolution (1680x1050), I can only have inferior one, and the sound is horrid, craking and hissing all the way.

When I  load Ubuntu 10.04, monitor goes "out of range" so I unplug and plug it again to the motherboard VGA exit, so the interface appears again.

So in short, a nightmare, I want to dump it and change for another motherboard, but ¿which one, any help?

---

### Post by tr333 on 2012-03-25
For anyone that might find this thread, there is a problem with the VGA (D-sub) port and Llano APUs in Linux.  Relevant bug report is at [http://pad.lv/943263](http://pad.lv/943263).

The workaround for this issue is to run from HDMI, not the VGA port.

---

