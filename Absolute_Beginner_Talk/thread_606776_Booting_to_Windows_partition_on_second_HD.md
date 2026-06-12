---
title: "Booting to Windows partition on second HD"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by linuxnooby on 2007-11-08
Prior to downloading the latest Ubuntu update, I was able to configure my boot menu, whereby I could boot to a Windows partition on Drive 1 (Ubuntu 2.62 being on drive 0).

However , with the latest update, I find that, by specifying  a Windows O/S at hd1,1 in the file menu.lst, it will no longer function. I can access my Windows Back-up system from the boot menu, this being at hd0,1.

The latest update introduced a new kernel.

Can someone please explain what might have happened, to prevent access to the non-linux drive ?

---

### Post by saphil on 2007-11-08
what loader are you using, grub or lilo?

Does your boot menu now NOT SHOW the windows option at all?  

There is a grub tool that might be able to get grub rebuilt to "see" the hd1,1 partition with Windows on it.  

We do dual-boot drives every quarter at school, and sometimes the only answer for messed-up bootloaders is a fresh install of Linux.  This is at least partly because we abuse our drives with weird configurations and lab testing, and almost everybody using the drives are new to linux.  Beginners can produce effects that the experts have never seen before!

---

### Post by linuxnooby on 2007-11-08
Following the update, the boot menu file was automatically updated and it did not include my earlier modifications (ie no reference to Windows), so I edited the menu.lst file (as previously) to show Windows back-up at hd0,1 and Windows at hd1,1, Linux being at hd0,3.

Upon selecting either Linux or Windows back-up, I am able to access what I expect to access but not so with Windows at hd 1.

The boot loader is Grub

The only way I can now access the master copy of Windows is to change the boot order in the Bios from drive 0 to drive 1 but then when I want to use Linux, it means changing back again.

---

### Post by logos34 on 2007-11-08
try adding [map lines]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

The kernel update [kicks out any non-ubuntu entries]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc") from grub 'automagic' section.

---

### Post by inversekinetix on 2007-11-08
You could try booting into windows and installing WinGRUB into windows, then you simply add one line of text to your windows boot.ini  and it will give you the option to boot either of your OSs.

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)


is a good guide.

---

### Post by linuxnooby on 2007-11-09
Thanks **Logos34** - You have hit the nail on the head. In the update process, the reference to drive mapping was omitted. I have just added the two mapping lines to the menu.lst file and can now boot to all 3 operating systems.

Thanks also **Inversekinetix** for your suggestion - I will try that also.

---

