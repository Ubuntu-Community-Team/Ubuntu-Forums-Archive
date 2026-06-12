---
title: "Tiger"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-11-16
i got tiger earlier and done a scan to check my comuter, i have the out put below.

is any of it serious? 
or slowing me down?

```

TIGER System Security Scanner

Tiger security scripts *** 3.2.1, 2003.10.10.18.00 ***
HTML Generator developed by the Advanced Research Corporation (R)
Fri Nov 16 13:00:31 GMT 2007
13:00> Beginning security report for localhost (i686 Linux 2.6.22-14-generic).

# Performing check of passwd files...
# Checking entries from /etc/passwd.

# WARN [pass014w]Login (backup) is disabled, but has a valid shell.

# WARN [pass014w]Login (bin) is disabled, but has a valid shell.

# WARN [pass014w]Login (daemon) is disabled, but has a valid shell.

# WARN [pass014w]Login (games) is disabled, but has a valid shell.

# WARN [pass014w]Login (gnats) is disabled, but has a valid shell.

# WARN [pass014w]Login (irc) is disabled, but has a valid shell.

# WARN [pass014w]Login (list) is disabled, but has a valid shell.

# WARN [pass014w]Login (lp) is disabled, but has a valid shell.

# WARN [pass014w]Login (mail) is disabled, but has a valid shell.

# WARN [pass014w]Login (man) is disabled, but has a valid shell.

# WARN [pass014w]Login (news) is disabled, but has a valid shell.

# WARN [pass014w]Login (nobody) is disabled, but has a valid shell.

# WARN [pass014w]Login (proxy) is disabled, but has a valid shell.

# WARN [pass014w]Login (root) is disabled, but has a valid shell.

# WARN [pass015w]Login ID sshd does not have a valid shell (/usr/sbin/nologin).

# WARN [pass015w]Login ID sync does not have a valid shell (/bin/sync).

# WARN [pass014w]Login (sys) is disabled, but has a valid shell.

# WARN [pass014w]Login (test) is disabled, but has a valid shell.

# WARN [pass014w]Login (uucp) is disabled, but has a valid shell.

# WARN [pass014w]Login (www-data) is disabled, but has a valid shell.

# WARN [pass012w]Home directory /nonexistent exists multiple times (2) in /etc/passwd.

# WARN [pass006w]Integrity of password files questionable (/usr/sbin/pwck -r).

# Performing check of group files...

# Performing check of user accounts...
# Checking accounts from /etc/passwd.

# WARN [acc022w]Login ID avg home directory (/home/avg) is not accessible.

# WARN [acc006w]Login ID gdm's home directory (/var/lib/gdm) has group `gdm' write access.

# WARN [acc022w]Login ID nobody home directory (/nonexistent) is not accessible.

# Performing check of /etc/hosts.equiv and .rhosts files...

# Checking accounts from /etc/passwd...

# Performing check of .netrc files...

# Checking accounts from /etc/passwd...

# Performing common access checks for root (in /etc/default/login, /securetty, and /etc/ttytab...

# WARN [root003w]Root user has message capability turned on.

# WARN [root001w]Remote root login allowed in /etc/ssh/sshd_config

# Performing check of PATH components...

# WARN [path009w]/etc/profile does not export an initial setting for PATH.

# Only checking user 'root'

# WARN [path001w]/usr/bin/amsn in root's PATH from default is group `scott' writable.

# WARN [path002w]/usr/bin/amsn in root's PATH from default is not owned by root (owned by scott).

# WARN [path001w]/usr/bin/amsn-remote in root's PATH from default is group `scott' writable.

# WARN [path002w]/usr/bin/amsn-remote in root's PATH from default is not owned by root (owned by scott).

# WARN [path001w]/usr/bin/amsn-remote-CLI in root's PATH from default is group `scott' writable.

# WARN [path002w]/usr/bin/amsn-remote-CLI in root's PATH from default is not owned by root (owned by scott).

# WARN [path001w]/usr/bin/avgdmilter in root's PATH from default is group `avg' writable.

# WARN [path002w]/usr/bin/avgdmilter in root's PATH from default is not owned by root (owned by avg).

# WARN [path001w]/usr/bin/avgqrtctl in root's PATH from default is group `avg' writable.

# WARN [path002w]/usr/bin/avgqrtctl in root's PATH from default is not owned by root (owned by avg).

# WARN [path001w]/usr/bin/avgscan in root's PATH from default is group `avg' writable.

# WARN [path002w]/usr/bin/avgscan in root's PATH from default is not owned by root (owned by avg).

# WARN [path001w]/usr/bin/avgspmctl in root's PATH from default is group `avg' writable.

# WARN [path002w]/usr/bin/avgspmctl in root's PATH from default is not owned by root (owned by avg).

# WARN [path001w]/usr/bin/avgupdate in root's PATH from default is group `avg' writable.

# WARN [path002w]/usr/bin/avgupdate in root's PATH from default is not owned by root (owned by avg).

# Performing check of anonymous FTP...

# Performing checks of mail aliases...
# Checking aliases from /etc/aliases.

# Performing check of `cron' entries...

# WARN [cron005w]Use of cron is not restricted

# Performing check of 'inetd'...
# Checking inetd entries from /etc/inetd.conf

# Performing check of services with tcp wrappers...
# Analysing inetd entries from /etc/inetd.conf

# Performing check of 'services' ...
# Checking services from /etc/services.

# WARN [inet003w]The port for service postgres is also assigned to service postgresql.

# WARN [inet003w]The port for service postgres is also assigned to service postgresql.

# WARN [inet003w]The port for service sane is also assigned to service sane-port.

# Performing NFS exports check...

# Performing check of system file permissions...

# Checking for known intrusion signs...
# Testing for promiscuous interfaces with /bin/ip
# Testing for backdoors in inetd.conf

# Performing check of files in system mail spool...

# Performing check for rookits...

# Performing system specific checks...
# Performing checks for Linux/2...

# Checking for single user-mode password...

# Checking boot loader file permissions...

# WARN [boot02]The configuration file /boot/grub/menu.lst has group permissions. Should be 0600

# FAIL [boot02]The configuration file /boot/grub/menu.lst has world permissions. Should be 0600

# WARN [boot06]The Grub bootloader does not have a password configured.

# Checking for vulnerabilities in inittab configuration...

# Checking for correct umask settings for init scripts...

# WARN [misc021w]There are no umask entries in /etc/init.d/rcS

# Checking Logins not used on the system ...

# Checking network configuration

# WARN [lin012w]The system accepts ICMP redirection messages

# WARN [lin017w]The system is not configured to log suspicious (martian) packets

# Verifying system specific password checks...

# Checking OS release...

# WARN [osv004w]Unreleased Debian GNU/Linux version `lenny/sid'

# Checking installed packages vs Debian Security Advisories...

# Checking md5sums of installed files

# FAIL [lin005f]Installed file `/usr/share/envy/linux-restricted-modules-2.6.22.1/debian/nvidia-glx.links.amd64.in' checksum differs from installed package 'envy'.

# FAIL [lin005f]Installed file `/usr/share/envy/linux-restricted-modules-2.6.22.1/debian/control.stub.in' checksum differs from installed package 'envy'.

# FAIL [lin005f]Installed file `/usr/share/envy/linux-restricted-modules-2.6.22.1/debian/changelog' checksum differs from installed package 'envy'.

# FAIL [lin005f]Installed file `/usr/share/envy/linux-restricted-modules-2.6.22.1/debian/nvidia-glx-dev.links.in' checksum differs from installed package 'envy'.

# FAIL [lin005f]Installed file `/usr/share/envy/linux-restricted-modules-2.6.22.1/debian/control.stub' checksum differs from installed package 'envy'.

# FAIL [lin005f]Installed file `/usr/share/envy/linux-restricted-modules-2.6.22.1/debian/d-i/kernel-versions' checksum differs from installed package 'envy'.

# FAIL [lin005f]Installed file `/usr/share/envy/linux-restricted-modules-2.6.22.1/debian/rules' checksum differs from installed package 'envy'.

# FAIL [lin005f]Installed file `/usr/share/envy/linux-restricted-modules-2.6.22.1/debian/control' checksum differs from installed package 'envy'.

# FAIL [lin005f]Installed file `/usr/share/envy/linux-restricted-modules-2.6.22.1/debian/nvidia-glx.links.in' checksum differs from installed package 'envy'.

# FAIL [lin005f]Installed file `/usr/share/envy/linux-restricted-modules-2.6.22.1/nvidia/NVIDIA-Linux-x86-100.14.19-pkg1.run' checksum differs from installed package 'envy'.

# FAIL [lin005f]Installed file `/usr/share/envy/linux-restricted-modules-2.6.22.1/nvidia/debian.binary/control.template' checksum differs from installed package 'envy'.

# FAIL [lin005f]Installed file `/usr/share/envy/linux-restricted-modules-2.6.22.1/nvidia/debian.binary/changelog' checksum differs from installed package 'envy'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.22-14-generic/modules.pcimap' checksum differs from installed package 'linux-image-2.6.22-14-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.22-14-generic/modules.dep' checksum differs from installed package 'linux-image-2.6.22-14-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.22-14-generic/modules.ieee1394map' checksum differs from installed package 'linux-image-2.6.22-14-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.22-14-generic/modules.usbmap' checksum differs from installed package 'linux-image-2.6.22-14-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.22-14-generic/modules.isapnpmap' checksum differs from installed package 'linux-image-2.6.22-14-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.22-14-generic/modules.inputmap' checksum differs from installed package 'linux-image-2.6.22-14-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.22-14-generic/modules.seriomap' checksum differs from installed package 'linux-image-2.6.22-14-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.22-14-generic/modules.alias' checksum differs from installed package 'linux-image-2.6.22-14-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.22-14-generic/modules.symbols' checksum differs from installed package 'linux-image-2.6.22-14-generic'.

# FAIL [lin005f]Installed file `/sbin/loadndisdriver' checksum differs from installed package 'ndiswrapper-common'.

# FAIL [lin005f]Installed file `/usr/sbin/ndiswrapper' checksum differs from installed package 'ndiswrapper-common'.

# Checking installed files against packages...

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/fxusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/fwlanusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/fglrx.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/fcusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/fcpci.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/fcdslusba.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/fcdslusb2.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/fcdslusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/fcdslslusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/fcdslsl.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/fcdsl2.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/fcdsl.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/ath_hal.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-14-generic/volatile/.mounted' does not belong to any package.

# WARN [lin001w]File `/lib/linux-restricted-modules/.nvidia_new_installed' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_microcode5.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_pcm4.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_initval08.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_initval04.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_microcode2.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_microcode11.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_initval02.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_initval09.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_microcode4.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_initval03.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_initval10.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_initval06.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_microcode5.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_pcm4.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_initval08.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_initval04.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_microcode2.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_microcode11.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_initval02.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_initval09.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_microcode4.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_initval03.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_initval10.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_initval06.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_initval01.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_initval07.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_pcm5.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/2.6.22-14-generic/bcm43xx_initval05.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_initval01.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_initval07.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_pcm5.fw' does not belong to any package.

# WARN [lin001w]File `/lib/firmware/bcm43xx_initval05.fw' does not belong to any package.

# WARN [lin001w]File `/usr/sbin/ndiswrapper-buginfo' does not belong to any package.

# WARN [lin001w]File `/usr/bin/package' does not belong to any package.

# Performing check of root directory...

# Checking device permissions...

# FAIL [dev002f]/dev/log has world permissions

# FAIL [dev002f]/dev/nvidia0 has world permissions

# FAIL [dev002f]/dev/nvidiactl has world permissions

# WARN [dev003w]File /dev/sndstat is a regular file in a device directory.

# Checking for existence of log files...

# FAIL [logf005f]Log file /var/log/btmp permission should be 660

# Checking for correct umask settings...

# Checking listening processes 

# WARN [lin003w]The process `dhclient3' is listening on socket 68 (UDP on every interface) is run by dhcp.

# WARN [lin002i]The process `sshd' is listening on socket 2995 (TCP) on every interface.

# WARN [lin003w]The process `vino-server' is listening on socket 5900 (TCP on every interface) is run by scott.

# Checking sshd_config configuration files...

# WARN [ssh004w]The PasswordAuthentication directive in /etc/ssh/sshd_config is set to the unapproved defult value: yes.

# Checking printer configuration files...

# Performing common access checks for root...

# FAIL [netw020f]There is no /etc/ftpusers file.

# Checking ntpd configuration...

# Checking unusual file names...

# ALERT [fsys005a]Unusual filename `._Speed Freak 2.8.dmg' found:

-rw-r--r-- 1 scott scott 82 Jul  8 22:19 /home/scott/.Trash/sf28/__MACOSX/._Speed Freak 2.8.dmg


# Looking for unusual device files...

# ALERT [fsys006a]Unexpected device files found:

crw------- 1 root root 5, 1 Oct 16 00:18 /lib/udev/devices/console
crw-r----- 1 root kmem 1, 2 Oct 16 00:18 /lib/udev/devices/kmem
brw------- 1 root root 7, 0 Oct 16 00:18 /lib/udev/devices/loop0
crw------- 1 root root 10, 200 Oct 16 00:18 /lib/udev/devices/net/tun
crw------- 1 root root 1, 3 Oct 16 00:18 /lib/udev/devices/null
crw------- 1 root root 108, 0 Oct 16 00:18 /lib/udev/devices/ppp
lrwxrwxrwx 1 root root 15 Oct 18 23:00 /lib/udev/devices/stderr -> /proc/self/fd/2


# Checking symbolic links...
--WARN-- [xxxxx] The following files are unowned:
/opt
/opt/grisoft
/usr/lib/menu/avggui
/usr/share/applications/avggui.desktop
/usr/share/pixmaps/avgico_big.png
/var/lib/dpkg/info/avg75fld.conffiles
/var/lib/dpkg/info/avg75fld.postinst
/var/lib/dpkg/info/avg75fld.postrm
/var/lib/dpkg/info/avg75fld.preinst
/var/lib/dpkg/info/avg75fld.prerm


# Performing check of embedded pathnames...
13:07> Security report completed for localhost.

```

anything serious? or slowing me down?
thanks

---

### Post by skymera on 2007-11-16
anyone got ideas?

all the WARN signs dont seem good to me :(

---

