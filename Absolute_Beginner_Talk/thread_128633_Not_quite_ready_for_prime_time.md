---
title: "Not quite ready for prime time"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by tiamet on 2006-02-11
I'm sitting here in the office using a WinXP computer, with no way to transfer data to the Ubuntu computer, and trying to figure out how to enable a modem in Ubuntu.  After searching hundreds of pages and reading endless code and warnings all I've found is that one needs to "download" another program. 
Well, if I could download a program I wouldn't need help with Ubuntu modem install,  "duh".

Ubuntu 5.10 is the second version I've tried and it's getting very close to being a useable OS, but until they can add support for more typical devices used in WinXP computers there will be resistance to using Ubuntu.

Hopefully the next version of Ubuntu will have most of the "fixes" in it.  Until then I have an $800 dust collector sitting on a desk.

---

### Post by fuscia on 2006-02-11
il pleure dans mon coeur pour toi.

---

### Post by soonindallas on 2006-02-13
[QUOTE=tiamet]I'm sitting here in the office using a WinXP computer, with no way to transfer data to the Ubuntu computer, and trying to figure out how to enable a modem in Ubuntu.  After searching hundreds of pages and reading endless code and warnings all I've found is that one needs to "download" another program. 
Well, if I could download a program I wouldn't need help with Ubuntu modem install,  "duh".

Ubuntu 5.10 is the second version I've tried and it's getting very close to being a useable OS, but until they can add support for more typical devices used in WinXP computers there will be resistance to using Ubuntu.

Hopefully the next version of Ubuntu will have most of the "fixes" in it.  Until then I have an $800 dust collector sitting on a desk.[/QUOTE]

hook em up with an ethernet cable, crossed.

---

### Post by fuscia on 2006-02-13
doesn't your computer have a cd burner? if so, just put all the tarballs on a cd and upload them into ubuntu. or, you could put them on a digital camera, or some other mass storage device.

---

### Post by mips on 2006-02-13
What brand&model modem do you have ?
Who is your ISP ?

Do you have 2 PC's or are you dual-booting ?

---

### Post by LordBug on 2006-02-13
We *really* need more information on this.  There's several ways to transfer data between PCs.  The easiest have already been mentioned, but we can guide you better if we know the specifics of your setup.

Is this all on 1 PC?  If so, Linux can mount your XP partitions.  NTFS support is read-only, unfortunately.  Also, people have developed drivers for the EXT3 filesystem for Windows.  I just read that there's ReiserFS drivers now too.  You could mount the Linux partitions in XP with those.

If it's 2 PCs, then I would highly recommend networking the two computers (as was mentioned before).  Easiest would be to have both connected to you already established network.  Backup plan would be to use a Crossover cable and direct-link the 2 together.  This will require a bit of manual network setup on BOTH computers, but it's easy enough to do.  With this, you could remote mount the XP shares on the Linux box with a simple mount command, or mount the Linux partitions on the XP box with a slightly longer Samba server setup.

Barring those, you could use USB thumb drives or recordable media (CDs/DVDs/floppies).

---

