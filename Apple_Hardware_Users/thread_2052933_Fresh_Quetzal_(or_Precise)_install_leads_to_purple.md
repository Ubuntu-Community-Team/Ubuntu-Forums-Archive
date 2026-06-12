---
title: "Fresh Quetzal (or Precise) install leads to purple screen on Macbook Pro 8,3"
date: 2012-09-04
forum: Apple Hardware Users
---

### Post by pete-woods on 2012-09-04
I've been trying to get Ubuntu installed on my MacBook Pro. The drive is partitioned normally,with EFI, OSX and Ubuntu partitions (I didn't bother with swap as I've got 16GB of RAM in it).

I have rEFIt installed on my OSX partition, which detects Ubuntu normally. I have the latest 12.10 installed on it. With default configuration, following GRUB the screen turns purple and stays that way. I can hear the Ubuntu start-up sound in the background, and if I hit ctrl-s I can hear the accessibility support kick in and it starts reading out the screen contents.

Unfortunately with the screen being purple, the machine is not much use.

If I add "nomodeset" to the kernel arguments and add an xorg.conf that selects the fbdev driver, I can actually log in, and the performance isn't too bad with llvmpipe for 3D. Just setting the fbdev driver on its own makes no improvement.
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fbdev"
EndSection
```

Trying the intel driver with the BusID pointed to PCI:0:2:0 doesn't help.
```
Section "Device"
        Identifier      "Device0"
        Driver          "intel"
        BusID           "0:2:0"
EndSection
```

Trying the radeon driver doesn't help either.
Trying the fglrx driver also does not improve things.

Trying the "outb" gmux commands from the [UEFIBooting page]("https://help.ubuntu.com/community/UEFIBooting#Selecting_the_graphic_card") makes the screen go blank immediately.

```
outb 0x728 1 # Switch select
outb 0x710 2 # Switch display
outb 0x740 2 # Switch DDC
outb 0x750 0 # Power down discrete graphics
```

I've tried very hard to get this working, but I think I've been defeated. I'd really appreciate some help! ](*,)

---

### Post by pete-woods on 2012-09-19
I fixed the problem by removing grub-efi and installing grub-pc. Then I ran
```
grub-install -f /dev/sda4
```
where sda4 is the partition that Ubuntu is installed on.

---

### Post by pete-woods on 2012-09-19
Following this, I was also able to uninstall rEFInd / rEFIt.

---

### Post by proycon on 2012-09-23
I had the purple/blank screen problem as well in EFI mode, but managed to solve it with extra boot parameters to the kernel in grub. See [http://ubuntuforums.org/showthread.php?t=2061791](http://ubuntuforums.org/showthread.php?t=2061791) , where I described my efforts to get EFI mode working.

---

