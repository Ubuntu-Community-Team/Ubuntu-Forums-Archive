---
title: "Lubuntu 16.04 LTS 64 bit on Macbook 3,1: very slow boot of the OS"
date: 2017-04-05
forum: Apple Hardware Users
---

### Post by erotavlas on 2017-04-05
Hi,
I recently installed lubuntu 16.04 LTS 64 bit on a Macbook 3,1, but I'm experimenting a very slow boot of the OS.
I searched on the web about how to analyse such booting services and other stuff.
I found with:
```
systemd-analyze blame
         13.859s apparmor.service
         13.450s plymouth-read-write.service
         10.816s NetworkManager-wait-online.service
          3.821s systemd-backlight@backlight:intel_backlight.service
          3.284s dev-sda2.device
          2.803s ModemManager.service
          2.588s grub-common.service
```
what are the services that requires more time. I also had teamviewer service that took about 23 seconds and so I removed it.
Is there any possibility to reduce such long time?

Thank you

P.S.
On my asus f550c laptop with ubuntu mate 16.04 LTS 64 bit I do not have such long time:
```
systemd-analyze blame
          5.887s NetworkManager-wait-online.service
          1.964s docker.service
           988ms gpu-manager.service
           710ms dev-sda2.device
           635ms click-system-hooks.service
```

---

### Post by howefield on 2017-04-05
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by brainzyy on 2017-04-14
I'm having the exact same problem on my Macbook4.1 with only Lubuntu 16.04 installed.

---

### Post by erotavlas on 2017-04-19
> **brainzyy said:**
> I'm having the exact same problem on my Macbook4.1 with only Lubuntu 16.04 installed.

I searched on the web. I found that we can use this [command]("https://wiki.archlinux.org/index.php/Improving_performance/Boot_process") to reduce the required time:
```
systemctl enable upower
```
Moreover, we can try to use [systemd-manager]("https://github.com/mmstick/systemd-manager") as described [here]("https://askubuntu.com/a/808934").
At the moment, I cannot try since I have not access to my PC. Let me know if it helps.

---

### Post by erotavlas on 2017-05-24
I tried with:
```

systemctl enable upower

```
without success.
```

Failed to execute operation: No such file or directory

```
Do you have any hint? I'm still fighting with my system.
Thank you

Hi,
I have a similar problem with lubuntu 16.04.2 LTS 64 bit.
With systemd-analyze-blame I get:
```

systemd-analyze blame
        12.564s apparmor.service
         11.068s NetworkManager-wait-online.service
          8.102s plymouth-read-write.service
          7.045s console-setup.service
          5.963s dev-sda2.device
          4.787s systemd-fsck@dev-disk-by\x2duuid-9C44\x2d7B35.service
          4.053s systemd-fsck@dev-disk-by\x2duuid-80970053\x2d8bad\x2d408e\x2dae
          2.063s ModemManager.service
          2.044s accounts-daemon.service
          1.907s NetworkManager.service
          1.606s wpa_supplicant.service
          1.595s thermald.service
          1.482s grub-common.service
          1.109s keyboard-setup.service
          1.063s systemd-udevd.service

```
with aa-status I get:
```

apparmor module is loaded.
22 profiles are loaded.
22 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/bin/freshclam
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/sbin/clamd
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
0 profiles are in complain mode.
10 processes have profiles defined.
10 processes are in enforce mode.
   /sbin/dhclient (4697) 
   /usr/bin/freshclam (774) 
   /usr/sbin/clamd (751) 
   /usr/sbin/cups-browsed (836) 
   /usr/sbin/cupsd (4956) 
   /usr/sbin/cupsd (4958) 
   /usr/sbin/cupsd (4959) 
   /usr/sbin/cupsd (4960) 
   /usr/sbin/cupsd (4961) 
   /usr/sbin/ntpd (1462) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

```
So I cannot disable app-armor (I tried it without great reduction of boot time).

I can confirm that without splash it reduces a lot the boot time
```

systemd-analyze blame
10.050s NetworkManager-wait-online.service
          6.194s dev-sda2.device
          2.566s apparmor.service
          2.473s console-setup.service
          2.404s ModemManager.service
          2.401s systemd-tmpfiles-setup.service
          2.397s thermald.service
          2.213s plymouth-read-write.service
          2.074s NetworkManager.service
          1.806s binfmt-support.service
          1.789s accounts-daemon.service
          1.595s systemd-fsck@dev-disk-by\x2duuid-9C44\x2d7B35.service
          1.355s bluetooth.service
          1.236s lightdm.service
          1.165s systemd-rfkill.service
          1.125s gpu-manager.service
          1.099s systemd-fsck@dev-disk-by\x2duuid-80970053\x2d8bad\x2d408e\x2dae
          1.097s systemd-udevd.service
          1.057s keyboard-setup.servic

```

Without splash and with acpi_backlight=vendor
```

systemd-analyze blame
         11.050s NetworkManager-wait-online.service
          6.197s dev-sda2.device
          3.467s systemd-fsck@dev-disk-by\x2duuid-80970053\x2d8bad\x2d408e\x2dae
          2.961s ModemManager.service
          2.733s NetworkManager.service
          2.693s accounts-daemon.service
          2.076s thermald.service
          2.041s gpu-manager.service
          1.996s boot-efi.mount
          1.439s wpa_supplicant.service
          1.378s preload.service
          1.344s systemd-udevd.service
          1.233s systemd-fsck@dev-disk-by\x2duuid-9C44\x2d7B35.service
          1.174s grub-common.service
          1.149s colord.service
          1.125s bluetooth.service
          1.069s keyboard-setup.service
          1.016s dev-sda4.swap

```

Without splash and with noplymouth
```

systemd-analyze blame
         11.200s NetworkManager-wait-online.service
          5.886s dev-sda2.device
          2.767s apparmor.service
          2.546s console-setup.service
          2.480s systemd-tmpfiles-setup.service
          2.282s plymouth-read-write.service
          2.244s ModemManager.service
          2.177s binfmt-support.service
          1.925s accounts-daemon.service
          1.759s NetworkManager.service
          1.466s colord.service
          1.366s thermald.service
          1.200s upower.service
          1.172s wpa_supplicant.service
          1.131s systemd-udevd.service
          1.093s keyboard-setup.service

```

Do you have any other suggestions?
Thank you

---

### Post by QIII on 2017-05-24
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2341677](https://ubuntuforums.org/showthread.php?t=2341677)

Hello!  Hijacking an old thread is not likely to get you a timely response to your issue, which may have an entirely different cause.

Best to start your own thread.

Cheers.

---

### Post by erotavlas on 2017-05-24
Hi,
you are right, but I'm fighting for over a month of trials and errors as stated in [this thread]("https://ubuntuforums.org/showthread.php?t=2357738").
I found this thread and I applied with success some stuff to my case.
In particular, I found that:
```

with splash
systemd-analyze
Startup finished in 15.299s (kernel) + 39.644s (userspace) = 54.943s

with splash acpi_backlight=vendor
systemd-analyze
Startup finished in 15.179s (kernel) + 45.809s (userspace) = 1min 989ms

without splash
systemd-analyze
Startup finished in 37.415s (kernel) + 27.135s (userspace) = 1min 4.550s

without splash noplymouth
systemd-analyze 
Startup finished in 36.882s (kernel) + 28.387s (userspace) = 1min 5.269s

without splash acpi_backlight=vendor
systemd-analyze 
Startup finished in 16.175s (kernel) + 28.057s (userspace) = 44.233s

```

Hi,
I had a time to investigate more deeply and I found a way to improve the boot time (read [this thread]("https://ubuntuforums.org/showthread.php?t=2362119&p=13648728#post13648728")).
By changing the kernel boot parameters I found the best combination:
```
with splash
systemd-analyze
Startup finished in 15.299s (kernel) + 39.644s (userspace) = 54.943s

with splash acpi_backlight=vendor
systemd-analyze
Startup finished in 15.179s (kernel) + 45.809s (userspace) = 1min 989ms

without splash
systemd-analyze
Startup finished in 37.415s (kernel) + 27.135s (userspace) = 1min 4.550s

without splash noplymouth
systemd-analyze 
Startup finished in 36.882s (kernel) + 28.387s (userspace) = 1min 5.269s

[B]without splash acpi_backlight=vendor
systemd-analyze 
Startup finished in 16.175s (kernel) + 28.057s (userspace) = 44.233s[/B]


```

---

### Post by QIII on 2017-05-24
Threads merged.

Besides not hijacking old threads, please don't make posts regarding the same problem in different areas of the forums.

---

### Post by erotavlas on 2017-05-24
> **QIII said:**
> Threads merged.

Besides not hijacking old threads, please don't make posts regarding the same problem in different areas of the forums.

You are right, I replied to an old thread. However, I did not open two threads for the same problem. I only stated in my thread that I found a possible solution on another old thread.

---

