---
title: "Yet another ndiswrapper problem -help!"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by James0044 on 2006-08-27
Hi guys, i'm trying (not very successfully) to install my Belkin Wireless Card.

I have installed ndiswrapper using Synaptic Package manager, and i have identified what PCI card i have using lspci -d. I have checked the pci id on the web, see below:

Card: Belkin 54g Wireless Network Card F5D7000uk 
Chipset: Ralink RT2500 802.11 Cardbus Reference Card (rev 01) 
pciid: 1814:0201 
Driver: Ndiswrapper 1.1 and Rt2500.INF file from [ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip](ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip) 
Other: Debian stable Sarge (2.4.27-2-386) works a treat. I followed the "InstallDebianSarge" instructions which were great. In the end however, I didn't need the "Install latest Ndiswrapper" section as version 1.1 comes already available. Also, needed unzip utility (apt-get install unzip). Cheers! 

and i have downloaded the zip file from the link. It contains 3 inf files for xp, me and 2000 i think. i have copied the .inf and .sys files across like in the guide, and i have run ndiswrapper -i on the Rt25000.inf

I get the following error message:

couldn't copy rt2500.inf at usr/sbin/ndiswrapper line 135

When i run ndiswrapper -l it tells me the rt2500 is installed, but gives the error message:

invalid driver!

i've now removed the driver using ndiswrapper -e.

I am a complete novice to Ubuntu, any help would be great!

Thanks 
James:confused:

---

### Post by Bachstelze on 2006-08-27
Run ndiswrapper -i with sudo :)

---

### Post by James0044 on 2006-08-27
Hi, i tried running it with sudo, because it told me i had to run it as root, it didn't work, but i'll give it another go.

thanks

---

### Post by newtanker on 2006-08-27
Sir,

From your header files, you are running a ralink chipset.  I currently use the msi implementation of that chipset.  Irregardless, ralink opensourced their drivers, and it is natively picked up by ubuntu without the kludge of ndiswrappers.  You would be advised to allow it to autodetect the card.

In the event of it not picking up the card automaticlly, you should pursue implementing the rt2x00 drivers rather than the workaround of the ndiswrapper, as it has several advantages over the wrapper technology.  

If you are using the standard gnome desktop under ubuntu, you can click on the network and the wireless will be under ra0, you just put in the SSID and the wep/wap key and off you run....should work.  Mine works better (more reliably) than the same computer dual booted under windows......

---

### Post by TFX360 on 2006-08-27
RT2500 has native support in Ubuntu. The driver is already supported.

You should get it working via:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28wifi%29%7C%28rt2500%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28wifi%29%7C%28rt2500%29)

and/or

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#head-af86b211b480d43b791cd9b4e698f96638d6d25f](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#head-af86b211b480d43b791cd9b4e698f96638d6d25f)


Kind regards,


TFX


PS: Ndiswrapper wil not work, it will give IOCTLADDRS errors.

---

### Post by James0044 on 2006-08-27
Thanks guys, sounds great.

I'll give that a go, and let you know how i get on!

---

### Post by mikeybrighton1 on 2006-08-27
I have problems with an OfficeConnect3com cardbus card. I used ndiswrapper to get it going which it eventually did. But it is clunky and I have alsorts of start up hangs etc and have to reboot at start. How do I get rid of the windows driver and start again? Thanks Mike

---

### Post by TFX360 on 2006-08-27
> **mikeybrighton1 said:**
> I have problems with an OfficeConnect3com cardbus card. I used ndiswrapper to get it going which it eventually did. But it is clunky and I have alsorts of start up hangs etc and have to reboot at start. How do I get rid of the windows driver and start again? Thanks Mike

Mike,


Please start your own thread for your problem. It's confusing and wil be more confusing.


Kind regards,


TFX

---

### Post by mikeybrighton1 on 2006-08-27
Sorry, new to this and Linux/Ubuntu
Mike

---

