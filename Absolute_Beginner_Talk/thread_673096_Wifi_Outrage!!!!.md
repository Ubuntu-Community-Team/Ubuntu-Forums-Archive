---
title: "Wifi Outrage!!!!"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Countra on 2008-01-20
This is the final war cry before i run into the complete raid of total desperation when this is closing in to my third day of having the WiFi MAX without being able to use if for my Linuxified situation. I greet you; O, great helping hand for comming here to help me being able to connect the WiFi MAX to ride out to the glorious internets with the Wii [and nintendo DS].
To be able to reach my amazing goal of using this USB WiFi dongle for what it was made for to so greatly do as it is a linux compatible device indeed i would still need youre help to make it possible since i am, infact, a bigginner to the wonderful realm of [Ubuntu] Linux.

This the answer i got when meeting with the untarred file [driver] for an installation through the magics of the terminal;
> arsham@arsham-desktop:~$ cd '/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0' 
arsham@arsham-desktop:~/Desktop/ZD1211LnxDrv_2_2_0_0$ make
/lib/modules/2.6.22-14-generic/build
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0
-I/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZD1211B
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.o
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
In file included from /home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:42:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.h:663: warning: &#8216;__packed__&#8217; attribute ignored
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:244: warning: function declaration isn&#8217;t a prototype
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:245: warning: function declaration isn&#8217;t a prototype
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:312: warning: useless storage class specifier in empty declaration
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;write&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;fd&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;buf&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;count&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:440: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall3&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:440: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;_syscall3&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:445: error: &#8216;dot11A_Channel&#8217; undeclared here (not in a function)
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_house_keeping&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:1441: warning: unused variable &#8216;tmpvalue&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_config&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:2313: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;U32&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_validate_frame&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:2688: warning: unused variable &#8216;len1&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_rx_isr&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:3927: error: &#8216;struct sk_buff&#8217; has no member named &#8216;mac&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_close&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:4608: warning: implicit declaration of function &#8216;re_initFdescBuf&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_xmit_frame&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:4701: warning: suggest parentheses around && within ||
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_watchdog&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:5335: warning: unused variable &#8216;ssidLenToDump&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:5334: warning: unused variable &#8216;cbTemp&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_ioctl_setiwencode&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:5724: warning: unused variable &#8216;bReconnect&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205wext_siwscan&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6595: warning: implicit declaration of function &#8216;zd_CmdProbeReq&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6539: warning: unused variable &#8216;ul_mac_ps_state&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6538: warning: unused variable &#8216;oldMacMode&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6537: warning: unused variable &#8216;i&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_translate_scan&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6715: warning: unknown conversion type character &#8216;,&#8217; in format
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6715: warning: spurious trailing &#8216;%&#8217; in format
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_list_bss&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6891: warning: spurious trailing &#8216;%&#8217; in format
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_ioctl&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7163: warning: implicit declaration of function &#8216;verify_area&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7572: warning: ISO C90 forbids mixed declarations and code
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_load_card_setting&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7940: warning: implicit declaration of function &#8216;open&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7957: warning: implicit declaration of function &#8216;read&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7961: warning: implicit declaration of function &#8216;close&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7967: warning: suggest parentheses around assignment used as truth value
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_save_card_setting&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:8113: warning: implicit declaration of function &#8216;write&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zdcb_AssocRequest&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9153: warning: implicit declaration of function &#8216;HashSearch&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9153: warning: assignment makes pointer from integer without a cast
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_set_zd_cbs&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9209: warning: assignment from incompatible pointer type
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;CalculateQuality&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9423: warning: ISO C90 forbids mixed declarations and code
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9425: warning: unused variable &#8216;rxOffset&#8217;
make[2]: *** [/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.o] Error 1
make[1]: *** [_module_/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2
arsham@arsham-desktop:~/Desktop/ZD1211LnxDrv_2_2_0_0$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

arsham@arsham-desktop:~/Desktop/ZD1211LnxDrv_2_2_0_0$ 

And as you can see the access point is still being held invalid by the great powers of the linux realm.
Now it is up to you; O, great helping hand to help me into the final battle against the great obstacle called "Installing the WiFi MAX Driver". May you be blessed by the holy penguin.

EDIT: If possible, using some software to emulate windows(such as Wine but Wine doesent work well with drivers) would be good to. Atleast for the moment.

---

### Post by Ub1476 on 2008-01-20
Hi, I most admit, that terminal output doesn't really make much sense. Could you provide the link to were you downloaded the driver from? 

Something which might work better though, is [NDISwrapper]("http://ndiswrapper.sourceforge.net/joomla/"). With this great thing you can use Windows drivers.

---

### Post by Whiffle on 2008-01-20
```

/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd12 05.c:34:26: error: linux/config.h: No such file or directory

```

Might be an issue.  Considering I have NO idea what your setup  is, I really can't help you.

---

### Post by Countra on 2008-01-20
Originally posted by: **Ub1476**> something which might work better though, is NDISwrapper. With this great thing you can use Windows drivers.
Yes, so i followed youre advice and as this seems to be a wonderful program and all i am still having some minor issues, would you mind clearing this up for me, please? Thanks =)

Ok, so in the README section it says:
> 
Once the driver has been unpacked, locate .inf and .sys files. If
necessary, move these files so both .inf and .sys are in the same
directory. Some drivers also come with firmware files, such as
fwrad16.bin etc. These files also should be in the same
directory. 
But.. well, if by "windows driver" it means the driver [for windows], that is, the .exe file, a driver intended to be used under windows then i have one yes, but it is just an .exe file! No messing around with .sys and .inf and stuff like that, you know what i mean? Just plain good old .exe files! :-D
Or yes, i might have done the so underrated but yet so common mistake of misunderstanding it! Yes, that must most certainly but the case. But then i dont know what to do now so i would need youre help with that =)

---

### Post by thelatinist on 2008-01-20
> **Countra said:**
> Originally posted by: **Ub1476**
But.. well, if by "windows driver" it means the driver [for windows], that is, the .exe file, a driver intended to be used under windows then i have one yes, but it is just an .exe file! No messing around with .sys and .inf and stuff like that, you know what i mean? Just plain good old .exe files! :-D

An .exe is not a windows driver, sorry to say.  It is an executable application, probably used to install the driver under windows.  If you have the driver installed under Windows, you could try to find the .sys and .inf files in your windows\system32 folder.

It would probably help us if you could tell us what wireless chipset you have.  Post the output of:

```
lspci | grep Wireless
lspci | grep 802.11
```

If those don't give any output, post the complete output of:

```
lspci
```

---

### Post by OttoDestruct on 2008-01-20
I realize this probably won't help much as you're using a different dongle, but the only way I was able to get the official Nintendo one working was through Virtualbox. (A brief howto can be found [here](http://ubuntuforums.org/showthread.php?t=640083))

If you do figure it out, feel free to post your own how-to or post in mine, and I can ask it to be made into a general 'Get your Wii / DS online with a Dongle' thread rather than having a bunch spread out.

---

### Post by Countra on 2008-01-20
this is the output for 
> root@arsham-desktop:~# lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 LE] (rev a1)
02:01.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
root@arsham-desktop:~# 


---

### Post by thelatinist on 2008-01-20
Um...you don't have a wireless card.

---

### Post by Frem on 2008-01-20
@thelatinist: Yes he does. Last line in the output, it's plugged into the FireWire port.

02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


@Countra: To use drivers provided in an EXE file with Ndiswrapper, you'll need to do a bit of poking. Use a combination of the command line programs unshield, cabextract, and unzip to try to get the inf file you need out. Alternatively, post it to googlepages, or megaupload, or something and I can try to help you extract the driver.

---

### Post by jleaker01z on 2008-01-20
Was your dongle plugged in when you issued that command?  (lspci)

---

### Post by thelatinist on 2008-01-21
> **Frem said:**
> @thelatinist: Yes he does. Last line in the output, it's plugged into the FireWire port.

02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link).

You're right of course.  This is why I shouldn't post at bedtime. ;-)

---

### Post by svenkatesan on 2008-01-21
Hi Countra

for ndiswrapper - .inf and .sys are required but you have only .exe file.Just this morning I tried and successfully extracted those sys and inf files by this method.May be this helps.

Use any zip extractor and extract the exe file,this will give data1.cab,data.htr and data2.cab files.These 3 files are required.

In windows,there is a free software called[COLOR="Red"]** i6comp**[/COLOR].Its being given as zip file.Extract the contents and in release folder you can see a folder called i6comp,put this folder into c:/windows directory.

start ---> run ---> cmd

you will be in the command prompt

go to the directory where you have extracted data1,data2,header file

then

type this

i6comp e -r data1.cab

this will extract all the files from the install shield compressed "data1" folder.

By default it will extract into the same folder,so take the inf and sys files,thats all.

Few hours back I successfully installed zd1211bu deriver in ndiswrapper but net connection not succeeded for some reason.I need to dig it out.

If u need a photo of the extraction see this blog (which is written in mother tongue)

[http://kumarlinux.blogspot.com](http://kumarlinux.blogspot.com).

---

### Post by svenkatesan on 2008-01-21
Just missed out

If your chip set is zd1211,better take all the sys files name started with zd1211,this will ensure ndiswrapper takes required sys file.

---

### Post by wieman01 on 2008-01-21
First off, it's a USB device if I am not mistaken so 'lspci' won't yield any results, no matter how hard you try. Do this instead:
> sudo lsusb
> sudo lshw -C network
> sudo iwlist scan
Then please also tell us exactly what device you have (you have not done so yet) and what chipset is uses. 

Are you on Ubuntu 32-bit or 64-bit?

---

### Post by Countra on 2008-01-21
Originally posted by **Svenkatesan**
> Hi Countra

for ndiswrapper - .inf and .sys are required but you have only .exe file.Just this morning I tried and successfully extracted those sys and inf files by this method.May be this helps.

Use any zip extractor and extract the exe file,this will give data1.cab,data.htr and data2.cab files.These 3 files are required.

In windows,there is a free software called i6comp.Its being given as zip file.Extract the contents and in release folder you can see a folder called i6comp,put this folder into c:/windows directory.

start ---> run ---> cmd

you will be in the command prompt

go to the directory where you have extracted data1,data2,header file

then

type this

i6comp e -r data1.cab

this will extract all the files from the install shield compressed "data1" folder.

By default it will extract into the same folder,so take the inf and sys files,thats all.

Few hours back I successfully installed zd1211bu deriver in ndiswrapper but net connection not succeeded for some reason.I need to dig it out.

If u need a photo of the extraction see this blog (which is written in mother tongue)

The blog was written in tamili? Cool! Well, i can't extract the .exe file. This is what i get when i try to:
**Command Output**
>   End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/arsham/Desktop/WIFIMAX_Setup_NDS.exe or
        /home/arsham/Desktop/WIFIMAX_Setup_NDS.exe.zip, and cannot find /home/arsham/Desktop/WIFIMAX_Setup_NDS.exe.ZIP, period.


> 
First off, it's a USB device if I am not mistaken so 'lspci' won't yield any results, no matter how hard you try. Do this instead:
Quote:
sudo lsusb
Quote:
sudo lshw -C network
Quote:
sudo iwlist scan 
Well, this is what i get by putting in those commands:
> arsham@arsham-desktop:~$ sudo lsusb
[sudo] password for arsham:
Bus 005 Device 004: ID 058f:6362 Alcor Micro Corp. 
Bus 005 Device 002: ID 0ace:1215 ZyDAS 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
arsham@arsham-desktop:~$ sudo lshw -c network
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

arsham@arsham-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:01:38:92:97:22
                    ESSID:"B2_private_CB"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=5/100  
                    Extra: Last beacon: 152ms ago

arsham@arsham-desktop:~$ 
Note, eth1 is my neighbors wireless router and i of course dont have the encryption key to it so it is to no good use :P

> Then please also tell us exactly what device you have (you have not done so yet) and what chipset is uses.

Are you on Ubuntu 32-bit or 64-bit?
I believe i did write it in in the first post i did in this thread but well, if i forgot to do that then the device is a WiFi MAX usb dongle by Datel and its chipset is ZD1211b (or rw?) by Zydas, more info here: [http://gear.ign.com/articles/704/704528p1.html](http://gear.ign.com/articles/704/704528p1.html)
And my ubuntu is.. Well if i remember correctly its a 64-bit but does it really matter?

---

### Post by wieman01 on 2008-01-21
> sudo lshw -C network
... with a capital "C" please. Could you do it again?

_**EDIT:**_
64-bit? Oh, this could mean trouble. At least it is a complicating factor when it comes to wireless support & drivers.

---

### Post by Countra on 2008-01-21
This is what i got
> root@arsham-desktop:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:14:85:6c:54:e4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=83.250.79.15 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:0e:8e:11:04:4a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g
root@arsham-desktop:~# 


---

### Post by wieman01 on 2008-01-21
The scan yields results, so the card is in fact working. What symptoms are there? Can you connect to any UNSECURED network using the network applet (i.e. network manager)? What happens if you try?

---

### Post by Countra on 2008-01-21
> The scan yields results, so the card is in fact working. What symptoms are there? Can you connect to any UNSECURED network using the network applet (i.e. network manager)? What happens if you try?
Card?  Network? The only router around me is my neighbors and that one is encrypted but i suppose it would work to connect to it if i had the password..
But thats not my objective, i wanted to get my [WiFi MAX USB Dongle]("http://gear.ign.com/articles/704/704528p1.html")
working so i can use it to provide wireless internet to a nintendo Wii (and ds) :-D
Not to connect to  a wireless router.. Sorry for any misunderstandings

---

### Post by bobdebouwer on 2008-01-21
I have just started reading this thread.

Being fairly new to linux cant help much in that respect, I can however recommend you buy a wireless router and connect wirelessly to the wii that way. Imho that would be the most sensible and reliable, plus the fact you dont need your pc on all the time when you want to be on the internet is a god send.

Being a former telephone and cable engineer this is the way I recommended. Personally I have 2 wrieless routers, 4 pcs, 2 laptops, a 360 and ps3. This was much simpler setup than trying to setup a pc as a wireless router.

If you really do wish to continue down the route of wireless pc router then I recommend getting a wireless pci card.

David

---

### Post by thelatinist on 2008-01-21
> **bobdebouwer said:**
> I have just started reading this thread.

Being fairly new to linux cant help much in that respect, I can however recommend you buy a wireless router and connect wirelessly to the wii that way. Imho that would be the most sensible and reliable, plus the fact you dont need your pc on all the time when you want to be on the internet is a god send. ... This was much simpler setup than trying to setup a pc as a wireless router.

+1.  There are quite a few relatively inexpensive wireless routers on the market.

---

### Post by Frem on 2008-01-21
Yes, getting a dedicated router is the optimal solution. However, Countra already owns a ~$40 piece of equipment presumably purchased exclusively for this purpose. Ideally, we want to get that working.

Countra, you're trying to share a wired connection coming though your ethernet card with your Wifi Max thing, right? Try looking at these links, the info there might help you double check your configuration.

[https://help.ubuntu.com/community/InternetConnectionSharing]("https://help.ubuntu.com/community/InternetConnectionSharing")
[http://ubuntuforums.org/showthread.php?t=91370]("http://ubuntuforums.org/showthread.php?t=91370")
[http://www.neowin.net/forum/index.php?showtopic=457340]("http://www.neowin.net/forum/index.php?showtopic=457340")

---

### Post by svenkatesan on 2008-01-21
Hi Countra
Again me.
After few reboots, my usb dongle with 1211 chipset able to connect to internet with less signal connection.

When I activate update sys,told me 300+ MB of data need to be download.I left the cpuon and went to bed.Morning woke up to see may key board lights are on blink.I realised the kernel crashed.

Reboot the pc,after enter the password comes to blank color screen.I think I need to repair.

I think the ndiswripper driver might have caused a crush,I am not sure.

So use the zd1211 driver with care.To know the chipset detail I opened and see the chip is name Authros.Quite strange.

---

### Post by FrankVdb on 2008-01-23
Make sure the protocol used is right. 802.11n doesn't work (yet) under Linux.

One of the symptoms of using a protocol that doesn't work, is that you indeed find and see your network but you won't be able to connect.

---

