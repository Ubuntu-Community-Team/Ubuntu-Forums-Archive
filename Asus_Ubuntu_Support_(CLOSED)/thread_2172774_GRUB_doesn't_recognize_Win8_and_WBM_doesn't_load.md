---
title: "GRUB doesn't recognize Win8 and WBM doesn't load"
date: 2013-09-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by magneto538 on 2013-09-06
[COLOR=#ff0000][FONT=courier new]***EDIT: my solution to fix this can be found in page 2 of this thread!***[/FONT][/COLOR]

Hello,
I'm writing as I am encountering lots of troubles in setting up my dual boot. 
I own an ASUS S56 ultrabook with UEFI. I've got installed Ubuntu 13.04  and Windows 8. I use Grub to choose the OS to be booted, but there is no  trace of any "Windows" entry: on Grub's menu, in fact, there are only 3  options - "Ubuntu", "Advanced *something*" and "Setup Menu". I even  tried to change the boot order: I put Windows Boot Manager at first -  and I thought I would have skipped loading Grub, as I was trying to load  Windows 8 without passing thru Grub - but it loads Grub anyways. Both  the OSs are installed with UEFI. Boot-repair recognizes that Windows 8  exists on my system, and everything seems to work well while running  boot-repair, but when I restart the PC there is no trace of Windows 8 in  Grub menu.

Here's the output of my BootInfo: [http://paste.ubuntu.com/6070623/](http://paste.ubuntu.com/6070623/)

How can I fix this?

Thanks in advance and regards.
Davide Magni

---

### Post by oldfred on 2013-09-06
Did this system have Windows 8 pre-installed? I looks like you now have Ubuntu & a Vista or data partition before the Windows 8 partition. But then partitions are not in the Windows expected order. Windows says the Microsoft reserved must be before the first data partition.

       Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)

Not sure what else might be an issue. Does Windows boot directly from UEFI? As grub can only chainload to a working Windows. 
You also show a Windows boot loader  in the MBR, so did you boot Boot-Repair in BIOS mode? Windows only boots with UEFI from gpt partitions.

---

### Post by magneto538 on 2013-09-09
So, what do you recommend to do? Should I erase everything from HDD (partitons & data) and start back from scratch? I see that, when installing, Windows creates a few partitions that are very important, and these are the partitions I have currently on HDD:

[IMG]http://oi44.tinypic.com/2e4g1s3.jpg[/IMG]

So I think I'm missing something. What may be the best solution? Erase everything and install Win 8 BEFORE Ubuntu? And then run boot-repair from Ubuntu when installed?
Last but not least, my PC had Win 8 Home (or something) installed, but I wanted it to be free from the tons of bloatware that was pre-installed (also, I had another copy of Win 8 Pro gifted from my university, so I wanted to use it), so I erased it and installed my own copy.

As I'm sort of an absolute beginner, I really hope to find help here.

Thank you!

---

### Post by oldfred on 2013-09-09
When you reinstalled Windows 8 did you install with secure boot. Not sure what a reinstall does.
Did you also turn fast boot off. That is often a major issue as the hibernation causes all sorts of issues. If only booting one copy of Windows and nothing else it does make Windows faster, but any other configuration causes issues.
I thought the MSR had to be before any data partition, but after rereading my link above, it just needs to be before the Windows system partition, so your partition layout should work.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

---

### Post by magneto538 on 2013-09-09
I didn't have neither secure boot nor fast boot activated when I installed any of the OSs, and they're still disabled. At this point, I really don't figure out what to do... Better burn Ubuntu down and go back to Win 8, if I can't have both running properly on my system. Hope someone has better advices.

---

### Post by oldfred on 2013-09-09
How are you trying to boot Windows? Did you try directly from UEFI menu?
Also grub2's os-prober does not create correct chain load entries. You have to use Boot-Repair to fix that bug.

---

### Post by magneto538 on 2013-09-09
What do you mean with "UEFI menu"? I've tried to boot Win from boot menu (by putting Windows Boot Master as first boot device), I don't see any other way to do it (but maybe I'm missing something).
I used boot-repair, like, 15 times. Here's a screen of boot-repair's advanced options. As I have a UEFI-based PC, before running "Recommended Repair" I have to change something in Advanced Settings (sorry for the OS's language, it's Italian):[IMG]http://oi43.tinypic.com/254zzo7.jpg[/IMG]

As you can see, I have to check "Separated /boot/efi partition", which is sda1 (as you can see in the screenshot from my previous post). I can also choose which OS to be loaded by default from the menu: I can choose between "sda 2 (Currently running OS - Ubuntu 13.04)" and "Windows 8 (via sda2 menu)". This means that boot-repair is able to recognize that on my system there is installed Windows 8, but whatever option I choose from the menu, nothing changes when I boot the system. Everytime, at startup, I am redirected to Grub, that only shows me the entries to load Ubuntu.

---

### Post by oldfred on 2013-09-09
Post link to BootInfo report from Boot-Repair.

You should get something like these which others posted from their UEFI menus. Windows should be a choice unless you renamed the Windows efi file using Boot-Repair.

---

### Post by magneto538 on 2013-09-10
My BootInfo: [URL="http://paste.ubuntu.com/6070623/"]http://paste.ubuntu.com/6070623/
[/URL]

...and my System Setup (one of the tabs is "Boot"):

[ATTACH=CONFIG]246149[/ATTACH][ATTACH=CONFIG]246150[/ATTACH][ATTACH=CONFIG]246147[/ATTACH][ATTACH=CONFIG]246148[/ATTACH]

EDIT: when I try to click on "Recommended Repair" on boot-repair (without changing any Advanced Setting), I get the following message:

> GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.

Until now, I tried only to activate "Separate /boot/efi partition" option, as I explained a few post ago. Should I try to create a "BIOS-Boot partition" as suggested by this error message? And, in this case, what should I do with the existing /boot/efi partition?

This whole thing is blowing my mind.

---

### Post by oldfred on 2013-09-10
You booted in BIOS mode. BIOS mode needs a bios_grub partition to install grub correctly, but you want UEFI mode. But you need to boot the Boot-Repair in UEFI mode not BIOS mode.

---

### Post by magneto538 on 2013-09-10
> **oldfred said:**
> You booted in BIOS mode. BIOS mode needs a bios_grub partition to install grub correctly, but you want UEFI mode. But you need to boot the Boot-Repair in UEFI mode not BIOS mode.

If I booted in BIOS mode, it means that I've installed Ubuntu in BIOS mode, right? How can I fix this whole thing? Should I reinstall Ubuntu in UEFI mode (which, actually, I thought I did) or is there any way to boot the system in UEFI mode without reinstalling everything?

---

### Post by oldfred on 2013-09-10
If you boot Boot-Repair in UEFI mode, it can uninstall BIOS grub-pc and install UEFI grub-efi which also makes a few other changes, but then you have an UEFI system.

---

### Post by magneto538 on 2013-09-11
Ok, I solved everything now! I just purged everything away and started back from scratch. Here's what I did:

1. Installed Ubuntu and cleansed everything from the HDD.
2. Removed swap.
3. Resized ext4 partition to approx. 70 GB
4. Created a 100 GB unformatted partition for Win 8 (remaining space is for Data partition)
5. Installed Win 8
6. Run boot-repair from Ubuntu Live. Everything is fine now, no more error messages and ****.
7. Once I boot, now, Grub shows an option to run Win 8. DONE!

I had a few troubles while trying to mount shared partitions on Ubuntu after running Win 8. For instance, I ran Win 8, then I rebooted and Ubuntu wasn't able to mount NTFS partitions as Win appeared to be hybernated. To solve this, I tried [this guide]("http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation") and it worked seamlessly.

Thanks a lot oldfred for your precious support. Thread solved.

---

