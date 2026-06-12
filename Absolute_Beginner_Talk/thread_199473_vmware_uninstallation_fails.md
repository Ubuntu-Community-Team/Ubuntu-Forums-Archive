---
title: "vmware uninstallation fails"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2006-06-18
Hello there! I've installed vmware player and regreted, now I can't uninstall it, the following error is shown, any ideas of how can I remove this package?

Regards

```

vinicius@cybertron:~$ sudo dpkg -r vmware-player
(Reading database ... 81485 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player

```

and the worst of all (that made me regret installing this software...) is that for every single package I have to install now I get this @#$@# message:

```

Probing for an unused private subnet (this might take some time...) [you damn bet it does]


```

and I need to confirm overrides for a lot of files on the damn VM etc files like dhcp and nat...

---

### Post by Kilz on 2006-06-18
[QUOTE=viniciuscarvalho]Hello there! I've installed vmware player and regreted, now I can't uninstall it, the following error is shown, any ideas of how can I remove this package?

Regards

```

vinicius@cybertron:~$ sudo dpkg -r vmware-player
(Reading database ... 81485 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player

```

and the worst of all (that made me regret installing this software...) is that for every single package I have to install now I get this @#$@# message:

```

Probing for an unused private subnet (this might take some time...) [you damn bet it does]


```

and I need to confirm overrides for a lot of files on the damn VM etc files like dhcp and nat...[/QUOTE]
Did you install it with apt/synaptic or the script from vmware?

---

### Post by viniciuscarvalho on 2006-06-19
[QUOTE=Kilz]Did you install it with apt/synaptic or the script from vmware?[/QUOTE]
I installed it using synaptic... :D

---

### Post by Kilz on 2006-06-19
[QUOTE=viniciuscarvalho]I installed it using synaptic... :D[/QUOTE]
I had problems similar to yours installing the player on my brothers computer. I got the install package [from vmware]("http://www.vmware.com/download/player/") and used that to install it, when it asked to set up networking I told it no. The error went away in synaptic after that. If you try it 
1. download the .tar installer 
2. untar it
3.open a terminal, navigate to the folder 
cd /path/to/folder
4. sudo ./vmware-install.pl
5. answer yes to overwrite a million times :) 
6. When it asks to setup networking type in no
7. If you make a mistake start over.

---

### Post by viniciuscarvalho on 2006-06-24
[QUOTE=Kilz]I had problems similar to yours installing the player on my brothers computer. I got the install package [from vmware]("http://www.vmware.com/download/player/") and used that to install it, when it asked to set up networking I told it no. The error went away in synaptic after that. If you try it 
1. download the .tar installer 
2. untar it
3.open a terminal, navigate to the folder 
cd /path/to/folder
4. sudo ./vmware-install.pl
5. answer yes to overwrite a million times :) 
6. When it asks to setup networking type in no
7. If you make a mistake start over.[/QUOTE]

I tried it, it complains about having another VMWare player installed on my machine. how can I get rid of this?

---

### Post by rhipwell on 2006-06-25
I've made a similar mistake - i install vmware server from the rpm using alien. I did not get any errors during the installation, however it will not properly launch. I am looking to remove the package from my computer now and dpkg and apt cannot find the package. I am unsure how I can locate all the files and purge them from my system. Anyone have any ideas?

---

### Post by wildkarde on 2006-08-14
I was having the same issue as you guys trying to uninstall

```
H:\>sudo apt-get remove vmware-player
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.0MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 152468 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is how i fixed it.  

```
H:\>ps -aux | grep vmware
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
root      4774  0.0  0.0   1684   632 ?        Ss   Aug06   0:08 /usr/bin/vmnet-natd -d /var/run/vmnet-natd-8.pid -m /var/run/vmnet-natd-8.mac -c /etc/vmware/vmnet8/nat/nat.conf
root     13398  0.0  0.0   1664   440 ?        Ss   10:32   0:00 /usr/bin/vmnet-natd -d /var/run/vmnet-natd-8.pid -m /var/run/vmnet-natd-8.mac -c /etc/vmware/vmnet8/nat/nat.conf
root     13407  0.0  0.0   1728   300 ?        Ss   10:32   0:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet1/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet1/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet1.pid vmnet1
root     13428  0.0  0.0   1724   300 ?        Ss   10:32   0:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet8/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet8/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet8.pid vmnet8
contarc  13606  0.0  0.0   2896   832 pts/7    S+   10:33   0:00 grep vmware
H:\>sudo sh
sh-3.1# kill -9 4774 13398 13407 13428
sh-3.1# ps -aux | grep vmware
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
root     14457  0.0  0.0   2888   816 pts/7    S+   10:37   0:00 grep vmware
sh-3.1# exit
exit
H:\>sudo apt-get remove vmware-player
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 32.0MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 152468 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done
***
* Updating MIME database in /usr/share/mime...
/usr/share/mime/packages/democracy.xml:21: parser error : XML declaration allowed only at the start of the document
<?xml version="1.0" encoding="UTF-8"?>
     ^

** (process:14711): WARNING **: Failed to parse '/usr/share/mime/packages/democracy.xml'

Wrote 476 strings at 20 - 2788
Wrote aliases at 2788 - 2934
Wrote parents at 2934 - 32e4
Wrote literal globs at 32e4 - 3340
Wrote suffix globs at 3340 - 6688
Wrote full globs at 6688 - 66ac
Wrote magic at 66ac - bcf8
Wrote namespace list at bcf8 - bd08
***
H:\>sudo apt-get remove vmware-player
Reading package lists... Done
Building dependency tree... Done
Package vmware-player is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
H:\>

```

Damn, should've used --purge.

---

### Post by wildkarde on 2006-08-14
Since I didnt use the --purge delimeter because i am actually trying to install the vmware free server, i had to reinstall.  

```
H:\>sudo apt-get install vmware-player
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  vmware-player-kernel-modules vmware-player-kernel-modules-2.6.15-26
The following NEW packages will be installed
  vmware-player vmware-player-kernel-modules vmware-player-kernel-modules-2.6.15-26
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.8MB/12.0MB of archives.
After unpacking 32.5MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get: 1 http://us.archive.ubuntu.com dapper/multiverse vmware-player 1.0.1-4 [11.8MB]
Fetched 11.8MB in 1m1s (194kB/s)
Preconfiguring packages ...
Selecting previously deselected package vmware-player-kernel-modules-2.6.15-26.
(Reading database ... 152009 files and directories currently installed.)
Unpacking vmware-player-kernel-modules-2.6.15-26 (from .../vmware-player-kernel-modules-2.6.15-26_2.6.15.10-9_i386.deb) ...
Selecting previously deselected package vmware-player-kernel-modules.
Unpacking vmware-player-kernel-modules (from .../vmware-player-kernel-modules_2.6.15.10-9_all.deb) ...
Selecting previously deselected package vmware-player.
Unpacking vmware-player (from .../vmware-player_1.0.1-4_i386.deb) ...
vmware-player-v1-0-1 license has already been accepted
Setting up vmware-player-kernel-modules-2.6.15-26 (2.6.15.10-9) ...

Setting up vmware-player-kernel-modules (2.6.15.10-9) ...
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.45.0/255.255.255.0 appears to be unused.

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.226.0/255.255.255.0 appears to be unused.

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
H:\>sudo apt-get --purge remove vmware-player
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  vmware-player*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.0MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 152427 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done
***
* Updating MIME database in /usr/share/mime...
/usr/share/mime/packages/democracy.xml:21: parser error : XML declaration allowed only at the start of the document
<?xml version="1.0" encoding="UTF-8"?>
     ^

** (process:20856): WARNING **: Failed to parse '/usr/share/mime/packages/democracy.xml'

Wrote 476 strings at 20 - 2788
Wrote aliases at 2788 - 2934
Wrote parents at 2934 - 32e4
Wrote literal globs at 32e4 - 3340
Wrote suffix globs at 3340 - 6688
Wrote full globs at 6688 - 66ac
Wrote magic at 66ac - bcf8
Wrote namespace list at bcf8 - bd08
***
Purging configuration files for vmware-player ...
***
* Updating MIME database in /usr/share/mime...
/usr/share/mime/packages/democracy.xml:21: parser error : XML declaration allowed only at the start of the document
<?xml version="1.0" encoding="UTF-8"?>
     ^

** (process:20881): WARNING **: Failed to parse '/usr/share/mime/packages/democracy.xml'

Wrote 476 strings at 20 - 2788
Wrote aliases at 2788 - 2934
Wrote parents at 2934 - 32e4
Wrote literal globs at 32e4 - 3340
Wrote suffix globs at 3340 - 6688
Wrote full globs at 6688 - 66ac
Wrote magic at 66ac - bcf8
Wrote namespace list at bcf8 - bd08
***
dpkg - warning: while removing vmware-player, directory `/var/run/vmware' not empty so not removed.
dpkg - warning: while removing vmware-player, directory `/etc/vmware' not empty so not removed.
H:\>cd /var/run/vmware
H:\>ls
contarc
H:\>cd contarc
H:\>ls
18105  4445
H:\>cd ..
H:\>ls
contarc
H:\>cd ..
H:\>ls
acpid.socket  Crack         cups               dhclient.eth1.pid   gdm.pid       hplip      network          sdp              syslogd.pid  vmnat.4774
atd.pid       crond.pid     dbus               dhclient.eth2.pid   hal           klogd      reboot-required  sudo             utmp         vmware
console       crond.reboot  dhclient.ath0.pid  dhclient.wlan0.pid  hotkey-setup  mdadm.pid  screen           synaptic.socket  vmnat.13398  xinetd.pid
H:\>sudo rm -rf vmware
H:\>sudo rm -rf /etc/vmware

```

Make sure to use the --purge if you're removing from apt.

---

