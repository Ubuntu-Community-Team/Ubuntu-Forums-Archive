---
title: "Dual boot Ubuntu &amp; W7 on Asus eee 1005HAB"
date: 2012-09-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by habduck on 2012-09-22
Newb here:

I was running XP and dual booting Ubuntu. I upgraded the Windows partition to W7 (didn't touch the Ubuntu partition) and now it boots right to W7 without the dual boot menu coming up.  How do I get that back?

(I really don't use or know much about Ubuntu. The reason I dual boot is to have an environment where I can rescue my data in case Windows crashes.  This came in very handy last year when XP wouldn't boot because I was able to rescue my data via Ubuntu before doing a fresh install of XP.)

---

### Post by nyamina on 2012-09-22
> **habduck said:**
> Newb here:

I was running XP and dual booting Ubuntu. I upgraded the Windows partition to W7 (didn't touch the Ubuntu partition) and now it boots right to W7 without the dual boot menu coming up.  How do I get that back?

As far as I know, Windows is unfriendly, and just installs over Grub, the Ubuntu bootloader. To solve it, just reinstall Grub. Boot up from the live cd / live usb and install boot repair (see: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)). This program should reinstall Grub, and all should be sweetness and light again.

On a side note, you would actually be able to rescue your data, if you ever needed to with just a live usb, without installing Ubuntu. I've done it for tons of people. You could just have Windows. 

But, of course, I would say you should just use Ubuntu, because it can do everything windows can, but then I'm biased =)

---

### Post by habduck on 2012-09-22
Thanks. That's just the tool I was looking for. (Even though  I didn't know it. LOL)  Downloaded the iso, burned it to a DVDRW, booted from it and it worked like a charm.  Had to go edit the grub.cfg but I'd done that before so it was easy.

TYVM for your assistance.

The other reason I like dual booting from the HD is that I travel a lot.  Last time I didn't have time to mess with reloading Windows but with Ubuntu on the HD it was easy to get on-line and deal with it later.

(sent from Firefox on Ubuntu :))

---

