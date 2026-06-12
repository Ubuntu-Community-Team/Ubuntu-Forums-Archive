---
title: "EFI problem on Macbook install"
date: 2014-05-17
forum: Apple Hardware Users
---

### Post by Gbor_Bernyi on 2014-05-17
[TABLE]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][CENTER][COLOR=#777777]down vote[/COLOR][/CENTER]
[/TD]
[TD="class: postcell, bgcolor: transparent"]I'm trying to put ubuntu-14.04-desktop-amd64+mac on a MacBook5,2 model but right after booting into the USB, it gives the error:
Could not open "\EFI\BOOT\fallback.efi": 14
Any ideas? S[COLOR=#444444]eems like it has come up at [/COLOR][bugs.launchpad.net/ubuntu/+bug/1241824]("https://bugs.launchpad.net/ubuntu/+bug/1241824")[COLOR=#444444] but not sure what to do step by step to apply the fixes; also [/COLOR][help.ubuntu.com/community/UEFIBooting]("https://help.ubuntu.com/community/UEFIBooting")[COLOR=#444444] is overly complex.[/COLOR]


[/TD]
[/TR]
[/TABLE]

---

### Post by Vinodh Moodley on 2014-05-18
Mount your EFI partition and copy fallback.efi from the EFI\ubuntu\ folder to the EFI\BOOT\ folder

---

