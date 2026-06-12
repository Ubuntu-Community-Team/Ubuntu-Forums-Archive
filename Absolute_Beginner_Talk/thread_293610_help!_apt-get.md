---
title: "help! apt-get"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by flajus on 2006-11-05
i dont understand i want to use "apt-get" command and then i get the error :
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened

please help me...

---

### Post by tronica on 2006-11-05
are you using "sudo apt-get" and also post your sources.list, maybe theres something wrong in ther.

> cat /etc/apt/sources.list

will give you the list

---

### Post by taurus on 2006-11-05
It means that probably another program's running in the background...  From a terminal, what is the output of this command?

```
ps -A
```

---

### Post by autocrosser on 2006-11-05
You need to be "root" to modify your system with apt-get--

Open a terminal and: sudo apt-get update

sudo apt-get upgrade

;)

---

### Post by flajus on 2006-11-12
> **tronica said:**
> are you using "sudo apt-get" and also post your sources.list, maybe theres something wrong in ther.



will give you the list

heres the list:
flajus@88:~$ cat /etc/apt/sources.list
#Atkomentuokite (istrinkite #) reikiamus saltinius (eilutes, prasidetancias deb)

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe mu ltiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

#Sifruotu DVD palaikymas (libdvdcss2 paketas), nuosavybiniai audio/video dekoder iai bei kiti multimedia paketai
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main              #Sifruotu DVD p alaikymas (libdvdcss2) ir kt

#Baltix GNU/Linux papildomu programu paketu saugykla.
#deb [ftp://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu_packages](ftp://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu_packages) breezy main    #Baltix paketu saugykla

#Lietuvisku debian paketu saugykla. Naudoti tik patyrusiems
#deb [ftp://debian.home.lt/debian](ftp://debian.home.lt/debian) unstable main contrib non-free              #Li etuvisku debian paketu saugykla

#Windows emuliatorius (WINE)
#deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) breezy/

# Source packages (deb-src) are needed only for developers and advanced users fo r compilation.
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe


deb [http://lt.archive.ubuntu.com/ubuntu/](http://lt.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://lt.archive.ubuntu.com/ubuntu/](http://lt.archive.ubuntu.com/ubuntu/) breezy main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe





and heres waht i get when i type ps -A :

flajus@88:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
    5 ?        00:00:00 kthread
    7 ?        00:00:00 kacpid
   79 ?        00:00:00 kblockd/0
  105 ?        00:00:00 pdflush
  106 ?        00:00:00 pdflush
  108 ?        00:00:00 aio/0
  107 ?        00:00:00 kswapd0
  693 ?        00:00:00 kseriod
 1804 ?        00:00:00 khubd
 2858 ?        00:00:00 kjournald
 2976 ?        00:00:00 udevd
 5027 ?        00:00:00 kgameportd
 5672 ?        00:00:00 dhclient3
 6047 ?        00:00:00 dd
 6049 ?        00:00:00 klogd
 6062 ?        00:00:00 dbus-daemon
 6075 ?        00:00:00 hald
 6080 ?        00:00:00 hald-addon-acpi
 6089 ?        00:00:04 hald-addon-stor
 6102 ?        00:00:00 PowerManager
 6416 ?        00:00:00 gdm
 6421 ?        00:00:00 gdm
 6479 ?        00:05:30 Xorg
 6544 ?        00:00:00 hpiod
 6554 ?        00:00:00 python
 6729 ?        00:00:06 nmbd
 6731 ?        00:00:00 smbd
 6756 ?        00:00:00 smbd
 6765 ?        00:00:00 hcid
 6771 ?        00:00:00 sdpd
 6781 ?        00:00:00 krfcommd
 6813 ?        00:00:00 atd
 6826 ?        00:00:00 cron
 6884 tty1     00:00:00 getty
 6885 tty2     00:00:00 getty
 6886 tty3     00:00:00 getty
 7077 ?        00:00:00 icewm-session
 7127 ?        00:00:00 ssh-agent
 7130 ?        00:00:00 dbus-daemon
 7131 ?        00:00:00 dbus-launch
 7132 ?        00:00:00 icewmbg
 7133 ?        00:00:04 icewm
 7134 ?        00:00:00 icewmtray
 7142 ?        00:06:26 firefox-bin
 7160 ?        00:00:00 gconfd-2
 7401 ?        00:00:00 acpid
 7434 ?        00:00:00 cupsd
 7562 ?        00:00:00 syslogd
 7756 ?        00:00:11 xchat
 7783 ?        00:00:00 screen
 7784 pts/1    00:00:00 bash
 7794 pts/1    00:02:34 skype
 7834 ?        00:00:04 nautilus
 7836 ?        00:00:00 gam_server
 7839 ?        00:00:00 bonobo-activati
 7841 ?        00:00:00 gnome-vfs-daemo
 7847 ?        00:00:00 mapping-daemon
 9424 ?        00:00:01 gnome-terminal
 9425 ?        00:00:00 gnome-pty-helpe
 9426 pts/0    00:00:00 bash
 9453 pts/0    00:00:00 ps


and heres what i type when i want to use apt-get:

flajus@88:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get:2 [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) breezy/main Packages
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) breezy/restricted Packages
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) breezy/main Sources
Hit [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) breezy/restricted Sources
Fetched 380B in 1s (342B/s)
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
flajus@88:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

---

