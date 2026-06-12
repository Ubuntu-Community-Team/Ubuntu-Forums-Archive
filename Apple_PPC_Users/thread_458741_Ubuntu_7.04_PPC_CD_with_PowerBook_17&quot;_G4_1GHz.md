---
title: "Ubuntu 7.04 PPC CD with PowerBook 17&quot; G4 1GHz"
date: 2007-05-29
forum: Apple PPC Users
---

### Post by ViReN on 2007-05-29
Hello All,

This is my first post here;). I tried to search but could not find the right solution.

My Mac configuration is as follows,

[SIZE="2"]Power Book G4 17" (Feb 2003)
1 GHz, 512 MB RAM,
60 GB HDD[/SIZE]

I have downloaded Ubuntu 7.04 PPC ISO from [http://cdimage.ubuntu.com/ports/releases/feisty/release/ubuntu-7.04-desktop-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/feisty/release/ubuntu-7.04-desktop-powerpc.iso)

Here is the problem:

1) I am not sure if what i have downloaded this is the right version
2) When I boot with the above CD, it throws a error some thing like PCI resouce at 0.000 some numbers

Kindly guide me.

Thanks in Advance.

---

### Post by tcrroadie on 2007-05-30
How far will the boot process actually get?  What you are seeing is normal text that displays just before the system starts to come up, and you see the Ubuntu boot splash screen with the progress bar.

The disc you are using is the correct disc for your system.

---

### Post by stmiller on 2007-05-30
It could be the nvidia chipset in that model causing a problem. You should know ahead of time that sleep/suspend does not work on Macs with Nvidia at this time under PPC Linux (due to not enough hardware info from Nvidia). But there is an open source project working on drivers right now.

It's possible that the Nvidia graphics chip is problematic with the Live CD. You can still install Ubuntu with the Alternate PPC CD. It goes right to an installer, and skips the graphical desktop.

---

### Post by ViReN on 2007-05-30
Dear All,

thank you very much for kind responses. I have been reading forums and found that I need to reset the partition table using the MAC OS X install disk. After this I was able to install and my G4 is up and running.

while booting, Initial Display showing logo is still rainbowish and there is one error that i can view  saying "at pci cannot allocate resource in region 2 of  0000:00:10.0". but things are running.

Now 2 Issues

1) Monitor Display is set at 1280x800 where as native resolution of screen is 1440 x 900 (Device NV17 GeForce 420 Go 32M)

i am not sure if it is using the x11 for display. xorg.conf shows  in section monitor says ID:Color LCD, Opt: DPMS, horiz: 28-72 , Vert:43-60 and down below display modes do show 1440 x 900 but in the system preferences screen resolution the highest available is 1280 x 800 what could be the issue?

2) Connecting to wireless router (linksys) is still an issue... 

my linksys router configuration is as follows
network mode - mixed
there is an SSID and have enabled SSID broadcast
security is WPA personal with TKIP
Access is allow all... DHCP enabled

---

### Post by stmiller on 2007-05-30
Hi, have you checked out the PPCFAQs? 

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

There are some notes for getting the airport extreme working.

And yes, resolution is determined by the settings in /etc/X11/xorg.conf

Edit that file by typing this in a terminal:

sudo gedit /etc/X11/xorg.conf


You can specify these items in the 'Screen' section by having lines like this:

```
Section "Screen"

DefaultDepth	24


SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection



```

You can remove any other resolutions in that section, like 1024x768, etc. Just leave the one resolution you want in this case.

After saving, hit Control+Alt+Backspace[delete key] to restart X.

---

### Post by ViReN on 2007-05-30
Hello,

Yep I have checked FAQ's... here is the log of various files related...... still no resolution change.... 


[quote=xorg.conf]
Section "Monitor"
	Identifier	"Color LCD"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 420 Go 32M]"
	Monitor		"Color LCD"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
EndSection
[/quote]

Attached Log log.txt for the graphic errors


for the WiFi.. i have read the thread sticky thread... and added lines to the /etc/interfaces... but :(

[quote=/etc/interfaces]

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid ssvirenlinksys
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk #123331232313#
[/quote]

[quote=KEM Log]
May 31 00:22:00 viren-laptop kernel: [  811.951013] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[/quote]

[quote=DAEMON Log]
May 31 00:26:07 viren-laptop firmware_helper[6032]: main: error loading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0001:10:12.0' with driver '(unknown)'
May 31 00:26:10 viren-laptop NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device
[/quote]

[quote=SYS Log]
May 31 00:28:10 viren-laptop kernel: [ 1182.468137] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
May 31 00:28:13 viren-laptop NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device 
May 31 00:28:22 viren-laptop dhclient: No DHCPOFFERS received.
May 31 00:28:22 viren-laptop dhclient: No working leases in persistent database - sleeping.
[/quote]

---

### Post by ViReN on 2007-05-30
it looks like in need to upgrade my firmware.... I tried to search / install the fw-cutter but cannot find it.... which other tool can i use to upgrade the firmware?

---

### Post by stmiller on 2007-05-31
> **ViReN said:**
> it looks like in need to upgrade my firmware.... I tried to search / install the fw-cutter but cannot find it.... which other tool can i use to upgrade the firmware?

Follow the instructions on the PPCFAQs. You can manually extract the firmware from an apple driver, but just follow the PPCFAQ instructions.

---

