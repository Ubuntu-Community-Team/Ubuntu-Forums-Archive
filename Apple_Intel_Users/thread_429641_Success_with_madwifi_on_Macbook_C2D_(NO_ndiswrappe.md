---
title: "Success with madwifi on Macbook C2D (NO ndiswrapper)"
date: 2007-05-01
forum: Apple Intel Users
---

### Post by widemos on 2007-05-01
I've managed to make madwifi work with a MacBook Core 2 Duo, WITHOUT ndiswrapper.

Just follow this:

[http://madwifi.org/ticket/1001#comment:179](http://madwifi.org/ticket/1001#comment:179)

Enjoy!!

---

### Post by ronocdh on 2007-05-01
> **widemos said:**
> I've managed to make madwifi work with a MacBook Core 2 Duo, WITHOUT ndiswrapper.

Just follow this:

[http://madwifi.org/ticket/1001#comment:179](http://madwifi.org/ticket/1001#comment:179)

Enjoy!!
Very interesting, thanks for the link. Can you tell us a little more about your setup, just so we know? For example, what kind of connection are you using this with? When I tried the Madwifi drivers, I was able to connect to my router only when I disabled encryption; neither WEP nor WPA worked with the drivers. (Yes, I know Madwifi has a section on WEP; it didn't help me.)

---

### Post by Romu on 2007-05-01
Whoww, it works, and I can reboot my Macbook Pro without any freeze. Thanks a lot.

Did you manage the WAP security ?

---

### Post by ronocdh on 2007-05-01
> **Romu said:**
> Whoww, it works, and I can reboot my Macbook Pro without any freeze. Thanks a lot.

Did you manage the WAP security ?
Congratulations on the boot, Romu! Please let us know your success with various encryptions.

---

### Post by widemos on 2007-05-01
I'm using 128 bit WEP encription, in a 802.11g environment. As far as I know, WPA should work also.

---

### Post by Nasiom on 2007-05-01
Hi,  

I got it to work on a Macbook Pro but only with WEP.

No WPA/WPA2 options whatsoever showing up in the Network Settings.

I even went on and install the latest madwifi build 0.9.3 nothing more than the previous build.

Anyone with a suggestion on this?

Thanks

-Nasiom

---

### Post by Romu on 2007-05-02
Nasiom, you just have to use the NetworkManager and when you're trying to connect a WPA protected network it will ask you for the password.

This worked perfectly for me on Edgy.

---

### Post by Chrisj303 on 2007-05-02
If you read down the linked thread, it seems that people are still having issues with encryption - firefox crashing/freezing.

I will try this later on today and report back.

Can't wait until we get the wi-fi issue properly sussed, i installed Feisty yesterday on my Macbook (tripleboot) and it seems that ALL of the previous issues are fixed. Very impressed.!

Soon, it seems, we will have the same hardware functionality regardless of what OS we are booted into.



cheers,
chrisj303

---

### Post by jezzeruk on 2007-05-02
Have the Madwifi drivers running, but have noticed a couple of issues.

1) Wont talk to my Airport at all works fine with another router, this could be a WPA2 issue, the other router doesnt support it, so cant test

2) DHCP is problematic, it can take a very long time to obtain an address, if at all.

3) Doesnt work well with low power networks, for example i connect to a network from OSX that only shows one bar, it connects fine on OSX, boot into Ubuntu and i cant stay connected to it

Anyone had similar experiences.

---

### Post by Azathoth_ on 2007-05-02
> **jezzeruk said:**
> Have the Madwifi drivers running, but have noticed a couple of issues.

3) Doesnt work well with low power networks, for example i connect to a network from OSX that only shows one bar, it connects fine on OSX, boot into Ubuntu and i cant stay connected to it

Anyone had similar experiences.

IT's normal, because madwifi is open source and it cannot use all chipset information. All atheros have a lower connection with madwifi

---

### Post by jezzeruk on 2007-05-03
Ok, was more of an observation than an issue, but good to know.

Anyone else have the same experience with DHCP?

---

### Post by Romu on 2007-05-03
No, personnaly with the Widemos tips :
1. I connect without trouble my Airport Express AP
2. No trouble with DHCP
3. The with other PCs working "out of the box" the NM icon has 4 bars when my Macbook Pro with the experimental madwifi has only 2.

And...WPA works !!! So wait for the next release to get a full working Ubuntu on the Macbook Pro "out of the box".

---

### Post by gmc on 2007-05-04
Hi Folks,

No wep/wpa/wpa2 connections here. The Macbook can see my Linksys wrt54g(dd-wrt) router but will not connect if any type of encryption.

Gord

---

### Post by ronocdh on 2007-05-04
> **gmc said:**
> Hi Folks,

No wep/wpa/wpa2 connections here. The Macbook can see my Linksys wrt54g(dd-wrt) router but will not connect if any type of encryption.

Gord
Post your wireless chipset information. Run ```
sudo update-pciids
``` and ```
lspci
```

---

### Post by gmc on 2007-05-04
> **ronocdh said:**
> Post your wireless chipset information. Run ```
sudo update-pciids
``` and ```
lspci
```

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```I've updated the pciids list and as you can see pretty much everything is detected. with the exception of the 00:07:00 device and that doesn't have anything to do with the wireless.

The problem is that the driver simply doesn't work with wep/wpa/wpa2 at this point. It's not really a big deal at the moment.. I'll just bide my time.

I was only throwing my .02 cents in to the hat.

Gord

P.S. It's a second generation Macbook C2D (white, 13.3")

---

### Post by bsantos on 2007-05-04
This is so great! :-D

At last I can dump ndiswrapper! This module even supports txpower management.

I'm using it with WPA and all. Sweet!

---

### Post by Chrisj303 on 2007-05-04
> **bsantos said:**
> This is so great! :-D

At last I can dump ndiswrapper! This module even supports txpower management.

I'm using it with WPA and all. Sweet!


Well would you mind shareing with the rest of use what youve done to get it working with WPA??

---

### Post by bsantos on 2007-05-04
[FONT=Tahoma]Nothing special, installed it and WPA worked. I used the following steps (as in [http://madwifi.org/ticket/1001#comment:179](http://madwifi.org/ticket/1001#comment:179) ):

sudo aptitude install build-essential svn
[/FONT][LEFT][FONT=Tahoma]mkdir ath-build
cd ath-build
[/FONT]svn checkout [http://svn.madwifi.org/branches/madwifi-hal-0.9.30.13](http://svn.madwifi.org/branches/madwifi-hal-0.9.30.13) madwifi
cd madwifi
make clean
make
sudo make install

When asked I removed all the old modules
[FONT=Tahoma]sudo modprobe ath_pci

I'm using NetworkManager, it even recovers when the connection is lost, ndiswrapper stopped working after the first drop (I have a low ap signal sometimes).
[/FONT][FONT=Tahoma]

[/FONT][/LEFT]
[FONT=Tahoma]
[/FONT]

---

### Post by ronocdh on 2007-05-04
I hate to sound like a broken record, but could you also post your chipset info, bsantos, as gmc did above? Some of us have WPA capability and others don't. It would be nice to find a correlation with hardware, if that's the issue.

---

### Post by stchman on 2007-05-04
> **gmc said:**
> Hi Folks,

No wep/wpa/wpa2 connections here. The Macbook can see my Linksys wrt54g(dd-wrt) router but will not connect if any type of encryption.

Gord

You need to install Gnome network manager to enable WEP, WPA/WPA2, follow my procedure to do this:

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

The last section deals with Gnome network manager.  Skip the madwifi portion as your wireless card works.

---

### Post by bsantos on 2007-05-04
How many versions of Intel Core 2 are there? :-|

02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 50100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

Device id: 0x0024

---

### Post by ronocdh on 2007-05-04
> **bsantos said:**
> How many versions of Intel Core 2 are there? :-|

That's precisely what I've been trying to get a grip on! Are all our problems really software or procedurally related? I had assumed we were just applying the same actions to different hardware...

---

### Post by gmc on 2007-05-04
As far as I know, there are at least two versions of the C2D Macbook, v1 has working native drivers and ndiswrapper, v2 only worked with ndiswrapper, until this driver came out.

I have v2 and at this point, I can only connect on a non-encrypted network. Hope this makes the matter as clear as mud.

Gord

---

### Post by ronocdh on 2007-05-04
> **gmc said:**
> As far as I know, there are at least two versions of the C2D Macbook, v1 has working native drivers and ndiswrapper, v2 only worked with ndiswrapper, until this driver came out.

I have v2 and at this point, I can only connect on a non-encrypted network. Hope this makes the matter as clear as mud.

Gord
Right, thanks. Gagginaspinnata just posted about Madwifi on a Core Duo MacBook Pro, chipset:
```
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```
This is of course different from the 5416/8 chipsets in the Core2 Duos; no surprise, perhaps, but I'd like to know more about whether the chipsets change in the C2D MBPs as we have seen them do in the C2D MBs.

---

### Post by bsantos on 2007-05-04
> **gmc said:**
> As far as I know, there are at least two versions of the C2D Macbook, v1 has working native drivers and ndiswrapper, v2 only worked with ndiswrapper, until this driver came out.

I have v2 and at this point, I can only connect on a non-encrypted network. Hope this makes the matter as clear as mud.

Gord


How do you see you have a v2 C2D? I thought that the Core Duo (not Core 2 Duo) were the ones who had native wireless support and Core 2 Duo needed ndiswrapper. The new chipset with 802.11n appeared in the Core 2 Duo. Was there another version of Core 2 Duo?

After all is there a MacBook Core Duo aka v1 and a Core 2 Duo aka v2 or is it more complex than that?

---

### Post by gmc on 2007-05-05
> **bsantos said:**
> How do you see you have a v2 C2D? I thought that the Core Duo (not Core 2 Duo) were the ones who had native wireless support and Core 2 Duo needed ndiswrapper. The new chipset with 802.11n appeared in the Core 2 Duo. Was there another version of Core 2 Duo?

After all is there a MacBook Core Duo aka v1 and a Core 2 Duo aka v2 or is it more complex than that?

As far as I can tell, there are 2 versions of the Macbook C2D as some people have success with wireless support on their C2D machines and some don't. I've noted that the lspci listings on some mac's report different chip revsion numbers.

It's quite possible that I'm talking out my a$$ on the subject but from my investigation in to the situation, it sure appears that Apple made some adjustments to the C2D version of the Macbook after it's original release.

Gord

---

### Post by Azathoth_ on 2007-05-05
It's too soon to have WEO/WPA/WPA2 connections on a AR5008 chipset, i mean, airport extreme on last C2D MB and MBP, and this is a fact

---

### Post by itsalan on 2007-05-05
Hi,

I'm having trouble getting this to work.  I have a C2D macbook, and when I run make, i get the following errors.  Any help is greatly appreciated...thanks!

Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/tmp/ath-build/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/ath-build/madwifi/ath/if_ath.o
  CC [M]  /tmp/ath-build/madwifi/ath/if_ath_pci.o
  LD [M]  /tmp/ath-build/madwifi/ath/ath_pci.o
  CC [M]  /tmp/ath-build/madwifi/ath_hal/ah_os.o
  HOSTCC  /tmp/ath-build/madwifi/ath_hal/uudecode
/tmp/ath-build/madwifi/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/tmp/ath-build/madwifi/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/tmp/ath-build/madwifi/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/tmp/ath-build/madwifi/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/tmp/ath-build/madwifi/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/tmp/ath-build/madwifi/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/tmp/ath-build/madwifi/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/tmp/ath-build/madwifi/ath_hal/uudecode.c: In function 'uudecode_usage':
/tmp/ath-build/madwifi/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/tmp/ath-build/madwifi/ath_hal/uudecode.c: At top level:
/tmp/ath-build/madwifi/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/tmp/ath-build/madwifi/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/tmp/ath-build/madwifi/ath_hal/uudecode.c: In function 'main':
/tmp/ath-build/madwifi/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/tmp/ath-build/madwifi/ath_hal/uudecode.c:121: error: for each function it appears in.)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/tmp/ath-build/madwifi/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/tmp/ath-build/madwifi/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/tmp/ath-build/madwifi/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/tmp/ath-build/madwifi/ath_hal/uudecode] Error 1
make[2]: *** [/tmp/ath-build/madwifi/ath_hal] Error 2
make[1]: *** [_module_/tmp/ath-build/madwifi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

---

### Post by ronocdh on 2007-05-05
Itsalan, I am not certain, but I believe that error output is because you don't have the resources necessary to compile. Try:```
sudo aptitude install build-essential
```

---

### Post by itsalan on 2007-05-06
Thanks ronocdh....that was it.

---

### Post by pacanukeha on 2007-05-06
I am using a C2D Macbook Pro 17".
lspci -vvv (after running update-pciids):
03:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
        Subsystem: Apple Computer Inc. Unknown device 0087
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at d8100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

Until today I could only use WEP, and then only with ndiswrapper.
After following the steps in bsantos' [post]("http://ubuntuforums.org/showpost.php?p=2592899&postcount=18") and then the /etc config steps in the [link]("http://www.stchman.com/ath_drv.html") from stchman's [post]("http://ubuntuforums.org/showpost.php?p=2593169&postcount=20") I now have the ath_pci driver successfully connecting with WPA to a fairly tempermental linksys WRV54G.

So big yays to this progress and thanks to all y'all :)

PS, there was some putzing around with wifi-radar and wpasupplicant.conf with no success until I followed the stchman steps.

---

### Post by also-rr on 2007-05-07
> **bsantos said:**
> [http://people.freebsd.org/~sam/ath_hal-20070428.tgz]("http://people.freebsd.org/%7Esam/ath_hal-20070428.tgz")

If you are installing .13 or later there is no need to replace the HAL! It's already integrated into this branch.

Instructions for Kubuntu are  [here]("http://www.revis.co.uk/site/?q=node/147") - they should also work on Ubuntu. These work on my C2D macbook pro with WPA and WEP.

You need to make sure you have build-essentials and svn installed before you start.

Good luck :)

---

### Post by Chrisj303 on 2007-05-07
Well, i don't know how or why, but i have WPA enterprise wireless!!

I follow bsantos guide a couple pages back, and just works! - thanks mate!


I'm using macbook core2duo

this is my lscpi output:

chris@chris-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)


*It has to be noted though - that the signal strength is only half what it would be when booted into OSX. But this is still a massive inprovment from the situation a few weeks ago!

---

### Post by Tribe on 2007-05-08
Does anyone know if the signal strength is better with madwifi driver compared with ndiswrapper's ?

Thx

---

### Post by Zelut on 2007-05-08
I thought I would post my lspci output to help try to find a pattern between what works and what doesn't.  I have *not* tried these steps yet, but based on what you see here does this match any of those that have been successful including WEP/WPA?

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

note: this is a macbook, C2D 2GHz.  I purchased it roughly two months ago if that helps tell whether its 1st or 2nd gen.  (Currently I have *only* been able to get it working with ndiswrapper)

---

### Post by ronocdh on 2007-05-08
Thank you for the post, but you need to do **sudo update-pciids** first so we can see your specific wireless chipset. =)

---

### Post by Zelut on 2007-05-08
my bad.. I ran update-pciid after I posted that (not going through this thread in order apparently).  Here is my updated output.

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

---

### Post by ronocdh on 2007-05-08
OK. So you used which driver to get wireless connectivity with ndiswrapper? The one off the Apple Boot Camp drivers CD? Or did you find it elsewhere? Also, have you tried the madwifi method posted by widemos? How about the version by bsantos (in this same thread)?

---

### Post by Zelut on 2007-05-08
For use with ndiswrapper I used this post from my blog:
[http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/](http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/)
(the above includes the steps I used, links to the driver, etc)

I just finished trying the instructions found here: (by bsantos)
[http://ubuntuforums.org/showpost.php?p=2592899&postcount=18](http://ubuntuforums.org/showpost.php?p=2592899&postcount=18)

The wireless works but looks like it doesn't support any encryption type.  Here is some of the output from dmesg and lsmod:

> ...dmesg cropped output...
[   20.480000] wlan: 0.8.4.2 (svn r2310)
[   20.512000] ath_pci: 0.9.4.5 (svn r2310)
[   20.512000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   20.512000] PCI: Setting latency timer of device 0000:02:00.0 to 64

[   20.696000] ath_rate_sample: 1.2 (svn r2310)
[   20.696000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   20.696000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   20.696000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   20.696000] wifi0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   20.696000] wifi0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   20.696000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   20.696000] wifi0: mac 12.10 phy 8.1 radio 12.0
[   20.696000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   20.696000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   20.696000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   20.696000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   20.696000] wifi0: Use hw queue 8 for CAB traffic
[   20.696000] wifi0: Use hw queue 9 for beacons
[   20.764000] wifi0: Atheros 5418: mem=0x90100000, irq=16

...lsmod | grep ath_pci...
ath_pci                96032  0 
wlan                  203760  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               233824  3 ath_rate_sample,ath_pci

should I perhaps try adding the wpasupplicant package as suggested in this thread here:
[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html) ?

update: wpasupplicant is already installed.. no difference.

---

### Post by Zelut on 2007-05-08
Here is a bit more info I came up with using '**sudo lspci -vvv**'.  So far the wireless is working but I can't connect to WEP.  We have an encrypted and non-encrypted network at our office (good for testing this I suppose.)  So far it'll see the encrypted networks but NetworkManager just spins and spins when trying to connect to them.

> 02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
        Subsystem: Apple Computer Inc. Unknown device 0087
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at 90100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2- AuxCurrent=375mA PME(D0+,D1+,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [60] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <512ns, L1 <64us
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <512ns, L1 <64us
                Link: ASPM L1 Enabled RCB 128 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
                Vector table: BAR=0 offset=00000000
                PBA: BAR=0 offset=00000000


---

### Post by bsantos on 2007-05-08
> **Tribe said:**
> Does anyone know if the signal strength is better with madwifi driver compared with ndiswrapper's ?

Thx


Even with ndiswrapper I always have 30-40% in places I have 100% on OSX. I don't know if it is a measurement issue or real signal loss.

With the native driver I noticed a huge boost on recovery, it recovers from casual ap dissociation almost instantly when the signal is good again, even with wpa. ndiswrapper ceased to connect after a few drops (or even one), took lots of time to signal a dissociation...

With the native driver you also have txpower support, so you can give it a bit more power:

sudo iwconfig ath0 txpower 14 (25mw which is the max)

for a list of values:

sudo iwlist ath0 txpower

:)

---

### Post by Chrisj303 on 2007-05-11
Well, i spoke too soon - my Wi-Fi has stopped working!:( 

Just like before i had it working, it gets half way (one green light) then flakes out..

I did manage to get both green lights last night, but it stalled while trying to get a network address.

I've tried re-installing just like before, but no luck. NOTHING has changed with the network - i just don't get it.

When it was working, it was working brilliantly as well, so i'm really missing it.

This must have happened to someone else on here, surely..? If anyone here has managed to get it working again PLEASE TELL - i really miss it!


Thans,

chrisj303

---

### Post by Zelut on 2007-05-11
My wireless is still yet to work with any encryption and it works poorly with network-manager and nm-applet.  I can connect well using a manual network setup.

Using the madwifi as mentioned in this thread, with the latest apple firmware updates, I can only connect to unencrypted, name-broadcasted networks.

---

### Post by ronocdh on 2007-05-11
I guess I forgot to post here, but this method worked for me, too. I've only tested on two WEP connections, but I can flip my router to WPA/WPA2 soon in order to test. I was pleased with the reception, actually; I've never had a "dropped call."

---

