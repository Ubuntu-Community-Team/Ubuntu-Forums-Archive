---
title: "Why does not (K)Ubuntu does not work for me?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by brownbagel on 2008-02-26
When I try to run Ubuntu from LiveCD, after the boot section it just simply does not work on my HTPC system. If I do the same with my other computer, I receive a full working load up without any problems and I'm able to test and play around with Ubuntu.

Here's the procedure: LiveCD boots up as it should and enters to the boot menu. I choose the first from the list, since I want to test the Ubuntu for a starters. Ubuntu logo with progress bar appears on screen. After a minute or so I get slowly scrolling text across the screen telling this and that (i have no idea what), possibly about some errors and things not succeed, it stays this way about 20 minutes. After this state I get a blank screen, endless blank screen, no activity what so ever, none.

Here's my system information:
Asus M2A-VM HDMI
Kingston 1024MB 667MHZ DDR NON-ECC DIMM x2
AMD Athlon 64 x2 4400+ 2.3Ghz
Club 3D Nvidia 8400GS 256 GDD2 PCI-E
Asus S/PDIF-kortti
Pioneer BDC-202BK Blu-Ray (reads also dvd/cd)
Windows Vista
Antec Fusion  HTPC case

I suppose that Ubuntu does not support something or some from my system. Is there anything I can do? I dont have previous knowledge of Linux or Ubuntu.

Thanks.

---

### Post by kesman on 2008-02-26
Have you tried the alternate install disk or the safe graphics mode in the LIVEcd?
What kind of monitor are you using? I had to install with alternate install cd with my lcd-tv, since it needs a custom resolution to be set that livecd isn't capable of.
Also, there's an option in the LIVEcd boot menu that allows you to edit the boot parameters. Remove splash and quiet from the end of the bootline and try again starting. This way you'll see what goes wrong during the startup.

---

### Post by oedha on 2008-02-26
could be your nvidia...:)
can you boot from safe graphic mode ( menu...2nd line )

---

### Post by brownbagel on 2008-02-26
Thanks guys! I shall try to run it again in safemode after work.

I'm using a projector as a "monitor", since this is a HTPC system.

Please, could you guide me how to edit the boot parameter; removing splash and the quiet mode. Is there anyway to get everyhing logged , e.g. a txt file. Would be easier to track what went wrong since I dont have any knowledge about linux systems?

Nvidia is well supported with Linux (i guess). They are offering drivers for Linux anyway :KS

---

### Post by oedha on 2008-02-26
nvidia will work later....after you install ubuntu and enabling the restricted driver
to edit boot menu....press F6 then edit it

---

