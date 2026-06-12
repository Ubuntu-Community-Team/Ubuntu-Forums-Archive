---
title: "Safest install for Kubuntu? GRUB on floppy?"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by Books on 2005-11-20
This is my first post. I'm new to Linux, first install, fear level *High*.

What is the safest way to install Kubuntu? I only have the one computer and if something goes wrong I won't be able to get on the net to ask questions. (I have all my data backed up to an external drive and DVD.)

I have two hard drives, both IDE 80GB. WinXP is on the first drive. I want to put Kubuntu on the second drive at the front of the drive. Here is my setup:

[FONT="Courier New"]Drive 1: |-------WinXP 40GB--------------|-----FAT32 data-----|---FAT32--|[/FONT]
[FONT="Courier New"]Drive 2: |--12GB FAT32---|---------------FAT32 data----------------------|[/FONT]

Question:  Is there any way to install Kubuntu to the second drive/partition 1 with absolutely no danger to WinXP on the first? I know there is an option to put GRUB on a floppy, but is even that option 100% safe? Is there anything that can go wrong?

Is 12 GB enough for Kubuntu?

Thank you for your patience! I'm experienced with Windows, so I don't know why this scares me so. :)

Books

---

### Post by apjone on 2005-11-20
yes , but you will be very limited

1GB SWAPFILE
5 GIG / {root}
5GIG /home

But thats my thoughts , ask others before you do it

TAKE BACKUPs OFF ALL AND ANY IMPORTANT DATA!!!!!!!!!!!!

---

### Post by aysiu on 2005-11-20
Safest way to install if fear is high? Don't install it.
I'm serious. Use the live CD. It runs off the CD and RAM--does *not* touch the hard drive, and it'll do several things for you:

1. Give you a sense of what the Kubuntu interface is like
2. Give you a sense of how well Kubuntu detects your hardware (sound, screen resolution, etc.)

It will not, however, give you a sense of how fast Kubuntu will run if installed on your computer. An installed OS is always faster than a live CD OS.

If your fear level is that high, I would play around with the live CD for a couple of weeks and get familiar with some Linux commands, the System Settings, and play around with installing software (yes, you can do this with a live CD--only your changes won't be saved, since the programs will be "installed" to RAM, not your hard drive).

Once you're a bit more confident, you can install it. But **always** back up your work before installing. Always. If you have to use 200 floppy disks or 50 burnt CDs or sign up for 20 free websites, do it. Any time you install an OS, especially if you don't know what you're doing, you risk losing data.

---

### Post by nevelis on 2005-11-20
Hey,

There's not much that could go wrong, it looks like you know what you're doing partition-wise...

If you install GRUB to the master boot record, it will pick up your Windows partition and configure a bootloader item, as well as a couple for Ubuntu.

If you get stuck and want to get rid of Grub/Linux (I cant believe I'm saying this ;) ), make a DOS boot disk image (get one [here]("http://www.mbhs.edu/~jaosborn/boot98se.exe")), it's an exe which writes a boot disk..  It'll boot into DOS, just type:

```
A:\> fdisk /mbr
```

And that'll reinstall your Windows boot code and XP will boot.

.. but do back up!!

Cheers,
Aaron

---

### Post by steve.horsley on 2005-11-20
IMHO, the biggest danger is that you sail through the installer questions hitting yes, yes, yes and accidentally choose to user the entire disk for Ubuntu, as this is the default.

---

### Post by matthewv on 2005-11-20
I always install GRUB to floppy... maybe I'm paranoid. I had LILO render xp on my father's comp unbootable twice, and after that I've always put a boot loader on the floppy. Shouldn't go wrong on the mbr though, putting on the floppys just wat i've always done.

---

