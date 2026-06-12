---
title: "Mount a SCSI tape share that Windows can use"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by alabamaXslim on 2007-02-10
I followed this thread setting up Samba and it worked excellently.

HOWTO: Setup Samba peer-to-peer with Windows 
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

NOOB ALERT. (Sound of claxon ringing)

Great Tutorial. I went from nothing to a Ubuntu 6.10 Server with Samba enabled shares in just 2 days. I followed the HOWTO to the letter and it all worked as advertised.

Now the next step for me is to share a tape drive. The ultimate goal being to use my Windows Backup software to backup the Windows Boxes to the shared tape device.

Here are my particulars:


**cat /proc/scsi/scsi shows**
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
Vendor: DELL Model: Alpha Server Rev: V1.0
Type: Direct-Access ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 06 Lun: 00
Vendor: HP Model: Ultrium 1-SCSI Rev: E21V
Type: Sequential-Access ANSI SCSI revision: 03


**ls -l /dev shows**
crw-rw---- 1 root tape 9, 0 2007-02-09 22:47 st0
crw-rw---- 1 root tape 9, 96 2007-02-09 22:47 st0a
crw-rw---- 1 root tape 9, 32 2007-02-09 22:47 st0l
crw-rw---- 1 root tape 9, 64 2007-02-09 22:47 st0m


**ls -l /media shows**
total 8
lrwxrwxrwx 1 root root 6 2007-02-09 14:56 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-02-09 14:56 cdrom0
lrwxrwxrwx 1 root root 7 2007-02-09 14:56 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-02-09 14:56 floppy0


**cat /etc/samba/smb.conf shows**
[global]
; General server settings
netbios name = ALPHA
server string =
workgroup = CJKNET
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

domain master = yes
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
guest ok = no
read only = yes
write list = root
create mask = 0664
directory mask = 0775

[printers]
path = /tmp
printable = yes
guest ok = no
browseable = yes

; Uncomment if you need to share your CD-/DVD-ROM Drive
[CD-ROM Drive]
path = /media/cdrom
browseable = yes
read only = yes
guest ok = no

[MyFiles]
path = /usr/local
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = derekw
force group = derekw


**cat /etc/fstab shows**
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=3a4df524-78da-44c1-ae92-a32e2618d990 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=52ae24f4-e463-47ea-af34-b18abb039439 /home ext3 defaults 0 2
# /dev/sda10
UUID=a670103e-a5e6-47a5-8193-c038465ccc65 /opt ext3 defaults 0 2
# /dev/sda8
UUID=25ec553b-b6cd-493b-8cdd-638af2e4ffca /tmp ext3 defaults 0 2
# /dev/sda6
UUID=a3a3f604-fd3e-4c67-9228-c36916fcfc97 /usr ext3 defaults 0 2
# /dev/sda11
UUID=bea65b31-699d-4e86-9714-a2947434656d /usr/local ext3 defaults 0 2
# /dev/sda7
UUID=ba658367-1c67-4305-b17e-00483d585a77 /var ext3 defaults 0 2
# /dev/sda9
UUID=66710c69-7006-478e-8995-cc7366ed9f7a none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0


**sudo mt-st -f /dev/st0 status shows**
SCSI 2 tape drive:
File number=-1, block number=-1, partition=0.
Tape block size 0 bytes. Density code 0x0 (default).
Soft error count since last status=0
General status bits on (50000):
DR_OPEN IM_REP_EN


**cat /etc/stinit.def shows**
# This file contains example definitions for different kinds of tape
# devices.
#
# You can find some examples in /usr/share/doc/mt-st/examples.
#
# Common definitions to be applied to all tape devices
# (This is the driver's default)
{buffer-writes read-ahead async-writes}


**sudo smbclient -L 192.168.0.100 -U% shows**
Domain=[CJKNET] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk
        CD-ROM Drive    Disk
        MyFiles         Disk
        IPC$            IPC       IPC Service ()
        ADMIN$          IPC       IPC Service ()
Domain=[CJKNET] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        ALPHA
        BIGBOY               Dad's Desk
        NEWKID               New Kid on the Block

        Workgroup            Master
        ---------            -------
        CJKNET               ALPHA



I can't think of any info you might need. I really appreciate any help someone can give.

All I really want to do is backup Windows using the windows back up to the SCSI tape drive installed in the Ubuntu server via the home network. Sounds easy, no?

Again, great HOWTO. Couldn't have done it with out you and learned a few things in the process.

***_alabamaXslim_***

---

