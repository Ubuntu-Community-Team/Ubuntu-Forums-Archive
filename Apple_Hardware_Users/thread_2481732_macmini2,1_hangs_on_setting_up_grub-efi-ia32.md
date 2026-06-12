---
title: "macmini2,1 hangs on setting up grub-efi-ia32"
date: 2022-12-07
forum: Apple Hardware Users
---

### Post by Peter_R._Wood on 2022-12-07
I've been running my macmini2,1 on Ubuntu for quite a few years now with minimal issues, but within the past week, something has happened that is preventing me from upgrading any packages. I'm not quite sure how this happened, but now when I run "sudo apt full-upgrade," I get the following:

```
peter@macmini:~$ sudo apt full-upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

```
When I run that command, I get this:

```
peter@macmini:~$ sudo dpkg --configure -a
Setting up grub-efi-ia32 (2.02-2ubuntu8.25) ...
Installing for i386-efi platform.

```
And then, the terminal just hangs there. If I run top, the "grub-install --target=i386-efi" appears briefly at the top, but then no longer seems to be doing anything. I have left it at this point for hours, but nothing seems to happen.

These are the processes running that have 'grub' in their path:

```
peter@macmini:~$ ps -eaf | grep grub
root     23080     1  0 Dec01 ?        00:00:00 efibootmgr -q -c -d /dev/sda -p 1 -w -L ubuntu -l \EFI\ubuntu\grubia32.efi
root     27298 27297  0 14:45 pts/3    00:00:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/grub-efi-ia32.postinst configure 2.02-2ubuntu8.23
root     27308 27298  0 14:45 pts/3    00:00:00 /bin/bash /var/lib/dpkg/info/grub-efi-ia32.postinst configure 2.02-2ubuntu8.23
root     27422 27308  0 14:45 pts/3    00:00:00 grub-install --target=i386-efi
peter    27461 25446  0 14:46 pts/4    00:00:00 grep --color=auto grub
```

It seems that until I get this process to finish, I won't be able to run apt upgrades.

Any suggestions on how to fix this?

Below is what I hope might be some useful info on my system:

```
uname -a:
Linux macmini 4.15.0-196-generic #207-Ubuntu SMP Thu Oct 27 21:24:58 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

From dmesg:




```
[    0.000000] efi: EFI v1.10 by Apple
[    0.000000] efi:  ACPI=0xbeefd000  ACPI 2.0=0xbeefd014  SMBIOS=0xbeebf000
[    0.000000] DMI: Apple Inc. Macmini2,1/Mac-F4208EAA, BIOS     MM21.88Z.009A.B00.0706281359 06/28/07
[    0.000000] ACPI: DSDT 0x00000000BEEF0000 00384E (v01 APPLE  Macmini  00020001 INTL 20050309)
[    0.149394] smpboot: CPU0: Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz (family: 0x6, model: 0xf, stepping: 0x6)
[2451605.862059] Hardware name: Apple Inc. Macmini2,1/Mac-F4208EAA, BIOS     MM21.88Z.009A.B00.07062

```

---

