---
title: "Battery monitor with Powerbook 12&quot;"
date: 2005-03-02
forum: Apple PPC Users
---

### Post by Viro on 2005-03-02
Alright guys, I'm running stock debian, but I thought that I'd post in this forum since Ubuntu was the last distro that I knew worked with the battery monitor.

That's my question, really. Any one have any ideas how to get the battery monitor working? Mine is just showing 0% all the time and it doesn't know the difference between being plugged into an A/C outlet and running on battery.

I'm guessing that this is due to APM not running, and my question is how to get APM running? I would be very very grateful if someone who had a Powerbook could post the output of ***ps -A*** and the output of ***lsmod*** so that I can see what modules need to be loaded.

Cheers.

---

### Post by val1984 on 2005-03-02
You could run this kernel :
[http://twolife.free.fr/vrac/ibook/kernel-image-2.6.9_5.1_powerpc.deb](http://twolife.free.fr/vrac/ibook/kernel-image-2.6.9_5.1_powerpc.deb)
It is APM enabled like under Ubuntu GNU/Linux and has sleep support for ATI based PowerBooks (sorry :( ).
It doesn't need an initrd with ext2/3 at least, dunno for other fs so you'll have to edit /etc/yaboot.conf and delete the reference to initrd.

---

### Post by Viro on 2005-03-02
I've solved the problem. All I needed to do was to load the module apm_emu to emulate APM since PPC machines don't support APM and all is fine. If anyone is interested, you need to add the line apm_emu to the file /etc/modules.

---

### Post by charlie763 on 2005-03-03
I got the output you asked for. Here is the ps -A part:
```
charles@ubuntu:~ $ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:02 events/0
    4 ?        00:00:00 khelper
   24 ?        00:00:00 kblockd/0
   36 ?        00:00:00 pdflush
   37 ?        00:00:00 pdflush
   38 ?        00:00:00 kswapd0
   39 ?        00:00:00 aio/0
  194 ?        00:00:00 kjournald
  264 ?        00:00:00 udevd
  837 ?        00:00:00 thermostat
  920 ?        00:00:00 khpsbpkt
 1230 ?        00:00:00 kjournald
 1817 ?        00:00:00 khubd
 2391 ?        00:00:00 knodemgrd_0
 2654 ?        00:00:00 portmap
 2929 ?        00:00:00 syslogd
 2964 ?        00:00:00 klogd
 3026 ?        00:00:00 apmd
 3051 ?        00:00:00 cupsd
 3071 ?        00:00:00 dbus-daemon-1
 3075 ?        00:00:00 hald
 3111 ?        00:00:00 famd
 3139 ?        00:00:00 inetd
 3179 ?        00:00:00 mysqld_safe
 3230 ?        00:00:00 mysqld
 3231 ?        00:00:00 logger
 3234 ?        00:00:00 mysqld
 3235 ?        00:00:00 mysqld
 3256 ?        00:00:00 pbbuttonsd
 3366 ?        00:00:00 master
 3380 ?        00:00:00 pickup
 3382 ?        00:00:00 qmgr
 3437 ?        00:00:00 powernowd
 3449 ?        00:00:00 nmbd
 3451 ?        00:00:00 smbd
 3462 ?        00:00:00 smbd
 3465 ?        00:00:00 rpc.statd
 3476 ?        00:00:00 mdadm
 3487 ?        00:00:00 atd
 3498 ?        00:00:00 cron
 3511 ?        00:00:00 apache2
 3512 ?        00:00:00 apache2
 3513 ?        00:00:00 apache2
 3514 ?        00:00:00 apache2
 3515 ?        00:00:00 apache2
 3516 ?        00:00:00 apache2
 3518 ?        00:00:00 apache2
 3529 ?        00:00:00 apache2
 3530 ?        00:00:00 apache2
 3531 ?        00:00:00 apache2
 3532 ?        00:00:00 apache2
 3533 ?        00:00:00 apache2
 3534 ?        00:00:00 apache2
 3535 ?        00:00:00 apache2
 3536 ?        00:00:00 apache2
 3537 ?        00:00:00 apache2
 3538 ?        00:00:00 apache2
 3539 ?        00:00:00 apache2
 3540 ?        00:00:00 apache2
 3541 ?        00:00:00 apache2
 3542 ?        00:00:00 apache2
 3543 ?        00:00:00 apache2
 3544 ?        00:00:00 apache2
 3545 ?        00:00:00 apache2
 3546 ?        00:00:00 apache2
 3547 ?        00:00:00 apache2
 3548 ?        00:00:00 apache2
 3549 ?        00:00:00 apache2
 3550 ?        00:00:00 apache2
 3551 ?        00:00:00 apache2
 3552 ?        00:00:00 apache2
 3553 ?        00:00:00 apache2
 3554 ?        00:00:00 apache2
 3555 ?        00:00:00 apache2
 3556 ?        00:00:00 apache2
 3557 ?        00:00:00 apache2
 3558 ?        00:00:00 apache2
 3559 ?        00:00:00 apache2
 3560 ?        00:00:00 apache2
 3561 ?        00:00:00 apache2
 3562 ?        00:00:00 apache2
 3563 ?        00:00:00 apache2
 3564 ?        00:00:00 apache2
 3565 ?        00:00:00 apache2
 3566 ?        00:00:00 apache2
 3567 ?        00:00:00 apache2
 3568 ?        00:00:00 apache2
 3569 ?        00:00:00 apache2
 3570 ?        00:00:00 apache2
 3571 ?        00:00:00 apache2
 3572 ?        00:00:00 apache2
 3573 ?        00:00:00 apache2
 3574 ?        00:00:00 apache2
 3575 ?        00:00:00 apache2
 3576 ?        00:00:00 apache2
 3577 ?        00:00:00 apache2
 3578 ?        00:00:00 apache2
 3579 ?        00:00:00 apache2
 3584 ?        00:00:00 gdm
 3594 ?        00:00:00 gdm
 3602 tty1     00:00:00 getty
 3604 tty2     00:00:00 getty
 3605 tty3     00:00:00 getty
 3606 tty4     00:00:00 getty
 3607 tty5     00:00:00 getty
 3608 tty6     00:00:00 getty
 3729 ?        00:00:05 XFree86
 3832 ?        00:00:00 x-session-manag
 3878 ?        00:00:00 ssh-agent
 3881 ?        00:00:00 dbus-launch
 3882 ?        00:00:00 dbus-daemon-1
 3884 ?        00:00:02 gconfd-2
 3887 ?        00:00:00 bonobo-activati
 3889 ?        00:00:01 at-spi-registry
 3891 ?        00:00:00 gnome-keyring-d
 3893 ?        00:00:00 esd
 3895 ?        00:00:00 gnome-settings-
 3905 ?        00:00:00 xscreensaver
 3929 ?        00:00:00 gnome-smproxy
 3931 ?        00:00:00 metacity
 3939 ?        00:00:02 gnome-panel
 3941 ?        00:00:01 nautilus
 3943 ?        00:00:00 gnome-volume-ma
 3949 ?        00:00:00 gnome-cups-icon
 3950 ?        00:00:00 nautilus
 3951 ?        00:00:00 nautilus
 3953 ?        00:00:00 gnome-vfs-daemo
 3954 ?        00:00:00 gnome-cups-icon
 3957 ?        00:00:00 gnome-vfs-daemo
 3958 ?        00:00:00 gnome-vfs-daemo
 3962 ?        00:00:00 mapping-daemon
 3963 ?        00:00:00 nautilus
 3964 ?        00:00:00 nautilus
 3965 ?        00:00:00 nautilus
 3967 ?        00:00:01 wnck-applet
 3969 ?        00:00:00 trashapplet
 3970 ?        00:00:00 trashapplet
 3971 ?        00:00:00 trashapplet
 3972 ?        00:00:00 trashapplet
 3973 ?        00:00:00 trashapplet
 3976 ?        00:00:01 stickynotes_app
 3978 ?        00:00:00 mini_commander_
 3980 ?        00:00:00 clock-applet
 3982 ?        00:00:00 mixer_applet2
 3984 ?        00:00:00 battstat-applet
 3987 ?        00:00:00 wireless-applet
 3989 ?        00:00:00 notification-ar
 4034 ?        00:00:00 scsi_eh_0
 4035 ?        00:00:00 usb-storage
 4142 ?        00:00:01 gnome-terminal
 4143 ?        00:00:00 gnome-pty-helpe
 4144 pts/0    00:00:00 bash
 4145 ?        00:00:00 gnome-terminal
 4146 ?        00:00:00 gnome-terminal
 4150 ?        00:00:00 gnome-cups-icon
 4151 pts/0    00:00:00 ps
charles@ubuntu:~ $
```

here is the lsmod part:
```
charles@ubuntu:~ $ lsmod
Module                  Size  Used by
nls_iso8859_1           4416  1
nls_cp437               6176  1
vfat                   15968  1
fat                    54052  1 vfat
nls_base                8672  4 nls_iso8859_1,nls_cp437,vfat,fat
sd_mod                 25152  2
usb_storage            84236  1
cpufreq_userspace       6404  2
cpufreq_powersave       2016  0
ipv6                  323896  12
sungem                 36836  0
crc32                   4832  1 sungem
sungem_phy             10240  1 sungem
ohci1394               41924  0
ehci_hcd               37156  0
hci_usb                15584  0
bluetooth              61508  1 hci_usb
ohci_hcd               26212  0
usbcore               139092  6 usb_storage,ehci_hcd,hci_usb,ohci_hcd
uninorth_agp            8544  1
agpgart                42412  1 uninorth_agp
tsdev                   8640  0
evdev                  11968  2
md                     56756  0
dm_mod                 73056  1
sbp2                   28080  0
ieee1394              448200  2 ohci1394,sbp2
ide_cd                 49764  0
apm_emu                 8204  2
snd_powermac           44304  3
snd_pcm_oss            68136  0
snd_mixer_oss          23264  3 snd_pcm_oss
snd_pcm               119800  2 snd_powermac,snd_pcm_oss
snd_page_alloc         13480  1 snd_pcm
snd_timer              29348  1 snd_pcm
snd                    67800  7 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11812  3 snd
therm_adt746x          12492  0
sr_mod                 22884  0
scsi_mod              155372  4 sd_mod,usb_storage,sbp2,sr_mod
cdrom                  49660  2 ide_cd,sr_mod
ext3                  130736  2
jbd                    71576  1 ext3
mbcache                10116  1 ext3
ide_disk               27072  4
unix                   31992  943
charles@ubuntu:~ $
```

---

