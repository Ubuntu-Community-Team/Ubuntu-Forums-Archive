---
title: "Bless Linux Parition with no OS X installed?"
date: 2009-07-20
forum: Apple Hardware Users
---

### Post by raronson on 2009-07-20
Hi.  I have a macbook4,1 with only the following on the drive:

```

/dev/sda1   *           1       29165   234260742+  83  Linux
/dev/sda2           29165       30402     9937808   82  Linux swap / Solaris

```I too was overzealous and wiped OS X completely before blessing the Linux partition.  I have no plans to reinstall OS X, and to cement the deal, my superdrive was gimped by the famous firmware update (does not read/write dvd's).

My question is:  is there a way to bless the Linux partition without an OS X install on the local machine?  If it helps, I have another macbook and network storage.  Also, I've installed Grub2 naively hoping that some EFI voodoo would take place with no luck.

Am I stuck looking at the gray screen for 30 seconds while the macbook slowly defaults to legacy boot mode, or can I somehow bless the Linux partition without a local install of OS X?  It's not a huge issue, but I'm more curious than anything.

Thanks for any help.

---

### Post by pxwpxw on 2009-07-21
> **raronson said:**
> Hi.  I have a macbook4,1 with only the following on the drive:

```

/dev/sda1   *           1       29165   234260742+  83  Linux
/dev/sda2           29165       30402     9937808   82  Linux swap / Solaris

```I too was overzealous and wiped OS X completely before blessing the Linux partition.  I have no plans to reinstall OS X, and to cement the deal, my superdrive was gimped by the famous firmware update (does not read/write dvd's).

My question is:  is there a way to bless the Linux partition without an OS X install on the local machine?  If it helps, I have another macbook and network storage.  Also, I've installed Grub2 naively hoping that some EFI voodoo would take place with no luck.


Am I stuck looking at the gray screen for 30 seconds while the macbook slowly defaults to legacy boot mode, or can I somehow bless the Linux partition without a local install of OS X?  It's not a huge issue, but I'm more curious than anything.

Thanks for any help.

If you have only grub1 or grub-pc (not efi) installed and a MSDOS partitoning scheme, you might be able to use the OSX DVD to setBoot for bootloader on the MBR.(the bless --device and legacy boot method) That is usually done before removing OSX.(Thread somewhere about that, speeding up from the 30 second wait),  Might also be faster using the Alt/Option key.

If you had an hfsplus partiton with refit.efi or grub.efi or elilo.efi it could be blessed as efi and setBoot, faster. Not being sure what you have, there are various possibilities.

---

### Post by Richardcavell on 2009-07-21
You can only bless a partition from within OS X.  You need to get your hands on an OS X installation.  It could be any - any OS X CD or DVD, or get someone to copy their OS X partition onto a USB key or external hard disk.

For the record, you can bless HFS files from within Ubuntu using hfsutils, but that's not HFS+ and it''s only blessing a file, not a partition.

Richard

---

### Post by raronson on 2009-07-21
Thanks Richard.  I think I'll copy over my wife's macbook partition to her external HFS+ usb drive on the network.

From here I'd just need to boot into it from *this* machine and bless the Linux partition?

Thanks for the help.

---

### Post by Richardcavell on 2009-07-21
Yes, that will work.

In fact, if you have a firewire cable and Firewire on both of the machines, you could boot her computer as an external hard drive (hold down T when booting it up) and boot off her partition directly.

Please note that the only operating system that will reliably boot externally is OS X.  I wish Apple would fix this, but they don't seem to be in a hurry about it.

Richard

---

### Post by raronson on 2009-07-22
I think you just saved me a lot of time and trouble with the firewire suggestion.  I remember reading that before somewhere, but it didn't register as a solution until you just mentioned it again.  Cheers, mate.

---

