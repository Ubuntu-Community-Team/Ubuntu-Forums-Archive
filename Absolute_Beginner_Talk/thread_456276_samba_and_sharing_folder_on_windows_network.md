---
title: "samba and sharing folder on windows network"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-05-27
ok. i installed smb and i can now access win machines on my local network.

i tried sharing folders on my ubuntu... the other people can access my machine using the IP but gets a login screen on trying to open it.

i tried both my regular user name and root with the password. did not work. 

how to fix it?

---

### Post by nickpaton on 2007-05-27
Look at [this]("http://ubuntuforums.org/showthread.php?t=202605") excellent HOWTO by Stormbringer for setting up Ubuntu and Windows networking - has worked every time for me since Dapper.

---

### Post by niglch on 2007-05-27
I'm having the same issue. I tried following the "Setting Up Samba" guide ([https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)) but it didn't seem to work as I'm still prompted for a password while trying to access Ubuntu (Feisty) shared folders via a Windows XP laptop. I also can't seem to get printer sharing to work. This is starting to get kind of annoying too because I need to boot into XP whenever someone tries to print something from the laptop.

Anyone have a solution?

---

### Post by Sushubh on 2007-05-27
thx

---

### Post by nickpaton on 2007-05-27
Niglch - I would suggest that you too look at the Stormbringer HOWTO and set up your PC's accordingly.

To help you both out, I've included my *sudo gedit /etc/samba/smb.conf* file which has some some small changes to Stormbringer's version:

> [global]
    ; General server settings
    netbios name = NAME_OF_UBUNTU_PC
    
    workgroup = WINDOWS_NETWORK_GROUP_NAME 
    ; Mine's MSHOME

    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    ;  Make* security = share* if you want no password login in Windows PC, 
    ;  or *security = share* if you want login in Windows PC.

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
; Windows.

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
    path = /home/nick/samba
    
    read only = no
    guest ok = no
    create mask = 0700
    directory mask = 0700
    force user = 
    force group = 
available = yes
browsable = yes
public = yes
writable = no

It is important to note that you must set up all PC's according to the HOWTO and not to take .conf file in isolation.

Also initially disable the firewall using Firestarter (applies to network printing from Ubuntu to a printer on an XP PC).  I can give more information on setting up Firestarter firewall rules to get it all to work if you need it.

Network printing - please can you clarify which PC the printer is fitted to, and the make and model of the printer and I'll see if I can help.
Also could you clarify what you would like to happen when printing (if you see what I mean LOL)

---

### Post by niglch on 2007-05-27
Both your smb.conf file and the one posted in the howto have gotten file sharing to work great for me (I'm not sure what the difference is), but I still can't seem to share my printer.
The printer is an HP DeskJet 3820 directly connected to a computer running Ubuntu 7.04 (NOT the laptop which runs windows XP). However, I want to have the printer act as a network printer to the windows laptop so I can print files remotely. If you need any more info, please tell me!

---

### Post by nickpaton on 2007-05-27
Glad it's going well.

To install your printer on your Ubuntu PC[ look at this post.]("http://ubuntuforums.org/showthread.php?t=449809")

To network it to your XP laptop look at [this]("http://ubuntuforums.org/showpost.php?p=1561331") post.

Note that for Feisty the full command for modifying the * /etc/cups/cupsd.conf* file is:

```
gksudo gedit /etc/cups/cupsd.conf
```

I personally have tried neither with having a printer on a remote XP PC, but hopefully this should all work.

Good luck - Nick

---

### Post by niglch on 2007-05-27
Thanks a bunch! everything seems to be working perfectly now. My cupsd.conf file was actually set up correctly -- I just couldn't figure out how to direct windows to the right printer and that second guide got it right apparently.

---

