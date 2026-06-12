---
title: "Fresh install help"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by r5gtt2k3 on 2008-03-14
Ok So I've installed Ubuntu again, And got a few errors that came up.

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

but when i goto the terminal an type dpkg --configure -a i get this error 

dpkg: requested operation requires superuser privilege

Am i doing something wrong ? 
I'm using Ubuntu Ultimate edition, I'm not sure if i should be asking in this forum, But i always get great help from here.

And the reason for me trying to do this as it wont update or let me do basically anything, Restricted drivers give me that error also, so not much i can do

---

### Post by medha on 2008-03-14
type: sudo dpkg --configure -a

It will ask you for the root password.

---

### Post by r5gtt2k3 on 2008-03-14
Thanks, when i add the Sudo infront, I get this. 

dpkg: status database area is locked by another process

---

### Post by medha on 2008-03-14
Are you using any other process such as apt-get, synaptic, aptitude, etc? Close all those and try again.

---

### Post by r5gtt2k3 on 2008-03-14
Not that im aware of, I even just restarted, and tried it, I got the same thing, This isn't going very well

---

### Post by smurphy_it on 2008-03-14
Go into a terminal and post the output from the following command:

ps -A

---

### Post by r5gtt2k3 on 2008-03-14
Hi, when i type ps -A i get this (it's pretty long)

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   31 ?        00:00:00 kblockd/0
   32 ?        00:00:00 kblockd/1
   33 ?        00:00:00 kacpid
   34 ?        00:00:00 kacpi_notify
  196 ?        00:00:00 kseriod
  224 ?        00:00:00 pdflush
  225 ?        00:00:00 pdflush
  226 ?        00:00:00 kswapd0
  277 ?        00:00:00 aio/0
  278 ?        00:00:00 aio/1
 2331 ?        00:00:00 ata/0
 2332 ?        00:00:00 ata/1
 2413 ?        00:00:00 ata_aux
 2415 ?        00:00:00 ksuspend_usbd
 2418 ?        00:00:00 khubd
 2434 ?        00:00:00 khpsbpkt
 2601 ?        00:00:00 knodemgrd_0
 2602 ?        00:00:00 knodemgrd_1
 2603 ?        00:00:00 scsi_eh_0
 2607 ?        00:00:00 scsi_eh_1
 2649 ?        00:00:00 scsi_eh_2
 2650 ?        00:00:00 scsi_eh_3
 2733 ?        00:00:00 scsi_eh_4
 2734 ?        00:00:00 scsi_eh_5
 2755 ?        00:00:00 scsi_eh_6
 2756 ?        00:00:00 scsi_eh_7
 2795 ?        00:00:00 scsi_eh_8
 2796 ?        00:00:00 scsi_eh_9
 3004 ?        00:00:00 kjournald
 3481 ?        00:00:00 udevd
 4549 ?        00:00:00 kgameportd
 4643 ?        00:00:00 kpsmoused
 5419 ?        00:00:00 portmap
 5502 ?        00:00:00 rpc.statd
 5736 tty4     00:00:00 getty
 5737 tty5     00:00:00 getty
 5739 tty2     00:00:00 getty
 5742 tty3     00:00:00 getty
 5743 tty1     00:00:00 getty
 5744 tty6     00:00:00 getty
 5950 ?        00:00:00 acpid
 5982 ?        00:00:00 kondemand/0
 5984 ?        00:00:00 kondemand/1
 6087 ?        00:00:00 syslogd
 6147 ?        00:00:00 dd
 6149 ?        00:00:00 klogd
 6182 ?        00:00:00 dbus-daemon
 6198 ?        00:00:00 NetworkManager
 6212 ?        00:00:00 NetworkManagerD
 6225 ?        00:00:00 system-tools-ba
 6226 ?        00:00:00 dbus-daemon
 6253 ?        00:00:00 hald
 6254 ?        00:00:00 hald-runner
 6343 ?        00:00:00 hald-addon-keyb
 6346 ?        00:00:00 hald-addon-keyb
 6369 ?        00:00:00 hald-addon-acpi
 6509 ?        00:00:00 cupsd
 6559 ?        00:00:00 hald-addon-stor
 6623 ?        00:00:00 mysqld_safe
 6687 ?        00:00:00 mysqld
 6688 ?        00:00:00 logger
 7241 ?        00:00:00 freshclam
 9447 ?        00:00:00 lockd
 9448 ?        00:00:00 rpciod/0
 9449 ?        00:00:00 rpciod/1
 9453 ?        00:00:00 nfsd4
 9454 ?        00:00:00 nfsd
 9455 ?        00:00:00 nfsd
 9456 ?        00:00:00 nfsd
 9457 ?        00:00:00 nfsd
 9458 ?        00:00:00 nfsd
 9459 ?        00:00:00 nfsd
 9460 ?        00:00:00 nfsd
 9461 ?        00:00:00 nfsd
 9469 ?        00:00:00 rpc.mountd
 9567 ?        00:00:00 nmbd
 9597 ?        00:00:00 smbd
 9659 ?        00:00:00 console-kit-dae
 9774 ?        00:00:00 avahi-daemon
 9775 ?        00:00:00 avahi-daemon
 9793 ?        00:00:00 dhcdbd
 9817 ?        00:00:00 hcid
 9835 ?        00:00:00 bluetoothd-serv
 9840 ?        00:00:00 bluetoothd-serv
 9846 ?        00:00:00 krfcommd
 9903 ?        00:00:00 smbd
10030 ?        00:00:00 dhclient
12722 ?        00:00:00 gdm
12742 ?        00:00:00 gdm
12754 tty7     00:00:22 Xorg
12755 ?        00:00:00 anacron
12773 ?        00:00:00 atd
12806 ?        00:00:00 cron
13049 ?        00:00:00 hald-addon-keyb
13057 ?        00:00:00 apache2
13060 ?        00:00:00 hald-addon-keyb
13074 ?        00:00:00 hald-addon-keyb
13096 ?        00:00:00 preload
13160 ?        00:00:00 apache2
13161 ?        00:00:00 apache2
13162 ?        00:00:00 apache2
13163 ?        00:00:00 apache2
13164 ?        00:00:00 apache2
13232 ?        00:00:00 gnome-keyring-d
13237 ?        00:00:00 x-session-manag
13276 ?        00:00:00 bash <defunct>
13283 ?        00:00:00 ssh-agent
13285 ?        00:00:00 gconfd-2
13289 ?        00:00:00 dbus-daemon
13291 ?        00:00:00 gnome-settings-
13297 ?        00:00:00 metacity
13299 ?        00:00:02 gnome-panel
13301 ?        00:00:00 nautilus
13316 ?        00:00:00 bonobo-activati
13320 ?        00:00:00 gnome-volume-ma
13326 ?        00:00:00 gnome-vfs-daemo
13327 ?        00:00:00 vino-session
13328 ?        00:00:00 bluetooth-apple
13330 ?        00:00:00 update-notifier
13339 ?        00:00:00 evolution-alarm
13350 ?        00:00:00 nm-applet
13352 ?        00:00:00 python
13357 ?        00:00:00 gnome-power-man
13363 ?        00:00:00 trashapplet
13377 ?        00:00:00 mapping-daemon
13510 ?        00:00:00 fast-user-switc
13512 ?        00:00:00 deskbar-applet
13514 ?        00:00:00 mixer_applet2
13531 ?        00:00:00 notification-da
13536 ?        00:00:00 gnome-screensav
13565 ?        00:00:00 firefox
13577 ?        00:00:00 run-mozilla.sh
13581 ?        00:00:13 firefox-bin
16075 ?        00:00:00 konsole
16078 ?        00:00:00 kdeinit
16083 ?        00:00:00 dcopserver
16086 ?        00:00:00 klauncher
16088 ?        00:00:00 kded
16274 pts/0    00:00:00 bash
16290 pts/0    00:00:00 ps

---

### Post by r5gtt2k3 on 2008-03-14
I also get this error window pop up when i try to update, I'vesearched everywhere now and still none of the wiser to actually attempt to fix it or see where my problem lies.

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.

It's saying close them down, But i dont see anything else actually running ? where can i kill the processes that are running ? an actually kill them ?

---

### Post by r5gtt2k3 on 2008-03-14
Ok Now I've managed to enable my unrestricted drivers (graphics card) but still nothing else :(

---

### Post by r5gtt2k3 on 2008-03-14
Awesome, It's installing things, Things are looking up, and I've made it look extra sexy :) I think it may be time to forget about windows... 

I still know nothing about this OS, But, If i use it from day to day I'm sure it's not to hard to pick up after a while. Hope there's a better messenger than aMSN, thats total shite :| It's got stuck on the screen too an wont close down, but i can sort that when the update has finished.

Wonder why i was getting all the errors to start with, Least i stuck with it, I'm happy now :D

---

### Post by Therion on 2008-03-14
Run your updates and that should settle out a lot of issues for you.  Do you have the "Upgrade" icon on your desktop still?  If so, use it; it's there for a reason. 

As a substitute for aMSN, try using Pidgin.  I like it much better than aMSN.

---

### Post by r5gtt2k3 on 2008-03-14
Hi Therion, I saw one of your replys in a post the other day and your link to Ubuntu Ultimate made me go an get it :D 

and yes, thats where the updates are updating from, Finally, I'll have a look at the recommendation too thanks :) Anything must be better than this msn client.

---

### Post by Therion on 2008-03-14
I think you'll find Ultimate Edition to be a pretty rockin' little distro.  If you have questions that relate to UE in particular feel free to PM me... 
Or swing by the [Ultimate Edition forums](http://forumubuntusoftware.info/).

---

