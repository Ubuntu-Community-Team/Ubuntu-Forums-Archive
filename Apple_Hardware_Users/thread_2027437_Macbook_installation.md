---
title: "Macbook installation"
date: 2012-07-16
forum: Apple Hardware Users
---

### Post by sareen2s on 2012-07-16
[INDENT]Having a Macbook 5.2 running on OSx 10.5.8
I have also windows7 running on it.I installed Ubuntu following the guidelines posted in the thread mentioned below.

[http://www.zebpedersen.co.uk/?p=962#comment-35628](http://www.zebpedersen.co.uk/?p=962#comment-35628)

But the problem is the option key shows me 2 options in the beginning one of reFit with a logo of mac and the other of windows.After i click the mac it gives me all the prompts of reFit Mac/Windows/Tux.After i select Tux the cursor blinks for a while and then my mac boots into Windows.
My Mac oSX is perfectly running well if i do not enter the boot menu.Pls help as i want to run Ubuntu on my mac.[/INDENT]

---

### Post by yentl on 2012-07-16
Have you run gptsync since you installed Ubuntu? If repartitioning occurred during the installation, then the MBR and GPT tables will fall out of sync, so you may not be able to boot into some systems properly.

---

### Post by yentl on 2012-07-16
You can run gptsync from rEFIt (it is the partitioning tool).

---

### Post by sareen2s on 2012-07-17
> **yentl said:**
> You can run gptsync from rEFIt (it is the partitioning tool).

Please can you let me know as to how to run gptsync as i very new to system.What i know from the mac system is one thing :-
"Every GPT-formatted disk is supposed to have an EFI System Partition, and Apple’s tools create one at the beginning of the disk. However, Mac OS X doesn’t actually use it; the EFI System Partition is completely empty on a standard Intel Mac. Apple has added a HFS+ file system driver to its firmware, and the firmware boots Mac OS X directly from the partition it is installed on."

But i already efi in the root.
So if you can guide me through it i will do it 100%.

---

### Post by yentl on 2012-07-17
In the rEFIt menu, you should be able to find an option that says 'start partitioning tool'. It's represented by one of the icons underneath the operating system icons (between start EFI shell and shutdown computer, I think) This is gptsync. If you click on it it will analyse whether the MBR and GPT tables are out of sync, and offer to synchronise them. 

If you want to make the Macbook firmware launch rEFIt by default, you will need to bless it. If you go into the rEFIt files you should find a script called something like 'bless refit'; run this script and you'll be welcomed by the rEFIt screen when you start up!

Hope this helps, and good luck.

---

### Post by sareen2s on 2012-07-17
After doing what was told that is "partitioning tool where it said "Tables are synchronised,no need to synchronise". Then ran the script "bless".

[IMG]https://docs.google.com/open?id=0B4hJCV9PdbzbMFE4WXN1dmE0b1k
[https://docs.google.com/open?id=0B4hJCV9PdbzbZFRySUxjZ0ozU0k](https://docs.google.com/open?id=0B4hJCV9PdbzbZFRySUxjZ0ozU0k)
https://docs.google.com/open?id=0B4hJCV9Pdbzbb1UzTktXOElobVU[/IMG]

The resultant is this , just the logo on the screen for more than half hr. then I just had to restart my MacBook with a sad face again.

---

### Post by yentl on 2012-07-17
Hmm, this is puzzling, I'm sorry that that didn't help.

Just out of curiosity, what happens when you select the Windows option in your boot menu (the one you get when you press alt on startup)? On my macbook that gives me the Ubuntu grub menu.

You could try putting Grub2 on a disk using [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/). This will be able to detect OS's installed in your system, and output kernel messages during booting. That way you might be able to find at what stage the kernel-loading got stuck at, if at all. It can also find any existing installation of grub on your system and try to chainload that. You can then see if that works to see if your problem might come from loading the bootloader itself.

---

