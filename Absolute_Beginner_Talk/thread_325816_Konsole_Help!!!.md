---
title: "Konsole Help!!!"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by independent8847 on 2006-12-26
i have been trying to use the sudo commands, but everytime i try to install something i get this message, 

"E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)."


Can anyone help me please?

---

### Post by taurus on 2006-12-26
Open a terminal and type

```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by independent8847 on 2006-12-26
i typed in the second command and this comes up

"E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

any help?

---

### Post by taurus on 2006-12-26
Any change you have synaptic running?  If not sure, what's the output of this command from a terminal?

```
ps -A
```

---

### Post by independent8847 on 2006-12-26
PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  154 ?        00:00:00 kseriod
  185 ?        00:00:00 pdflush
  186 ?        00:00:00 pdflush
  187 ?        00:00:00 kswapd0
  188 ?        00:00:00 aio/0
 1759 ?        00:00:00 khubd
 1826 ?        00:00:00 kjournald
 1882 ?        00:00:00 logd
 2035 ?        00:00:00 udevd
 2731 ?        00:00:00 shpchpd
 2765 ?        00:00:00 irda_sir_wq
 2835 ?        00:00:00 pccardd
 2866 ?        00:00:00 pccardd
 2879 ?        00:00:00 kpsmoused
 3172 ?        00:00:00 dhclient3
 3215 ?        00:00:00 dhclient3
 3703 tty1     00:00:00 getty
 3704 tty2     00:00:00 getty
 3705 tty3     00:00:00 getty
 3710 tty4     00:00:00 getty
 3711 tty5     00:00:00 getty
 3712 tty6     00:00:00 getty
 3935 ?        00:00:00 acpid
 4026 ?        00:00:00 syslogd
 4052 ?        00:00:00 dd
 4054 ?        00:00:00 klogd
 4067 ?        00:00:00 kdm
 4083 tty7     00:04:01 Xorg
 4097 ?        00:00:00 kdm
 4100 ?        00:00:00 cupsd
 4131 ?        00:00:00 hpiod
 4136 ?        00:00:00 python
 4181 ?        00:00:00 apt-index-watch
 4236 ?        00:00:00 freshclam
 4252 ?        00:00:02 dbus-daemon
 4267 ?        00:00:06 hald
 4269 ?        00:00:00 hald-runner
 4275 ?        00:00:00 hald-addon-acpi
 4278 ?        00:00:00 hald-addon-keyb
 4302 ?        00:00:00 hald-addon-stor
 4340 ?        00:00:00 ondemand
 4385 ?        00:00:00 hcid
 4391 ?        00:00:00 sdpd
 4403 ?        00:00:00 krfcommd
 4436 ?        00:00:00 atd
 4449 ?        00:00:00 cron
 4557 ?        00:00:00 x-session-manag
 4596 ?        00:00:00 ssh-agent
 4599 ?        00:00:00 dbus-launch
 4600 ?        00:00:00 dbus-daemon
 4634 ?        00:00:00 start_kdeinit
 4635 ?        00:00:00 kdeinit
 4638 ?        00:00:01 dcopserver
 4641 ?        00:00:00 klauncher
 4643 ?        00:00:04 kded
 4649 ?        00:00:00 kwrapper
 4651 ?        00:00:00 ksmserver
 4652 ?        00:00:08 kwin
 4654 ?        00:00:08 kdesktop
 4656 ?        00:00:25 kicker
 4660 ?        00:00:00 kio_uiserver
 4675 ?        00:00:07 artsd
 4679 ?        00:00:00 kaccess
 4684 ?        00:00:00 kmix
 4685 ?        00:00:01 katapult
 4692 ?        00:00:00 aspell
 4695 ?        00:01:23 amarokapp
 4697 ?        00:00:00 guidance-power-
 4700 ?        00:00:00 knotify
 4701 ?        00:00:00 passkey-agent
 4704 ?        00:00:00 kbluetoothd
 4706 ?        00:00:00 klipper
 4710 ?        00:00:11 guidance-power-
 4726 ?        00:00:00 ruby
 4752 ?        00:05:22 firefox-bin
 4761 ?        00:00:00 gconfd-2
 4772 ?        00:00:00 netstat <defunct>
 5023 ?        00:01:05 kopete
 5039 ?        00:00:00 kwalletmanager
 5086 ?        00:00:05 konqueror
 5347 ?        00:00:00 scsi_eh_0
 5348 ?        00:00:00 usb-storage
 5377 ?        00:00:00 hald-addon-stor
 5415 ?        00:00:00 kjournald
 5421 ?        00:00:00 kio_file
 5448 ?        00:00:00 amarokapp
 5463 ?        00:00:02 konsole
 5464 pts/1    00:00:00 bash
 5480 pts/1    00:00:01 apt-get
 5506 pts/1    00:00:00 dpkg
 5512 pts/1    00:00:00 frontend
 5519 pts/1    00:00:00 preinst
 5521 pts/1    00:00:00 whiptail
 5522 pts/2    00:00:00 bash
 5608 pts/3    00:00:00 bash
 5624 pts/3    00:00:00 ps

---

### Post by independent8847 on 2006-12-26
anything?

---

### Post by taurus on 2006-12-26
Here's one!!!

```
5480 pts/1 00:00:01 apt-get
```
Do you have apt-get running from another terminal or something?

---

### Post by independent8847 on 2006-12-26
no all i have running right now is kopete, firefox, and konsole

---

### Post by taurus on 2006-12-26
Then, you need to kill that process so type these from a terminal.

```
sudo kill -9 5480
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by independent8847 on 2006-12-26
Password:
john@john-laptop:~$ sudo aptitude update
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release

Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Get:4 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release [5161B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources
Fetched 5355B in 1s (2678B/s)
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

---

### Post by taurus on 2006-12-26
Looks to me like you've mixed **dapper** with **edgy** repos in your /etc/apt/sources.list!!!  Paste the output of your /etc/apt/sources.list here then...

```
cat /etc/apt/sources.list
```

---

### Post by independent8847 on 2006-12-26
## Add comments (##) in front of any line to remove it from being checked. 
 ## Use the following sources.list at your own risk. 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

 ## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

 ## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

 ## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiversedeb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by independent8847 on 2006-12-26
i have no idea what to do now

---

### Post by taurus on 2006-12-26
The last patch of your repos look kind of :confused:!!!

```

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://www.getautomatix.com/apt dapper main

```
Therefore, you need to edit /etc/apt/sources.list and make the lines from above to look like these...

Edit:
```
kdesu kate /etc/apt/sources.list
```

```

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://www.getautomatix.com/apt edgy main

```
Then, you need to import the key for automatix...

```

wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
sudo aptitude update
sudo aptitude upgrade

```

---

### Post by independent8847 on 2006-12-26
when i insert the first line into konsole, it reads as

"john@john-laptop:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--15:00:02--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... failed: Connection refused."

anything?

---

### Post by TooRight on 2006-12-26
The site seems to be down :( , you'll have to try again later

---

### Post by taurus on 2006-12-26
> **TooRight said:**
> The site seems to be down :( , you'll have to try again later

Yes, the site is currently down so you can either wait until later (or even tomorrow) or just put a # in front of it in /etc/apt/sources.list to comment it out...

---

### Post by independent8847 on 2006-12-26
damn alright thanks for the help

---

### Post by independent8847 on 2006-12-26
are you ure that the site will be back up by tomorrow?

---

### Post by independent8847 on 2006-12-26
i tried to get the update cause the site was back up and this is what happens...




john@john-laptop:~$ sudo aptitude update
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 6B in 3s (2B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

---

### Post by taurus on 2006-12-26
Do you have something else like synaptic that's running in the background?

```
ps -A
```

---

### Post by independent8847 on 2006-12-26
can anyone fix this lock thing?

---

### Post by independent8847 on 2006-12-26
no all thats running is kopete and firefox

---

### Post by independent8847 on 2006-12-26
john@john-laptop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  154 ?        00:00:00 kseriod
  185 ?        00:00:00 pdflush
  186 ?        00:00:00 pdflush
  187 ?        00:00:00 kswapd0
  188 ?        00:00:00 aio/0
 1759 ?        00:00:00 khubd
 1826 ?        00:00:00 kjournald
 1882 ?        00:00:00 logd
 2035 ?        00:00:00 udevd
 2731 ?        00:00:00 shpchpd
 2765 ?        00:00:00 irda_sir_wq
 2835 ?        00:00:00 pccardd
 2866 ?        00:00:00 pccardd
 2879 ?        00:00:00 kpsmoused
 3172 ?        00:00:00 dhclient3
 3215 ?        00:00:00 dhclient3
 3703 tty1     00:00:00 getty
 3704 tty2     00:00:00 getty
 3705 tty3     00:00:00 getty
 3710 tty4     00:00:00 getty
 3711 tty5     00:00:00 getty
 3712 tty6     00:00:00 getty
 3935 ?        00:00:00 acpid
 4026 ?        00:00:00 syslogd
 4052 ?        00:00:00 dd
 4054 ?        00:00:00 klogd
 4067 ?        00:00:00 kdm
 4083 tty7     00:10:18 Xorg
 4097 ?        00:00:00 kdm
 4100 ?        00:00:00 cupsd
 4131 ?        00:00:00 hpiod
 4136 ?        00:00:00 python
 4181 ?        00:00:00 apt-index-watch
 4236 ?        00:00:00 freshclam
 4252 ?        00:00:07 dbus-daemon
 4267 ?        00:00:11 hald
 4269 ?        00:00:00 hald-runner
 4275 ?        00:00:00 hald-addon-acpi
 4278 ?        00:00:00 hald-addon-keyb
 4302 ?        00:00:03 hald-addon-stor
 4340 ?        00:00:00 ondemand
 4385 ?        00:00:00 hcid
 4391 ?        00:00:00 sdpd
 4403 ?        00:00:00 krfcommd
 4436 ?        00:00:00 atd
 4449 ?        00:00:00 cron
 4557 ?        00:00:00 x-session-manag
 4596 ?        00:00:00 ssh-agent
 4599 ?        00:00:00 dbus-launch
 4600 ?        00:00:00 dbus-daemon
 4634 ?        00:00:00 start_kdeinit
 4635 ?        00:00:00 kdeinit
 4638 ?        00:00:01 dcopserver
 4641 ?        00:00:00 klauncher
 4643 ?        00:00:07 kded
 4649 ?        00:00:00 kwrapper
 4651 ?        00:00:00 ksmserver
 4652 ?        00:00:15 kwin
 4654 ?        00:00:11 kdesktop
 4656 ?        00:00:35 kicker
 4660 ?        00:00:00 kio_uiserver
 4675 ?        00:00:12 artsd
 4679 ?        00:00:01 kaccess
 4684 ?        00:00:01 kmix
 4685 ?        00:00:01 katapult
 4692 ?        00:00:00 aspell
 4697 ?        00:00:00 guidance-power-
 4700 ?        00:00:01 knotify
 4701 ?        00:00:00 passkey-agent
 4704 ?        00:00:00 kbluetoothd
 4706 ?        00:00:01 klipper
 4710 ?        00:00:28 guidance-power-
 4752 ?        00:13:43 firefox-bin
 4761 ?        00:00:00 gconfd-2
 4772 ?        00:00:00 netstat <defunct>
 5023 ?        00:04:02 kopete
 5039 ?        00:00:00 kwalletmanager
 5086 ?        00:00:05 konqueror
 5506 ?        00:00:00 dpkg
 5512 ?        00:00:00 frontend
 5519 ?        00:00:00 preinst
 5521 ?        02:55:10 whiptail
 5648 ?        00:00:00 kio_file
 6048 ?        00:00:00 kdesud
 6064 ?        00:00:00 kdeinit
 6069 ?        00:00:00 dcopserver
 6072 ?        00:00:00 klauncher
 6074 ?        00:00:00 kded
 6079 ?        00:00:00 kio_file
 6082 ?        00:00:00 kio_uiserver
 6506 ?        00:00:01 konsole
 6507 pts/2    00:00:00 bash
 6532 pts/2    00:00:00 ps

---

### Post by taurus on 2006-12-26
```
**5506 ? 00:00:00 dpkg**
```

```
sudo kill -9 5506
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by independent8847 on 2006-12-26
john@john-laptop:~$ sudo kill -9 5506
john@john-laptop:~$ sudo aptitude update
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources
Get:6 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Fetched 6B in 3s (2B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: Couldn't rebuild package cache

---

### Post by taurus on 2006-12-26
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by independent8847 on 2006-12-26
i think everything is fine like as in no errors but this is what i got after the update...


"john@john-laptop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  zenity
The following packages will be upgraded:
  sun-java5-bin sun-java5-jre
2 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/29.8MB of archives. After unpacking 83.2MB will be used.
Do you want to continue? [Y/n/?] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
(Reading database ...
dpkg: serious warning: files list file for package `sun-java5-bin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `sun-java5-jre' missing, assuming package has no files currently installed.
84152 files and directories currently installed.)
Preparing to replace sun-java5-bin 1.5.0-08-0ubuntu1 (using .../sun-java5-bin_1.5.0-08-0ubuntu1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing /var/cache/apt/archives/sun-java5-bin_1.5.0-08-0ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Preparing to replace sun-java5-jre 1.5.0-08-0ubuntu1 (using .../sun-java5-jre_1.5.0-08-0ubuntu1_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-08-0ubuntu1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
***
* Updating MIME database in /usr/share/mime...
Wrote 477 strings at 20 - 2790
Wrote aliases at 2790 - 2944
Wrote parents at 2944 - 32f4
Wrote literal globs at 32f4 - 3350
Wrote suffix globs at 3350 - 6648
Wrote full globs at 6648 - 666c
Wrote magic at 666c - bc7c
Wrote namespace list at bc7c - bc8c
***
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java5-bin_1.5.0-08-0ubuntu1_i386.deb
 /var/cache/apt/archives/sun-java5-jre_1.5.0-08-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
john@john-laptop:~$

---

### Post by Frak on 2006-12-26
After reinstalling Kubuntu, I've run across something that gave me an error just like yours, hopefully exact.

My tip - make sure that Adept Updater isn't running in the system tray, if it is, right click->quit.

I don't know if that will help, but hey, you never know! Good luck mate!

---

### Post by taurus on 2006-12-26
Were you trying to install Sun's java and somehow stopped it before it completed?

---

### Post by independent8847 on 2006-12-26
yea im trying to install sunjava for my limewire.. i got limewire in my internet folder but i click on it and it tries to load but doesnt.  im guessing i have to update my java but idk how i like cant

---

### Post by taurus on 2006-12-26
The easiest way to install Sun's java is to use automatix2.

---

### Post by independent8847 on 2006-12-26
like in adept updater i try to install it and i click apply changes and i get an error message as like an error in the software download or something

---

### Post by independent8847 on 2006-12-26
can you tell me how to get that like a command please

---

### Post by Frak on 2006-12-26
sudo aptitude install automatix2,
but follow the instructions on [http://getautomatix.com](http://getautomatix.com) before you do anything.

---

### Post by independent8847 on 2006-12-26
i installed automatix2 and everytime i try to run it, it says 

DPKG is running

please close dpkg and restart automatix

any halp??:-k

---

### Post by taurus on 2006-12-26
> **independent8847 said:**
> i installed automatix2 and everytime i try to run it, it says 

DPKG is running

please close dpkg and restart automatix

any halp??:-k
Sounds like you have dpkg running in the background again like you did before!!!  Therefore, you need to kill it again before you start automatix2...

```
ps -A
```

---

### Post by independent8847 on 2006-12-26
i tried looking for it using that code and it didnt work

but ill see what i get

---

### Post by independent8847 on 2006-12-26
PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  154 ?        00:00:00 kseriod
  185 ?        00:00:00 pdflush
  186 ?        00:00:00 pdflush
  187 ?        00:00:00 kswapd0
  188 ?        00:00:00 aio/0
 1759 ?        00:00:00 khubd
 1826 ?        00:00:01 kjournald
 1882 ?        00:00:00 logd
 2035 ?        00:00:00 udevd
 2731 ?        00:00:00 shpchpd
 2765 ?        00:00:00 irda_sir_wq
 2835 ?        00:00:00 pccardd
 2866 ?        00:00:00 pccardd
 2879 ?        00:00:00 kpsmoused
 3172 ?        00:00:00 dhclient3
 3215 ?        00:00:00 dhclient3
 3703 tty1     00:00:00 getty
 3704 tty2     00:00:00 getty
 3705 tty3     00:00:00 getty
 3710 tty4     00:00:00 getty
 3711 tty5     00:00:00 getty
 3712 tty6     00:00:00 getty
 3935 ?        00:00:00 acpid
 4026 ?        00:00:00 syslogd
 4052 ?        00:00:00 dd
 4054 ?        00:00:00 klogd
 4067 ?        00:00:00 kdm
 4100 ?        00:00:00 cupsd
 4131 ?        00:00:00 hpiod
 4136 ?        00:00:00 python
 4181 ?        00:00:00 apt-index-watch
 4236 ?        00:00:00 freshclam
 4252 ?        00:00:12 dbus-daemon
 4267 ?        00:00:14 hald
 4269 ?        00:00:00 hald-runner
 4275 ?        00:00:00 hald-addon-acpi
 4278 ?        00:00:00 hald-addon-keyb
 4302 ?        00:00:05 hald-addon-stor
 4340 ?        00:00:00 ondemand
 4385 ?        00:00:00 hcid
 4391 ?        00:00:00 sdpd
 4403 ?        00:00:00 krfcommd
 4436 ?        00:00:00 atd
 4449 ?        00:00:00 cron
 5512 ?        00:00:00 frontend
 5519 ?        00:00:00 preinst
 5521 ?        05:48:34 whiptail
 9828 ?        00:00:00 dhclient
10511 tty7     00:00:34 Xorg
10512 ?        00:00:00 kdm
10526 ?        00:00:00 x-session-manag
10565 ?        00:00:00 ssh-agent
10568 ?        00:00:00 dbus-launch
10569 ?        00:00:00 dbus-daemon
10603 ?        00:00:00 start_kdeinit
10604 ?        00:00:00 kdeinit
10607 ?        00:00:00 dcopserver
10610 ?        00:00:00 klauncher
10612 ?        00:00:01 kded
10618 ?        00:00:00 kwrapper
10620 ?        00:00:00 ksmserver
10621 ?        00:00:01 kwin
10623 ?        00:00:02 kdesktop
10625 ?        00:00:03 kicker
10627 ?        00:00:00 kio_file
10629 ?        00:00:00 kio_uiserver
10645 ?        00:00:01 artsd
10649 ?        00:00:00 kaccess
10653 ?        00:00:00 kmix
10654 ?        00:00:00 katapult
10661 ?        00:00:00 aspell
10665 ?        00:00:08 amarokapp
10667 ?        00:00:00 guidance-power-
10669 ?        00:00:00 passkey-agent
10673 ?        00:00:02 guidance-power-
10674 ?        00:00:00 kbluetoothd
10676 ?        00:00:00 knotify
10677 ?        00:00:00 klipper
10696 ?        00:00:00 ruby
10709 ?        00:00:00 automatix2
10712 ?        00:00:00 kdesu
10714 ?        00:00:00 kdesud
10717 pts/2    00:00:00 kdesu_stub
10720 pts/3    00:00:00 sudo
10721 ?        00:00:00 automatix2
10724 ?        00:00:00 kdesu
10727 pts/4    00:00:00 kdesu_stub
10730 pts/5    00:00:00 sudo
10816 ?        00:00:49 firefox-bin
10825 ?        00:00:00 gconfd-2
10840 ?        00:00:00 netstat <defunct>
11051 ?        00:00:00 konsole
11052 pts/6    00:00:00 bash
11068 pts/6    00:00:00 ps

---

### Post by taurus on 2006-12-26
You can't have two copies of automatix2 running at the same time...

```
10709 ? 00:00:00 automatix2
10721 ? 00:00:00 automatix2
```
Therefore, you need to quit one of them and use the other only!

---

### Post by independent8847 on 2006-12-26
ok so i quit one and tried and the same thing happened, so then i dod the other one and the same thing happens...? what now?

---

### Post by taurus on 2006-12-26
Why don't you quit it and reboot.  Then, start only one session of automatix2 (and NO synaptic, adept, apt-get, nor aptitude).

---

### Post by d3v1ant_0n3 on 2006-12-26
I started reading this thread, and can I say it's one of the best examples of 'How to help someone out in Beginner's ' I've seen. Can see why you're a mod, Taurus.

btw, is it as cold there as it is down in Vero tonite? It's farking FREEZING.

---

### Post by taurus on 2006-12-26
> **d3v1ant_0n3 said:**
> 
btw, is it as cold there as it is down in Vero tonite? It's farking FREEZING.

It's already 45F (with some winds) and will be around the freezing mark tonight (or early tomorrow morning) so need to put on a pair of socks when I go to bed tonight...  ](*,)

---

### Post by independent8847 on 2006-12-26
niceeeeeeeeeee thanks you soooo much my frostwire works like a charm:)

---

### Post by taurus on 2006-12-26
> **independent8847 said:**
> niceeeeeeeeeee thanks you soooo much my frostwire works like a charm:)

Glad to hear that you've finally got it to work.  Remember, you can only run one at a time:  automatix2, synaptic, adept, apt-get, aptitude...

---

### Post by Frak on 2006-12-26
Just in case, as many have had this problem with fresh installations of FW:
 
 [http://ubuntuforums.org/showthread.p...ire+to+connect](http://ubuntuforums.org/showthread.p...ire+to+connect)
 
 Just in case. ;)

---

