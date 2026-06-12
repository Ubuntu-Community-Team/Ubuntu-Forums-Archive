---
title: "Network setup issues"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by rcane84 on 2007-10-20
Hello everyone,

I have Ubuntu installed on an older P3 desktop and Windows XP Pro on a P4 Laptop.  I have been trying to set up a network and have had some success but it is not all the way there.  From the Ubuntu desktop I am able to see the shared files on my Windows computer and am able to transfer them over no problem.  The thing is I can't do it the other way.  When I try to access what should be my Ubuntu shared folder (all of \home) I am unable to do so from XP machine.  I have followed the following setup advice for samba:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I set samba and decided to go with a fixed dhcp lease.  Here is the code (sudo gedit /etc/samba/smb.conf) I hopefully configured right. 

[global]
   ; General server settings
   netbios name = RICHARD


   workgroup = WORKGROUP
   announce version = 5.0
   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE
SO_RCVBUF=8192 SO_SNDBUF=8192

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
   valid users = %S
   create mode = 0600
   directory mode = 0755

   browseable = yes
   read only = no
   veto files = /*.{*}/.*/mail/bin/

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
server string = richard
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
   path = /home
   browseable = yes
   read only = no
   guest ok = no
   create mask = 0644

   directory mask = 0755
   force user = RICHARD
   force group = RICHARD
available = yes
public = yes
writable = no

[samba]
path = /home/samba
available = yes
browseable = no
public = yes
writable = yes


 I have tried disconnecting both the windows firewall and the Telus Internet Security firewall (internet access provider security) and it hasn’t made any difference.  I seem to be doing fine until I get to this part:

With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address>\MyFiles
NOTE: To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above. 
- Click "Finish"

I followed this I get a pop up window saying “Attempting to contact \\192.168.0.101\MyFiles...” then I have to enter my username and password and the same window asking me to enter my username and passoword pops up over and over.   I’ve tried typing “Richard” – the computer’s name instead of the ip address with no luck.  I’ve also tried varying the “MyFiles part” with \home with no luck.  I’m also running AVG free edition for linux does that make a difference?  

I’ve made sure that \home is a shared folder in Ubuntu under system>administration>shared folders.  Please let me know if any of you have some suggestions I might try.  I think I may have also done something like “ chmod 0770 \home” in the terminal.  I probably shouldn’t have though I don’t know if it wrecked it.  I can’t remember why I did it.  It was super early.

Thanks for the help!

Richard

---

