---
title: "rEFInd - EFI Shell -UEFI version"
date: 2016-01-22
forum: Apple Hardware Users
---

### Post by cave-canem on 2016-01-22
Hello!
 
Sorry for the errors - is a computer translation.
 
Anyone using EFI Shell or Memtest86 on Mac?
 I am wondering in what gives the command "ver" (EFI  Shell) or similar information from Memtest86.
 In other words, interests me what version of UEFI is used in Mac.
 (From the Apple support I received a reply that they do not have this information).

Respond please, and if possible, specify _Boot ROM_ version (or the year of production of the computer)
 Thanks in advance for your answers!

P.S.
I have MacBookAir4,1 BOOT ROM ver.MBA41.0077.B12, UEFI ver. 1.10

---

### Post by oldfred on 2016-01-22
From Ubuntu you can run this, do not think before you boot you can get that detailed info:

sudo dmidecode > bios.txt

And on my old BIOS system you get this, plus a lot of other data in bios.txt

```
Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
    Vendor: Phoenix Technologies LTD
    Version: 2.00   
    Release Date: 08/30/2006
    Address: 0xE4180
    Runtime Size: 114304 bytes
    ROM Size: 1024 kB
    Characteristics:

```

---

### Post by cave-canem on 2016-01-22
Thank you for your answer, oldfred, but I'm just thinking to install Ubuntu on my Mac.
 
In this way, command ```
dmidecode
``` is not available on OS X.
 
I am not interested in version BOOT ROM, but the version of **UEFI** used in Apple BOOT ROM

I also very much needed information about the UEFI versions on **modern** **Apple** computers, so I'm trying to get it in different ways, including UBUNTU community

I hope for understanding my problem!

---

### Post by oldfred on 2016-01-22
Can you boot Ubuntu live installer in UEFI mode?
Either directly or with rEFInd?

BIOS entry in dmidecode is UEFI version on my newer UEFI system(not Mac).
```



BIOS Information
    Vendor: American Megatrends Inc.
    Version: 1304
    Release Date: 07/11/2014
Further down is this:
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 4.6
```

And if just UEFI version, did you not post it above?
> UEFI ver. 1.10

---

### Post by cave-canem on 2016-01-22
If I understand you correctly, your code displays information about the BIOS, but Mac is not a BIOS, he EFI (since 2006), which Apple calls BOOT ROM, and so I was wondering version of UEFI specification used in **modern**** Apple computers** (ie in the UEFI specification BOOT ROM)
[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) section "**History**".

Please note that I'm interested in it just for the **modern Apple ****computers**, I have the same model 2011y. ver UEFI 1.10, so that through my Mac I can not get the information that interests me.

While I found no other way but to anyone (having a Mac, and most likely using rEFInd and **EFI Shell, **see link above) will execute the command "ver" in the EFI Shell, and share with me the result.

Thank you for your patience!

---

### Post by rogerio-luz-coelho on 2016-01-30
See if this is what you need: 

[https://support.apple.com/en-us/HT201518](https://support.apple.com/en-us/HT201518)

---

### Post by cave-canem on 2016-01-30
Thanks, but I asked what number of UEFI specification correspond to the  BOOT ROM of modern computers from Apple.
[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface (History)]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface")

---

