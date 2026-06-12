---
title: "XBMC setup samba but not connecting"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-05-30
I followed the guide here: [http://ubuntuforums.org/showthread.php?t=438577&highlight=xbmc](http://ubuntuforums.org/showthread.php?t=438577&highlight=xbmc) and I am using the latest version of xbmc. However, when I edit the network location I get an invalid computer name error. The following is what I input at the screen on xbmc

Protocol: Windows Network (SMB)
Server name: 192.168.1.xxx
shared: /Data/ (Trying to share a partition - have also tried MyFiles like the guide does)
username: blake
password: xxx

Here is a copy of my smb config file as well:

[PHP]#======================= Global Settings =======================

[global]

[global]
; General server settings
netbios name = Ubuntu-Desktop
server string = (leavethisblank)
workgroup = NETWORK
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

;interfaces = 127.0.0.1, 192.168.1.1/24
interfaces = lo, eth1 (put you ethX here ,eth0 or 1 etc.)
bind interfaces only = true

hosts allow = 127.0.0.1, 192.168.1.122 (the ip of your xbox goes here)
hosts deny = 0.0.0.0/0

passdb backend = tdbsam
security = user
encrypt passwords = true
username map = /etc/samba/smbusers
obey pam restrictions = yes
invalid users = root

name resolve order = hosts wins bcast

wins support = no

; printing = CUPS
; printcap name = CUPS

syslog = 1
syslog only = yes

# Do something sensible when Samba crashes: mail the admin a backtrace
panic action = /usr/share/samba/panic-action %d

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0700
;browseable = no
;read only = yes
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = yes

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = no
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
;[print$]
;path = /var/lib/samba/printers
;browseable = no
;guest ok = no
;read only = yes
;write list = root
;create mask = 0644
;directory mask = 0755

;[printers]
;path = /tmp
;printable = no
;guest ok = no
;browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = no
;read only = yes
;guest ok = no

[MyFiles]
path = /media/Data/
browseable = yes
read only = yes
guest ok = no
create mask = 0600
directory mask = 0700
force user = blake
force group = blake
   read only = yes
   guest ok = no
[/PHP]

My workgroup is named NETWORK on my windows machines and I changed it last night to NETWORK on ubuntu. Also, do I need to still right click and hit share? It will not let me do this with my data partition. Any ideas what I am doing wrong?

---

### Post by jba6511 on 2007-05-30
night time experts, a little help????

---

### Post by druhboruch on 2007-06-03
I tried samba, but it was a bit slow and choppy.
You may consider xbox streaming daemon:  [http://xbmsd.sourceforge.net/](http://xbmsd.sourceforge.net/)
Deb is available and it is very easy to configure.
Works as a charm.

---

### Post by jba6511 on 2007-06-03
got as far as downloading and installing but then I am clueless. Where does it install to and how do you configure it? Sorry complete newbie to linux here. I want to share my /media/Data folder if that helps at all.

---

### Post by druhboruch on 2007-06-04
Folder /media is used by Ubuntu to mount removable volumes.
I would move my pics, mp3 and movies to the directory under my home folder:


Now all you have to do is to edit the configuration file: 

```
sudo gedit /etc/xbmcd/xbmcd.conf
```

Type in the path to your shared folder in the appropriate section and restart the daemon: 

```
sudo /etc/init.d/xbmcd restart
```

I will post my config file as soon as I get home.

---

### Post by jba6511 on 2007-06-04
thanks. I appreciate it. I will use your conf file as an example.

---

### Post by druhboruch on 2007-06-04
```
sudo gedit /etc/xbmsd/xbmsd.conf
```

Just change the following lines

Replace with your path /media/data
```
# The root directory of the server. This MUST be specified, otherwise
# the daemon won't start.
#
root /export

```


```
# The user and group that xbmsd should run as. Only applicable if
# started as root. The default user is nobody, and the default group
# is the default group of the user. The example below runs as user
# nobody and group users.
#
user root
group users
```

Restart daemon or reboot.
Enjoy.

:)

---

### Post by jba6511 on 2007-06-04
> **druhboruch said:**
> ```
sudo gedit /etc/xbmsd/xbmsd.conf
```

Just change the following lines

Replace with your path /media/data
```
# The root directory of the server. This MUST be specified, otherwise
# the daemon won't start.
#
root /export

```


```
# The user and group that xbmsd should run as. Only applicable if
# started as root. The default user is nobody, and the default group
# is the default group of the user. The example below runs as user
# nobody and group users.
#
user root
group users
```

Restart daemon or reboot.
Enjoy.

:)

do I leave it as user root or is this suppose to be changed to the user I log on as?
so:
user blake
group blake

???Sorry, newbie still.

---

### Post by druhboruch on 2007-06-04
You have to run daemon as user who has read rigths to your media files.
Root always has access to everyting, so at first you could leave it as is to make sure that everything works.

I run xbmsd as root.

If you are concerned about security, then you can change it later.
It is xbox, not  Pentagon...

---

### Post by jba6511 on 2007-06-04
i changed the first part to read

root /media/data

and left the second part alone. However, xbmc still can not find it. I updated xbmc to the latest svn build from yesterday and when I go to videos -> add source -> xbmsp and enter my info I got nothing. This might sound crazy but do I need to start the daemon or something? I rebooted after changing the conf file and then tried. I do not know why this is so hard for me.

---

### Post by behemot on 2007-06-05
Double check your changes:
Make sure that you run your daemon as root and group users.
If you run as nobody than daemon would not have access rights to your media folder.

Please restart your daemon:

```
sudo /etc/init.d/xbmsd restart
```

It will tell you if it successfully started and if not then post the error you get.

Port 1400 must be open on your server.  If you have firewall just disable it for now.

Check  your network setup.  You should be able to ping and FTP to your xbox.

I understand that you can FTP to xbox since you transferred XBMC to it.

Try to setup your XBMC as dash.

Your server should be auto-discovered by xbox.  When you add new source, just let it be discovered.  It will find it.

---

### Post by Voorhees1979 on 2008-04-25
Hi

Thanks for this info. Does anyone know how to add two paths?

I have root /media/Archive/Movies for my ripped films. But I also have another one I would like to add /media/disk/TV

But I dont know how to share these two folders from different drives at the same time.

I tried
root /media/Archive/Movies
root /media/disk/TV

but it still only showed my movies folder

Many thanks for any help

---

