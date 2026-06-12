---
title: "Samba woes in Gutsy"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by blop on 2007-11-11
Hey all...

Since i installed Gutsy after a successfull time on Feisty i have been having real issues with Samba and network sharing in general.

I cannot access my ubuntu shares from my XP machine....the ubuntu pc appears in the MS Workgroup but double clicking on it to see shares gives me this error:

\\p2pserver is unaccessible. You may not have permission

I can access the windows shares from XP tho...

cheers all!

---

### Post by djchandler on 2007-11-11
> **blop said:**
> Hey all...

Since i installed Gutsy after a successfull time on Feisty i have been having real issues with Samba and network sharing in general.

I cannot access my ubuntu shares from my XP machine....the ubuntu pc appears in the MS Workgroup but double clicking on it to see shares gives me this error:

\\p2pserver is unaccessible. You may not have permission

I can access the windows shares from XP tho...

cheers all!

Have you tried the Shared Folders menu item under System>Administration?

I suggest re-trying to share the folders previously shared under Feisty.

DJ

---

### Post by ant2ne on 2007-11-11
Seems to be my day to give samba advice.
[http://ubuntuforums.org/showthread.php?t=292006](http://ubuntuforums.org/showthread.php?t=292006)

---

### Post by Peter09 on 2007-11-12
I believe there is a problem in Gutsy with name resolution (DHCP). This may be giving you this problem.

Try pinging a shared host by IP address and the by Host name. If IP address works, but Host name does not then you have the problem.

Trying mounting the share by IP address.

---

### Post by SpiritIsReality on 2007-11-12
howdy
Peter09 ... thanks! I'll try that.
trails

---

### Post by blop on 2007-11-12
Hi i did a clean install of Gutsy so there is no residue of Feisty....which surprises me as to why im having so many problems.

If there is a problem with Networking in Gutsy you would of thought the devs would of held off release....

I will try the suggestions....just of intrest how do i map to a samba share via IP?

---

### Post by Peter09 on 2007-11-12
I use the mount command, withs CIFS in fstab it looks like this.

//192.168.0.8/nas1share		/mnt/nas1/nas1share	cifs	rw,defaults,errors=remount-rw

You should be able to mount the share from the command line, although the syntax of mount on the command line is slightly different.

type the command 'mount' in the terminal to get the details

Just realised that an easier way is to goto the 'place' menu top left and select 'connect to server'. Use the drop down menu to select windows share and put the ip address of the server in server field, put the share name in the share field. When run it should give you an icon on the desktop which mounts the share.

---

### Post by blop on 2007-11-12
Sorry, i think i confused things... i can access my Windows Xp shares from Ubuntu. But i cannot access my Ubuntu samba shares from XP. So i dont think your suggestion will help me.....


cold someone check over my config file?

[global]
    ; General server settings
    netbios name = P2Pserver
    server string = all your internets are mine
    workgroup = NETPLAY
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

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



[p2pHOME]
path = /home/p2p
available = yes
browsable = yes
public = yes
writable = yes
force user = p2p
force group = p2p

[sda3]
path = /media/sda3
available = yes
browsable = yes
public = yes
writable = yes
force user = p2p
force group = p2p

[sdb1]
path = /media/sdb1
available = yes
browsable = yes
public = yes
writable = yes
force user = p2p
force group = p2p

---

### Post by ant2ne on 2007-11-12
.> **ant2ne said:**
> Seems to be my day to give samba advice.
[http://ubuntuforums.org/showthread.php?t=292006](http://ubuntuforums.org/showthread.php?t=292006)Read **my** reply to this post here. I'm certain it will help you access your samba shares from the XP computer.

---

