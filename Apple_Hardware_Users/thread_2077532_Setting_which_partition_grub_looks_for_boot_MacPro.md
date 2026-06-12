---
title: "Setting which partition grub looks for boot MacPro"
date: 2012-10-28
forum: Apple Hardware Users
---

### Post by mike-g2 on 2012-10-28
Hi all,

I've put myself in a bit of a pickle when trying to upgrade my OS from 10.04 to 12.04. I have gotten myself part of the way out but need some additional help.

My machine is a MacPro and so it uses an older form of EFI (instead of BIOS). 

Here's my problem.  Grub looks at the wrong partition for the core.img (/dev/sda9 instead of /dev/sda2). How to I reset the MBR so that grub looks in the proper place?

Results from boot-repair can be found at: 
[INDENT][http://paste.ubuntu.com/1313957/](http://paste.ubuntu.com/1313957/)[/INDENT]
(beware it's a bit of a mess).

---

### Post by oldfred on 2012-10-28
I do not know Macs.

But it looks like you have a hybrid MBR/gpt configuration. Macs do that for Windows but you do not have to for Linux.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
[http://www.rodsbooks.com/gdisk/booting.html](http://www.rodsbooks.com/gdisk/booting.html)

---

### Post by mike-g2 on 2012-10-29
Hi Oldfred,

Thanks for the info.  I looked over it, but it is largely greek to me.  I do recall using rEFIt when I was doing the original install of Ubuntu 4 years ago.

I'm going to see if I can make sense of this documentation, but I'm really hoping someone out there wiht knowledge of Macs will chime in.

Mike

---

### Post by oldfred on 2012-10-29
Moved you to the Apple sub-forum and put Macbook in the title so you may attract someone with a Mac to help.

Update to MacPro
Fixed title

---

### Post by mike-g2 on 2012-10-29
Thanks Oldfred,

Just to be clear it's a MacPro, not a MacBookPro.

---

### Post by YannBuntu on 2012-10-30
Hello
it's a Mac hardware, but you don't seem to have any MacOS on it, do you?

---

### Post by YannBuntu on 2012-10-30
You have 3 Ubuntu systems (sda3, sda7, sda9).

If you want your main system to be sda7 (the 12.04.1 with 3.5 kernel), and use sda2 as separate boot, just:
1) run Boot-Repair --> Advanced options
2) In the "GRUB location" tab, untick "Separate /boot/efi", and tick "Separate /boot: sda2"
3) Apply
4) indicate the new URL that will appear.

---

### Post by mike-g2 on 2012-10-30
Hi YannaBuntu,

Thanks for the help and yep, I only have Ubuntu installed on this machine.

I tried doing what you suggested with boot-repair.  I was able  untick "Separate /boot/efi".  I could not change the box for "Separate /boot" since it was 'greyed out', but it was checked and set to sda2.

However, when I tried to apply these changes I got the following message.

[INDENT]GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.[/INDENT]

So I used gparted and created such a partition and then reran boot-repair which had me install and reinstall some grub-pc packages and said it was fixed.

The url with the results are at: [http://paste.ubuntu.com/1318414/](http://paste.ubuntu.com/1318414/)

It seems like Grub is pointed to the right place now, though I'm confused a bit by what bios_boot partition that boot-repair had me make is doing.

Dare I resetart this sucker?
Mike

---

### Post by oldfred on 2012-10-30
Not sure, gpt partitioning has a protective MBR and you have installed grub to the MBR. But with GPT there is not space after MBR for the rest of grub or core.img.

But does a MacPro let you boot from MBR? Or do you have to go thru its efi partition which is somewhat UEFIi v1 and somewhat UEFI v2. But both Windows and Ubuntu only truly work with UEFI v2 full implementations.

---

### Post by YannBuntu on 2012-10-30
> **mike-g2 said:**
> The url with the results are at: [http://paste.ubuntu.com/1318414/](http://paste.ubuntu.com/1318414/)

As Oldfred said, GRUB2 needs a BIOS-Boot partition to be installed on a GPT disk. You did it correctly, so everything looks ok now.

---

### Post by mike-g2 on 2012-10-30
Alright.  Thanks to both of you for looking at the file.  I'll restart the machine tomorrow. I'll be keeping my fingers crossed and will let you know if it works.

---

### Post by oldfred on 2012-10-30
This is not a recommendation for this boot loader as I have not used it, but he seems to understand efi and efi with Macs. It may have some useful info or links to useful info or a way that may work with a Mac.

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/linux.html](http://www.rodsbooks.com/refind/linux.html)

---

### Post by YannBuntu on 2012-10-31
> **oldfred said:**
> This is not a recommendation for this boot loader as I have not used it, but he seems to understand efi and efi with Macs. It may have some useful info or links to useful info or a way that may work with a Mac.

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/linux.html](http://www.rodsbooks.com/refind/linux.html)

I would have recommended Refind (or Refit) if Mike was still using MacOS, but he has no MacOS, and everything is currently working correctly with GRUB.
So better not installing Refind, it may break everything..

---

### Post by mike-g2 on 2012-11-02
I agree, it may not be set up perfectly, but it works so I don't want to reconfigure it more than necessary.

Good news! I just rebooted and it works!  Thanks to both of you for your help!

---

### Post by YannBuntu on 2012-11-08
BTW, it's the first time i see GRUB working as main bootloader on a Mac. Is it a recent hardware?
please can you indicate the exact reference?

---

### Post by mike-g2 on 2012-11-08
It's actually a pretty old machine.  A macpro 3,1 from circa 2008.  I did originally install rEFI and still have an hfs+ partition.

---

### Post by YannBuntu on 2012-11-09
And now, do you see the rEFIt menu before the GRUB menu appears?

---

### Post by mike-g2 on 2012-11-09
Nope.  I just get the grub menu.

---

### Post by YannBuntu on 2012-11-10
ok thanks

---

