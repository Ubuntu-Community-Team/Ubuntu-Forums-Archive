---
title: "Seemingly long boot, Ubuntu 18.04."
date: 2019-03-26
forum: Apple Hardware Users
---

### Post by hattermt on 2019-03-26
I'm fairly comfortable with linux. I'm running Ubuntu 18.04 on a Macbook Pro 5 (2009), single OS on an SSD with 8gb of ram. It runs great but I feel that the boot is slow. When I turn off the quiet splash and watch the commands go by it gets to the end and seems to pause longer than it should. Maybe I'm wrong. I know that these run concurrently, but I'n wondering something is out of place.

Can someone please look at this and tell me what you think? 

```

systemd-analyze blame
     1min 1.066s plymouth-quit-wait.service
          6.442s NetworkManager-wait-online.service
          1.579s dev-sda2.device
          1.547s dev-loop18.device
          1.541s dev-loop17.device
          1.534s dev-loop19.device
          1.511s dev-loop16.device
          1.476s dev-loop15.device
          1.315s dev-loop8.device
          1.297s dev-loop9.device
          1.259s dev-loop12.device
          1.240s dev-loop13.device
          1.233s dev-loop10.device
          1.221s dev-loop14.device
          1.190s dev-loop11.device
           853ms snapd.service
           841ms dev-loop7.device
           838ms dev-loop6.device
           838ms dev-loop5.device
           831ms dev-loop3.device
           817ms udisks2.service
           813ms dev-loop1.device
           810ms dev-loop4.device
           810ms dev-loop0.device
           804ms networkd-dispatcher.service
           796ms dev-loop2.device
           695ms swapfile.swap
           688ms fwupd.service
           467ms apparmor.service
           389ms snap-gnome\x2d3\x2d28\x2d1804-23.mount
           384ms avahi-daemon.service
           380ms NetworkManager.service
           373ms snap-gnome\x2dcharacters-206.mount
           369ms snap-gnome\x2dsystem\x2dmonitor-70.mount
           363ms keyboard-setup.service
           358ms upower.service
           336ms snap-gnome\x2d3\x2d26\x2d1604-82.mount
           324ms systemd-journal-flush.service
           304ms networking.service
           295ms plymouth-start.service
           283ms snap-gtk\x2dcommon\x2dthemes-818.mount
           278ms ModemManager.service
           277ms systemd-udev-trigger.service
           276ms snap-core-6531.mount
           273ms pommed.service
           271ms systemd-journald.service
           270ms wpa_supplicant.service
           267ms snap-canonical\x2dlivepatch-58.mount
           263ms snap-spotify-34.mount
           256ms snap-core18-782.mount
           253ms snap-core-6350.mount
           253ms snap-gnome\x2dcalculator-260.mount
           251ms snap-libreoffice-106.mount
           245ms snap-gnome\x2dcharacters-139.mount
           244ms snap-gnome\x2dlogs-57.mount
           242ms snap-gnome\x2dcalculator-352.mount
           239ms accounts-daemon.service
           236ms snap-gnome\x2dsystem\x2dmonitor-57.mount
           233ms snap-vlc-770.mount
           225ms snap-gnome\x2dlogs-45.mount
           223ms snap-gtk\x2dcommon\x2dthemes-1198.mount
           213ms snap-gnome\x2d3\x2d26\x2d1604-74.mount
           205ms grub-common.service
           201ms tlp.service
           192ms apport.service
           180ms systemd-logind.service
           178ms speech-dispatcher.service
           169ms thermald.service
           166ms gdm.service
           141ms rsyslog.service
           125ms pppd-dns.service
           108ms systemd-timesyncd.service
           100ms user@121.service
           100ms gpu-manager.service
            99ms snapd.seeded.service
            89ms user@1000.service
            88ms systemd-resolved.service
            74ms systemd-udevd.service
            69ms polkit.service
            66ms packagekit.service
            51ms dns-clean.service
            49ms bolt.service
            45ms systemd-modules-load.service
            45ms systemd-fsck@dev-disk-by\x2duuid-1C32\x2d6CD2.service
            44ms kmod-static-nodes.service
            43ms systemd-random-seed.service
            42ms dev-mqueue.mount
            42ms systemd-tmpfiles-setup.service
            41ms sys-kernel-debug.mount
            41ms systemd-remount-fs.service
            39ms systemd-tmpfiles-setup-dev.service
            35ms dev-hugepages.mount
            34ms ufw.service
            34ms systemd-update-utmp.service
            30ms systemd-sysctl.service
            28ms systemd-tmpfiles-clean.service
            25ms sys-fs-fuse-connections.mount
            25ms iio-sensor-proxy.service
            24ms colord.service
            23ms plymouth-read-write.service
            22ms bluetooth.service
            19ms boot-efi.mount
            19ms kerneloops.service
            13ms systemd-update-utmp-runlevel.service
            13ms snapd.socket
            12ms sys-kernel-config.mount
            12ms systemd-backlight@leds:smc::kbd_backlight.service
            12ms setvtrgb.service
            11ms systemd-user-sessions.service
             9ms console-setup.service
             8ms systemd-backlight@backlight:nv_backlight.service
             7ms rtkit-daemon.service


```

---

### Post by QIII on 2019-03-26
Moved to Apple Hardware Users as a more appropriate sub-forum.

---

### Post by oldfred on 2019-03-26
Are the number to default loop devices growing?
I un-installed mine, to only use .deb apps.

       boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

---

### Post by hattermt on 2019-03-27
I was wondering about the loop devices, They didn't seem to be growing. I switched to Ubuntu Mate 18.04 and there are only 5 loop device's right now. I'll keep an eye on it. I switched for something a little lighter, so far so good, and it boots faster.

---

