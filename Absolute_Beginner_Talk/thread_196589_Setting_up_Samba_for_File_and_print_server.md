---
title: "Setting up Samba for File and print server"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by clemkonan on 2006-06-14
My old machine a Duron 800  will  be running ubuntu as a file and print server. I decided not to go with NAS lite hopefully this is a good choice. My instructions were to load Samba via synaptic manger  then select applications> system tools>Run as different user. Type sudo gedit -w /etc/samba/smb.con and  edit the section Share Definitions. to read:

Browseable = yes
create mask = 0775
directory mask = 0775

My file is close but different , I started to make the change but decided to stop. Here is the output
homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0775

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
 Do I have the right file?

---

### Post by andrecasteliano on 2006-06-14
You can follow this link:

[http://wiki.ubuntu.com/SettingUpSamba](http://wiki.ubuntu.com/SettingUpSamba)

---

