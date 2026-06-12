---
title: "Installing ubuntu on windows device (surface pro) for dual boot"
date: 2014-07-27
forum: Any Other OS
---

### Post by larry23 on 2014-07-27
Hello.


Does anyone have any experience getting ubuntu (13.04 in my case) to work on the Microsoft Surface Pro? I am running into an issue that I can not find many cases of, as it seems like the majority of my searches result in posts by people having issues AFTER installation (Oh god, I'm not even there yet) .


[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) was a helpful high level overview of what I would be doing. [http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu) this page was a great guide to start with, I first started by doing everything here. One thing NOT mentioned is what to select for the device for boot loader installation. Intuition would have me believe the windows *boot loader* (dev/sda2) would be the correct drive... While some sources say the entire drive (dev/sda) and others say the linux partition (dev/sda7) . I've selected all three different options, and all three gave the same result: After ~ 2 minutes of installation activity, I get the error message ```
the 'grub-efi' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.
```

I've read a few possibilities for the cause of this but I'm not what's at play here:

1) Connection to the internet. Some people have reported connecting to the internet fixes this, but I can't see how... package downloading during install that corrects an issue? At any rate, I can't test this since wifi doesn't work prior to install and I can't tether to my phone since i'm installing from USB.
2) The boot loader being the first partition on the drive. As I said, my windows boot loader appears to be second as dev/sda2, behind a NTFS partition for the entire size of the drive. Does this even count as a 'partition'?
3) Updates to the flash drive's files manually. [http://forums.kali.org/showthread.php?271-How-to-EFI-install-Kali-Linux&highlight=uefi](http://forums.kali.org/showthread.php?271-How-to-EFI-install-Kali-Linux&highlight=uefi) one source, [http://forums.kali.org/showthread.php?271-How-to-EFI-install-Kali-Linux&p=2566&viewfull=1#post2566](http://forums.kali.org/showthread.php?271-How-to-EFI-install-Kali-Linux&p=2566&viewfull=1#post2566) another source.

Could anyone help me with this?

Thank you

---

### Post by javispedro2 on 2014-08-24
Unless you have a specific reason, please try more recent versions of Ubuntu.

---

