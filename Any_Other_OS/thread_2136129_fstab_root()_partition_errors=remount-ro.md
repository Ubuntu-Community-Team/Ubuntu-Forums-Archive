---
title: "fstab root(/) partition errors=remount-ro"
date: 2013-04-16
forum: Any Other OS
---

### Post by Curitibano on 2013-04-16
[COLOR=#333333][FONT=Lucida Grande]Hi there,[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]I have the following problem.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Since yesterday I found out that my Root partition is running full with unknown data.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Yesterday I already removed a 5.8 Gb log file, but the problem is returning.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]I think the problem occured after a hard reboot I had to do after a total freeze of Mint13 Mate[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]On every boot or reboot there's less diskspace left and according to fstab [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]the Root partition is read-only:[/FONT][/COLOR]

[LIST]
[*]marcel@AMD2800 /media $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc    /proc    proc    nodev,noexec,nosuid    0    0
[COLOR=#FF0000]#Entry for /dev/sda1 :
UUID=7dd92e0f-251d-4167-8701-1e42653d4f18    /    ext4    errors=remount-ro    0    1[/COLOR]
#Entry for /dev/sda5 :
UUID=127c34c4-1578-438f-b073-703e1271d2fd    /home    ext4    defaults    02
#Entry for /dev/sdb5 :
UUID=1058C61758C5FB8A    /media/Backup    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
#Entry for /dev/sda4 :
UUID=4758A78C56BA37BD    /media/Data\040PC    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
#Entry for /dev/sda3 :
UUID=216EF14B4E348E49    /media/Data_Marcel    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda6 :
UUID=77c38ca4-7b5f-4585-b784-f9b280d692c6    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0
[/LIST]
[COLOR=#333333][FONT=Lucida Grande]Output for mount:[/FONT][/COLOR]

[LIST]
[*]marcel@AMD2800 /media $ mount
[COLOR=#FF0000]/dev/sda1 on / type ext4 (rw,errors=remount-ro)[/COLOR]
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda5 on /home type ext4 (rw)
/dev/sdb5 on /media/Backup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /media/Data PC type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /media/Data_Marcel type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/marcel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marcel)
[/LIST]
[COLOR=#333333][FONT=Lucida Grande]I guess the problem of running out of diskspace has to do with being RO of the Root partition[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Already tried all the possible options in Recovery mode, like clean, fsck and [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]the command "mount -n -o remount,rw /", but I'm out of ideas right now.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Anyone a solution for my problem?[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]TIA[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]-----------------[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]AMD 2800 [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]2 Gb DDR Ram[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Mint 13 Mate[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]**Update:**[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]After looking around at the Ubuntu forum  I found out that the [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]logfile I deleted yesterday appeared in [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]/root/.local/share/Trash/files.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]I opened the folder as administrator, but when I try to delete the [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]file it appears again after a few seconds.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]The name of the file is uvcdynctrl-udev.2.2.2.log, but there is [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]more to delete in this folder.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Guess it has to do with  Root(/) being read-only.[/FONT][/COLOR][TABLE="width: 500"]
[TR]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by ajgreeny on 2013-04-16
That log file is something to do with your webcam, I think.  Can you unplug it (I'm assuming this is a desktop machine as you appear to have a floppy disk showing in fstab) then restart and see if the problem goes away.

Then you'll need to figure out how to get your webcam working again.

---

### Post by Curitibano on 2013-04-16
The webcam is not!!! the problem.
The problem is that Root is Read-Only and I can't delete files even as administrator.
Already tried things as fsck and mount -n -o remount, rw /.

---

### Post by Curitibano on 2013-04-17
[COLOR=#000000][FONT=Lucida Grande]Thanks guys for [/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]the tips.[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]The solution for deleting the files permanently was easy.

[/FONT][/COLOR][TABLE="class: outer_border, width: 500"]
[TR]
[TD][COLOR=#2E8B57][FONT=Monaco]Open in the File Manager the Root partition as Administrator to find out where you have to delete the files[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]In my case it was in /root/.local/share/Trash[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]Open a Root Terminal[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]cd  /root/.local/share/Trash/files[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]rm -rf <filename> or <foldername>[/FONT][/COLOR][/TD]
[/TR]
[/TABLE]
[COLOR=#000000][FONT=Lucida Grande]
[/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]That's it[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]After doing this I now have left 7.3 Gb at my Root partition and isn't getting less[/FONT][/COLOR]

---

