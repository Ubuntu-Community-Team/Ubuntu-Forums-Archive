---
title: "iMac PowerPC 750 Problems"
date: 2009-01-26
forum: Apple Hardware Users
---

### Post by CyberAxe on 2009-01-26
I&#8217;m trying to get xubuntu 8.10 working on these frontloading Macs as Mac OS just doesn&#8217;t cut the mustard.

I've been able to install it and boot into it by using the video=ofonly, however once it boots it is in low graphics mode and I cannot fix this, I have tried editing the xorg.conf but it was blank to start with so I tried using some code from ones I found on the forum to no avail.

Also I don't know if it's related to it being in low graphics mode but most things won&#8217;t run within xubuntu I can get the system panel open to change appearance and such but if I try and open terminal or Firefox for example it will try to load them then close.

Here&#8217;s the specs taken from one of them in case it helps, thanks.

```

Hardware Overview:
  Machine Model:	iMac
  CPU Type:		PowerPC 750  (22.15)
  Number Of CPUs:	1
  CPU Speed:		500 MHz
  L2 Cache (per CPU):	256 KB
  Memory:		128 MB
  Bus Speed:		100 MHz
  Boot ROM Version:	4.1.9f1
  Serial Number:	VM1330LLLFU

Network:
  Internal Modem:
    Interface:		modem
    Type:		PPP (PPPSerial)

  Built-in Ethernet:
    Interface:		en0
    Type:		Ethernet
    IP Address:		192.168.1.223
    Subnet Mask:	255.255.255.0
    Broadcast Address:	192.168.1.255
    Router Address:	192.168.1.1
    DNS Servers:	208.67.222.222, 208.67.220.220
    Domain:		Springboard
    Ethernet Address:	00:03:93:40:8e:7e

Memory:
  DIMM0/J13:
    Size:		Empty
    Type:		Empty
    Speed:		Empty

  DIMM1/J14:
    Size:		128 MB
    Type:		SDRAM
    Speed:		PC100-222S

PCI/AGP Cards:
  ATY,Rage128Pro2:
    Type:		display
    Bus:		AGP
    Display Type:	CRT
    VRAM (Total):	16 MB
    Vendor:		ATI (0x1002)
    Device ID:		0x5452
    Revision ID:	0x0000
    ROM Revision:	113-XXXXX-104

  Display:
    Resolution:		1024 x 768 @ 75 Hz
    Depth:		32-bit Color
    Mirror:		Off
    Online:		Yes
    Main Display:	Yes

```

---

### Post by tripolitan on 2009-01-26
8.10 will not run in graphics mode on your iMac. According to the website, it should not even install on your hardware.

Your iMac is too old and too low on resources. Minimum 384MB RAM is required.

For video (I believe your video chip is ATI Pro-turbo), try using the frame buffer option at the time of install, it could also be video=fb or something like that....check the boot options.

Try Debian PPC, text mode.

---

### Post by thomasthetug on 2009-01-26
This is off topic, but they have 8.10 for Ppc?

---

### Post by SNAFU0062000 on 2009-01-27
I have the same problem going on i think you may have been reeding my form if not ill get it for you. but i have tryed Xubuntu8.10 Ubuntu8.10 8.4(ALL FOR POWER PC) and all end up the same my PowerPC 750 @ 700mhz 60g HD and 1gRAM. you will need to get more RAM but i am just about to Give Up. Here is my Link  

[http://ubuntuforums.org/showthread.php?t=1047276](http://ubuntuforums.org/showthread.php?t=1047276)


I Hope this help you more then me and maybe we can get are computers up and running.

---

### Post by CyberAxe on 2009-01-27
I'll try the framebuffer option when i try next install.

More ram is not an option, these all belong to a charity run organisation and they dont have the funds to spend on upgrading equipment hence why they have such ancient hardware in the first place.

I shall try 7.10 as that seems to be more lower amounts of memory friendly, plus 7.04 links all seem to no longer exist.

Thanks.

---

