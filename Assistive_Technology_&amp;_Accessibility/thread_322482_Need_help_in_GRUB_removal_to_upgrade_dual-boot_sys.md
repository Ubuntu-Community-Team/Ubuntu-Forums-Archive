---
title: "Need help in GRUB removal to upgrade dual-boot system"
date: 2006-12-20
forum: Assistive Technology &amp; Accessibility
---

### Post by James King on 2006-12-20
Hi:

I'm a relative newbie in Ubuntu with advanced glaucoma, and was a reader of messages on the AT list until hit with many other medial problems preventing me from keepiing up with the development of Edgy.  I was able to upgrade my XP-Ubuntu dual-boot system from Breezy to Dapper before having to put off experiementing with Ubuntu for many months.

My problem is that I can't figure or find out how to remove GRUB from my hard disk partitioions in order to upgrade my XP programs separately from my Dapper or Edgy programs while using Norton GHOST or Drive Image XML images to move from a 30 GB hard disk to a 100 GB hard disk on the same DELL Latitude D610 laptop with an 80 GB modular hard disk.  I must unmake the tie that GRUB makes betwee the XP partitioons and the Dapper partitions in order to separately upgrade images of some programs (such as the PlusTek Book Reader and the Book Courier and the Monomouse) without losing the settings of some essential legacy programs (such as ZoomText 8.0 and Dragon Naturally Speaking Pro 8.0).  This is necessary to avoid the visual agony of having to reinstall any programs or settings without ZoomText, since all the on-screen instructions are in very small font sizes -- and because the Dragon voice macros depend on the ZoomText settings.  

Whenever i rrestore an image of the pyramid consisting of software composed  of the XP operatiing system and these key application programs (which do not yet have Linux equivalents) on a hard disk that has been re-partitioned either for a Ubuntu upgrade, a hard disk upgrade, or an XP upgrade, I get only an error message (e.g.,GRUB # 22) and/or a computer  unbootable from any hard disk.

I have looked -- as welll as my visual challenges have allowed -- for iniformation on how to uninstall GRUB from the Master Boot Record of any dual-boot system, and have been unable to find it even on the GNU/GRUB website or the The Official Ubuntu Book.

Can anyone give me a step-by-step recipe for removing GRUB from either or both an operatinig dual-boot system or a non-operating dual-boot system using Partition Magic, the Microsoft XP Install CD, the Dapper CD, the Symantiec Systemworks CD, the Symantec Recovery CD, or the (Linux) System Rescue CD?

I would appreciate greatly any help on this.  Without it, I shall not be able to make much use of new Ubuntu releases until they all include a full-screen equivalent of at least ZoomText, if not Dragon Naturally Speaking Professional.

Thanks to Henrik and the AT List Members for help and encouragement in the past.  Your work is very excitiing.  I was able to iinstall Dapper using the "F5 Moderately Visually Iimpaired" option, although it was very difficult to fit the High-Contrast Big-Priing Inverted Theme on my 14-inch laptop screen by moving it around with the tiny pointer on Dapper (I am happy to see that the F5 MVI pointer in Edgy is somewhto the GRUat bigger).

I look forward to trying to install Edgy and  Feisty(?) as woon as I can find a solution to my GRUB problem without having to learn visually challenginig command-line programming.

James King

---

### Post by acturneruk on 2006-12-20
It's been a few years since I've had Windows on my machine, but if I remember correctly you can boot with the winxp disc into the recovery console, or whatever they call it, and use the fixmbr command to reset the MBR.

HTH

---

### Post by Paloseco on 2007-04-29
There is the supergrub that allow you to restore the windows MBR.

---

