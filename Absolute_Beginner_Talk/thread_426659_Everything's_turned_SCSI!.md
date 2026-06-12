---
title: "Everything's turned SCSI!"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-04-28
(X)ubuntu 7.04 refers to my IDE HDDs now as sda (for the first HDD) rather than hda.  I. e. SCSI rather than IDE.
I don't have a problem with this, but anybody know why?
:confused:

---

### Post by [S|G] on 2007-04-28
Are your HDDs SATA by any chance? SATA hard drives show up as SDx and not HDx

---

### Post by Bachstelze on 2007-04-28
Because they changed the way ATA drives are handled (ATA and SCSI drive are now handled by the same driver).

---

### Post by RAKninja on 2007-04-28
yea, treats em the same, very effeciant... now if someone could just tell me how to take care of this dumb integrated graphics preventing my boot..

---

### Post by Blofeld on 2007-04-28
@Hymn:  I see, thanks!
@SG:  Boy, aren't they ever NOT sATA ... I have two old-*** parallel IDE drives.
:lolflag:

---

### Post by jerrylamos on 2007-04-28
Well the force fit of IDE and SATA into SCSI causes lots of us grief winding up in an error message "can't access tty" which is basically fsck getting all fouled up with CD vs hard drive and I don't know what else.  There are some fixes which work for some people, see my post  "Workarounds" in "Installations and Upgrades".

I also had some integrated graphics problem(s) which are fixed for the moment; what are the symptoms of your problems?  Also see "Workarounds"...

Cheers, Jerry

---

### Post by RAKninja on 2007-04-28
i got a few threads about it, and i mention it in every post because its been about a week, and i havent been able to figgure it out... i'll check "workarounds" again, but the only two (a workaround wiki and a older post somewhere on these boards) i could find are for edgy at the latest, and didnt work for me there either.

basically im running off of my PCI geforce 6200 with drivers and glx and everything pretty much working.  the parts that mess up do so, i suspect, because my bios is set to intel integrated graphics control.  if i try to boot with the bios set to pci, i crash after the third bar on the splash loading screen (i cant tell where it is with the f2-f7 thing during boot, it shoots by too fast) all i can tell is i am getting some sort of page fault.  as i mentioned before i did try the blacklisting and adding various lines to grub kernel load line, and xorg.conf.

---

