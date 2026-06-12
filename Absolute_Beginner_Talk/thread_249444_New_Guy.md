---
title: "New Guy"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by DarkAngel624 on 2006-09-02
Hi...as you already know, I'm new to the forums, and to Linux as well..been playing with Windows for nearly forever, and wanted to learn something new...so, here I am..

My problem is with GRUB.
Here is my current hard drive setup

Primary
Master - 30GB Seagate Barracuda (Linux loaded on this one)
Slave  - 120GB Samsung SpinPoint (NTFS this is my storage drive)

3ware Escalade 7000-2 RAID
2 60GB IBM/Hitachi Deskstars in RAID 0

At first, I couldn't get anything Linux to load, and figured that if I set the 30GB to be the first boot in BIOS, that it would work...and it did..I have no problem switching this through BIOS, but if GRUB can configure it to where I wouldn't have to...why ignore it...get some help and figure it out...

My problem is..when I go to Grub to switch to WinXP it will tell me that that it can't find the NT Loader...which basically means...GRUB isn't pointing to the RAID Array...

The settings for WinXP over GRUB is

root (hd2,0)
Filesystem type unknown, partition type 0x7
saved default
make active

map (hd0) (hd2)
Map (hd2) (hd0)
chainloader +1

If I look through Partition Magic, it will have the RAID array listed as Disk3, storage drive as Disk2, and Linux as Disk1. I'm not sure if that will help..I just can't see it being as simple as hd3...and mainly it's because of the RAID array

I'm currently running on Windows XP right now, as I am trying to find Linux drivers for my wireless network card...

and then of course, the other question I have is...mounting drives....I was told that Linux can see NTFS drives...but just can't write to them..which is fine by me...and I'm not sure of how to do that as well..

I'm not up to speed on the command line...I'm assuming that all these commands that I have seen posted are run through the "run command"...if not..I'd really like to understand this more...

If there is anyone that can give me some insight, or direct me to a post that deals with my question, I would really appreciate any help at all..

Thanks for your time
Mario

---

### Post by kidders on 2006-09-03
Hi there,

Just for future reference, it's pretty important to remember:

[LIST=1]
[*]Give your thread a title that might help people guess what's in it
[*]Try to limit yourself to one issue per thread
[/LIST]

Anyhow, let's start at the start :P

**GRUB**

Grub is pretty unforgiving, but it *does* have one nice feature that most other bootloaders don't ... it lets you edit your boot scripts during the boot process itself. Select something and hit 'e' to edit it. Once you find something that works, make it permanent in your /boot/grub.conf.

One of the things you need to bear in mind is that the grub bootloader typically installs itself in the master boot record of your primary boot device. If you then use your CMOS utility to alter the boot sequence, your PC won't know to look for it any more. Be wary of installing bootloaders on more than one hard drive ... things can start to get confusing!

**NTFS FILESYSTEMS**
Linux is able to read and write to NTFS, just as it is the other Microsoft filesystems. The problem is that, since Microsoft refuses to tell anyone how they work, they all have to be reverse-engineered, which takes time. The FAT filesystems are quite old, so enough time has passed to consider non-Windows implementations of it "stable"; not so with NTFS though. At present, although full read/write access to NTFS is possible with Linux, it is not considered "safe", so there is a small risk that it might bork your system.

What I would suggest is that you read up on the exact nature and probability of a screw-up, and decide on that basis whether you think writing is worth the risk.

What I suggest is this:

I - From a terminal, type **sudo nano -w /etc/fstab**

Very, very carefully, add a line to the end of the file, being super-careful not to accidentally alter anything else:

```

/dev/sda1 /mnt/windoze ntfs ro,noauto,noexec 0 0

```

[LIST]
[*]*/dev/sda1* is the device name of your NTFS partition.
[*]*/mnt/windoze* is the location you want to mount it to.
[*]*ntfs* is the filesystem type. Using auto-detection for fixed devices is unnecessary (and not recommended).
[*]*ro,noauto,noexec* means "Read only", "Don't auto-mount at startup" and "Disallow execution of files on this volume". Remove "ro" and "noauto" if you like, but "noexec" prevents accidental injection of executable code from a quite obviously virus-ridden Windows partition.
[*]*0 0* are advanced options to do with how clean-up is handled.
[/LIST]

II - Create your mount point

In a terminal window, create someplace for your filesystem to live, by typing **sudo mkdir /mnt/windoze** It's important to do this as root.

Now, any time you want access to your NTFS files, simply **sudo mount /mnt/windoze** and then dismount with **sudo umount /mnt/windoze**

If you want to avoid using "sudo" all the time, add the word "users" to the "options" part of the /etc/fstab line you made. Of course, you can just leave it mounted all the time if you like, by removing the word "noauto".

To transition from read-only mode to full read/write mode, use **sudo mount -o remount,rw /mnt/windoze** This saves you having to close all open files, dismount the filesystem and mount it again with new options.

**DEALING WITH THE COMMAND LINE**

Using a terminal window and pasting things into a "Run" dialog in a graphical environment are not always the same thing, especially if you are running a sequence of commands that may be dependent on eachother. Also, error messages that you would otherwise be able to see, such as "Segmentation fault" or "Command failed - file not found", or some such, are not visible from a "Run" dialog, so you won't necessarily know if a command you typed was successful unless there's some physical evidence of it afterwards, such as an application opening.

If in doubt, install and run a "terminal emulator", which gives you access to a terminal from within a graphical environment, much like "CMD" does in Windows.

**WIRELESS CARDS**

Some wireless cards can be a pain to get going in Linux. Tbh, smooth, clean wireless network access is something the Linux world hasn't gotten quite right yet. What kind of hardware do you have?

Quite often, the solution can actually be to use the Windows drivers for your wireless adapter. Ndiswrapper is designed just for this purpose. It works by "wrapping" your Windows drivers in code necessary to get them to cooperate with a Linux kernel. Of course, once that's done, prepare to learn more than you ever wanted to know about WEP, WPA, LEAP and lots of other boring technical crap :P

I hope all this is of some help ... let me know if anything else crops up :)

---

### Post by confused57 on 2006-09-03
This entry "might" boot your Windows from grub:

```
title                Windows
rootnoverify    (hd3,0)
savedefault
makeactive
map               (hd0) (hd3)
map               (hd3) (hd0)
chainloader +1
```

---

