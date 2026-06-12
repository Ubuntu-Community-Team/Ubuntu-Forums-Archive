---
title: "Ubuntu 22.04 + Samba on a 2017 Mac Mini with TB 3 Raid 5 array"
date: 2024-11-18
forum: Apple Hardware Users
---

### Post by copz1998 on 2024-11-18
Greetings,
I am repurposing my 2017 Mac Mini i7 w/ 64GB RAM and a Thunderbolt-3 enclosure with 5 SSDs running as a RAID 5 array. I have one Windows 11 machine (for gaming), and the rest are Macs. 

When I try to connect to one of the shares on the RAID array, I can connect (mount the share), but the folder of the RAID share shows empty (even though it has 1+ TBs of data). 

I can see the array data when I log into the Mac Mini and can use the data. Also, when I set up a share in my home directory, I can see it and edit files. 

It seems to me that Samba can't see the TB 3 device or the symlink in my home folder to the raid array. For diagnosing purposes, I chmod 777 with me as the user/group for the different shares, but I still get permission errors on Windows 11, and on macOS, I am unable to add content to the TB3 share due to permissions errors. 

I have tried several solutions posted on various forms with similar problems, with negative results. 

Any suggestions are greatly appreciated.

---------------------------------------------
[COLOR=#000000][FONT=Menlo]Load smb config files from /etc/samba/smb.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Loaded services file OK.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Weak crypto is allowed by GnuTLS (e.g. NTLM as a compatibility fallback)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Server role: ROLE_STANDALONE[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# Global parameters[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][global][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    log file = /var/log/samba/log.%m[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    logging = file[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    map to guest = Bad User[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    max log size = 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    netbios name = SELBYNAS[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    obey pam restrictions = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    pam password change = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    panic action = /usr/share/samba/panic-action %d[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    passwd program = /usr/bin/passwd %u[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    server role = standalone server[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    server string = %h selbynas_server (Samba, Ubuntu)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    smb1 unix extensions = No[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    unix password sync = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    usershare allow guests = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    idmap config * : backend = tdb[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    wide links = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][homes][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    comment = Home Directories[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    create mask = 0755[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][printers][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    browseable = No[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    comment = All Printers[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    path = /var/tmp[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    printable = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][print$][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    comment = Printer Drivers[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    path = /var/lib/samba/printers[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][user][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    comment = Selbynas share directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    path = /home/user[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    read only = No[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][user2][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    comment = Selbynas share user2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    path = /mnt/md0/selbynas/user2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    read only = No[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][selbynas][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    comment = Selbynas share[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    guest ok = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    path = /mnt/md0/selbynas[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    read only = No[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
 ------------------------------------------------------

[COLOR=#2FB41D][FONT=Menlo]**user@selbynas-Mac-Mini**[COLOR=#000000]:[/COLOR][COLOR=#400bd9]**/mnt/md0**[/COLOR][COLOR=#000000]$ ls -l[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]total 20[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwx------   2 root       root     16384 Sep  7 07:12 [COLOR=#400bd9]**lost+found**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxrwx+ 18 user www-data  4096 Nov 12 06:57 [COLOR=#0000a3]selbynas[/COLOR][/FONT][/COLOR]
[COLOR=#2FB41D][FONT=Menlo]**user@selbynas-Mac-Mini**[COLOR=#000000]:[/COLOR][COLOR=#400bd9]**/mnt/md0**[/COLOR][COLOR=#000000]$ 
--------------
[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x+  2 user user  4096 Oct 23 07:23 [COLOR=#400bd9]**9z22t-qwcst**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x+ 12 user www-data    4096 Sep  9 08:30 [COLOR=#400bd9]**fastfetch**[/COLOR][/FONT][/COLOR]
[FONT=Menlo][COLOR=#000000]drwxrwxrwx+ 18 [/COLOR][COLOR=#000000]user[/COLOR][COLOR=#000000] www-data    4096 Oct 22 07:40 [/COLOR][COLOR=#0000a3]user2[/COLOR][/FONT]
[COLOR=#000000][FONT=Menlo]drwxrwx---+  3 user user  4096 Oct 22 07:48 user2[COLOR=#400bd9]**-Sync**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxrwx+ 28 user user  4096 Nov  8 20:37 [COLOR=#0000a3]MacStudio-ralphbrown[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x+  2 user user  4096 Oct 23 07:23 [COLOR=#400bd9]**MacStudio-Sync**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x+  7 user user  4096 Oct 23 09:30 [COLOR=#400bd9]**Media**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x+  2 user user  4096 Nov  9 16:44 [COLOR=#400bd9]**nextcloud**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x+  5 user www-data    4096 Sep  7 20:24 [COLOR=#400bd9]**Plex**[/COLOR][/FONT][/COLOR]
[FONT=Menlo][COLOR=#000000]drwxrwxrwx+ 62 [/COLOR][COLOR=#000000]user[/COLOR][COLOR=#000000] www-data   12288 Oct 22 07:36 [/COLOR][COLOR=#0000a3]user[/COLOR][/FONT]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x+  2 user user 4096 Oct 23 07:23 [COLOR=#400bd9]**Selbynas**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x+  2 user user  4096 Oct 23 07:23 [COLOR=#400bd9]**Selbynas-Sync-home**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x+  2 user user  4096 Oct 23 07:23 [COLOR=#400bd9]**syncthing**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxr-xr-x   2 user user  4096 Nov 12 07:02 [COLOR=#400bd9]**testshare1**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxrwx+  7 user www-data    4096 Oct 22 11:01 [COLOR=#0000a3]Windows11[/COLOR][/FONT][/COLOR]
[COLOR=#2FB41D][FONT=Menlo]**ralphbrown@selbynas-Mac-Mini**[COLOR=#000000]:[/COLOR][COLOR=#400bd9]**/mnt/md0/selbynas**[/COLOR][COLOR=#000000]$ [/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-----------------------
[/FONT][/COLOR]
[COLOR=#400BD9][FONT=Menlo][COLOR=#000000]:[/COLOR]**/mnt/md0/selbynas**[COLOR=#000000]$ df -h[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Filesystem      Size  Used Avail Use% Mounted on[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs           6.3G  5.5M  6.3G   1% /run[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/nvme0n1p2  916G  137G  732G  16% /[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs            32G   16K   32G   1% /dev/shm[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs           5.0M   12K  5.0M   1% /run/lock[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/nvme0n1p1  1.1G  6.2M  1.1G   1% /boot/efi[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sda1       1.8T  423G  1.3T  25% /mnt/sdb1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs           6.3G  152K  6.3G   1% /run/user/1000[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdb1       3.6T  465G  3.0T  14% /media/user/backup[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/md0        7.3T  2.0T  4.9T  29% /mnt/md0[/FONT][/COLOR]
[COLOR=#2FB41D][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]

---

