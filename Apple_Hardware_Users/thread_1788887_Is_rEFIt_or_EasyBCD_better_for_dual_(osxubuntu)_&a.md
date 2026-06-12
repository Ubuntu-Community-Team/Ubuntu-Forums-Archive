---
title: "Is rEFIt or EasyBCD better for dual (osx/ubuntu) &amp; triple (osx/ubuntu/win) boot?"
date: 2011-06-23
forum: Apple Hardware Users
---

### Post by swarup on 2011-06-23
I have been using rEFIt for several years on my BMP 5,1 to dual boot osx and ubuntu 9.04. I'd like to upgrade to ubuntu 11.04, and will wipe the HD and set everything up again. Is rEFIt still the recommended way to go? Someone on the apple forum had [EasyBCD]("http://neosmart.net/dl.php?id=1") as their footer, and it seems to be an alternative to rEFIt. ...or is it rather an alternative to GRUB, and I still need rEFIt? Or does it perhaps replace both rEFIt and GRUB? Whatever it is--an alternative to rEFIt or to GRUB, or to both, do folks think it is worth switching over to EasyBCD?

I am going to be getting an iMAC soon, and will need to set up a triple boot (osx/ubuntu/win) on that, so my question applies to this scenario as well.

---

### Post by ishueli on 2011-06-23
I use rEFIT on my iMac with triple boot. Have no problems at all. Pretty stable on iMac. Need to be careful during installation. Avoid mistakes.

---

### Post by swarup on 2011-06-23
When did you get your iMac? I had read of some problems doing it with the newest model this year for some reason.

I am very interested to hear of experiences with anyone who has used EasyBCD. Does it collapse the rEFit/GRUB process into one i.e. eliminate the need for two separate tools, thus giving a faster boot?

---

### Post by srs5694 on 2011-06-23
No, EasyBCD is a Windows tool. It's basically a tool to enable editing the Windows BCD file, which is (very roughly) Windows' equivalent of GRUB's grub.cfg file. Thus, EasyBCD is useless without a Windows installation. It also can't boot Linux directly, so if you use BCD as your primary boot selector, it will boot Linux by launching GRUB. I'm not sure how you'd use BCD without rEFIt or some other way of selecting it on a Mac, although I wouldn't be surprised if there's some way to get it to launch without first selecting it from a menu.

If you want to use the fewest tools possible, your best bet is probably to ditch rEFIt and use GRUB 2 as the primary boot loader. It can redirect the boot process to Windows, boot Linux directly, boot OS X via its .efi boot file, and even boot OS X directly; however, my experience is that GRUB's ability to boot OS X directly is rather unreliable. Sometimes it works quite well, sometimes it works but some specific features or devices don't work (no sound, for instance), and sometimes it fails miserably. Booting OS X via its .efi file is more reliable, but IIRC you've got to be using GRUB in EFI mode to do that, and I'm not sure if that would enable you to boot Windows from a standard BIOS installation.

Given this mess of contradictory requirements, IMHO the best solution remains to use rEFIt to select your OS and then rely on OS-specific boot loaders (BCD, GRUB, or OS X's .efi file) to boot each OS. You can set GRUB's timeout to a very low value and/or set it to not display its menu if you want to avoid the delay and visual clues that another boot loader is present when booting Linux. If you don't like GRUB for other reasons, you could try another boot loader, such as LILO (BIOS-mode), GRUB Legacy (BIOS-mode), or ELILO (EFI-mode).

---

### Post by swarup on 2011-06-23
Hey, thanks for the info. I thought EasyBCD might be some new, more efficient tool for running multiple boots on Macs. But now I see that's not the case, so I'll stick with rEFIt. I was quite satisfied with it, and I don't have any problem with GRUB either. I'll stick with the traditional approach then of using rEFIt to select the OS, and then having the bootloader for each OS run that boot for that OS. Thanks again. :)

---

### Post by swarup on 2011-06-23
One last question here: If I am to set up a triple boot on an iMac (osx/ubuntu/win), then, since there would be a win os in that scenario, would EasyBCD be a good option to rEFIt? Or even there, rEFIt would be easier to work with?

The reason I ask is because the way the right about it on their home page, it sounds like it turns multiple booting into a piece of cake and nothing else is needed.

---

