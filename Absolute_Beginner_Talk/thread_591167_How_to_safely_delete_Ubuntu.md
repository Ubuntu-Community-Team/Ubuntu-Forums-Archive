---
title: "How to safely delete Ubuntu"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-10-25
Hi, i just got a new computer. and it's going to be a clean Linux no windows machine.

So i want to delete Ubuntu on my now primary computer making it a gaming machine, but i don't have the vista boot CD (I have a boot partition) so how do i delete ubuntu safely without Windows boot CD :confused:

---

### Post by ghantoos on 2007-10-25
You can try using a LiveCD Ubuntu, knoppix, etc..

Hope this helps,

cheers,

ghantoos

---

### Post by ajmannen on 2007-10-25
yes but HOW, if i just delete the ubuntu partition Grub stops working and Vista won't boot

---

### Post by mikeyphi on 2007-10-25
> **ajmannen said:**
> Hi, i just got a new computer. and it's going to be a clean Linux no windows machine.

So i want to delete Ubuntu on my now primary computer making it a gaming machine, but i don't have the vista boot CD (I have a boot partition) so how do i delete ubuntu safely without Windows boot CD :confused:

After removing Ubuntu you will (probably) have to 'fixMBR' from a windows prompt before windows will boot - so, since you don't have a vista CD, make sure you will be able to do that!!!

---

### Post by ghantoos on 2007-10-25
You should restore the Vista MBR,
This might help.
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

Cheers,

ghantoos

---

### Post by LetThereBeRawk on 2007-10-25
Two major steps in getting what you want done (1) Perform some partition maintenance (2) Restore the Vista boot sector/master boot record. I can give you an overview of what you'll need to do for getting rid of the partitions, but someone else may have to chime in for guidance on restoring the Vista loader. So, I would get all of the steps before starting at all.

- Partition Maintenance
1) Your best bet would probably be to boot from a live CD partitioning tool (I like the GPartEd Live CD)
2) Remove the Linux and Linux swap partitions
3) (Optional) Expand the partition(s) that you're left with to fill up the disc if you want to do that
3) Enable the boot flag on the Vista partition

- Rewrite a Vista MBR/boot sector
Fixmbr isn't available in Vista anymore. XP's boot loader is totally different than Vista's. I haven't repaired a Vista boot loader after removing Linux yet, so I'm curious to see what comes up here. I've not used it, but you may look into a utility called mbrfix. Go here to read up a little on it ([http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm))

Hope that might give you an idea of what you're looking at.

---

