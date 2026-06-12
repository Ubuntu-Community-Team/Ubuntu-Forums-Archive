---
title: "RAID Array on a Power Mac G5"
date: 2010-06-29
forum: Apple Hardware Users
---

### Post by mister k on 2010-06-29
Hey people,

I'm just about to be given a Power Mac G5 (Late 2005) Dual 2.0GHz. I think this was the last G5 produced.
I plan on using it as file server/NAS and will probably run 10.04 LTS (or maybe 8.04 LTS).

Ideally I would install a SATA RAID controller and run 4 1TB drives in a RAID 5 configuration.

The only thing I'm unsure about is choosing a compatible RAID controller. I need to find a RAID controller that

- Is PCIe
- Is compatible with both the Power Mac and Ubuntu PPC
- Does true hardware RAID
- Doesn't cost a fortune!

Am I right in thinking that the card might need to be open firmware compatible? If it makes any difference, I plan on running the OS from a separate 5th drive.

Has anyone had any experience doing something similar? Can anyone point me in the right direction for choosing a card?

I've found [this]("http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=280509132551&ssPageName=ADME:X:RTQ:GB:1123") on eBay. I asked the seller and he claims it supports true hardware RAID and says the chipset is a Silicon Image SIL3124. I does seem suspiciously cheap though...

Thanks in advance for any help!

---

### Post by linuxopjemac on 2010-06-29
I don't have experience with RAID on PowerPC. I do run a Dell Server running ClearOS with a 3Ware hardware RAID controller.. ClearOS, which is based on CentOS, which is based on RedHat, has support for the following:

>       Adaptec SCSI - 200x, 21xx, 22xx, 27xx, 28xx, 29xx, 32xx, 34xx, 39xx, 54xx
    *
      Adaptec IDE - 2400A
    *
      3ware IDE - Escalade 3W 5xxx/6xxx/7xxx


I guess that these cards work out of the box under Linux. You might want to Google these cards for powerpc support. But I t hink that if they work on Intel, they should also work on PPC.

---

### Post by linuxopjemac on 2010-06-29
more info:
[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

---

