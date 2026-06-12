---
title: "Booting into Windows 7 from grub rescue prompt"
date: 2013-05-13
forum: Any Other OS
---

### Post by Abdhul Lathif on 2013-05-13
My laptop had BOSS Linux 4.0(an Indian variant of Linux) and Windows 7. I erased my partition where Linux was installed,now I'm stuck with grub rescue prompt. Can I use Windows 7 installation disk and 'Repair' my OS...???Is there any other way to boot into Windows 7 from grub rescue prompt itself..???
My laptop doesn't have a CD/DVD drive,Kindly help me resolve this issue. Thanks

---

### Post by kiyop on 2013-05-13
If your laptop can boot from USB media, raw-write Super Grub2 disk or boot repair to some USB media such as an USB thumb and insert the USB media to your laptop and boot from it.
Super grub2 disk: [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)
Boot repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Abdhul Lathif on 2013-05-14
Will the Super Grub Disk work with this OS(BOSS Linux).Also how can I make sure I have grub '2'...???
Thanks.

---

### Post by kiyop on 2013-05-15
> **Abdhul Lathif said:**
> Will the Super Grub Disk work with this OS(BOSS Linux).Also how can I make sure I have grub '2'...???
Thanks.
I think that Super Grub(2) Disk works good for BOSS Linux on PCs with MS-DOS partition table.
I am not sure if Super Grub(2) Disk works correctly for (U)EFI and secure boot. I hope it works correctly.
By the way, you erased the BOSS linux, didn't you? If you erased, you need not worry about BOSS linux. Super grub(2) disk and/or Boot repair will find Windows and enable booting with Windows.

Why not using Boot-repair?

About whether Grub2 or Grub legacy, I could found the following URL with 10 seconds Google'ing. :wink:
[http://wiki.bosslinux.in/wiki/index.php/Differences_between_GRUB_in_BOSS_3.1_%28grub-legacy%29_and_GRUB_in_BOSS_4.0_%28grub2%29](http://wiki.bosslinux.in/wiki/index.php/Differences_between_GRUB_in_BOSS_3.1_%28grub-legacy%29_and_GRUB_in_BOSS_4.0_%28grub2%29)
[http://lmgtfy.com/?q=boss+linux+grub+legacy+grub2](http://lmgtfy.com/?q=boss+linux+grub+legacy+grub2)

First of all, you should not erase the contents in the root (/) or /boot partition of BOSS linux, because the Grub2 code installed on the MBR of the internal HDD must use the files in the /boot/grub directory.
You should have search like  [http://lmgtfy.com/?q=grub+remove+windows7](http://lmgtfy.com/?q=grub+remove+windows7) before you erased the BOSS linux
Be careful in the futere.[URL="http://wiki.bosslinux.in/wiki/index.php/Differences_between_GRUB_in_BOSS_3.1_%28grub-legacy%29_and_GRUB_in_BOSS_4.0_%28grub2%29"]
[/URL]

---

### Post by Rebelli0us on 2013-05-15
Boot from USB flash and repair. I'd use Grub Customizer, "Change Environment", refresh then "Install to MBR"...simple GUI no command lines.

---

