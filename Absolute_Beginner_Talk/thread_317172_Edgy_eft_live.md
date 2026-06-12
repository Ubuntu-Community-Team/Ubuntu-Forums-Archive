---
title: "Edgy eft live"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by keheikev on 2006-12-12
Hi all,
I am testing edgy eft the live cd with my new pc a HP pentium D 3.0 GHZ. The HP included keyboard will not work with the live cd. There must be a basic incompatibility there. I will try another keyboard but I kind of like the new one and suspect it will not work with a full install. I did check the cd both its iso with jacksum and the utility on the disk. Is it that a pentium with two cores needs an x64 bit version maybe? 
I do recall that most of my previous pre install experience with linux on my old now dead system was with knoppix is it that the live isn't quite good yet on edgy compared to knoppix or could it be that dapper does this better in 6.06 or 6.10?
Kiheikev
glad to be back

---

### Post by 23meg on 2006-12-12
Is the keyboard listed in System / Administration / Device Manager ?

---

### Post by keheikev on 2006-12-12
Well it must be in the cd the keyboard driver is flat out not working. Strange though I checked the md5 sums for my peace of mind and integrity and this happens. I could download knoppix which I know or try a another x86 iso?
md5 checksums
b950a4d7cf3151e5f213843e2ad77fe3 iso file downloaded
b950a4d7cf3151e5f213843e2ad77fe3 Ubuntu hashes page
This is saying to me burn another image and see if that works out.
Strange Strange Strange brew here.
Never have had the o/s not detect hardware.
Kiheikev

---

### Post by Drilldown on 2006-12-12
Just tested Edgy Live on Pentium D820 2.8MHz dual core.  945P-A Motherboard/DDRII RAM.  SATA HDD.  Nvidia GForce 6600LE PCI Express video. High Def motherboard sound, optical PSII mouse, standard PS II keyboard. 

Started with Ubuntu color bar running scans, went to black screen / blinking cursor at top left after a couple of minutes.  Waited 15 minutes, considered it a failed load.

Incompatible components?  Wrong install disk?
-Standard desktop 6.10 ISO install used, NOT the X64.
Processor is X64 capable.  New to this and experimenting..

I'm listening :-)

---

### Post by keheikev on 2006-12-12
Its listed there although I have to get there with the mouse lol,
The spare keyboard did not work either so I will burn again with imagburn. Burning another cd now.

---

### Post by keheikev on 2006-12-12
Well I did burn the cd at a lower speed 12x and it seemed to load faster and not halt a bit like before (didnt mention that)I was thinking it was the strange black media imation my wife has had fore awhile that never works that good. Anyway I still have no keyboard driver on this iso. I downloaded from the Univ of Utah server so maybe there is a bad version out there. I will try a different locale. Drilldown maybe if you burn a a slower rate your cd dvd drive can pick it up better?
Kevin

---

### Post by Drilldown on 2006-12-12
I'm very good with compatibility problems.  When I saw you using the same chipset, meaning similar systems, and no answers... A:  Middle of the night, nobody knows or - incompatibility.

I don't do bad burns:  Tested the disk on another system first and worked just fine.  Since nobody but newbie me is around right now :-)

I suspect the pentium D, or some related mainboard component that I identified is causing serious incompatibilities.  I call it feedback to improve standards and life in general in ubuntu.

Likely, we'll both wait until morning, regardless.  Post the components you know on your system and maybe we improve the lives of those in our situation.  Who knows, I've got the hardware and I'm willing to experiment, You?  Listening another 45min tonight.

---

### Post by Drilldown on 2006-12-12
OH.  One last thing.
[http://www.driverguidetoolkit.com/](http://www.driverguidetoolkit.com/)

If you don't know what hardware you have, other than it's a Dell, kinda thing?  It's a windoze kinda thing, but that's a kinda thing I've used with excellent result in the past to identify what runs the machine.  I'll run it, see what it says.

---

### Post by Drilldown on 2006-12-12
I'll probably be called out for gross negligence/stupidity in here, but... What the heck.  In for a penny, in for a pound.

The only thing I back-up is data:  Externally.  :-)

List created: 12/12/2006 3:59:21 AM
***************************************************************************************

Driver:            NVIDIA GeForce 6600 LE
Driver Type:       Display adapters
Driver Version:    8.1.9.8
Driver Date:       12/10/2005
Manufacturer:      NVIDIA
ProviderName:      NVIDIA
Num files:         16
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:32 AM


***************************************************************************************

Driver:            Realtek RTL8169/8110 Family Gigabit Ethernet NIC
Driver Type:       Network adapters
Driver Version:    5.611.1231.2003
Driver Date:       12/31/2003
Manufacturer:      Realtek Semiconductor Corp.
ProviderName:      Realtek Semiconductor Corp.
Num files:         2
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:32 AM


***************************************************************************************

Driver:            Intel(R) 82801 PCI Bridge - 244E
Driver Type:       System devices
Driver Version:    7.0.0.1011
Driver Date:       01/10/2005
Manufacturer:      Intel
ProviderName:      Intel
Num files:         21
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:32 AM


***************************************************************************************

Driver:            Intel(R) 945G/P Processor to I/O Controller - 2770
Driver Type:       System devices
Driver Version:    7.0.0.1017
Driver Date:       02/24/2005
Manufacturer:      Intel
ProviderName:      Intel
Num files:         21
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:32 AM


***************************************************************************************

Driver:            Intel(R) 945G/P PCI Express Root Port - 2771
Driver Type:       System devices
Driver Version:    7.0.0.1017
Driver Date:       02/24/2005
Manufacturer:      Intel
ProviderName:      Intel
Num files:         21
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:33 AM


***************************************************************************************

Driver:            Intel(R) 82801GB LPC Interface Controller - 27B8
Driver Type:       System devices
Driver Version:    7.0.0.1014
Driver Date:       01/19/2005
Manufacturer:      Intel
ProviderName:      Intel
Num files:         21
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:33 AM


***************************************************************************************

Driver:            Intel(R) 82801GB Serial ATA Storage Controllers - 27C0
Driver Type:       IDE ATA/ATAPI controllers
Driver Version:    7.0.0.1014
Driver Date:       01/19/2005
Manufacturer:      Intel
ProviderName:      Intel
Num files:         9
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:33 AM


***************************************************************************************

Driver:            Intel(R) 82801GB USB Universal Host Controller - 27C8
Driver Type:       Universal Serial Bus controllers
Driver Version:    7.0.0.1014
Driver Date:       01/19/2005
Manufacturer:      Intel
ProviderName:      Intel
Num files:         14
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:33 AM


***************************************************************************************

Driver:            Intel(R) 82801GB USB Universal Host Controller - 27C9
Driver Type:       Universal Serial Bus controllers
Driver Version:    7.0.0.1014
Driver Date:       01/19/2005
Manufacturer:      Intel
ProviderName:      Intel
Num files:         14
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:33 AM


***************************************************************************************

Driver:            Intel(R) 82801GB USB Universal Host Controller - 27CA
Driver Type:       Universal Serial Bus controllers
Driver Version:    7.0.0.1014
Driver Date:       01/19/2005
Manufacturer:      Intel
ProviderName:      Intel
Num files:         14
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:33 AM


***************************************************************************************

Driver:            Intel(R) 82801GB USB Universal Host Controller - 27CB
Driver Type:       Universal Serial Bus controllers
Driver Version:    7.0.0.1014
Driver Date:       01/19/2005
Manufacturer:      Intel
ProviderName:      Intel
Num files:         14
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:33 AM


***************************************************************************************

Driver:            Intel(R) 82801GB USB2 Enhanced Host Controller - 27CC
Driver Type:       Universal Serial Bus controllers
Driver Version:    7.0.0.1014
Driver Date:       01/19/2005
Manufacturer:      Intel
ProviderName:      Intel
Num files:         14
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:33 AM


***************************************************************************************

Driver:            Intel(R) 82801GB SMBus Controller - 27DA
Driver Type:       System devices
Driver Version:    7.0.0.1014
Driver Date:       01/19/2005
Manufacturer:      Intel
ProviderName:      Intel
Num files:         21
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:34 AM


***************************************************************************************

Driver:            Canon MP360
Driver Type:       Imaging devices
Driver Version:    7.0.2.0
Driver Date:       10/01/2003
Manufacturer:      Canon
ProviderName:      Canon
Num files:         22
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:35 AM


***************************************************************************************

Driver:            Canon MP360 Series Printer
Driver Type:       Printers
Driver Version:    1.73.0.0
Driver Date:       10-7-2003
Manufacturer:      Canon
ProviderName:      Canon
Num files:         28
Backed Up:         False
XMLIgnition:       12/12/2006 3:57:35 AM

---

### Post by houstonbofh on 2006-12-12
Dual core with late Nvidia cards seems to be causing issues for some.  On the keyboard, go into the BIOS and enable "Legacy Keyboard Support" and see if it helps.  Some USB keyboards do not identify themselves nice.

---

### Post by Drilldown on 2006-12-12
G'Night all.

---

### Post by keheikev on 2006-12-12
Its a ps2 keyboard in both cases the spare and the one that came with the machine. The bios is so barebones it doesnt have that option for keyboard type. I think my next step is trying 6.10 like I had on my older machine. I will try the link you sent Drilldown.
Keheikev

---

### Post by keheikev on 2006-12-13
I will try that driver guide toolkit to get a specific list of components. My system is very similar to yours Drilldown only the the processor is 3.0 GHZ. Have to wait till I get back from work. Heres a thought could there be some windows chicanery that is specifically blocking Ubuntu from working here? I am going to download 6.06 LTS and see if that doesnt work better. I don't think that imgburn is the problem but it did give two errors before the burn started Unable to lock volume and unable to dismount volume access denied then I clicked continued and it burned the image file.
Kiheikev

---

### Post by keheikev on 2006-12-14
Its funny ubuntu start menu works fine from the cd using the keyboard but still no ability to use the keyboard using edgy eft live cd. I see in devices that there is ibm ps/2 keyboard support. What does this mean. Should I try the 6.06 or 6.10 versions or maybe the alternative versions with the text setup? How could the the md5 sums be okay and the disk checks out from the ubuntu start menu.
Keheikev

---

### Post by keheikev on 2006-12-14
Well its got to be a bug I redownloaded and burned a new good image of both 6.06 and 6.10 and the keyboard works great in 6.06 but not at all in 6.10. Only the numlock key comes on.
Kiheikev

---

### Post by Sef on 2006-12-14
> Well I did burn the cd at a lower speed 12x

For best results when burning, burn at 4x or lower.

---

