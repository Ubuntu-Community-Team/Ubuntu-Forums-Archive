---
title: "[SOLVED] dual boot no space"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by kerrymorgan1 on 2007-08-17
why would my computer say 

"GDM could not write to your authorization file. This could mean that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator."
???
when i first did the partition thing i set aside 50 gigs for it....... 
can someone please help me fix this please.......

it wont let me even log in to my computer it pops up this and restarts again.... i log in and the message pops in again..... the circle of death

thanks in advance

---

### Post by heimo on 2007-08-17
> **kerrymorgan1 said:**
> why would my computer say 

"GDM could not write to your authorization file. This could mean that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator."
???
when i first did the partition thing i set aside 50 gigs for it....... 
can someone please help me fix this please.......

it wont let me even log in to my computer it pops up this and restarts again.... i log in and the message pops in again..... the circle of death


A bit unclear to me, but do you already know that it actually is out of space? You could change to virtual console by hitting ctrl+alt+F2, logging in and running df command to see how much space you have. Then if it's full, run apt-get clean to make a little space, hit ctrl+alt+F7 and try logging in. But then, this may not be disk space related at all.

---

### Post by kerrymorgan1 on 2007-08-17
fixed mate thanks for the help ...... I'm logged in now 94% space used

next question though where is my space i know you can't stand behind me and point to me delete that delete that........ but is there any way to find and locate things on this computer i don't need (possible things i didn't format and remained on the drive) and delete of course

this is a 500G sata Hd i set aside 50 for this....

---

### Post by taurus on 2007-08-17
Check to make sure you don't have anything large in /var/backup.  Also, may want to clean out the archives.

```
sudo apt-get clean
sudo du -h /var
```

---

### Post by heimo on 2007-08-17
> **kerrymorgan1 said:**
> next question though where is my space

Do you have Applications->Accessories->Disk Usage Analyzer? Try that one.

---

### Post by kerrymorgan1 on 2007-08-17
i run that and didn't see anything out of the ordinary really.....
but when i look in the properties of the / folder it says  155393 items totalling 53.1 GB

i just installed Linux 2 days ago?.....

will i have to re format and reiinstall?

---

### Post by taurus on 2007-08-17
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
sudo du -h /var
```

---

### Post by kerrymorgan1 on 2007-08-17
> **heimo said:**
> Do you have Applications->Accessories->Disk Usage Analyzer? Try that one.

that brought up heaps

---

### Post by heimo on 2007-08-17
> **taurus said:**
> What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
sudo du -h /var
```


Or even:
```

sudo du -sh /*
```

---

### Post by kerrymorgan1 on 2007-08-17
> **taurus said:**
> What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
sudo du -h /var
```

kerryandjane@KandJ-desktop:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
kerryandjane@KandJ-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.8G  2.4G  230M  92% /
varrun               1007M  100K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
procbususb           1007M   96K 1007M   1% /proc/bus/usb
udev                 1007M   96K 1007M   1% /dev
devshm               1007M     0 1007M   0% /dev/shm
lrm                  1007M   13M  994M   2% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             417G   49G  369G  12% /media/sda1
/dev/sdb1             441M  375M   66M  86% /media/PackardBell
kerryandjane@KandJ-desktop:~$ sudo du -h /var
0       /var/lock
0       /var/run/sudo/kerryandjane
0       /var/run/sudo
0       /var/run/console
16K     /var/run/hplip
4.0K    /var/run/cups/certs
12K     /var/run/cups
4.0K    /var/run/avahi-daemon
8.0K    /var/run/NetworkManager
4.0K    /var/run/hal
4.0K    /var/run/dbus
8.0K    /var/run/klogd
0       /var/run/screen
0       /var/run/pppconfig
4.0K    /var/run/network
100K    /var/run
1.6M    /var/backups
6.1M    /var/cache/app-install
4.0K    /var/cache/apt/archives/partial
16K     /var/cache/apt/archives
20M     /var/cache/apt
4.0K    /var/cache/cups/ppd
8.0K    /var/cache/cups
4.9M    /var/cache/debconf
28K     /var/cache/dictionaries-common
752K    /var/cache/fontconfig
4.0K    /var/cache/gnome-system-tools/backup
8.0K    /var/cache/gnome-system-tools
4.0K    /var/cache/locate
4.0K    /var/cache/man/X11R6
4.0K    /var/cache/man/cat1
4.0K    /var/cache/man/cat2
4.0K    /var/cache/man/cat3
4.0K    /var/cache/man/cat4
4.0K    /var/cache/man/cat5
4.0K    /var/cache/man/cat6
4.0K    /var/cache/man/cat7
4.0K    /var/cache/man/cat8
4.0K    /var/cache/man/cat9
4.0K    /var/cache/man/fsstnd
4.0K    /var/cache/man/local
4.0K    /var/cache/man/oldlocal
4.0K    /var/cache/man/opt
396K    /var/cache/man
4.0K    /var/cache/pppconfig
44K     /var/cache/restricted-manager
4.0K    /var/cache/samba
28K     /var/cache/system-tools-backends/backup/First/etc
32K     /var/cache/system-tools-backends/backup/First
8.0K    /var/cache/system-tools-backends/backup/1/var/cache/system-tools-backends
12K     /var/cache/system-tools-backends/backup/1/var/cache
16K     /var/cache/system-tools-backends/backup/1/var
20K     /var/cache/system-tools-backends/backup/1
8.0K    /var/cache/system-tools-backends/backup/2/etc
12K     /var/cache/system-tools-backends/backup/2
68K     /var/cache/system-tools-backends/backup
76K     /var/cache/system-tools-backends
256K    /var/cache/modass
33M     /var/cache
1.9M    /var/crash
4.0K    /var/games
4.0K    /var/lib/NetworkManager
20K     /var/lib/acpi-support
8.0K    /var/lib/alsa
8.0K    /var/lib/apt/lists/partial
32M     /var/lib/apt/lists
4.0K    /var/lib/apt/mirrors/partial
8.0K    /var/lib/apt/mirrors
4.0K    /var/lib/apt/periodic
32M     /var/lib/apt
1.9M    /var/lib/aptitude
3.5M    /var/lib/aspell
4.0K    /var/lib/avahi-autoipd
52K     /var/lib/belocs
12K     /var/lib/binfmts
4.0K    /var/lib/bittorrent
8.0K    /var/lib/dbus
8.0K    /var/lib/defoma/fontconfig.d/A
4.0K    /var/lib/defoma/fontconfig.d/B
8.0K    /var/lib/defoma/fontconfig.d/C
64K     /var/lib/defoma/fontconfig.d/D
4.0K    /var/lib/defoma/fontconfig.d/E
4.0K    /var/lib/defoma/fontconfig.d/F
8.0K    /var/lib/defoma/fontconfig.d/G
4.0K    /var/lib/defoma/fontconfig.d/H
4.0K    /var/lib/defoma/fontconfig.d/J
4.0K    /var/lib/defoma/fontconfig.d/K
8.0K    /var/lib/defoma/fontconfig.d/L
56K     /var/lib/defoma/fontconfig.d/M
4.0K    /var/lib/defoma/fontconfig.d/N
4.0K    /var/lib/defoma/fontconfig.d/O
12K     /var/lib/defoma/fontconfig.d/P
4.0K    /var/lib/defoma/fontconfig.d/R
4.0K    /var/lib/defoma/fontconfig.d/S
12K     /var/lib/defoma/fontconfig.d/T
4.0K    /var/lib/defoma/fontconfig.d/U
4.0K    /var/lib/defoma/fontconfig.d/V
8.0K    /var/lib/defoma/fontconfig.d/a
8.0K    /var/lib/defoma/fontconfig.d/j
8.0K    /var/lib/defoma/fontconfig.d/m
4.0K    /var/lib/defoma/fontconfig.d/u
388K    /var/lib/defoma/fontconfig.d
4.0K    /var/lib/defoma/gs.d/dirs/CMap
200K    /var/lib/defoma/gs.d/dirs/fonts
208K    /var/lib/defoma/gs.d/dirs
324K    /var/lib/defoma/gs.d
164K    /var/lib/defoma/libwmf0.2-7.d
144K    /var/lib/defoma/pango.d
72K     /var/lib/defoma/scripts
4.0K    /var/lib/defoma/x-ttcidfont-conf.d/dirs/CID
284K    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
292K    /var/lib/defoma/x-ttcidfont-conf.d/dirs
664K    /var/lib/defoma/x-ttcidfont-conf.d
2.2M    /var/lib/defoma
8.0K    /var/lib/dhcp3
8.0K    /var/lib/dictionaries-common/aspell
12K     /var/lib/dictionaries-common/wordlist
24K     /var/lib/dictionaries-common
204K    /var/lib/doc-base/info
208K    /var/lib/doc-base
288K    /var/lib/dpkg/alternatives
33M     /var/lib/dpkg/info
4.0K    /var/lib/dpkg/methods/disk
4.0K    /var/lib/dpkg/methods/floppy
4.0K    /var/lib/dpkg/methods/mnt
16K     /var/lib/dpkg/methods
4.0K    /var/lib/dpkg/parts
4.0K    /var/lib/dpkg/updates
37M     /var/lib/dpkg
1.4M    /var/lib/gcj-4.1
72K     /var/lib/gconf/debian.defaults
52M     /var/lib/gconf/defaults
52M     /var/lib/gconf
44K     /var/lib/gdm/.fontconfig
60K     /var/lib/gdm
4.0K    /var/lib/gstreamer/0.10
8.0K    /var/lib/gstreamer
12K     /var/lib/initramfs-tools
4.0K    /var/lib/initscripts
12K     /var/lib/locales/supported.d
16K     /var/lib/locales
8.0K    /var/lib/logrotate
68K     /var/lib/misc
8.0K    /var/lib/mozilla-firefox/extensions.d
12K     /var/lib/mozilla-firefox
8.0K    /var/lib/mozilla-thunderbird/extensions.d
12K     /var/lib/mozilla-thunderbird
148K    /var/lib/scrollkeeper/C
60K     /var/lib/scrollkeeper/af
60K     /var/lib/scrollkeeper/am
60K     /var/lib/scrollkeeper/an
60K     /var/lib/scrollkeeper/ar
60K     /var/lib/scrollkeeper/as
60K     /var/lib/scrollkeeper/az
68K     /var/lib/scrollkeeper/be
80K     /var/lib/scrollkeeper/bg
60K     /var/lib/scrollkeeper/bn
60K     /var/lib/scrollkeeper/br
60K     /var/lib/scrollkeeper/bs
60K     /var/lib/scrollkeeper/ca
60K     /var/lib/scrollkeeper/co
72K     /var/lib/scrollkeeper/cs
60K     /var/lib/scrollkeeper/cy
60K     /var/lib/scrollkeeper/da
80K     /var/lib/scrollkeeper/de
68K     /var/lib/scrollkeeper/el
60K     /var/lib/scrollkeeper/en
84K     /var/lib/scrollkeeper/en_GB
60K     /var/lib/scrollkeeper/eo
124K    /var/lib/scrollkeeper/es
64K     /var/lib/scrollkeeper/et
72K     /var/lib/scrollkeeper/eu
60K     /var/lib/scrollkeeper/fa
72K     /var/lib/scrollkeeper/fi
60K     /var/lib/scrollkeeper/fo
116K    /var/lib/scrollkeeper/fr
60K     /var/lib/scrollkeeper/ga
60K     /var/lib/scrollkeeper/gl
60K     /var/lib/scrollkeeper/gu
60K     /var/lib/scrollkeeper/he
60K     /var/lib/scrollkeeper/hr
72K     /var/lib/scrollkeeper/hu
60K     /var/lib/scrollkeeper/hy
60K     /var/lib/scrollkeeper/ia
72K     /var/lib/scrollkeeper/id
60K     /var/lib/scrollkeeper/is
100K    /var/lib/scrollkeeper/it
88K     /var/lib/scrollkeeper/ja
60K     /var/lib/scrollkeeper/ka
60K     /var/lib/scrollkeeper/kk
60K     /var/lib/scrollkeeper/kn
96K     /var/lib/scrollkeeper/ko
60K     /var/lib/scrollkeeper/ku
60K     /var/lib/scrollkeeper/ky
60K     /var/lib/scrollkeeper/lb
60K     /var/lib/scrollkeeper/lg
60K     /var/lib/scrollkeeper/li
60K     /var/lib/scrollkeeper/lo
60K     /var/lib/scrollkeeper/lt
60K     /var/lib/scrollkeeper/lv
60K     /var/lib/scrollkeeper/mg
60K     /var/lib/scrollkeeper/mi
60K     /var/lib/scrollkeeper/ml
60K     /var/lib/scrollkeeper/mn
60K     /var/lib/scrollkeeper/mr
60K     /var/lib/scrollkeeper/ms
60K     /var/lib/scrollkeeper/my
60K     /var/lib/scrollkeeper/nb
60K     /var/lib/scrollkeeper/ne
72K     /var/lib/scrollkeeper/nl
60K     /var/lib/scrollkeeper/nn
60K     /var/lib/scrollkeeper/no
60K     /var/lib/scrollkeeper/oc
60K     /var/lib/scrollkeeper/or
68K     /var/lib/scrollkeeper/pa
60K     /var/lib/scrollkeeper/pl
72K     /var/lib/scrollkeeper/pt
72K     /var/lib/scrollkeeper/pt_BR
60K     /var/lib/scrollkeeper/rm
68K     /var/lib/scrollkeeper/ro
92K     /var/lib/scrollkeeper/ru
60K     /var/lib/scrollkeeper/rw
60K     /var/lib/scrollkeeper/se
60K     /var/lib/scrollkeeper/si
60K     /var/lib/scrollkeeper/sk
60K     /var/lib/scrollkeeper/sl
60K     /var/lib/scrollkeeper/sq
68K     /var/lib/scrollkeeper/sr
60K     /var/lib/scrollkeeper/sr@Latn
108K    /var/lib/scrollkeeper/sv
60K     /var/lib/scrollkeeper/sw
60K     /var/lib/scrollkeeper/ta
60K     /var/lib/scrollkeeper/te
60K     /var/lib/scrollkeeper/tg
60K     /var/lib/scrollkeeper/th
60K     /var/lib/scrollkeeper/tk
60K     /var/lib/scrollkeeper/tl
60K     /var/lib/scrollkeeper/tr
60K     /var/lib/scrollkeeper/ug
92K     /var/lib/scrollkeeper/uk
60K     /var/lib/scrollkeeper/ur
60K     /var/lib/scrollkeeper/uz
60K     /var/lib/scrollkeeper/vi
60K     /var/lib/scrollkeeper/wa
60K     /var/lib/scrollkeeper/wo
60K     /var/lib/scrollkeeper/xh
60K     /var/lib/scrollkeeper/yi
60K     /var/lib/scrollkeeper/yo
88K     /var/lib/scrollkeeper/zh_CN
76K     /var/lib/scrollkeeper/zh_TW
60K     /var/lib/scrollkeeper/zu
1.4M    /var/lib/scrollkeeper/TOC
1.4M    /var/lib/scrollkeeper/index
9.6M    /var/lib/scrollkeeper
152K    /var/lib/python-support/python2.5/apport
16K     /var/lib/python-support/python2.5/dbus/mainloop
136K    /var/lib/python-support/python2.5/dbus
24K     /var/lib/python-support/python2.5/gtk-2.0/bonobo
20K     /var/lib/python-support/python2.5/gtk-2.0/egg
20K     /var/lib/python-support/python2.5/gtk-2.0/gksu
36K     /var/lib/python-support/python2.5/gtk-2.0/gnome
20K     /var/lib/python-support/python2.5/gtk-2.0/gnomevfs
32K     /var/lib/python-support/python2.5/gtk-2.0/gobject
88K     /var/lib/python-support/python2.5/gtk-2.0/gtk
20K     /var/lib/python-support/python2.5/gtk-2.0/pynotify
336K    /var/lib/python-support/python2.5/gtk-2.0
88K     /var/lib/python-support/python2.5/invest
156K    /var/lib/python-support/python2.5/xdg
1.4M    /var/lib/python-support/python2.5
1.4M    /var/lib/python-support
8.0K    /var/lib/security
4.0K    /var/lib/sgml-base
1.3M    /var/lib/slocate
4.0K    /var/lib/snmp
4.0K    /var/lib/synaptic
8.0K    /var/lib/ucf/cache
28K     /var/lib/ucf
4.0K    /var/lib/update-manager
4.0K    /var/lib/update-notifier/user.d
8.0K    /var/lib/update-notifier
8.0K    /var/lib/urandom
4.0K    /var/lib/vim/addons
8.0K    /var/lib/vim
28K     /var/lib/x11
4.0K    /var/lib/xkb
32K     /var/lib/xml-core
142M    /var/lib
4.0K    /var/local
4.0K    /var/log/bittorrent
16K     /var/log/cups
4.0K    /var/log/dist-upgrade
12K     /var/log/fsck
24K     /var/log/gdm
4.0K    /var/log/news
4.0K    /var/log/samba
4.0K    /var/log/unattended-upgrades
740K    /var/log/installer
4.5M    /var/log
4.0K    /var/mail
4.0K    /var/opt
16K     /var/spool/anacron
8.0K    /var/spool/cron/atjobs
4.0K    /var/spool/cron/atspool
4.0K    /var/spool/cron/crontabs
20K     /var/spool/cron
4.0K    /var/spool/cups/tmp
8.0K    /var/spool/cups
4.0K    /var/spool/openoffice/uno_packages/cache
8.0K    /var/spool/openoffice/uno_packages
12K     /var/spool/openoffice
60K     /var/spool
4.0K    /var/tmp
182M    /var


Hope i did it right

---

### Post by kerrymorgan1 on 2007-08-17
> **taurus said:**
> What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
sudo du -h /var
```

> **heimo said:**
> Or even:
```

sudo du -sh /*
```

kerryandjane@KandJ-desktop:~$ sudo du -sh /
51G     /

---

### Post by taurus on 2007-08-17
I thought you said you set aside 50GB for Ubuntu but it's only 2.8GB!

```
/dev/sda5 [COLOR="Blue"]2.8G[/COLOR] 2.4G 230M 92% /
```

p.s.  By the way, the argument for the first command is lower case letter l as in larry, not number 1.

```
sudo fdisk -[COLOR="Blue"]l[/COLOR]
```

---

### Post by kerrymorgan1 on 2007-08-17
kerryandjane@KandJ-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
102 heads, 51 sectors/track, 187768 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      167893   436689667+   7  HPFS/NTFS
/dev/sda2          167894      169020     2931327    f  W95 Ext'd (LBA)
/dev/sda5          167894      169020     2931301+  83  Linux
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 465 MB, 465829888 bytes
227 heads, 6 sectors/track, 167 cylinders
Units = cylinders of 1362 * 2048 = 2789376 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         167      454896    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 6) logical=(0, 1, 1)


Really? 2G? you sure? is there anyway to make more without deleting what ive done on here?

---

### Post by kerrymorgan1 on 2007-08-17
umm do you think i loaded Linux on to my swap drive? haha and damb ..... Linux isn't for dummies huh?

is there a way that i can check the size of my swap drive?

---

### Post by taurus on 2007-08-17
Doesn't look like you have a swap partition either, just /!

If you want to reduce the space on /dev/sda1 and give it to /dev/sda5, you can try using GParted LiveCD and before you do that, better backup your data just in case.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by heimo on 2007-08-17
> **kerrymorgan1 said:**
> kerryandjane@KandJ-desktop:~$ sudo du -sh /
51G     /

You omitted asterisk * <-- from the end, just after slash /, without space between.

```
sudo du -sh /*
```

---

### Post by taurus on 2007-08-17
> **kerrymorgan1 said:**
> umm do you think i loaded Linux on to my swap drive? haha and damb ..... Linux isn't for dummies huh?

is there a way that i can check the size of my swap drive?

```
free
cat /etc/fstab
```

---

### Post by kerrymorgan1 on 2007-08-17
kerryandjane@KandJ-desktop:~$ sudo du -sh /*
5.7M    /bin
27M     /boot
0       /cdrom
112K    /dev
8.8M    /etc
44M     /home
4.0K    /initrd
0       /initrd.img
0       /initrd.img.old
278M    /lib
2.6M    /lib32
0       /lib64
48K     /lost+found
49G     /media
4.0K    /mnt
4.0K    /opt
0       /proc
124K    /root
6.9M    /sbin
4.0K    /srv
0       /sys
52K     /tmp
1.9G    /usr
182M    /var
0       /vmlinuz
0       /vmlinuz.old

---

### Post by kerrymorgan1 on 2007-08-17
> **taurus said:**
> ```
free
cat /etc/fstab
```

Mem:       2060536     842268    1218268          0      20824     395660
-/+ buffers/cache:     425784    1634752
Swap:            0          0          0

---

### Post by taurus on 2007-08-17
> **kerrymorgan1 said:**
> Mem:       2060536     842268    1218268          0      20824     395660
-/+ buffers/cache:     425784    1634752
**Swap:            0          0          0**

You have no swap at all.

---

### Post by kerrymorgan1 on 2007-08-17
why in the / properties would it say 53.1G used? is this is for my linux hard drive right?

---

### Post by kerrymorgan1 on 2007-08-17
> **taurus said:**
> You have no swap at all.

oh ........ still works fine though i followed someones instructions and it works loads and gives me the option to go on windows or Ubuntu

---

### Post by taurus on 2007-08-17
> **kerrymorgan1 said:**
> oh ........ still works fine though i followed someones instructions and it works loads and gives me the option to go on windows or Ubuntu

That's called bootloader, GRUB, not swap.

---

### Post by heimo on 2007-08-17
> **kerrymorgan1 said:**
> why in the / properties would it say 53.1G used? is this is for my linux hard drive right?

Most of that stuff is under /media - but your root partition itself (/), which contains also /var (which takes ~182MB) and /home (44MB), is just about 2.8GB, which is quite small. Most of your root partition space is taken by programs.

---

### Post by kerrymorgan1 on 2007-08-17
media? are you saying most of the 51G is taken by media? 
can i just go in the the folder and delete the whole folder?

---

### Post by kerrymorgan1 on 2007-08-17
for some reason SDA1 (my windows partition) is in the media drive? can i delete it?

---

### Post by heimo on 2007-08-17
> **kerrymorgan1 said:**
> for some reason SDA1 (my windows partition) is in the media drive? can i delete it?

You most probably don't want to do that. And it wouldn't make more space to your root partition anyway. Your only long term solution would be to resize root partition. There are tools to do that, I'm uncertain if the one on Live CD can do it in this situation. Partition Magic on Windows might. But what ever you do, you should backup your personal files before making any changes to partitioning.

---

