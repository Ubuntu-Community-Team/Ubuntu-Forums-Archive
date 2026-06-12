---
title: "can't share folders at all, and a wierd sftp in network"
date: 2008-06-30
forum: Arch and derivatives
---

### Post by savagenator on 2008-06-30
hello all

i have a series of problem i am hoping you can help me with. I am using gnome:

1. I can't share folders with other computers on my network anymore using nfs and the tools gnome comes with, i have before.

2. When i click networks under places, it does not pop up unless i type "nautilus network:" in the terminal then click it afterwords. It pops up as many times as i had clicked it.

3. I have a thing called "SFTP File Transfer on linux" that gives the error "unable to mount location Connection refused by server"

Please help. I have a feeling it is one of the daemons running in the backround. 

Here is my rc.conf:
```
#
# /etc/rc.conf - Main Configuration for Arch Linux
#

# -----------------------------------------------------------------------
# LOCALIZATION
# -----------------------------------------------------------------------
#
# LOCALE: available languages can be listed with the 'locale -a' command
# HARDWARECLOCK: set to "UTC" or "localtime"
# USEDIRECTISA: use direct I/O requests instead of /dev/rtc for hwclock
# TIMEZONE: timezones are found in /usr/share/zoneinfo
# KEYMAP: keymaps are found in /usr/share/kbd/keymaps
# CONSOLEFONT: found in /usr/share/kbd/consolefonts (only needed for non-US)
# CONSOLEMAP: found in /usr/share/kbd/consoletrans
# USECOLOR: use ANSI color sequences in startup messages
#
LOCALE="en_US.utf8"
HARDWARECLOCK="localtime"
USEDIRECTISA="yes"
TIMEZONE="Canada/Pacific"
KEYMAP="us"
CONSOLEFONT=
CONSOLEMAP=
USECOLOR="yes"

# -----------------------------------------------------------------------
# HARDWARE
# -----------------------------------------------------------------------
#
# MOD_AUTOLOAD: Allow autoloading of modules at boot and when needed
# MOD_BLACKLIST: Prevent udev from loading these modules
# MODULES: Modules to load at boot-up. Prefix with a ! to blacklist.
#
# NOTE: Use of 'MOD_BLACKLIST' is deprecated. Please use ! in the MODULES array.
#
MOD_AUTOLOAD="yes"
#MOD_BLACKLIST=() #deprecated
MODULES=(powernow-k8 cpufreq_ondemand 3c59x forcedeth mii slhc ac97_bus snd-mixer-oss snd-pcm-oss snd-page-alloc snd-pcm snd-timer snd snd-ac97-codec snd-intel8x0 soundcore fuse)

# Scan for LVM volume groups at startup, required if you use LVM
USELVM="no"

# -----------------------------------------------------------------------
# NETWORKING
# -----------------------------------------------------------------------
#
# HOSTNAME: Hostname of machine. Should also be put in /etc/hosts
#*changed from myhost
HOSTNAME="localhost"

# Use 'ifconfig -a' or 'ls /sys/class/net/' to see all available interfaces.
#
# Interfaces to start at boot-up (in this order)
# Declare each interface then list in INTERFACES
#   - prefix an entry in INTERFACES with a ! to disable it
#   - no hyphens in your interface names - Bash doesn't like it
# 
# DHCP:     Set your interface to "dhcp" (eth0="dhcp")
# Wireless: See network profiles below
#
#eth0="eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255"
eth0="dhcp"
INTERFACES=(eth0)

# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
gateway="default gw 192.168.1.1"
ROUTES=(!gateway)
 
# Enable these network profiles at boot-up.  These are only useful
# if you happen to need multiple network configurations (ie, laptop users)
#   - set to 'menu' to present a menu during boot-up (dialog package required)
#   - prefix an entry with a ! to disable it
#
# Network profiles are found in /etc/network.d
#
# This now requires the netcfg package
#
#NETWORKS=(main)

# -----------------------------------------------------------------------
# DAEMONS
# -----------------------------------------------------------------------
#
# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#
DAEMONS=(syslog-ng network netfs crond hal fam !cpufreq gdm preload clamav avahi-daemon avahi-dnsconfd alsa pulseaudio stbd !mpd httpd mysqld dbus portmap samba nfslock nfsd !dhcdbd !networkmanager)
```

and just the daemons by themselves:
DAEMONS=(syslog-ng network netfs crond hal fam !cpufreq gdm preload clamav avahi-daemon avahi-dnsconfd alsa pulseaudio stbd !mpd httpd mysqld dbus portmap samba nfslock nfsd !dhcdbd !networkmanager)

Thank you!

---

### Post by savagenator on 2008-07-01
I am going to conclude that this is a gnome-system-tools problem, since I am using shares-admin to share folders, but it is not working.

Any help with that information?

also i get the error " Unknown property: GtkComboBox.items" when i run it in terminal. When i click properties in gnome-nettools for my connection, it gives an error that the interface cannot exist.

---

### Post by ruffEdgz on 2008-07-01
**1. I can't share folders with other computers on my network anymore using nfs and the tools gnome comes with, i have before.**
~ Do you remember what you have done in the past that might have changed this. I don't think it would just stop working out of nowhere.

**2. When i click networks under places, it does not pop up unless i type "nautilus network:" in the terminal then click it afterwords. It pops up as many times as i had clicked it.**
~ I don't know about this one because I don't use it that much. I know for my computer that it does sometimes come up slowly so it could be trying to load it. When you load up arch for the firs time, do you see the process running (go to your terminal and type: "ps -ely | grep nau")

**3. I have a thing called "SFTP File Transfer on linux" that gives the error "unable to mount location Connection refused by server"**
~ I had this problem happening when I was trying to go from a RHEL server to my computer using scp. I found that I needed my 'sshd' on and to configure my /etc/ssh/ssh_config and /etc/ssh/sshd_config to fit what I wanted. I used the tutorial below to help me out:

[http://wiki.archlinux.org/index.php/SSH#Configuring_the_SSH_server](http://wiki.archlinux.org/index.php/SSH#Configuring_the_SSH_server)

Hope this helps :D

---

### Post by savagenator on 2008-07-01
> **ruffEdgz said:**
> **1. I can't share folders with other computers on my network anymore using nfs and the tools gnome comes with, i have before.**
~ Do you remember what you have done in the past that might have changed this. I don't think it would just stop working out of nowhere.

**2. When i click networks under places, it does not pop up unless i type "nautilus network:" in the terminal then click it afterwords. It pops up as many times as i had clicked it.**
~ I don't know about this one because I don't use it that much. I know for my computer that it does sometimes come up slowly so it could be trying to load it. When you load up arch for the firs time, do you see the process running (go to your terminal and type: "ps -ely | grep nau")

**3. I have a thing called "SFTP File Transfer on linux" that gives the error "unable to mount location Connection refused by server"**
~ I had this problem happening when I was trying to go from a RHEL server to my computer using scp. I found that I needed my 'sshd' on and to configure my /etc/ssh/ssh_config and /etc/ssh/sshd_config to fit what I wanted. I used the tutorial below to help me out:

[http://wiki.archlinux.org/index.php/SSH#Configuring_the_SSH_server](http://wiki.archlinux.org/index.php/SSH#Configuring_the_SSH_server)

Hope this helps :D

Thank you for your response.

The ssh helped me, i can now sftp into my computer :) 

but i still cannot make a windows share from the same computer. That is the whole problem. 

New developement: 
DAEMONS=(syslog-ng network hal !dhcdbd !networkmanager crond fam dbus !cpufreq gdm preload clamav avahi-daemon avahi-dnsconfd alsa pulseaudio stbd sshd !mpd httpd mysqld portmap !samba nfslock nfsd !netfs !smbnetfs )

still doesn't work

---

### Post by ruffEdgz on 2008-07-01
> 
New developement:
DAEMONS=(syslog-ng network hal !dhcdbd !networkmanager crond fam dbus !cpufreq gdm preload clamav avahi-daemon avahi-dnsconfd alsa pulseaudio stbd sshd !mpd httpd mysqld portmap !samba nfslock nfsd !netfs !smbnetfs )


What do you mean this doesn't work?? From what I see, it seems that dhcdbd, networkmanager, cpufreq, samba, mpd, netfs and smbnetfs don't run when the OS starts. The ! means they won't run at all unless you manually run them. So maybe the reason you can't share is because a daemon isn't running (I know samba is used for the windows part of sharing)

Please explain a bit more if you can :D

---

### Post by savagenator on 2008-07-02
thank you so much! I just started samba and it worked!

actually that was very stupid of me. I assumed i did not need samba to be up to do this.

thank you!

---

### Post by ruffEdgz on 2008-07-02
> **savagenator said:**
> thank you so much! I just started samba and it worked!

actually that was very stupid of me. I assumed i did not need samba to be up to do this.

thank you!

Glad to help :D

Resolved

---

