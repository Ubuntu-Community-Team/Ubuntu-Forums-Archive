---
title: "2 HD dual boot: always MBR error on win drive after reboots"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by wildcardny on 2007-05-14
Hi all.  New linux and ubuntu user here with a problem I've yet to solve:

I initially had pre-existing win2k drive as master and installed ubuntu on slave, but constantly got grub error or "error loading OS" upon boot (or reboots after a windows session), so I set system as follows:

Ubuntu installed on 200Gb master (hda);  boot partition sized accordingly (to deal with apparently bios limitation on this larger drive) w/ grub installed to that drive

Win2kpro on 20GB drive set as slave (hdb).  

At long last ended up with a successful dual booting system; or so I thought.  

Whenever I log into windows after an ubuntu session, I get a drive error bluescreen and  always have to repair the mbr of the win drive.

I am seeking solutions/suggestions from any and all.  TIA

---

### Post by nightskywind83 on 2007-05-15
This is *very* interesting, to say the least.

You said GRUB was installed onto hda, the ubuntu drive.  Could it possibly be installed on your Win2k drive as well?  It may yet be there unless you did a fresh Win2k install... Unless...

My experience is mostly dual booting XP and Linux.  I do know that in order to "fix" a Windows drive on which GRUB was installed to allow dual booting, you should run the recovery console and use the fixmbr command.  However, I should point out that my experience has always been to install windows on the master HD, and linux on the slave, and during linux installation it would write GRUB to the Windows MBR to enable the dual boot.

Hope this helps.  Any further info you can provide may help.

---

### Post by wildcardny on 2007-05-16
With win2k drive as master and u'b'tu installed on slave, grub ended on  master, which windows doesn't like at all (I've been using UBCD utilities to fix mbr errors and try my hand at manually fixing grub probs).  So I tried the inverse and made sure grub went on the linux drive .  At that point, win2k's mbr healthy. If I disable u'b'tu drive comapletely I can boot windowss all day w/o issue.  But once I hav ubuntu back inthe mix, issues w/ win2k whenever I try to boot into that os.

---

### Post by wildcardny on 2007-05-16
Addendum: I'm a d***head.  Upon logging into windows the OS always displayed what I took to be new hardware found applet and I habitually just canceled it, thinking it was "finding" the linux drive (which I'd forgotten I'd long disabled in device manager).   What it was actually doing was adding the fixed windows volume. Once I let it complete, everything went smoothly.  So a successful dual-booting system now

---

### Post by adromidon on 2007-05-16
Great congradulations glad you got it working

---

### Post by wildcardny on 2007-05-17
Yes, thanks.  I'm liking it so far.

---

