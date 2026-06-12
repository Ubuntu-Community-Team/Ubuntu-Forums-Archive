---
title: "Another GRUB problem"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by cypherzero on 2007-05-03
Last time I installed Ubuntu to an external disk, which was fine apart from I had to reinstall GRUB using something like:
[FONT="Courier New"]**sudo grub-install /dev/hda --root-directory=/media/g/**[/FONT]
to allow my computer to boot without the external disk attached

After reinstalling with  Kubuntu I now get the error message
[FONT="Courier New"]**/dev/sda does not have any corresponding BIOS drive.**[/FONT]
When I try this

(sda now appears to be my internal drive)

[FONT="Courier New"]**sudo grub-install /dev/sda --root-directory=/media/g/ --recheck**[/FONT]
does not help!

Please help, I need to move my computer tomorrow and can't take my external drive along with me!

---

