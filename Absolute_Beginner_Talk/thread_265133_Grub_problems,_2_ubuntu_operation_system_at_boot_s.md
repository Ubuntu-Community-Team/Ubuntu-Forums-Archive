---
title: "Grub problems, 2 ubuntu operation system at boot screen"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by bubi1980 on 2006-09-25
hi,

I think I have something messed up with reinstalling ubuntu.
I had a dual boot system (XP and Ubuntu on same hdd). I deleted ubuntu with Gparted, because I wanted to reinstall it. When I started the reinstallation, I didnt get further (program froze every time I run it) than "prepare partitions" "scanning all devices" after selecting "manual edit partitions" during the first steps of installation.
So I tried the automatic partitioning on other hdd. It worked fine, ubuntu was finally installed.

If i boot my computer I get an option to choose ubuntu or windows Xp booting. What now happens is that I have 2 times "ubuntu ...amd64" and two times "ubuntu recovery" or something like that and one time  "ubuntu safe" mode, which I can select to boot. Of course also WIndows XP boot.
Is it possible that GRub was not removed well with deleting Ubuntu, and still has some reference to boot the old "deleted" ubuntu ??

My excuses for the faults and difficult explains in the text, but english is not my native language;) 

Can I remove those 2 other ubuntu boot options from Grub?

---

### Post by BitTorrentBuddha on 2006-09-25
If you know which ones are the left over ones you can simply remove them from the menu.lst file. To edit it (and make a backup), run this command ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo gedit /boot/grub/menu.lst
``` (Replace gedit with your text editor of choice should you be running Kubuntu instead.) All the boot options are located on the bottom and look (somewhat) like this: ```
title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot
```
Simply delete the left over ones and save, then when you reboot, they'll be gone. [color=red]Make sure you delete the extra ones, not the ones you use to boot from, double check this before making making changes to the menu.lst file.[/color]

---

