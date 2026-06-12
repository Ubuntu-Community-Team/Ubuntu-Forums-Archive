---
title: "grub, bless problems on dual boot Mac OS Sonoma 14.5 and Ubuntu 24.04 LTS"
date: 2024-05-24
forum: Apple Hardware Users
---

### Post by fbagnato1 on 2024-05-24
Hello all,

I am in the process of setting up an old iMac with a dual boot OCLP install of Mac OS 14.5 Sonoma and Ubuntu 24.04 LTS.

I am at the stage of getting grub working properly but am encountering errors.

The Ubuntu install installed grub which was not functioning without some manual changes, which I have done.
grub was not displaying the Mac OS which I added by adding the following lines in /etc/grub.d/40_custom:

```
menuentry "Apple Mac OS" {
      insmod hfsplus
      search --set=root --file /System/Library/CoreServices/boot.efi
      chainloader /System/Library/CoreServices/boot.efi
    }
```

Upon the next boot grub was showing and Ubuntu was booting correctly through grub. The Mac OS was also listed. It works the first time I select it booting the OCLP install of Mac OS Sonoma however after a restart grub no longer displays at boot time, but the Mac boots directly into the Mac OS.
So, after some reading on the rEFInd website (which is an excellent website BTW) it seemed the solution was to "bless" the grub boot loader file.

So I did the following in the Mac OS:

1) Disabled SIP
2) Opened Terminal
3) Entered the following commands:
```
sudo su
mkdir /Volumes/ESP 
mount -t msdos /dev/disk0s1 /Volumes/ESP 
bless --mount /Volumes/ESP --setBoot --file /Volumes/ESP/efi/ubuntu/grubx64.efi --shortform
```

So I reboot and now the grub menu is displayed, however if I select the Mac OS entry that I entered I get an error

Error is:
```
/EndEntire
file path: /ACPI(a0341d0,0)/PCI(0,b)/Sata(0,0,0)/HD(1,28,64000,22bce3bb0fe8a845,2,2)/File(\System\Library\CoreServices)/File(boot.efi)/EndEntireOP
OCM: Failed to start image - Already started
BS: Failed to start OpenCore image - Already started
Halting on critical error
```

Booting into Mac OS no longer works at this point, whether from the OCLP loader, grub or a rEFInd USB stick.

It was working before the bless command (well at least the first boot of it seeing grub was then hijacked by the OpenCore loader)

I had backed up the setup with Clonezilla before running the bless command so I was able to restore to an earlier setup but am at a loss to figure out what is going wrong.

It seems to be loading OpenCore before grub is displayed, then by executing the grub Mac OS entry it is reporting that it is already running (which does not seem to be the case).

I need to know how to make grub always show without OpenCore hijacking it and taking over. I also need to be able to select the Mac OS from the grub menu and for it to boot (not just the first time).

Regards,
fbagnato

---

