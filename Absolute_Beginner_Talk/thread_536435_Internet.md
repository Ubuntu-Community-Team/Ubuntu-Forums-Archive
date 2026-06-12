---
title: "Internet"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by stuart.mullett on 2007-08-27
I have just brought a edimax(EW7108PCG) wireless lan cardbus and i would like some help in setting it up to my broadband connectoin Router. I have only just started to use ubuntu or any linux O/S so a very simple step by step guide would be very nice.

Many Thanks
Stuart

---

### Post by solar george on 2007-08-27
What model is it?

Could you type 
```
lspci
```
into a terminal and post the output.

---

### Post by stuart.mullett on 2007-08-27
What do you mean by what model

---

### Post by solar george on 2007-08-27
Just plug it in and post the output of lspci.

---

### Post by ntlam on 2007-08-27
> **stuart.mullett said:**
> What do you mean by what model

this mean you need to know the detail of your wireless card. You can also look it up on windows hardwares

---

### Post by stuart.mullett on 2007-08-29
Listed below is the information asked fore.hope this helps

kim@kim-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)

00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)

00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)

00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)

00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)

00:07.0 Communication controller: Agere Systems 56k WinModem (rev 01)

00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO

00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)

00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)

00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)

01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)

02:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI

kim@kim-laptop:~$

---

### Post by solar george on 2007-08-29
> 02:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI

You seem to have a RaLink RT61 based card try,

[http://ubuntuforums.org/showthread.php?t=296822&highlight=RaLink+RT61](http://ubuntuforums.org/showthread.php?t=296822&highlight=RaLink+RT61)

---

### Post by stuart.mullett on 2007-08-30
Thanks for the info i will give it a go and let you know

---

