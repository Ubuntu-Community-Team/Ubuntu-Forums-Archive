---
title: "iMac G4/800 15&quot; no video"
date: 2008-09-02
forum: Apple Hardware Users
---

### Post by ristosu on 2008-09-02
I'm trying to boot Ubuntu 6.06.1 live CD. I get the yaboot prompt as usual. Then it loads the kernel and the ramdisk. The last message says: DO_QUIESCE finished. This half screen of text stays while the boot continues, the disk is spinning as it should.

The machine is a 1st generation flat-panel iMac, PowerMac4,2, with GeForce2 video (the 17" models had GeForce4). Has anyone succeeded (or failed) with a similar machine?

Risto

---

### Post by tiresia on 2008-09-02
Have you tried at the first prompt?
'video=ofonly'

---

### Post by ristosu on 2008-09-03
I have tried 'live video=ofonly', it made no difference.

Risto

---

### Post by stream303 on 2008-09-05
I'd be tempted to add "nosplash" to your kernel parameters.  I'm surprised that the live-cd is giving you trouble with the nvidia.

Also, perhaps you'd get farther with the "alternate" installer rather than the live-cd.  And, I'd definitely try the 8.04 LTS as well.

---

### Post by ristosu on 2008-09-06
> **stream303 said:**
> I'd be tempted to add "nosplash" to your kernel parameters.  I'm surprised that the live-cd is giving you trouble with the nvidia.

Also, perhaps you'd get farther with the "alternate" installer rather than the live-cd.  And, I'd definitely try the 8.04 LTS as well.
Nosplash didn't make any visible difference.

Then I tried 8.04 LTS alternate, and it works :)

Could it be that the 256 MB RAM is not enough for the live CD?

Thanks,
Risto

---

### Post by ristosu on 2008-09-08
I've been a little hasty in my conclusion, sorry.

Actually the 6.06.1 Live CD did work when it reached the graphical X desktop. Only the loading of the drivers etc. was invisible. When in X, changing to virtual terminal 1 (Ctrl-Alt-F1) shows something, but not the expected.

Risto

---

### Post by sh2008seo on 2008-09-08
[**Warhammer Online**](http://www.tgacn.com/warhammer-online.php) game development began under the company Climax Online. The project was officially canceled in June 2004 when Games Workshop determined that the roll-out costs would be too expensive.[6] However, work on the game never actually stopped as Climax Online continued the project using their own funds until the company reported in late 2004 that the Warhammer Online project was shut down due to difficulty in securing a publishing agreement.With the license available again, Games Workshop was approached by Mythic Entertainment, who were interested in acquiring the license and starting a new project from scratch. A long-standing relationship between several Games Workshop managers and the CEO of Mythic Mark Jacobs ensured that a deal was quickly reached. The [**Warhammer Online**](http://www.tgacn.com/warhammer-online.php) license was acquired by Mythic on May 18, 2005.[7]Though [**Warhammer Online**](http://www.tgacn.com/warhammer-online-gold.php)** gold**: Age of Reckoning is being developed by Mythic Entertainment, Games Workshop is also involved with the ongoing development of the project. Their role seems to be not only to ensure that the project remains true to the Warhammer Fantasy IP, but also to work with Mythic to allow for the appropriate development and extension of the IP as necessitated for the MMO. Mythic has previously created successful MMOs, including Dark Age of Camelot. It is hoped that Mythic having developed some MMO game play elements and 25 years of Games Workshop's game industry background will lead to a successful game[8].[**Warhammer Online**](http://www.tgacn.com/warhammer-online.php) :Age of Reckoning is not purely derived from either Warhammer Fantasy Battles or Warhammer Fantasy Roleplay or any other source alone, but rather from the Warhammer Fantasy universe as a whole.

---

