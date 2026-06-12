---
title: "Grub Menu: two linux kernels?"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by chraej on 2007-10-09
i've installed ubuntu and had it working and loading 100% of the time i booted my computer. Then i used the automatic updater and it asked my to restart my computer, now i have 2 linux kernels (plus each has a recovery mode) on my Grub menu and it doesnt matter which one i choose to boot from i still only get the computer to load 70% of the time, the other 30% of the time it hangs up on the orange and black load screen now...help!

---

### Post by jd65pl on 2007-10-09
When you update your install there maybe an update to the kernel. Your kernel has been updated to a more recent version however the kernel that was there previously remains on your system, this is fine. If you are not happy with having more than one kernel on your grub menu, you could comment it out. By editing the file, first make a backup.

```
cp /boot/grub/menu.lst /boot/grub/menu.lst_bkup
gksudo gedit /boot/grub/menu.lst
```

Insert a # at the start of any lines you want to comment out. Alternatively you could remove the old kernel.

---

### Post by por100pre1 on 2007-10-09
> **jd65pl said:**
> When you update your install there maybe an update to the kernel. Your kernel has been updated to a more recent version however the kernel that was there previously remains on your system, this is fine. If you are not happy with having more than one kernel on your grub menu, you could comment it out. By editing the file, first make a backup.

```
cp /boot/grub/menu.lst /boot/grub/menu.lst_bkup
gksudo gedit /boot/grub/menu.lst
```

Insert a # at the start of any lines you want to comment out. Alternatively you could remove the old kernel.

IMHO, to remove the old kernel is NOT a good idea at this moment. When Ubuntu doesn't "load", does it just freeze or does it load a command line interface? :-k

---

### Post by jrharvey on 2007-10-09
I had the exact same problem and i could not get the newest kernel to boot. Are you sure you tryed BOTH kernels. I just got done discussing this with someone else because I couldnt boot kernel 2.6.20-16.

---

### Post by ronmarley1 on 2007-10-09
To add my two cents:
I like to have two kernels in GRUB "just in case."

---

### Post by chraej on 2007-10-09
it just freezes, no command line, the orange load bar just stops, my hdd light goes black and it just freezes everything up.

---

### Post by alienexplorers on 2007-10-09
Have you tried using all modes including recovery mode for both kernels.

---

### Post by goodboyCerberus on 2007-10-09
Is there a kernel listed with "(recovery mode)"? Can you at least boot using this option to make fixes?


Bah.

---

### Post by chraej on 2007-10-09
yes, both kernels have recovery mode, however i've yet to have one of them load successfully, they too freeze at random points (however usually at 3 bars)

+ on occasion i will also get an error saying that there is not enough buffer space

---

### Post by strabes on 2007-10-09
When the GRUB menu comes up, [edit the kernel line](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) and remove the "splash" text. Then boot up. Tell us on what part it freezes.

---

### Post by jrharvey on 2007-10-09
OK i just fixed my issue but i was wondering if you had an onboard video card. If you do then you need to switch it to the onboard and then configure your xserver and then switch back to your other graphics card.

---

### Post by chraej on 2007-10-10
i'm running linux on my laptop (hp dv6125) w/ nvidia Geforce 6150 go

my new problem rather than startup is getting compiz working w/out losing borders/terminal becoming completely white and not working at all/my computer booting to a pure black screen rather than the welcome screen of ubuntu...

---

