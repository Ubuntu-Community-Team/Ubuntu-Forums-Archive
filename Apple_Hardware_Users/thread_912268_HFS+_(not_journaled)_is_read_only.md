---
title: "HFS+ (not journaled) is read only"
date: 2008-09-06
forum: Apple Hardware Users
---

### Post by philipashlock on 2008-09-06
I have an external USB SATA drive that I formatted as HFS+ with journaling off in OSX. When I first used the drive in ubuntu 7.10 it was able to mount automatically as read/write.

I've since removed the drive from the external enclosure and installed it in my computer, so it's now directly connected via SATA cables. I added the line in fstab:

```
/dev/sdb1 /media/ashlock hfsplus defaults 0 0
```

and the drive mounted fine, but now it's read-only, I get the same results when mounting it from the command line:

```
sudo mount -t hfsplus /dev/sdb1 /media/ashlock/
```

Does anybody know why the drive would no longer have write access? Before removing it from the external enclosure, I also used it as an external drive in OSX, is it possible that OSX somehow enabled journaling? This doesn't seem very likely to me, but is there a way I can check to see if journaling was enabled?

---

### Post by cyberdork33 on 2008-09-06
look in your dmesg output when the drive is mounted. It will tell you if it detects journaling and mounts it read-only.

---

### Post by schauerlich on 2008-09-07
Sometimes disabling journaling doesn't "stick" for some reason, and you have to enable it and then disable it again with diskutil. In a terminal from OS X:

```

diskutil enableJournal /dev/diskxsy
diskutil disableJournal /dev/diskxsy

```

Where x is the HD number and y is the partition number.

---

### Post by philipashlock on 2008-09-08
Thanks for the help, I looked in the dmesg output and saw that it was read-only because it hadn't been cleanly unmounted and i had to install and run fsck.hfsplus to fix it.

---

### Post by cyberdork33 on 2008-09-08
> **philipashlock said:**
> Thanks for the help, I looked in the dmesg output and saw that it was read-only because it hadn't been cleanly unmounted and i had to install and run fsck.hfsplus to fix it.

Please mark this thread as solved from the thread tools menu. Thanks.

---

### Post by NetpigsBang on 2008-09-08
**[[color=magenta]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=seagreen]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[color=red]Make money online,now![/color]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by sh2008seo on 2008-09-08
[**Warhammer Online**](http://www.tgacn.com/warhammer-online.php) game development began under the company Climax Online. The project was officially canceled in June 2004 when Games Workshop determined that the roll-out costs would be too expensive.[6] However, work on the game never actually stopped as Climax Online continued the project using their own funds until the company reported in late 2004 that the Warhammer Online project was shut down due to difficulty in securing a publishing agreement.With the license available again, Games Workshop was approached by Mythic Entertainment, who were interested in acquiring the license and starting a new project from scratch. A long-standing relationship between several Games Workshop managers and the CEO of Mythic Mark Jacobs ensured that a deal was quickly reached. The [**Warhammer Online**](http://www.tgacn.com/warhammer-online.php) license was acquired by Mythic on May 18, 2005.[7]Though [**Warhammer Online**](http://www.tgacn.com/warhammer-online-gold.php)** gold**: Age of Reckoning is being developed by Mythic Entertainment, Games Workshop is also involved with the ongoing development of the project. Their role seems to be not only to ensure that the project remains true to the Warhammer Fantasy IP, but also to work with Mythic to allow for the appropriate development and extension of the IP as necessitated for the MMO. Mythic has previously created successful MMOs, including Dark Age of Camelot. It is hoped that Mythic having developed some MMO game play elements and 25 years of Games Workshop's game industry background will lead to a successful game[8].[**Warhammer Online**](http://www.tgacn.com/warhammer-online.php) :Age of Reckoning is not purely derived from either Warhammer Fantasy Battles or Warhammer Fantasy Roleplay or any other source alone, but rather from the Warhammer Fantasy universe as a whole.

---

### Post by Spoony_Man on 2010-10-01
> **cyberdork33 said:**
> look in your dmesg output when the drive is mounted. It will tell you if it detects journaling and mounts it read-only.

This guy +1!

---

