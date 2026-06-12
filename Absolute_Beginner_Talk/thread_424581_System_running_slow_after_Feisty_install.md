---
title: "System running slow after Feisty install"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by dberg on 2007-04-26
I did a fresh install of Feisty a couple of days ago and have now noticed that my system runs much slower than it did with Dapper. My internet speed if fine, it is just opening programs that is very slow.

Anyone know why this would be?

Thanks

---

### Post by diskotek on 2007-04-27
i'm not sure but it may be relavent with your system specs. dapper probably runs faster like in my machine...
you tried any ubuntu customization? however they are mostly for edgy eft it may apply to you as well:
[http://blog.lxpages.com/2007/04/24/ubuntu-performance-guides/](http://blog.lxpages.com/2007/04/24/ubuntu-performance-guides/)

---

### Post by dberg on 2007-04-27
I have tried several of the "performance enhancing" options on that website but nothing has helped very much.

Does anybody else know how to help with this, I timed it and it literally takes 11 seconds to open an application (i.e. Firefox, terminal, calculator, etc.) there has to be some sort of explanation as to why my system is so much slower than it was with Dapper. I am not running desktop effects or anything fancy.

---

### Post by toddward on 2007-04-27
I can't remember the commands, but you should be able to change how linux interacts with your hard-disks.  That seems to be your culprit.

---

### Post by johnny4north on 2007-04-27
Toddwared may be right here is a link that may help you out ..[http://www.go2linux.org/node/20](http://www.go2linux.org/node/20)

---

### Post by dberg on 2007-04-27
alright, here is the physical info from my drive, the problem is I am far too inexperienced at this to know what to make of it.

```
dberg@dberg-desktop:~$ sudo hdparm -I /dev/hdb1
Password:

/dev/hdb1:

ATA device, with non-removable media
        Model Number:       ST3160023A                              
        Serial Number:      4LJ39H99            
        Firmware Revision:  8.01    
Standards:
        Used: ATA/ATAPI-6 T13 1410D revision 2 
        Supported: 6 5 4 
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  312581808
        device size with M = 1024*1024:      152627 MBytes
        device size with M = 1000*1000:      160041 MBytes (160 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = ?
        Recommended acoustic management value: 128, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
                unknown 84[11]
                unknown 84[12]
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 1 determined by CSEL
Checksum: correct

```

---

### Post by toddward on 2007-04-28
Awesome, that's what it was.  You can change parameters with it as well, right?

---

### Post by dberg on 2007-04-28
> **toddward said:**
> Awesome, that's what it was.  You can change parameters with it as well, right?

I would assume that it is possible to change parameters also, trouble is I don't know what parameters would be need to be changed to fix this problem. Can anyone who knows more about it than I do suggest some things that would be good to change (and also how to do that)?

---

