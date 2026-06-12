---
title: "Can't unmount USB key/stick in Xubuntu"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Jeremiah_P on 2008-01-14
Xubuntu 07.10 (fresh install)

Upon insertion, my usb key automounted without a problem (FAT filesystem).  I moved some files from the desktop to the memory stick, and deleted and reorganized files on the stick.  I even learned to empty the deleted trash to commit the deletions and free up space on the key (as opposed to Windows which doesn't keep trash for removable media).

I was ready to remove the key but, remembering Windows 2000 Pro's old problem with synching file system changes for removeable media, I thought it was best to manually unmount the memory stick first.  Right clicking the key from Xubuntu's Xfce desktop and choosing UNMOUNT resulted in two error dialogs: "CANNOT UNMOUNT VOLUME: An application is preventing the volume 'JEREMIAH' from being unmounted." -and- "UNABLE TO UNMOUNT "JEREMIAH": Unknown error"

I gave it 10, 20, and 30 minutes to see if perhaps Linux hadn't yet flushed all read/writes to the stick.  Multiple attempts resulted in the same errors.

I searched around and found several threads that addressed this problem, but none were written clearly or ended in resolution, so I thought I'd start another one here.  Following the advice of other divergent threads, I ran the following commands from the terminal window (obviously my username and USB volume name are both JEREMIAH):

```

jeremiah@desktop-pc:~$ sudo umount /media/JEREMIAH/
umount: /media/JEREMIAH: device is busy
umount: /media/JEREMIAH: device is busy
jeremiah@desktop-pc:~$ sudo lsof | grep /media/JEREMIAH
Thunar     5471   jeremiah   23r      DIR        8,1   16384          1 /media/JEREMIAH
jeremiah@desktop-pc:~$ kill 5471
jeremiah@desktop-pc:~$ sudo lsof | grep /media/JEREMIAH
jeremiah@desktop-pc:~$ sudo umount /media/JEREMIAH/
jeremiah@desktop-pc:~$ 

```

I then physically removed the key and inserted the memory key into my Windows XP machine.  The filesystem was fine and as I had organized it.  There were two additional directories on the key that came from Linux:  ".Trash-1002" and "SyncApp"  

[LIST]
[*]It appears that the Unmount command from Xfce isn't alerting the Thunar file manager of the need to release the drive?  Thunar was still functional after killing the 5471 process in the above example.  

[*]So, does Xubuntu support "suprise removal" of the USB memory stick?  

[*]What can be done to automount the USB memory sticks in such a way that they always synch file changes on the fly (similar to Windows XP & Vista flushing read/writes upon file closure)?  

[*]Should I report this experience as a bug for Xubuntu 7.10?
[/LIST]

---

### Post by ajmorris on 2008-01-14
hi there,
when the usb device is plugged in, and being unable to mount, before you do the kill 5471... could you please post the output of ```
ps -A
```

---

### Post by Nezing on 2008-01-14
aj,I have a differnt problem,with my usb pen-drive.I took it to a friends house (XP),and like a fool I unplugged it,whilst talking,came home,and valla...cannot mount it.Yes,I can go and plug it into an XP desktop at work tomorrow,and then unplug it correctly,via  the Safetly Remove Hardware solution,but just in case I have this problem at home in the future,I have followed your instructions,via Terminal,and get this:

 5022 ?        00:00:03 thunar-tpa
 5027 ?        00:00:01 notification-da
 6128 ?        00:00:00 pdflush
 6767 ?        00:00:00 hcid
 6777 ?        00:00:00 bluetoothd-serv
 6778 ?        00:00:00 bluetoothd-serv
 6783 ?        00:00:00 krfcommd
 8881 ?        00:00:00 gnome-vfs-daemo
 9053 ?        00:00:00 xfce4-cpugraph-
 9054 ?        00:00:01 xfce4-screensho <defunct>
 9055 ?        00:00:00 xfce4-systemloa <defunct>
 9056 ?        00:00:00 xfce4-weather-p <defunct>
 9057 ?        00:00:00 thunderbird <defunct>
 9232 ?        00:00:00 firefox
 9244 ?        00:00:00 run-mozilla.sh
 9248 ?        00:00:37 firefox-bin
 9272 ?        00:00:00 scsi_eh_10
 9273 ?        00:00:00 usb-storage
 9314 ?        00:00:00 hald-addon-stor
 9323 ?        00:00:00 xfce4-terminal
 9324 ?        00:00:00 gnome-pty-helpe
 9325 pts/0    00:00:00 bash
 9341 pts/0    00:00:00 ps

---

### Post by fickendichdu on 2008-01-14
I have made the mistake with XP like you before.  When you plug it in Ubuntu will give you an error with some details.  You can type in the sudo command and it will force the mount and allow you to use it.

Also on the other issue make sure you do not have a program running that is using your pen drive.

---

### Post by ajmorris on 2008-01-14
> **Nezing said:**
> aj,I have a differnt problem,with my usb pen-drive.I took it to a friends house (XP),and like a fool I unplugged it,whilst talking,came home,and valla...cannot mount it.Yes,I can go and plug it into an XP desktop at work tomorrow,and then unplug it correctly,via  the Safetly Remove Hardware solution,but just in case I have this problem at home in the future,I have followed your instructions,via Terminal,and get this:


Unfortunately, that command was to show jeremiah's processes to detect which process had the process id of 5471 so that he knew what was preventing him from unmounting his flash disk. im not quite sure how you can solve your problem... i might be able to figure it out if you run sudo fsck

First, run ```
sudo fdisk -l
```
then, find what /dev/DEVICE your flash disk is on, then run ```
sudo fsck /dev/sdb1
``` (where sdb1 is the device for your flash disk

---

### Post by PsychoticSpoon on 2008-02-26
I hope this thread isn't officially dead yet.

I'm having the same problem - XFCE is set to automatically mount my USB stick, but I can't unmount it. I can't do it by right-clicking on its icon, nor can I do it from the command line. The only program that I have actively running, i.e. with a window open, is a terminal.

I'm going to post the information that ajmorris requested, since it appears that I have the same problem.

```

user@xubuntu:~$ sudo umount /media/SanDisk
umount: /media/SanDisk: device is busy
umount: /media/SanDisk: device is busy
user@xubuntu:~$ lsof | grep SanDisk
Thunar    4841         user   20r       DIR        8,33      4096        1 /media/SanDisk
user@xubuntu:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:05 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   26 ?        00:00:00 kblockd/0
   27 ?        00:00:02 kacpid
   28 ?        00:00:00 kacpi_notify
  129 ?        00:00:00 kseriod
  149 ?        00:00:00 pdflush
  150 ?        00:00:01 kswapd0
  201 ?        00:00:00 aio/0
 1947 ?        00:00:00 ksuspend_usbd
 1948 ?        00:00:00 khubd
 2028 ?        00:00:00 ata/0
 2029 ?        00:00:00 ata_aux
 2065 ?        00:00:00 scsi_eh_0
 2066 ?        00:00:00 scsi_eh_1
 2151 ?        00:00:00 scsi_eh_2
 2152 ?        00:00:03 usb-storage
 2442 ?        00:00:00 udevd
 3360 ?        00:00:00 kpsmoused
 3916 tty4     00:00:00 getty
 3917 tty5     00:00:00 getty
 3921 tty2     00:00:00 getty
 3922 tty3     00:00:00 getty
 3931 tty1     00:00:00 getty
 3932 tty6     00:00:00 getty
 4120 ?        00:00:00 acpid
 4152 ?        00:00:00 kondemand/0
 4227 ?        00:00:00 syslogd
 4283 ?        00:00:00 dd
 4285 ?        00:00:00 klogd
 4306 ?        00:00:02 dbus-daemon
 4322 ?        00:00:00 NetworkManager
 4336 ?        00:00:00 NetworkManagerD
 4349 ?        00:00:00 system-tools-ba
 4350 ?        00:00:00 dbus-daemon
 4369 ?        00:00:04 hald
 4370 ?        00:00:00 hald-runner
 4424 ?        00:00:00 hald-addon-keyb
 4425 ?        00:00:00 hald-addon-keyb
 4428 ?        00:00:00 hald-addon-acpi
 4431 ?        00:00:00 hald-addon-keyb
 4432 ?        00:00:00 hald-addon-keyb
 4433 ?        00:00:00 hald-addon-keyb
 4444 ?        00:00:00 cupsd
 4483 ?        00:00:00 hald-addon-stor
 4571 ?        00:00:00 avahi-daemon
 4572 ?        00:00:00 avahi-daemon
 4586 ?        00:00:00 dhcdbd
 4619 ?        00:00:00 gdm
 4620 ?        00:00:00 gdm
 4627 tty7     00:02:40 Xorg
 4664 ?        00:00:00 atd
 4678 ?        00:00:00 cron
 4792 ?        00:00:00 x-session-manag
 4822 ?        00:00:00 ssh-agent
 4825 ?        00:00:00 dbus-launch
 4826 ?        00:00:00 dbus-daemon
 4831 ?        00:00:05 xfce-mcs-manage
 4833 ?        00:00:00 gnome-keyring-d
 4835 ?        00:00:00 gconfd-2
 4837 ?        00:00:05 xfwm4
 4839 ?        00:00:21 xfce4-panel
 4841 ?        00:00:44 Thunar
 4843 ?        00:00:00 gam_server
 4845 ?        00:00:09 xfdesktop
 4847 ?        00:00:08 xfce4-menu-plug
 4851 ?        00:00:02 nm-applet
 4853 ?        00:00:00 python
 4855 ?        00:00:05 update-notifier
 4856 ?        00:00:00 gnome-power-man
 4862 ?        00:00:04 notification-da
 4882 ?        00:00:00 wpa_supplicant
 4888 ?        00:00:00 dhclient
 8542 ?        00:00:00 pdflush
 8845 ?        00:00:00 xfce4-systemloa <defunct>
 8846 ?        00:00:01 xfce4-cpugraph-
 9135 ?        00:00:00 scsi_eh_7
 9136 ?        00:00:03 usb-storage
 9176 ?        00:00:00 hald-addon-stor
 9423 ?        00:00:01 xfce4-terminal
 9424 ?        00:00:00 gnome-pty-helpe
 9425 pts/0    00:00:00 bash
 9534 ?        00:00:00 scsi_eh_8
 9535 ?        00:00:00 usb-storage
 9575 ?        00:00:00 hald-addon-stor
 9600 pts/0    00:00:00 ps

```

It might also be worth noting that I can plug in other USB drives during this time, and mount and unmount them at will.

---

### Post by tedpoe on 2008-03-29
I had that happen as well running eeeXubuntu.  After shutting down, I went back to it today, reinserted the same flash drive, and then emptied the Trash.  I had no problem unmounting via Thunar, then.  Could you check and see if you left something in the Trash?  That might be the cause of the issue here.

Ted

---

