---
title: "wireless network not working after upgrade"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by tech overloaded mom on 2007-03-12
D-link WDA-1320 networking card worked fine before installing some upgrades 3 days ago, but now it doesn't appear in Networking (driver?) although it is recognized by Device Manager (hardware).

At first (after the update) I just got the black screen of death, but thanks to the wonderfully helpful site, [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/), I was at least able to get back into GUI using sudo dpkg-reconfigure xserver-org.

I've read a lot of posts and tried a lot of different things, but to no avail. I tried to revert to a previous version of xserver, but that didn't help.

I tried to use a driver from D-link with ndiswrapper, but I got the error message that Neta3ab in an invalid driver.

I even tried to reinstall the desk top with sudo apt-get install ubuntu-desktop, but since the updates remain that didn't help.

Like a fool I believed that updates only bring good things. I never thought of anything like this happening, so no, I didn't record what updates I was installing (19 of them). It looks like from other postings that this has happened in the past and that without knowing which update caused the problem I am out of luck.

I bought the D-link card on purpose because it was supposed to work with Ubuntu. In fact the whole reason I tried Linux was the hope that I could put an older Win98 machine back into service. It is a dual boot because the kids still like some of the older games.

Is there anyway I can get things back to the way they were?

---

### Post by siciliancasanova on 2007-03-12
What's your output when you enter:```
iwconfig
```
?

Did you try using NDISGTK to install the .inf file in the driver?

---

### Post by tech overloaded mom on 2007-03-12
iwconfig returns:

lo      no wireless extensions
eth0  no wireless extensions
sit0    no wireless extensions

NDISGTK? No, how would I do that?

---

### Post by siciliancasanova on 2007-03-12
The easiest way would by to go to **System > Administration > Synaptic Package Manager**

Also, just to make sure that your firmware is working, what is your output for:

```
lspci
```

?

---

### Post by tech overloaded mom on 2007-03-12
lspci returns:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
00:0e.0 Multimedia controller: C-Cube Microsystems Cinemaster C 3.0 DVD Decoder (rev 01)
00:0f.0 Multimedia audio controller: Aureal Semiconductor Vortex 1 (rev 02)
00:10.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 04)


(2nd to last is the Atheros Ethernet controller. That should be the wireless D-Link card. The other controller is the wired card I am using to connect now.)


I used Synaptic to install NDISGTK. Now what do I do with it?

---

### Post by siciliancasanova on 2007-03-12
```
00:10.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
```

That line there shows that your Wireless card is recognized by the system and that it is now pinned down to a driver problem.

Download whatever driver you need onto your system.

Launch synaptic package manager and search WINE

Use WINE to extract the .exe format of your driver

Then go to **System > Administration > Windows Wireless Drivers** (NDISGTK)

And click "**Install New Driver**"

Then browse the extracted driver and click the .inf file

---

### Post by tech overloaded mom on 2007-03-13
I can try Wine if you think it would help(with the .exe file in the driver folder on the disk that came with the card), but I downloaded the driver's inf file from D-Link's website. That is the driver that I got the error message on (Not a valid driver).

When I run Windows Wireless Drivers (Stupid me! I was looking around for a program called NDISGTK) it says that the driver is already loaded and if I click configure network it is not listed in Network Settings. Now what?

---

### Post by siciliancasanova on 2007-03-13
Go to Synaptic and install wifi-radar and run it.  Are there any networks showing up?

---

### Post by tech overloaded mom on 2007-03-13
How would that work if I don't have a driver? I know from my laptop that there are open networks out there.

Network settings only shows two connection possiblities: wired and telephone (the card for which I removed to put the wireless one in). Before I ran the updates three days ago both the wired and wireless drivers were there. Two months ago when I installed Ubuntu and the wireless card, the wireless card worked right away. No need for a Windows driver.

Is there anyway to go back to the original install? Just to start over?

---

### Post by siciliancasanova on 2007-03-13
Wifi-radar is a good program regardless if you are having problems.  It is also a way of double checking to see if your driver is functioning and it's not just a setting that you entered wrong in **System > Administration > Networking**

The driver you installed might be bad.  Like I said before I would download the most updated .exe (naturally their windows drivers will be more up-to-date) and extract it with WINE and then try using System > Administration > Windows Wireless Drivers to install the driver again.

EDIT: This will also let you know if/when your driver is installed```
sudo iwlist scan
```

---

### Post by tech overloaded mom on 2007-03-13
I downloaded Wi-fi and as expected, no networks were found.

I also installed Wine. Where is it? I can't find it in the menus and how would I use it to extract the driver?

Thanks for hanging in there with me.

---

### Post by siciliancasanova on 2007-03-13
First open up ```
winecfg
```

and make sure it's mapping to your linux drive, probably z:

Then just right click on the downloaded .exe and there should be an option to extract it with WINE.  Browse the directory and save it somewhere in your user account, proabably on the desktop would function easiest

---

### Post by tech overloaded mom on 2007-03-13
The downloaded file is a zip file. Extracted it contains a setup.exe file and a folder named drivers. In this folder is two folders - Win2KXP and Win9X. Both contain a file named NetA3AB.inf plus a .sys and .dll file. The XP file also contains a .cat and .dat. Isn't this what we are looking for without using Wine?

---

### Post by siciliancasanova on 2007-03-13
Now did you try using System > Administration > Windows Wireless Drivers to try and install NetA3AB.inf that's found in the extracted driver, in the drivers folder?

Yes it's the same but there might have been an error in the .inf you first downloaded, this is a way of double checking.

---

### Post by tech overloaded mom on 2007-03-13
If I install the .inf driver from the Win9X folder it says that the hardware isn't present. When I uninstall it and install the .inf from the Win2KXP folder it says "yes" the hardware is present, but if I try to configure the network the wireless card still doesn't appear.

---

### Post by siciliancasanova on 2007-03-13
Install the .inf file from the XP folder so that it says the hardware is present

Does anything happen when you input```
sudo iwlist scan
```

Also when you say "the wireless card doesn't apper" do you mean that in **System > Administration > Networking** there is only a selection for Wired Connection and Modem Connection and no button for Wireless Connection?

---

### Post by tech overloaded mom on 2007-03-13
sudo iwlist scan returns: "Interface doesn't support scanning" in all three lo, eth0, and sit0.

Yes, there is no wireless listing in Networking.

I need to sign off for the night. Thanks for all your help. I've learned alot even though the problem isn't solved. I'll check postings again tomorrow afternoon.

---

### Post by siciliancasanova on 2007-03-13
Yes I need to get some food and so forth but we now have the problem pinned down to the driver.  I invite anyone else with suggestions to jump in and help us solve this.  I will search for some similar problems with your card when I return.

---

### Post by adamchri on 2007-03-13
Did the upgrade involve a new kernel version? If so, can you boot into the pre-update kernel?

I ran into this exact same problem this morning on Feisty Fawn 7.04: After applying several updates (including kernel 2.6.20-10) from update-notifier my wireless (iw3945) stopped working after reboot. Booting the old kernel (2.6.20-9) everything works fine.

(Well... mp3 playback is broken in MPlayer and video looks much too bright but hey, Feisty is still in testing ;-)

Output from lspci is normal, but eth1 is just gone (eth0 is the wired card I'm using now) and iwconfig finds no cards with wireless extensions.

Maybe a bug in kernel 2.6.20-10?

---

### Post by adamchri on 2007-03-13
> **adamchri said:**
> Maybe a bug in kernel 2.6.20-10?

Well, not quite. It was just the restricted modules package missing. Refer to this thread: [http://ubuntuforums.org/showthread.php?t=383343](http://ubuntuforums.org/showthread.php?t=383343)

My wireless works again now :-)

---

### Post by tech overloaded mom on 2007-03-13
Ohhhhh, I get it! To return to a previous version one simply boots to an earlier kernal. If anyone is writing up Unbuntu Troubleshooting 101 please include this. Duh!

I have 3 choices in my Grub bootloader (besides recovery modes and Win98 ) :

kernal 2.6.17-11-generic
kernal 2.6.17-10-386
kernal 2.6.17-10-generic

The generics don't allow me to use my wireless card, but the 386 does. Yea! I'm guessing that that was my previous version. I'll carefully monitor my updates in the future.

Thanks Adamchri for the link to the other thread.

You guys saved me from having to bail back to Windows. Along the way I found that a driver was available (download) for my D-Link card for Win98 and got that side of the dual-boot working wirelessly. My inability to find this before is what pushed me to try Ubuntu. Refuse Vista. Long live Linux!!!

---

### Post by floke on 2007-03-13
This is great.
I love a happy ending!

---

### Post by siciliancasanova on 2007-03-13
Hey glad you found your solution.  I am pretty new here as well and kind of like helping people with what little I do know to bump their thread back to the top and learn something myself.

---

### Post by rjpilla on 2007-03-14
Loss my wireless on recent upgrade also. Got it working by removing the network manager. Guess will reinstall manager on next upgrade

---

### Post by tech overloaded mom on 2007-03-15
:lolflag:  If it doesn't work fire the manager. I'll have to give that a try if it happens again. Thanks.

---

