---
title: "Installing 10.04"
date: 2015-10-18
forum: Apple Hardware Users
---

### Post by alink327 on 2015-10-18
[B]Hi,

I am super new to Linux and am really lost after a few days of trying to install linux

I am trying to install Ubuntu 10.04 onto a MacPro3,1 (currently running OSX 10.7.5) and make it a dual boot.  I have one 500GB hard drive for Mac and another empty 500GB (which i want to install Linux on)

I made a live USB using ubuntu 10.04 (64bit) iso with Mac Linux USB Loader 2.  After making the USB, my USB now contains a folder called efi, then inside efi a folder called boot, which contains boot.efi, boot.iso, bootX64.efi.  I have also installed rEFInd as suggested.

When I reboot my computer with USB connect to my machine, the machine completely skips rEFind and jump straight into USB boot, asking me if I want to:[/B]
1)Boot Linux from ISO file
2)Modify Linux Kernel Boot options

**If I choose Boot Linux from ISO file, I get the following message:**

Kernel path: /casper/vmlinuz | ramdisc path: /casper/initrd.lz
boot parameters:

Loading Linux kernel... done
Loading initial RAM disc ... done
Attempting to boot the Linux distribution now...
error: no suitable video mode found.
Booting in blind mode

[B]Then I'm pretty much stuck here.

When I try to boot my computer without by USB drive I do get into rEFInd screen with my Mac booting drive.
When I plug my USB drive in after rEFInd screen appears (I plug USB in, then refresh rEFInd), I see two additional options:[/B] Boot EFI\boot\boot.efi from USB **or** Boot fall back something something

**If I choose to boot from EFI\boot\boot.efi I get the following:**
Kernel path: | ramdisc path:
boot parameters:

Loading Linux Kernel ... done

unaligned pointer 0x2
Aborted. Press any key to exit

[B]If I choose to boot from the fallback option, I just get back to the blind mode I originally described.

Can someone point me to the right direction?  I'm sure it's just a noob mistake...[/B]

Thanks!!!

---

### Post by Dennis N on 2015-10-18
Ubuntu 10.04 doesn't support UEFI booting, so you need a version that does. I suggest Ubuntu 14.04. Besides that, 10.04 is out of support, meaning you can't install new software from the repositories, or get upgrades.

---

### Post by alink327 on 2015-10-18
Hi Dennis,

Thank you so much for such a quick reply.  What booting method should I use to run 10.04 then?  Do you think there is a way to overcome the UEFI booting problem and make 10.04 bootable on my MacPro3,1?

I am not worried about installing softwares and support.  I am using this machine for research purposes, so I only need to run one non-commercial software which was written to work with 10.04.

Thank you!

---

### Post by Dennis N on 2015-10-18
There is an Apple Hardware Users subforum here that probably could give you good advice if you post a question there:

[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by alink327 on 2015-10-18
Anyone who is familiar with installing 10.04 on rather old Mac machine (MacPro3,1), please help.

Thank you

---

### Post by mystics on 2015-10-18
There is an entry on the community wiki with some information on 10.04 on your model of MacBook: [https://help.ubuntu.com/community/MacBookPro3-1/Lucid](https://help.ubuntu.com/community/MacBookPro3-1/Lucid)

I'm not sure how accurate it is. I will say that an added issue with 10.04 that may arise is that if anything doesn't work out of the box, you may not be able to fix it. You might want to see if 12.04 or 14.04 can run the program before going ahead with 10.04. If either of those are able to work with the program but something else breaks, you're more likely to be able to download software to fix it. You can do that by testing it out in a virtual machine.

---

### Post by Bucky Ball on 2015-10-18
To reiterate: You shouldn't be installing 10.04 LTS at all! That is why people are not able to tell you much about it, it is end of life (EOL). There are no updates, no support, it is dead, finished, gone and the forums and Canonical no longer support it.

Unless you have very specific reasons for installing an old, unsupported release and are not intending to go online with the machine (as there are no security updates) then avoid. 

Please install a supported release, [I suggest 14.04 LTS]("http://www.ubuntu.com/download/desktop") as above, and report back if you have the same issues or others. There is NO way to install 10.04 using UEFI and you should not be using 10.04, period. 

Good luck.

---

