---
title: "[SOLVED] help getting feisty on a SATA...twist"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by pcrussell50 on 2007-09-03
the title should say it all, but there's a twist...

i have this asus mobo with an athlon64 3800+ cpu.  the mainboard will take sata or ide drives or both.  for the past year, i've been running two ide drives with no sata drives in a standard, master-slave configuration, and dual booting with winxp on c: and ubuntu on the other drive.  no muss, no fuss.  booting took me to the standard grub screen where you choose which os to boot.  i loved it.

now, i have a sata drive that i'm using as c: with winxp, and an ide drive that i want to put feisty on.

when i go to install feisty off the live cd, everything goes perfectly normally.  when the page comes up to choose where to put it, i give it the whole ide drive...80Gb.  it installs normally.

the trouble arises when i try to reboot.  it just boots straight to windows on the sata drive.  it's as if that boot menu where you select which OS, never made it to the sata drive.

here's the twist...from googling, i think my mainboard's support of sata is one of those SATA/RAID, or fakeRAID things.  i vaguely know what a raid is, but i do not want to use it as a raid, i just want two separate drives, like hundreds of other use.  and it works just like that in winxp, as long as you run this floppy during install of windows.  apparently, the floppy helps windows "see" the sata drive just like a standard ide c:   where the raid part comes in i'm not so sure except during windows bootup, the the c: (sata) drive appears by itself as drive 0 in a raid list.   so, i guess my "raid" consists of one drive and not an array.  i'm concluding that the way my mainboard handles sata is by way of a raid, even if it's only one drive.

anyhoo, any ideas on how i can get feisty to dual boot?

remember, i have a whole, separate ide drive to devote to feisty.

regards,
peter

---

### Post by annda on 2007-09-03
on which disk did you install GRUB? if it was the second (feisty) disk, you need to tell BIOS to boot from that - either by permanently changing the BIOS settings or hitting the right key during boot to change the boot order.

---

### Post by Mongo5000 on 2007-09-03
I have the same setup and what annda suggested works perfectly.

I do however have 2 sata drives in a raid with vista and 3 storage partitions but its basically the same.

---

### Post by pcrussell50 on 2007-09-03
> **annda said:**
> on which disk did you install GRUB? if it was the second (feisty) disk, you need to tell BIOS to boot from that - either by permanently changing the BIOS settings or hitting the right key during boot to change the boot order.

first, great stuff to go check out. thanks.  as soon as i get home from this trip, i'll look into it.

now, do i have a choice as to where i install the GRUB?  i don't recall being offered the choice in the feisty live cd installer.

second, i like the idea of intervening during boot with a key stroke, and then choosing which drive to boot.  any ideas as to which keys to try first?  i ASSume the function, keys.  i suppose a little googling usng the name of my bios  might turn something up.

---

### Post by pcrussell50 on 2007-09-06
the trick was just as annda said, and mongo5000 backed it up.  when i installed feisty onto the ide drive, grub went there with it.  i went to the bios, and told it to give boot priority to the ide before the sata/raid drive, and we're good to go.  the grub comes up on reboot and gives me the choice between xp or ubuntu.  sweetness prevails.

-peter

---

### Post by armandh on 2007-09-06
with a single drive and 2 partitions grub has the mbr and determines what partitions boot 
when there is 2 drives and the mobo can select where to boot from it must select the drive with the grub. 
if each drive can boot, possibly the mobo can select between active drives with out a loader.

---

