---
title: "samba share on external hard drive"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-12-30
setup:

laptop with ubuntu 6.06 server command line only with printer and usb hdd attached
2 dual boot winxp home / ubuntu computers

The usb drive has 3 folders (luna,rebecca,music) in it that will be for backups.
How do I go about setting up samba so that both windows & linux can access those folders?

Tried screwin round w some of teh docs but they are from 2005 and i want to be up to date. The wiki thing says all different stuff too so I just want something dumb me can understand.. :P

---

### Post by blueridgedog on 2007-12-30
Other forum users have found this guide helpful:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Note that the drive being a USB/removable will only change the nature of the mount and mount point and will not be relative to getting samba to work.

---

### Post by lunaz on 2007-12-30
I have no idea what I'm doing so here's some outputs: Got to the part where it wants me to map network drives in windows. Keeps asking for pws over & over again and afaik they are all the same for each user on both computers (server,her computer). Tried connecting with \\JOEDIRT\media\samba and ipaddress instead of JOEDIRT, same thing; can't connect. Should I be using the name of the server instead (teh-serverer)?

smb.conf
```
luna@teh-serverer:/$ cat /etc/samba/smb.conf
[global]
    ; General server settings
    netbios name = teh-serverer
    server string =
    workgroup = JOEDIRT
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/samba
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = luna
    force group = usb-shares
```

groups
```
luna@teh-serverer:/$ groups luna
luna : luna adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin usb-shares
luna@teh-serverer:/$ groups rebecca
rebecca : users usb-shares
luna@teh-serverer:/$
```

fstab
```
luna@teh-serverer:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda3       /var            ext3    defaults        0       2
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
luna@teh-serverer:/$
```

mount
```
luna@teh-serverer:/$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/hda2 on /home type ext3 (rw)
/dev/hda3 on /var type ext3 (rw)
/dev/sda1 on /media/samba type vfat (rw)
luna@teh-serverer:/$ 
```

listing of /media/samba/ - nothing is in the folders yet...
```
luna@teh-serverer:/media/samba$ ls -la
total 68
drwxr-xr-x 5 root root 16384 1969-12-31 17:00 .
drwxr-xr-x 6 root root  4096 2007-12-30 14:45 ..
drwxr-xr-x 2 root root 16384 2007-12-30 13:39 luna
drwxr-xr-x 2 root root 16384 2007-12-30 13:39 music
drwxr-xr-x 2 root root 16384 2007-12-30 13:39 rebecca
luna@teh-serverer:/media/samba$ 

```

UPDATE: I managed to connect to it..some how, but now I can't make any files in the folders, access denied.

Tried to change owners/groups/permissions, but it says no such file or directory.
```
luna@teh-serverer:/media/samba$ ls -la
total 68
drwxr-xr-x 5 root root 16384 1969-12-31 17:00 .
drwxr-xr-x 5 root root  4096 2007-12-30 16:15 ..
drwxr-xr-x 2 root root 16384 2007-12-30 13:39 luna
drwxr-xr-x 2 root root 16384 2007-12-30 13:39 music
drwxr-xr-x 2 root root 16384 2007-12-30 13:39 rebecca
luna@teh-serverer:/media/samba$ sudo chown luna luna:usb-shares
chown: cannot access `luna:usb-shares': No such file or directory
luna@teh-serverer:/media/samba$ sudo chown luna:usb-shares luna
chown: changing ownership of `luna': Operation not permitted
luna@teh-serverer:/media/samba$ sudo -i
root@teh-serverer:~# chown rebecca:usb-shares rebecca
chown: cannot access `rebecca': No such file or directory
root@teh-serverer:~# cd /media/samba
root@teh-serverer:/media/samba# ls
luna  music  rebecca
root@teh-serverer:/media/samba# chown rebecca:usb-shares rebecca
chown: changing ownership of `rebecca': Operation not permitted
root@teh-serverer:/media/samba# chmod 0777 /media/samba
root@teh-serverer:/media/samba# ls -la
total 68
drwxr-xr-x 5 root root 16384 Dec 31  1969 .
drwxr-xr-x 5 root root  4096 Dec 30 16:15 ..
drwxr-xr-x 2 root root 16384 Dec 30 13:39 luna
drwxr-xr-x 2 root root 16384 Dec 30 13:39 music
drwxr-xr-x 2 root root 16384 Dec 30 13:39 rebecca
root@teh-serverer:/media/samba# chown luna:usb-shares luna
chown: changing ownership of `luna': Operation not permitted
root@teh-serverer:/media/samba# chown luna luna:usb-shares
chown: cannot access `luna:usb-shares': No such file or directory
root@teh-serverer:/media/samba# ls
luna  music  rebecca
root@teh-serverer:/media/samba#
```

---

### Post by blueridgedog on 2007-12-30
Ok, before I did too deep into the output of what you send (and I will)

Can you go to the linux box and enter:

sudo smbpasswd -a USERNAME

Where USERNAME is the name of the test user?

Also, can you see that all systems involved in the setup are in the workgroup JOEDIRT?

Try this and report back while I look over the other items.

---

### Post by blueridgedog on 2007-12-30
Also, after each change that we make involving sambe, issue:

sudo  /etc/init.d/samba restart

---

### Post by blueridgedog on 2007-12-30
Ok, some initial thoughts and suggestions.

Until you get it working, drop the group voodoo.  I know where you are going, but you don't want to test fly the plane all at once when you can test fly a component at a time.

I suggest the following changes:

[MyFiles]
    path = /media/samba
    browseable = yes
    read only = no
    guest ok = no
    writable = yes                  //add this but not this comment
    create mask = 0644
    directory mask = 0755
    ;force user = luna             Comment this out
    ;force group = usb-shares Comment this out


luna@teh-serverer:/media/samba$ sudo chown luna luna:usb-shares

Should be 

sudo chown luna:usb-shares /media/samba/luna -R

root@teh-serverer:~# chown rebecca:usb-shares rebecca

Should be 

sudo chown rebecca:usb-shares /media/samba/luna -R

Don't forget the media folder.

The syntax is chown USER:GROUP /Path/to/file/or/Directory [options]

Try these changes, along with the smbpasswd and workgroup mentioned before and restart samba.

---

### Post by lunaz on 2007-12-30
OK, I redid both luna & rebecca's smb passwords and restarted samba with no errors. Her smb pw is the same as her login. Luna's smb pw is the same as longin pw on the server but NOT the desktop.

Rebecca's windows install is in workgroup JOEDIRT
Laptop server is in workgroup JOEDIRT according to smb.conf
Luna's ubuntu install is in domain JOEDIRT

---

### Post by blueridgedog on 2007-12-30
You can supply the password you made when asked, but I usually always make the user accounts match username and password on the server and the windows system and on samba (three actual sets of accounts - no wonder people use LDAP or AD).

---

### Post by lunaz on 2007-12-30
Just tried making those changes to the config file, saved it tried to do chown again but still get errors :(

```
luna@teh-serverer:/etc/network$ sudo /etc/init.d/samba stop
Password:
 * Stopping Samba daemons...                                             [ ok ] 
luna@teh-serverer:/etc/network$ sudo nano /etc/samba/smb.conf
luna@teh-serverer:/etc/network$ sudo chown luna:usb-shares /media/samba/luna -R
chown: changing ownership of `/media/samba/luna': Operation not permitted
luna@teh-serverer:/etc/network$ sudo chown rebecca:usb-shares /media/samba/rebecca -R
chown: changing ownership of `/media/samba/rebecca': Operation not permitted
luna@teh-serverer:/etc/network$
```

---

### Post by blueridgedog on 2007-12-30
Sorry, my bad.  The command was off at first, but the chown will not work on fat32/vfat.  The file system can't support file level permissions.

---

### Post by lunaz on 2007-12-30
No directories either? :(

---

### Post by blueridgedog on 2007-12-30
Help me a bit more.  You can make directories, but fat32 has no permissions.  Is that what you were asking?

---

### Post by lunaz on 2007-12-30
Oops, I meant, if fat32 has no permissions, how can I open up those directories in /media/samba/ to put files in?

Or should I just format that drive as ext3 and get the drivers for windows?

---

### Post by blueridgedog on 2007-12-31
Ext3 is the way to go, especially given your desire to have multiple users.

if you want to use fat32, then I would make the group own the mount point:
```

sudo umount /dev/sda1
sudo chown luna:usb-shares /media/samba
sudo chmod 777 /media/samba
sudo mount -t vfat -o gid=GIDNUMBER,UID=UIDNUMBER /dev/sda1 /media/samba
```

(You will need to get the GID and UID from the system, it is the numerical value)

This should enable users to access the share via Samba.

We may have to tweak it a bit more, but glad to help.

---

### Post by lunaz on 2007-12-31
Sweet thanks I'll try that when I get home. How do you format the drive to ext3 with the command line?

...and where do I get ext3 drivers for windows? lol

---

### Post by Emmett on 2007-12-31
How do you format the drive to ext3 with the command line?

I would use Synaptic and install gparted. It has a GUI.

...and where do I get ext3 drivers for windows? 

I am running a server and 2 PC's. One XP and 1 Vista. I did not have to install a driver for ext3 when I converted mine. I do not believe when Samba is running that you need one. I may be wrong though as I am just learning Kubuntu 7.1

Hope this Helps,,

Emmett

---

### Post by lunaz on 2007-12-31
Trying to format it to ext 3 but it gives error & tries to mount during the process.
edit: wow, the fdisk thing worked, wonder why that would & not the graphical one.

---

### Post by blueridgedog on 2007-12-31
As a rule, I find that command line utilities work.  Graphical ones some times seem too go off in a corner and mumble a bit to themselves.  They have come a long way mind you, but when I need to partition a disk I fire up fdisk as well.

However, I would not attempt to talk someone through using it, whereas I can talk someone though gparted.

---

### Post by lunaz on 2008-01-01
Making progress!
I can rw to the luna share
She can rw to the rebecca share
I can rw to the music share
She can r but not w to the music share

When I mapped the network drives on her computer it did NOT ask me for any pws. When I did mine, it asked for pws.

Should I make a new user called music and add it to group usb-shares to get the music folder working? or is there some better way to fix that?

smb.conf
```
luna@teh-serverer:~$ cat /etc/samba/smb.conf
[global]
    ; General server settings
    netbios name = teh-serverer
    server string =
    workgroup = JOEDIRT
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[teh-backuperer]
    path = /media/samba
    browseable = yes
    read only = no
    guest ok = no
    writable = yes
    create mask = 0644
    directory mask = 0755
    ;force user = luna
    ;force group = usb-shares
luna@teh-serverer:~$
```

permissions, groups, so far
```
luna@teh-serverer:/media/samba$ ls -la
total 36
drwxrwxrwx 6 root    root        4096 2008-01-01 13:00 .
drwxr-xr-x 5 root    root        4096 2007-12-30 16:15 ..
drwx------ 2 root    root       16384 2007-12-31 20:04 lost+found
drwxr-xr-x 2 luna    usb-shares  4096 2008-01-01 13:29 luna
drwxrwx--- 3 root    usb-shares  4096 2008-01-01 13:59 music
-rw-r--r-- 1 rebecca users          0 2008-01-01 13:00 New Text Document.txt
drwxr-xr-x 3 rebecca usb-shares  4096 2008-01-01 14:03 rebecca
luna@teh-serverer:/media/samba$ groups luna
luna : luna adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin usb-shares
luna@teh-serverer:/media/samba$ groups rebecca
rebecca : users usb-shares
luna@teh-serverer:/media/samba$
```

---

### Post by blueridgedog on 2008-01-01
Well, samba appears to be wide open, I suggest you change the permission on the directory as a first test:

sudo shmod 777 /media/samba/music

---

### Post by lunaz on 2008-01-01
Changing the permissions on music to 777 lets both users rw. What's next step? I definitely don't want everyone in my folders.. :P

---

### Post by blueridgedog on 2008-01-01
Well, it is not everyone, they still have to have a valid username/password in smbpasswd.

This is what you stated:

> Making progress!
I can rw to the luna share
She can rw to the rebecca share
I can rw to the music share
She can r but not w to the music share

So I assumed you wanted her to RW to the music folder.

But the music folder is RWX to the group:

drwx**rwx**--- 3 root    usb-shares  4096 2008-01-01 13:59 music

My suspicion is that samba is not looking at the group permissions.

Since the samba share is not public and it authentication is user based, I think you are ok.

An alternative would be to create three samba shares rather than one.

---

### Post by lunaz on 2008-01-01
I want both of us to have full access to the music folder, and to our own backup folder, but not the other person's backup folder.

---

### Post by lunaz on 2008-01-02
Lil more messing tonight....

Both users can make files & folders on the music share, but they can't use files owned by the other person.

```
luna@teh-serverer:/media/samba$ cat /etc/samba/smb.conf
[global]
    ; General server settings
    netbios name = teh-serverer
    server string =
    workgroup = JOEDIRT
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[teh-backuperer]
    path = /media/samba
    browseable = yes
    read only = no
    guest ok = no
    writable = yes
    create mask = 0755
    directory mask = 0755
    ;force user = luna
    force group = usb-shares
luna@teh-serverer:/media/samba$
```

```

luna@teh-serverer:/media/samba$ ls -la
total 36
drwxrwxrwx 6 root    root        4096 2008-01-01 18:38 .
drwxr-xr-x 5 root    root        4096 2007-12-30 16:15 ..
drwx------ 2 root    root       16384 2007-12-31 20:04 lost+found
drwxrwxrwx 3 luna    usb-shares  4096 2008-01-02 19:49 luna
drwxrwxrwx 4 root    usb-shares  4096 2008-01-02 19:50 music
drwxrwxrwx 3 rebecca usb-shares  4096 2008-01-02 19:48 rebecca
luna@teh-serverer:/media/samba$
```

```
luna@teh-serverer:/media/samba$ cd music
luna@teh-serverer:/media/samba/music$ ls -la
total 16
drwxrwxrwx 4 root    usb-shares 4096 2008-01-02 19:50 .
drwxrwxrwx 6 root    root       4096 2008-01-01 18:38 ..
drwxr-xr-x 2 rebecca usb-shares 4096 2008-01-02 19:47 testmfolder1
drwxr-xr-x 2 luna    usb-shares 4096 2008-01-02 19:50 testmfolder2
luna@teh-serverer:/media/samba/music$ cd testmfolder1
luna@teh-serverer:/media/samba/music/testmfolder1$ ls -la
total 8
drwxr-xr-x 2 rebecca usb-shares 4096 2008-01-02 19:47 .
drwxrwxrwx 4 root    usb-shares 4096 2008-01-02 19:50 ..
-rwxr--r-- 1 rebecca usb-shares    0 2008-01-02 19:47 testmfile1.txt
luna@teh-serverer:/media/samba/music/testmfolder1$ cd ..
luna@teh-serverer:/media/samba/music$ cd testmfolder2
luna@teh-serverer:/media/samba/music/testmfolder2$ ls -la
total 8
drwxr-xr-x 2 luna usb-shares 4096 2008-01-02 19:50 .
drwxrwxrwx 4 root usb-shares 4096 2008-01-02 19:50 ..
-rwxr--r-- 1 luna usb-shares    0 2008-01-02 19:50 testmfile2.txt
luna@teh-serverer:/media/samba/music/testmfolder2$
```

---

### Post by blueridgedog on 2008-01-02
> **lunaz said:**
> Lil more messing tonight....

Both users can make files & folders on the music share, but they can't use files owned by the other person.



If you want Music to be wide open, you will (I think) need to create another samab share just for it, that allows public access.

However, that said, you seem to have the nuts and bolts of it down pat (conceptually).

---

### Post by lunaz on 2008-01-05
Ok I got the music & luna shares working on my computer using either windows or linux, at least so far... :P

I got the music & rebecca shares working on her computer using windows but not linux. She can get to the music folder with full rights but can't write to the rebecca folder. :(

Only thing I can come up with is the UID & GID for rebecca are different on the server and her computer.

smb.conf
```

luna@teh-serverer:/media/samba$ cat /etc/samba/smb.conf
[global]
    ; General server settings
    netbios name = teh-serverer
    server string =
    workgroup = JOEDIRT
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[rebecca]
    path = /media/samba/rebecca
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = rebecca
    force group = rebecca

[luna]
    path = /media/samba/luna
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = luna
    force group = luna

[music]
    path = /media/samba/music
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0777
    directory mask = 0777
    force group = usb-shares
luna@teh-serverer:/media/samba$
```

id for both users on the server:
```
luna@teh-serverer:/media/samba$ id rebecca
uid=1002(rebecca) gid=100(users) groups=100(users),1001(usb-shares),1002(rebecca)

luna@teh-serverer:/media/samba$ id luna
uid=1000(luna) gid=1000(luna) groups=1000(luna),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),108(lpadmin),109(scanner),110(admin),1001(usb-shares)
luna@teh-serverer:/media/samba$
```

id for luna on luna's computer:
```
luna@badassness:~$ id luna
uid=1000(luna) gid=1000(luna) groups=1000(luna),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin)
luna@badassness:~$
```

id for rebecca on rebecca's computer:
```
rebecca@soggy:~$ id rebecca
uid=1000(rebecca) gid=1000(rebecca) groups=1000(rebecca),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin)
rebecca@soggy:~$
```

Should I change her UID/GID #s on her computer to 1002?

---

### Post by blueridgedog on 2008-01-06
Ok, you have tossed a curve ball (either I was asleep in this thread...) as I did not know you were trying to connect from windows and Linux to a samba share on a given Ubuntu box.

> I got the music & rebecca shares working on her computer using windows but not linux. She can get to the music folder with full rights but can't write to the rebecca folder.

Only thing I can come up with is the UID & GID for rebecca are different on the server and her computer.

I assume you are using a mount command with the smbfs?  

> Should I change her UID/GID #s on her computer to 1002?

If it works when connecting from the WindowsXP side, then I would concluded that samba is setup right, but I would like the answer to the connection question before think about UID/GID's.  The underlying UID/GID matching should not matter if using smbfs.

However, that said, you have made great progress and went the distance with just a few hints as to breaking up the shares in your smb.conf to fine tune the permissions you want.

---

### Post by lunaz on 2008-01-08
I did mount the shares Ok, they showed up on the desktop, and she can get to the rebecca folder. She just can't make new files or write to them.

Also a funny thing happened... I went to shut down her computer and got some error about CIFS not responding, so I turned samba off from the server then the computer shut down.

I never saw that before, but I just updated the server today...

---

### Post by lunaz on 2008-01-08
Here's some output from her computer. She's user#1002 on the server, but #1000 on this computer. As far as I know the permissions are the same on her folder and the luna folder, but mine works for me.

```
rebecca@soggy:~$ cd /media/music
rebecca@soggy:/media/music$ ls -la
total 4
drwxrwxrwx 3 root root    0 2008-01-08 18:26 .
drwxr-xr-x 9 root root 4096 2008-01-05 17:45 ..
drwx------ 4 1002 1001    0 2008-01-08 18:26 .Trash-rebecca
rebecca@soggy:/media/music$ cd ..
rebecca@soggy:/media$ cd rebecca
rebecca@soggy:/media/rebecca$ ls -la
total 4
drwxrwxrwx 5 root root    0 2008-01-08 18:26 .
drwxr-xr-x 9 root root 4096 2008-01-05 17:45 ..
drwxr-xr-x 2 1002 1002    0 2008-01-05 15:05 rebecca
drwx------ 2 1002 1002    0 2008-01-08 18:26 .Trash-rebecca
drwxr-xr-x 2 1002 1002    0 2008-01-05 17:48 untitled folder
rebecca@soggy:/media/rebecca$
```

---

### Post by lunaz on 2008-01-11
I changed the permissions on all 3 shares to 0777 in the smb.conf file. Still rebecca can't make new files or write to any files in her share. The only ting she can do is make new folders. Every folder she makes inside the rebecca share is owned by user 1002...

---

### Post by blueridgedog on 2008-01-12
How is her system mounting the share?  What is the command or the entry in fstab?  I am drawing a blank as well, but perhaps that will spark a thought.

---

### Post by lunaz on 2008-01-13
It's the fstab; I followed this guide to get that part of it working.

[http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/](http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/)

---

### Post by lunaz on 2008-02-02
Well still no closer to getting her rebecca folder working. I'm thinking of downgrading hers to the LTS or something.

I tried making her rebecca share the same as the music share in the smb.conf file on the server and the fstab on her comp (except the path names of course). No changes, still can't make new documents or write to documents; just can make new folders.

Tried to add the following to the rebecca share in smb.conf no go:

writeable = yes
valid users = 1002,rebecca (or just one at a time)

Tried commenting out the force user & group lines, tried just force group usb-shares like the music share, tried using just the UID/GID numbers on the server...

Using chmod or chown commands on the client gives permission denied or operation not permitted errors. Changing to root makes no difference, output below

Anything else I can do to get this working?
Why does the music share work but not the rebecca share?

OUTPUTS
```
luna@teh-serverer:/$ cat /etc/samba/smb.conf
[global]
    ; General server settings
    netbios name = teh-serverer
    server string =
    workgroup = JOEDIRT
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[rebecca]
    path = /media/samba/rebecca
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0777
    directory mask = 0777
    force group = usb-shares

[luna]
    path = /media/samba/luna
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0777
    directory mask = 0777
    force user = luna
    force group = luna

[music]
    path = /media/samba/music
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0777
    directory mask = 0777
    force group = usb-shares
luna@teh-serverer:/$
```

```
rebecca@soggy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ecaa0c9f-579d-4f66-91c1-9e4479c9bc03 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4E3859DF3859C69D /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=4777-1DEC  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=e476c6e2-da4a-d7b2-c7be-d43b46b927ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//192.168.1.102/music /media/music cifs auto,iocharset=utf8,uid=rebecca,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0
//192.168.1.102/rebecca /media/rebecca cifs auto,iocharset=utf8,uid=rebecca,gid=users,credentials=/root/.cifscredentials,file_mode=0777,dir_mode=0777 0 0
rebecca@soggy:~$
```

```
rebecca@soggy:~$ cd /media/
rebecca@soggy:/media$ ls
cdrom  cdrom0  cdrom1  floppy  floppy0  music  rebecca  sda1  sda3
rebecca@soggy:/media$ sudo chmod -R 777 rebecca
Password:
chmod: changing permissions of `rebecca': Permission denied
rebecca@soggy:/media$ sudo chown -R rebecca:rebecca rebecca
chown: changing ownership of `rebecca/new file': Permission denied
chown: changing ownership of `rebecca/.Trash-rebecca/new file': Permission denied
chown: changing ownership of `rebecca/.Trash-rebecca/test1 (copy)': Permission denied
chown: changing ownership of `rebecca/.Trash-rebecca/test1': Permission denied
chown: changing ownership of `rebecca/.Trash-rebecca/itworks': Permission denied
chown: changing ownership of `rebecca/.Trash-rebecca/asfd': Permission denied
chown: changing ownership of `rebecca/.Trash-rebecca/untitled folder': Permission denied
chown: changing ownership of `rebecca/.Trash-rebecca/test2/new file': Permission denied
chown: changing ownership of `rebecca/.Trash-rebecca/test2': Permission denied
chown: changing ownership of `rebecca/.Trash-rebecca/rebecca/rebecca1.txt': Permission denied
chown: changing ownership of `rebecca/.Trash-rebecca/rebecca': Permission denied
chown: changing ownership of `rebecca/.Trash-rebecca': Permission denied
chown: changing ownership of `rebecca/untitled folder': Permission denied
chown: changing ownership of `rebecca': Permission denied
rebecca@soggy:/media$
```

---

