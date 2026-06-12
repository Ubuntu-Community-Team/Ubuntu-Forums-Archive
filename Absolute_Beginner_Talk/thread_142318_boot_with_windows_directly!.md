---
title: "boot with windows directly!"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by cobweb on 2006-03-10
hi, I had had both linux and windows on my computer.
Windows was on the C drive.
A few hours ago, I reinstalled windows again onto that drive, and did not do anything to the partitions that linux was installed.

Now when I boot my computer, it directly opens with Windows. No options are presented whether to boot with Linux or Windows!

What can I do? I hope reinstalling windows to the same partition that it was installed before has nothing to do with Linux partitions :(

Thanks for any help.

---

### Post by Jimmey on 2006-03-10
It's probably wiped GRUB. Search the forums for "reinstalling grub".

---

### Post by meborc on 2006-03-10
don't panic, your linux partitions are ok... what happened was that windows overwrite your grub menu... that means that you dont have one any more :) ... try to rescue with installation/live cd... it should allow you to reinstall grub... and all is well \\:D/

---

### Post by Ignite_nz on 2006-03-10
I'm guessing Ubuntu is still there, were they both installed on the same drive? If not the try browsing the drive that Ubuntu was installed onto, and if it's there it means that re-installing XP has overwritten your Mastbe Boot Record (MBR). But i'm not sure how to fix/edit it. Try playing around with msconfig in windows. Or I could be completely wrong and it could be something different.

Either way I'm sure that someone else here will shed a bit more light on the issue for you.

---

### Post by cobweb on 2006-03-10
[QUOTE=meborc]don't panic, your linux partitions are ok... what happened was that windows overwrite your grub menu... that means that you dont have one any more :) ... try to rescue with installation/live cd... it should allow you to reinstall grub... and all is well \\:D/[/QUOTE]

ok, i have the installation cd. and i know about that grub file..

is it possible to install only the grub file with the cd. i don't wanna corrupt the linux partitions while trying to install that single file. so could you please explain it step by step? i would really appreciate it.

---

### Post by cobweb on 2006-03-10
ok i should have searched the forum, now i've found the related links. thanks a lot.

---

### Post by dermotti on 2006-03-10
mepis live CD has a grub installer thats super easy to use and wont touch your partitions. I keep it handy :-) [http://www.mepis.org](http://www.mepis.org)

---

### Post by AtinLango on 2006-03-10
Use your Ubuntu installation CD to re-install GRUB as follows:

1. Boot your computer with the installation CD in.
2. Type *rescue* at the boot prompt.
3. Continue normally as if installing.
4. At a certain point it will know that you are rescuing.
5. Assuming your Ubuntu Partition was X, choose *dev/disc/disc0/partX*
6. At the prompt, type *grub-install /dev/hda* (exactly).
7. Type *umount /dev/hdaX*, where X is Ubuntu partition.
8. Type *reboot*.

---

