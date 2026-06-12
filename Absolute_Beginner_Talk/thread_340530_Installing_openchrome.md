---
title: "Installing openchrome"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by luminal101 on 2007-01-17
I'm desperately trying to install openchrome to enable 2D acceleration. I've read the previous threads about this subject, but I couldn't match them with my problem:

Compiling and installing the driver was easy, as in [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) . When I restart Xorg, I get a black screen. The final entry in Xorg.0.log is:
**
(II) VIA: driver for VIA chipsets: CLE266, KM400/KN400, K8M800,
	PM800/PM880/CN400, VM800
(II) Primary Device is: PCI 01:00:0
(EE) No devices detected.

Fatal server error:
no screens found
**

A bit earlier in the same file, it says:
**
(II) Bus 7: bridge is at (0:19:1), (0,7,7), BCTRL: 0x0004 (VGA_EN is cleared)
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x3343) rev 2, Mem @ 0xa0000000/29, 0xc9000000/24
**

I assume that this 'PCI 1:0:0' should be the graphics device. Why is it unknown to the system? Is this a problem? Can I somehow determine the type of graphics chip? The only information I have is from the data sheet of the laptop, which says 'VIA / S3G UniChrome Pro IGP'.

Is there any solution to the 'Fatal server error: no screens found' problem?

Thanks!!

Frank

---

### Post by DaneDog on 2007-01-19
I have had this happen before.... not sure why i was too new at this to know exactly what caused it...

make sure that "via" is the driver in your X-org file... 
you can always run dpkg-reconfigure xserver-xorg  to select the VIA driver or the Vesa Driver
I seemed to have a problem with booting when i got warnings during compiling, try recompiling your driver.

PCI is the video card mine registers as the same thing... not sure all cards might read that for linux

What is the bios your computer uses? what brand laptop?

The openchrome works for most chipsets AFAIK.

if you can get to a console run "sudo nano /etc/X11/xorg.conf" the X must be capitolized in X11, pick vesa as a driver to get back into ubuntu,  or run the dpkg-reconfigure xserver-xorg

Sorry if i'm not better help but I have been playing with the "HORRIBLE" unichrome chipset for a good 3 weeks straight... so i figured some of this info may be useful...

BTW the website for via is [http://www.via.com.tw/en/index.jsp](http://www.via.com.tw/en/index.jsp)

let me know how it works out...

---

### Post by luminal101 on 2007-01-19
Three weeks... so I got two more to go...:-? 

I reinstalled the driver, but with no success. I don't get any apparent warnings/errors while compiling or installation, so I think that's not the problem. I ran dpkg-reconfigure and I edited xorg.conf manually, but both with the same "Fatal server error: no screens found" message.

It's a MAXDATA Eco 4010 laptop. The bios is 'PhoenixBIOS R1.09'. The chipset is 'VN890 / 8237A'. Could it be that openchrome does not support this chipset? How can I find out??

Such a pain for these stupid chips... but Ubuntu is great!

Thanks!! Frank

---

### Post by luminal101 on 2007-01-19
Problem solved!!!:-D 

I could manage to enable 2D acceleration with the driver from this site: [http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=184](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=184) The installation guide is a bit confusing, but it works.

Now in /var/log/Xorg.0.log it says 'Chipset P4M890 found', while the datasheet of the laptop claims a 'VIA VN890' chipset. Guess that's a mistake, and that's why I couldn't find a driver for 'VN890'.

Thanks anyway!!!

Frank

---

### Post by furni on 2007-04-28
HI 
i have laptop with chipset vn890 too.
I try to install this driver and i have problem.
 >  
[email]root@onion:/home/artur/via/1/cle266cn400cn-cx700cn800xorg40072-kernel-src_20061226b.zip[/email]_FILES/CLE266CN400CN-CX700CN800XORG40072-kernel-src_20061226b/src# ./makedriver drmWhich version driver you want to release ? 
72
mkdir: nie mo&#380;na utworzy&#263; katalogu `/CLE266CN400CN-CX700CN800XORG40072/': File exists
mkdir: nie mo&#380;na utworzy&#263; katalogu `/CLE266CN400CN-CX700CN800XORG40072//': File exists
Which CPU do you use ? 
1. VIA C3-2(C5N/C5P), C7, Intel Pentium 2/3/4
2. VIA C3
3. AMD K7
4. AMD K8 with 32 bits OS(x86)
5. AMD K8 with 64 bits OS(x86_64)
1
cp: nie mo&#380;na wykona&#263; stat na `3D/DRI-Xorg_bin///via_dri.so': No such file or directory
cd: 5: can't cd to ../../../../../../config/imake
okay, continuing in programs/Xserver/hw/xfree86/drivers/via
+ rm -f Makefile.bak
+ mv -f Makefile Makefile.bak
../../../../../../config/imake/imake -I../../../../../../config/cf  -Wundef -DTOPDIR=../../../../../.. -DCURDIR=programs/Xserver/hw/xfree86/drivers/via
/bin/sh: ../../../../../../config/imake/imake: not found
make: *** [Makefile] B&#322;&#261;d 127
Vim: Warning: Input is not from a terminal
Makefile:4: *** polecenia zaczynaj&#261; si&#281; przed pierwszym obiektem. Stop.
cp: nie mo&#380;na wykona&#263; stat na `via_drv.o': No such file or directory
 -------- Complete to make & copy driver --------
root@onion:


and i dont know what is wrong.

---

### Post by jimmysp on 2007-04-28
Hello everybody,

After a few months, I came back to Ubuntu and downloaded 7.04.
I was very pleased with the first impression of it (it detected and installed the atheros driver :) ) except for the problem with my Unichrome Pro graphics card.

After looking into it for the night, I think I finally made it work with the **OpenChrome** driver.
It works smooth now with the via driver, in 1280x800, while at the beginning it was working in vesa 800x600.
For installation, I followed the steps from [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome), except i used another branch of the driver, with the command: 
```
svn co http://svn.openchrome.org/svn/branches/vt3336_branch openchrome-vt3336
```

I hope this helps somebody else too, until the guys that handle this driver can fix it in the ubuntu distribution.

Ps. My hardware is a Fujitsu Siemens L7320, with GPU vn800 (I think, I don't remember this very well). Also, I am very young in the Linux world, so if anyone with more experience can tell me if it is ok or something wrong what I just did, I would be grateful.

---

### Post by furni on 2007-06-08
I installed and I have such error.

Xorg.0.log:
> 

(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) VIA: driver for VIA chipsets: CLE266, KM400/KN400, K8M800,
	PM800/PM880/CN400, VM800/CN700/P4M800Pro
(II) Primary Device is: PCI 01:00:0
(EE) No devices detected.

Fatal server error:
no screens found

 

lspci
> 
..
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3371 (rev 01)
..


now i use vesa driver but i have problem when i want change console. i press ctrl+alt+F1 i have black screen and i have to restart laptop to back to work.

---

