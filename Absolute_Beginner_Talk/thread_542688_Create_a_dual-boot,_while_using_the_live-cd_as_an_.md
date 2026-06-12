---
title: "Create a dual-boot, while using the live-cd as an install cd?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Genecks on 2007-09-04
I want to create a dual-boot with Windows XP and Ubuntu Feisty. I don't feel like downloading the Alternate CD, so I was wondering if it's possible to create a dual-boot with just the Live-CD.

How do I create a dual-boot system with the Live-CD?

I know I have to resize the NTFS partition. However, I want to partition table to look like this:

1. ntfs
2. ext3 (/)
3. swap (linux swap)
4. extended
5. ext3 (/home)

I also want to have /home within the ext3, extended partition.

How would I do all of this?
The thing I'm not sure about is getting GRUB to give me XP and Ubuntu as the choices when I boot up.
How would I go about that?

---

### Post by mlentink on 2007-09-04
> **Genecks said:**
> How do I create a dual-boot system with the Live-CD?
By using the "manual partition" option in the installer
> **Genecks said:**
> How would I do all of this?By using the "manual partition" option in the installer. Please see also [this]("http://http://www.psychocats.net/ubuntu/installing#partitioning")

> **Genecks said:**
> The thing I'm not sure about is getting GRUB to give me XP and Ubuntu as the choices when I boot up.
How would I go about that? The Installer will take care of that for you, provided Windows was installed first, which I presume it was

---

### Post by meborc on 2007-09-04
be sure to defrag your win partition many times before resizing! otherwise you might loose data.

---

