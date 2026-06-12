---
title: "Networking with XP... Smb.conf problem"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Nermi on 2008-03-24
Three XP computers in the network called MAIN, and one Ubuntu computer named NERMI-DESKTOP. 
I am trying to set up my network, and am having problems. 
I installed samba, and created a user. Set up a sharing folder as well.
 
When I go to to Places -> Network, it shows me an icon 'Windows network". I click on that, and it finds my Windows workgroup (MAIN). But, when I try to access MAIN, it comes up with a prompt that says "Sorry, couldn't display all the contents of 'Windows Network: main'."

Here is my smb.conf file:
```

[global]
    ; General server settings
    netbios name = NERMI-DESKTOP
    
    workgroup = MAIN
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

[Documents]
path = /home/nermi/Documents
available = yes
browsable = yes
public = yes
writable = no

[untitled ]
path = /home/nermi/Desktop/untitled folder
available = yes
browsable = yes
public = yes
writable = no

```

I looked around and searched, and couldn't figure it out, so I thought I'd ask. 
Thankful for any help or information. 


Nermi

---

### Post by Mauler5858 on 2008-03-24
Is your workgroup name in the linux box in the same case(all caps) as the xp boxes?

---

### Post by Nermi on 2008-03-24
Yes it is. 
Now, however I change NetBios Name to 'nermi' and I WINS support to 'yes'... and I can see and browse my folder on Ubuntu from Windows, but I can't browse my windows network. 

It is interesting that Ubuntu properly recognizes the Network, and the network name (MAIN), but then refuses to connect to it / display network computers --- " Sorry, couldn't display all the contents of 'Windows Network: main' ". 

Well. I just realized I changed two more things in my smb.conf file. Wins support = yes, and I made a new sharing folder and chmod it to 0777. That folder (Samba) can be seen from Windows. 

Here is new smb.conf file: 

```


[global]
    ; General server settings
    netbios name = NERMI
    
    workgroup = MAIN
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
    path = /media/cdrom
    browseable = yes
    read only = yes
    guest ok = yes


[samba]
path = /home/samba
available = yes
browsable = yes
public = yes
writable = no

```

I am following this tutorial:
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

---

