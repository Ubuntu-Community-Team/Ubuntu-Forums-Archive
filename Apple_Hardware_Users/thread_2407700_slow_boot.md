---
title: "slow boot"
date: 2018-12-07
forum: Apple Hardware Users
---

### Post by robilio on 2018-12-07
Hello,
I've just installed kubuntu 18.10 on my old Macbook (MacBook "Core 2 Duo" 2.4 13" (White-08)) and everything is almost ok but the boot time.
It is *very* long, 5 minutes. Something is wrong but I do not understand what.
Can anybody help me identifying (and hopefully solving...) this problem?

Here ([https://pastebin.com/FhJn4zg8](https://pastebin.com/FhJn4zg8)) is the output of the dmesg command just after the boot process.

Here instead there is the output of the commands systemd-analyze and systemd-analyze blame
```
 Startup finished in 2min 22.034s (kernel) + 2min 54.836s (userspace) = 5min 16.871sgraphical.target reached after 30.445s in userspace
 1min 38.918s apt-daily-upgrade.service
      45.690s apt-daily.service
      11.148s logrotate.service
      11.037s snapd.service
      10.652s udisks2.service
       9.506s networkd-dispatcher.service
       9.023s NetworkManager-wait-online.service
       8.732s ModemManager.service
       7.484s dev-sda2.device
       7.059s accounts-daemon.service
       6.525s NetworkManager.service
       6.055s grub-common.service
       5.795s avahi-daemon.service
       5.715s bluetooth.service
       5.554s thermald.service
       5.075s rsyslog.service
       5.036s apport.service
       4.992s systemd-logind.service
       4.977s gpu-manager.service
       4.948s wpa_supplicant.service
       2.194s apparmor.service
       1.762s keyboard-setup.service
       1.589s systemd-journal-flush.service
       1.424s upower.service
       1.312s systemd-resolved.service
       1.264s systemd-tmpfiles-clean.service
       1.114s systemd-rfkill.service
       1.072s systemd-sysusers.service
        905ms polkit.service
        890ms systemd-modules-load.service
        837ms systemd-udevd.service
        798ms systemd-tmpfiles-setup.service
        661ms grub-initrd-fallback.service
        588ms systemd-backlight@backlight:intel_backlight.service
        575ms packagekit.service
        574ms systemd-sysctl.service
        557ms systemd-user-sessions.service
        516ms systemd-timesyncd.service
        504ms systemd-journald.service
        472ms swapfile.swap
        424ms pppd-dns.service
        397ms user@1000.service
        357ms setvtrgb.service
        354ms console-setup.service
        326ms systemd-random-seed.service
        307ms snapd.seeded.service
        305ms ufw.service
        274ms plymouth-read-write.service
        274ms systemd-tmpfiles-setup-dev.service
        228ms systemd-udev-trigger.service
        226ms kerneloops.service
        207ms kmod-static-nodes.service
        200ms dev-hugepages.mount
        198ms sys-kernel-debug.mount
        194ms systemd-fsck@dev-disk-by\x2duuid-C61D\x2d19CB.service
        168ms systemd-remount-fs.service
        128ms dev-mqueue.mount
        116ms systemd-update-utmp.service
        111ms rtkit-daemon.service
        103ms sddm.service
         77ms plymouth-quit.service
         68ms boot-efi.mount
         30ms systemd-update-utmp-runlevel.service
         27ms plymouth-start.service
         15ms sys-kernel-config.mount
          7ms sys-fs-fuse-connections.mount
          3ms snapd.socket

```
Thank you so much to anybody will help me!

Bye, R.
:)

---

