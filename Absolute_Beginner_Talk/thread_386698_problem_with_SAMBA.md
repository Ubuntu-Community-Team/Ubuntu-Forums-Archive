---
title: "problem with SAMBA"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by retrodans on 2007-03-17
I have set up SAMBA on my ubuntu computer, apparently without a hitch using the tutorial on:
[http://www.ubuntuforums.org/showthread.php?t=202605]("http://www.ubuntuforums.org/showthread.php?t=202605")

It seems activated and no error messages came up, I then attempted to connect to it using my windows computer, I went to map a network drive inserting:
\\badger\samba

It doesn't connect, coming up with the error message:
> the network path \\badger\samba could not be found

can anyone work out why this isn't working, I have attached below my smb.conf file, please help, as I need to start moving files across the network.

Thankyou for any advice

```
[global]

    ; General server settings

    netbios name = badger

    server string =

    workgroup = TITHE

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

    path = /media/samba/

    browseable = yes

    read only = no

    guest ok = no

    create mask = 0644

    directory mask = 0755

    force user = badger

    force group = badger

```

---

### Post by dstew on 2007-03-17
I think you need 

\\badger\media\samba

---

### Post by retrodans on 2007-03-17
sadly I am still getting the same response from map network drive, thanks for the idea though!

---

### Post by PartickThistle on 2007-03-17
```
\\badger\MyFiles 
```

If that fails, you may want to try the IP address;

```
\\the-ip-address\MyFiles 
```

---

### Post by retrodans on 2007-03-17
wicked, thanks a lot for that, it sorted out the windows to ubuntu problem now, is there a way to get the ubuntu competer to see the windows network?  

I have gone to places > Network Servers (in ubuntu) and my tithe network is listed there but the only computer there is the ubuntu box, the other systems on the network aren't listed?  Do i need to do a similar mapping on Ubuntu?

---

### Post by PartickThistle on 2007-03-17
Check that both workgroups are the same.

Also, check that you have these installed;

[b]libgnomevfs2-extra
libsmbclient[/b]

sudo apt-get or install via synaptic.  :)

---

### Post by retrodans on 2007-03-17
cheers, they were installed so restarted X to see if that reset it and now it seems to work fine!

Thankyou for your help!

---

### Post by PartickThistle on 2007-03-17
You're welcome!

---

