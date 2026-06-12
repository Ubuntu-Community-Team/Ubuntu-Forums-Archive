---
title: "Sharing files between Windows and Ubuntu"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-05-31
Ok i know that samba should be used to accomplish this task. HOwever, I have read several guides and can not get this to work. The last one I tried was this HOWTO here, but it is for older version of ubuntu (I am using Fiesty) [http://ubuntuforums.org/showthread.php?t=202605&highlight=HOWTO+Samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=HOWTO+Samba)

I want to share between ubuntu and windows xp machine, and eventually be able to share with my xbox media center (have another thread on this but not making any progress). Can someone please point me in the right direction? Here is my current samba.conf

[PHP]
global]
    ; General server settings
    netbios name = Ubuntu-Desktop
    server string =
    workgroup = NETWORK
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
    path = /home/samba/
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = blake
    force group = blake
available = no
browsable = yes
public = no
writable = no[/PHP]

---

### Post by lazyart on 2007-05-31
What I did.  Start to finish.

Navigate to folder you wish to share. Right click, enable sharing as SMB.
sudo smbpasswd -e *username*
sudo smbpasswd -a *username*

Username now has access across the network to the folder as if user was logged in locally.

---

### Post by jba6511 on 2007-05-31
will this work if I want to allow another windows machine access to the share?

---

### Post by dstew on 2007-05-31
The above is for sharing a folder on your linux system with your XP system. To access an XP shared folder, you mount the folder using a regular mount command, like this:```
sudo mount -t smbfs //XPservername/XPsharename /mnt/XPservername -o uid=linuxusername,gid=linuxgroupname
```

Of course, you first have to enable sharing on your XP. If XP needs a password, the mount command will prompt you. Because you use sudo, it will ask first for the sudo password, then for the XP password. Also, your mount point has to be created before you issue the mount command. 

To automatically mount the XP shared folder at boot time, you can add a line to your /etc/fstab file:

//XPservername/XPsharedfoldername /mnt/XPsharedfoldername smbfs username=XPusername,password=XPpassword,workgroup=WORKGROUPNAME 0 0

---

### Post by fjf on 2007-05-31
I keep hoping that someone creates a GUI for SAMBA that normal people can use.  It will happen.  I know.  Just wish I knew how to code it....

---

### Post by jba6511 on 2007-05-31
Failed to find user Joe in passdb backend.

Get that after running sudo smbpasswd -e Joe

---

### Post by lazyart on 2007-05-31
It possible (and not the first time) that I got the -e and -a sequence reversed.

Try -a first, then -e.  Also, Joe has to be a ubuntu username.  When you access from Windows you will be prompted for your ubuntu credentials.

---

### Post by jba6511 on 2007-05-31
ok that works when I run -a first. However, windows does not show the share or the computer that the share is on.

---

### Post by jba6511 on 2007-06-01
can someone explain exactly how they did this with fiesty and windows? I see tons of these threads and no definitive answers yet,

---

### Post by Speedoo on 2007-06-06
Brilliant!  I'm now able to share my linux folder with my Windows laptop!  Much easier than all that Samba configuration stuff (or did I need that too?) 
Thanks!

---

### Post by Speedoo on 2007-06-06
Lazy Art summed it up a few posts up:

What I did. Start to finish.

Navigate to folder you wish to share. Right click, enable sharing as SMB.
sudo smbpasswd -e username
sudo smbpasswd -a username

Username now has access across the network to the folder as if user was logged in locally.

I think someone said the -e and the -a above were reversed, but it worked this way for me.  It also magically enabled my printer sharing, which I've been trying to get to work all day.
Thanks again, LazyArt!

---

### Post by FlintZA on 2007-06-09
I struggled with "sudo smbpasswd -a username" which kept telling me it failed to change the password, I found calling sudo smbpasswd -a username with my current username worked well. -a adds the new user mentioned, since my username already exists I could just enable :)

---

