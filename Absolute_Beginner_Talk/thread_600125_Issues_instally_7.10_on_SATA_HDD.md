---
title: "Issues instally 7.10 on SATA HDD"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Tipharet on 2007-11-01
So for some reason I am unable to install gutsy on my system when I have feisty installed prior. I have 3 HDD's ; 1 SATA and 2 IDE drivers on IDE0. Prior and now I disable to two IDE drives in the BIOS ( I have also left them enabled and it does not make a difference). I then boot to disc. I have 3 Partitions on the SATA; 1-Windows 2-Ubuntu and 3 -Swap. With Feisty I was able to just go through the setup choose my partition and leave everything else default. Grub would install and it would detect my windows install fine.

Now when I try to install 7.10, leaving grub installing to hd0 does not work, I receive an error 15 on reboot. I have also tried changing the grub install path to \dev\sda, this does not work either. Once installed I have tried reinstalling Grub via live disc but it can never find stage1. I have also tried using the super grub disc, this does not work either, that also gives me an error 15.

I am not sure what to do here Ive googled around a bit and have tried lots of things, none of which solve my issue.

Any help would be much appreciated.

Im not sure if this is related, but I have tried using Gparted from the live disc and it gives me an input/output error?

edit: I did not see the typo on the thread title, my apologies.

---

### Post by Hospadar on 2007-11-02
try unplugging all but the drives you want to install on and then installing and booting.  when you reconnect the other drives, make sure the primary boot device is the correct drive.

---

### Post by Tipharet on 2007-11-02
Leave the grub install path default?

Im not sure why unplugging the drives would matter when they are disabled? 

My sata is the first boot device.

---

### Post by adrian15 on 2007-11-06
> **Tipharet said:**
> . I have also tried using the super grub disc, this does not work either, that also gives me an error 15.

Can you please describe the exact steps that lead you to that error 15?

Thank you.

adrian15

---

### Post by brianbarry on 2007-11-06
If the drives are connected they may still be enumerated by the system  thereby throwing off the partition numbers with grub, if not mistaken I believe the grub error relates to that very issue.

Brian

---

