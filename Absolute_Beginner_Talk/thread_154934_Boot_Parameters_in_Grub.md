---
title: "Boot Parameters in Grub"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by spandon on 2006-04-04
****
Hi,
My Machine is an Acer Aspire 1654 WLMi (Centrino M760, Ati m X300.
I am wanting to dual boot, Windows and Ubuntu Dapper.
Have tested Breezy 5.10 Live cd and this works, by adding these commands at boot:
[B]Live acpi=off, hw-detect/start_pcmcia=false, vga=771
[/B]
Live cd of Dapper flight 5 did not work, locked up prior to loading desktop (light brown screen and mouse pointer - then dead)

Live cd of Dapper flight 6 WORKS, with the these commands added at boot:
**Live noapic nolapic, hw-detect/start_pcmcia=false, vga=771**

My problem is:
Do I have to enter the above commands prior to installing, what do I have to do if anything once installed?

If anyone can assist, could you please give instructions step by step as I am fairly new to Ubuntu (although am running Dapper on 2 desktops already)
Thanks
Don

---

### Post by waster on 2006-04-04
you can edit /boot/grub/menu/lst to add these parameters once you have installed. You will need to do it by hand on the first reboot after installation.

---

### Post by spandon on 2006-04-04
Hi waster,
Yes I thought that I may have to enter those parameters in /boot/grub/menu/lst, but where about in this file should I insert them, and would I enter all on the same line?
many thanks for your reply
Don

---

### Post by waster on 2006-04-04
Here is a snippet from one of mine:

title           Ubuntu, kernel 2.6.12-10-amd64-k8 Default
root            (hd0,0)
kernel          /vmlinuz root=/dev/md0 ro quiet splash
initrd          /initrd.img
savedefault
boot

you will just change the kernel line, adding the required "noapic nolapic, hw-detect/start_pcmcia=false, vga=771" after quiet splash

---

### Post by spandon on 2006-04-04
Hi Waster,
Got it.
Many Thanks
Don

---

