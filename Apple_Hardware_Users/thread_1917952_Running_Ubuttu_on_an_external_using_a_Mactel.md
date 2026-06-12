---
title: "Running Ubuttu on an external using a Mactel"
date: 2012-01-31
forum: Apple Hardware Users
---

### Post by Nyixa on 2012-01-31
Hey,
So, in an attempt to do something quite challenging, I have began the process of trying to get Ubuntu 11.10 running on my USB external HD. I was able to successfully install Ubuntu on the external. Then I encountered the common Mactel bug (root error). I sycned the partition tables using rEFIt. Then I encountered one of two things- either the perpetual Linux penguin logo, or a "no operating system" in white text on a black screen error. I tried booting from the Live Ubuntu CD, going into terminal and recovering Grub, but I finally ran into an error I can't figure out. [INDENT]$ sudo mount /dev/sdc1 /mnt
$ sudo grub-install --root-directory=/mnt /dev/sdc1
grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged...
grub-setup: error: will not proceed with blocklists.
[/INDENT]I'm smart enough to understand that Grub thinks this is a bad idea, my question is, why? And more importantly, what is a blocklist?

I don't have enough free disk space to run Ubuntu on my Mac, hence the attempt to get it running on an external. I am aware this is generally considered undesirable, but it seems like the best option for me as I am wholly interested in running Ubuntu using virtualbox. Unless anyone can attest to successfully using a USB drive to boot Ubuntu on their Mactel. Any help is appreciated, thanks in advance!

*Please forgive the mispelling in the thread title! It's late here -.-

---

### Post by cyberdork33 on 2012-01-31
You will only be able to boot natively off an external disk if you boot via EFI which is troublesome to say the least. Even if you get it to boot you will very likely have hardware issues.

---

### Post by Nyixa on 2012-01-31
Do you know if booting from a USB flashdrive is a adequate way to run Ubuntu on a Mac? I just don't have the HD space to spare for a partition.

---

### Post by pindar on 2012-01-31
> **cyberdork33 said:**
> You will only be able to boot natively off an external disk if you boot via EFI which is troublesome to say the least. Even if you get it to boot you will very likely have hardware issues.
That's simply not true, or better: it depends on your hardware. Setting up an external disk with EFI isn't all that hard. I ran several linux distributions from an external disk on my mac mini without any hardware issues. My new iMac had some problems, but they are mostly resolved in newer versions. So much depends on the hardware you are trying to use.

---

