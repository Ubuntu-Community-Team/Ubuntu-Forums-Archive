---
title: "Corrupt HDD | Ubuntu on External Drive via USB"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by anothrguitarist on 2008-01-02
About a year ago, my computer's hard drive went bad, and I was forced to buy a new machine. Since then, I've learned how to install Linux and have purchased an external hard drive. I have successfully installed Ubuntu on the external drive, and it works on several computers, but the computer that I want to fix cannot boot an OS from a USB cable. Here's what I've tried:

- Installing Windows on the External Drive (no permission)
- Upgrading BIOS
- Creating a Grub floppy disk

As for the Grub floppy disk, it works with the other computers, but the following command gives me an error when trying to boot from the broken machine:

grub> find /vmlinuz

I've tried to look for the drive in different ways as well, but it does not recognize any hard disk drive. I have a few additional ideas in mind. I am thinking about creating a FreeDOS boot disk (or something similar) and trying to boot ubuntu from there, and I am going to try create a super grub floppy disk as well. Do any of these ideas seem plausible, or can someone think of another solution? Am I out of luck?

(P.S. I can boot from a CD, if needed, but I don't have any spare CD-Rs)

---

### Post by marx2k on 2008-01-02
Get a spare CD-R and run Super Grub Rescue Disc - [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) - works every time for me (You can also install it on a USB flashdrive from that site or on a floppy)

---

### Post by anothrguitarist on 2008-01-03
No dice.

I tried super grub on a floppy disk, but it did not recognize either hard drive. One thing was curious, however, easy swap worked and it said that my drive was FAT. Does this mean anything to anyone? Should I still try FreeDOS? Can free Dos load another OS from a usb drive?

P.S. Would putting grub on another partition help?

---

