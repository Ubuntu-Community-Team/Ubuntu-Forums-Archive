---
title: "Problem updating openssh-server"
date: 2014-09-15
forum: Any Other OS
---

### Post by shay2 on 2014-09-15
[COLOR=#000000][FONT=Tahoma]Hi all,[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]I am not a linux expert so please bare with me [/FONT][/COLOR][IMG]http://forum.xbian.org/images/smilies/blush.gif[/IMG]

[COLOR=#000000][FONT=Tahoma]Getting the following error while trying to update packages on xbian RC-3:

[/FONT][/COLOR][TABLE="class: tborder, width: 1596"]
[TR]
[TD="class: trow2 post_content"]xbian@xbian /etc/sysctl.d $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
libhal-storage1 libhal1 ufsutils update-notifier-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
openssh-server
Suggested packages:
ssh-askpass rssh molly-guard ufw monkeysphere
Recommended packages:
xauth
The following packages will be upgraded:
openssh-server
1 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
6 not fully installed or removed.
Need to get 0 B/316 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Create a snapshot of '/tmp/btrfs-snap/root/@' in '/tmp/btrfs-snap/root/@btrfs-auto-snap_apt-run-2014-09-09-0528'
Transaction commit: none (default)
Delete subvolume '/tmp/btrfs-snap/root/@last_good_known'
Create a snapshot of '/tmp/btrfs-snap/root/@btrfs-auto-snap_apt-run-2014-09-09-0528' in '/tmp/btrfs-snap/root/@last_good_known'
Transaction commit: none (default)
Delete subvolume '/tmp/btrfs-snap/root/@btrfs-auto-snap_apt-run-2014-09-08-2155'
@btrfs-auto-snap_apt-run-2014-09-09-0528, 1 created snapshots, 1 destroyed snapshots, 0 warnings.
Preconfiguring packages ...
(Reading database ... 34165 files and directories currently installed.)
Preparing to replace openssh-server 1:6.0p1-4+deb7u1 (using .../openssh-server_1%3a6.0p1-4+deb7u2_armhf.deb) ...
ssh config: Aborting because ssh/use_old_init_script = false
dpkg: error processing /var/cache/apt/archives/openssh-server_1%3a6.0p1-4+deb7u2_armhf.deb (--unpack):
subprocess new pre-installation script returned error exit status 1
ssh config: Aborting because ssh/use_old_init_script = false
ssh config: Aborting because ssh/use_old_init_script = false
Errors were encountered while processing:
/var/cache/apt/archives/openssh-server_1%3a6.0p1-4+deb7u2_armhf.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



[/TD]
[/TR]
[TR]
[TD="class: trow1 post_buttons"][/TD]
[/TR]
[/TABLE]
[COLOR=#000000][FONT=Tahoma]Tried looking this up online and asking on Xbian forums but couldn't find anything relevant...[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]Help...?[/FONT][/COLOR]

---

### Post by deadflowr on 2014-09-15
Moved to Other Operating Systems and Projects, as this is not 'buntu.

---

