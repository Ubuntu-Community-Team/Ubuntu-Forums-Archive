---
title: "Grub / NTLDR mising"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Stom on 2006-08-11
Hello,

sda = documents
sdb = o/s drive
[INDENT]sdb1 = Windows XP Pro
sdb2 = ext3 / Ubuntu root
sdb5 = swap[/INDENT]
sdc = documents

Just done my first install of Ubuntu 6.06 Dapper Drake, and i've successfully knocked out NTLDR :D I installed using the alternate install cd. When asked if i wanted to install GRUB to the MBR i selected "no", choosing to install it to sdb2.

On next boot GRUB loaded, and boots Ubunut fine but if i try and boot Windows XP i get the "NTLDR is missing, press Ctrl+Alt+Del to restart". How do i set this up so that grub can boot either Ubuntu or Windows XP?

Thanks in advance for any help,
Stom

---

### Post by Indras on 2006-08-11
The easiest way I know if is to boot from the Windows XP CD and select the recovery option, which will bring you to a command line.  Type:
```
> fixmbr
> fixboot
```

Then, when you restart your system, Windows XP should boot.  Once you have that working, boot up from the Ubuntu Live CD.  Open a terminal and type:
```
# sudo grub
grub> root (sd0,1)
grub> setup (sd0)
grub> quit
```

That will install grub to the MBR, which should then have no problems booting to Ubuntu or chainloading to NTLDR.

Otherwise, it is also possible to have NTLDR act as your primary bootloader, in which case, follow the first step (boot from xp cd, fixboot, fixmbr) then boot from the live cd and copy the boot sector from sdb2 into a file and set up boot.ini to point to it.  I don't remember the exact steps, but google "boot linux with ntldr" and you should have no problems getting more info.

---

### Post by Stom on 2006-08-11
Hi, i tried:

```

> fixmbr
> fixboot

```

But i still get grub, and it still says "NTLDR missing" when i try to boot to windows.

This may not be related but... i updated my Ubuntu, and restarted. The new entry in the boot menu was listed incorrectly, just like the previous one (which i modified). Originally they were pointing to (hd1,1) which - i thought - is same thing as sdb1 (the windows partition). Apparently not, and only changing them to (hd0,1) will boot ubuntu.

---

### Post by r4ik on 2006-08-11
If i am not wrong it can be done from the command line,

[http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI](http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI)

Good luck !

---

### Post by Stom on 2006-08-11
Thanks for the link, very handy. 

Unfortunately i still havent got Windows booting properly. I think i may wipe the entire drive and reload a backup image of XP Pro i have.

Does anyone knwo my stalling point? What i did wrong? What not to do in the future or something that i should do instead?

Thanks for the advice

---

### Post by Indras on 2006-08-12
The only other thing I can think is that your Windows XP partition is not set as bootable.  Boot from the live CD and start Gnome Partition Editor (System->Administration).

Make sure that in the far right column (flags) there is the word "boot" next to your Windows XP partition.

---

### Post by TFX360 on 2006-08-12
> **Indras said:**
> The easiest way I know if is to boot from the Windows XP CD and select the recovery option, which will bring you to a command line.  Type:
```
> fixmbr
> fixboot
```

Then, when you restart your system, Windows XP should boot.  Once you have that working, boot up from the Ubuntu Live CD.  Open a terminal and type:
```
# sudo grub
grub> root (sd0,1)
grub> setup (sd0)
grub> quit
```

That will install grub to the MBR, which should then have no problems booting to Ubuntu or chainloading to NTLDR.

Otherwise, it is also possible to have NTLDR act as your primary bootloader, in which case, follow the first step (boot from xp cd, fixboot, fixmbr) then boot from the live cd and copy the boot sector from sdb2 into a file and set up boot.ini to point to it.  I don't remember the exact steps, but google "boot linux with ntldr" and you should have no problems getting more info.

Just for being curious, CAN you use both hd(0,1) or sd(0,1)? I have SATA drives both are handled in grub as hd I believe. I'll check later.


Kind regards,


TFX

---

