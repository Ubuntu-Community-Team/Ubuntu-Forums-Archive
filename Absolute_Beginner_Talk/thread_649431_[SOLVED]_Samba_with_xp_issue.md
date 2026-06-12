---
title: "[SOLVED] Samba with xp issue"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by ckennow on 2007-12-24
NOOB ALERT

I have Ubutnu Server installed with Perfect Server setup per the instructions at the HOWTO forums for Gutsy Gibbon.  Now I just need to get samba working.  I know it works cuz i had it working with the destop version of Gutsy.

Please Help I went through the samba with xp walkthrough but when I try to look at my workgroup (called UBUNTUHOME) server1 doesn't show up.  However when I restart samba server1 does show up but when I double click on it in windows it gives me the error that i don't have permission to view that computer.

The reappearance of server1 seems to be erratic upon the restart of samba.

Please tell me which files you need to see to help me troubleshoot this.  I have searched the forums and tried multiple solutions including but not limited to the removal and resetup of samba.

---

### Post by blueridgedog on 2007-12-24
I would post the file /etc/samba/smb.conf

What are the IP addresses of the two systems and are the users in common, ie, if user "Jane" is the user logged into XP, is there a corresponding user "Jane" on the server.  

Also, is the server running a firewall and can it be removed for the duration of our testing?

---

### Post by spiderbatdad on 2007-12-24
this guide will get shares working, but good luck sharing printing! [https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

---

### Post by heatpumpcontrol on 2007-12-24
Don't if this helps but make sure that the Windows user account is also a user of the server and that it has been activated (logged into) at least once on the server..... just checking.

---

### Post by blueridgedog on 2007-12-24
You would be surprised how many times people don't create matching user accounts and user credentials.  

The Samba server and the client OS's that will connect to it should share an identical set of users (with the same passwords).  Granted it can be done otherwise, but why?

---

### Post by ckennow on 2007-12-24
chad@server1:~$ cat /etc/samba/smb.conf
[global]
    ; General server settings
    netbios name = server1
    server string =
    workgroup = UBUNTUHOME
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
    path = /media/Backup/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = chad
    force group = chad

---

### Post by spiderbatdad on 2007-12-24
the windows side needs to be configured by the guide i posted above. Very carefully. step by step

---

### Post by ckennow on 2007-12-24
XP Pro IP is 192.168.1.101
Gutsy Server1 IP is  192.168.1.102

XP Pro login is chad with exact same password as ubuntu and samba login

---

### Post by blueridgedog on 2007-12-24
run sudo smbpasswd -a chad

When prompted enter the password for chad.

Let me know if things change.

---

### Post by blueridgedog on 2007-12-24
Since I am going to bed, I will leave you with a few more suggestions in case you are a night owl and the smbpasswd tip is not a home run.

What do you have in /var/log/samba?  Can you tail the error log for more information?

(tail is a linux command that basically means "show me the end of a file).

Also, for the sake of simplicity, lets setup your share a bit more wide open for testing:

[MyFiles]
path = /media/Backup/
browseable = yes
read only = no
public = yes
guest ok = yes
create mask = 0644
directory mask = 0755

Restart samba after changing the config file.

---

### Post by ckennow on 2007-12-24
root@server1:/var/log/samba# dir

cores     
log.smbd        
log.wb-SERVER1  
log.winbindd-idmap
log.nmbd  
log.wb-BUILTIN  
log.winbindd

which is the error log and what am i looking for

---

### Post by spiderbatdad on 2007-12-24
you can check the daemon.log in System-->Administration-->System Log

---

### Post by ckennow on 2007-12-24
> **spiderbatdad said:**
> you can check the daemon.log in System-->Administration-->System Log

in xp? or gutsy?

---

### Post by spiderbatdad on 2007-12-24
gusty

---

### Post by ckennow on 2007-12-25
> **spiderbatdad said:**
> this guide will get shares working, but good luck sharing printing! [https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)


chad@server1:~$ sudo mount -t cifs -o username=ubuntu,password=IIIIIIII,workgroup=MSHOME,gid=smb,uid=$USER,file_mode=770,dir_mode=770,rw //ltpc/"Shared Documents" /media/winshares
WARNING: 'file_mode' not expressed in octal.
WARNING: 'dir_mode' not expressed in octal.

---

### Post by spiderbatdad on 2007-12-25
you shouldnt have to worry about the mounting issue it configuring the windows side above those mount instructions that is important. later samba should display the shares for you under the network. You can also set those permissions manually in /smb.conf

---

### Post by spiderbatdad on 2007-12-25
those numbers should be 0777 and 0777  the author made a mistake but clarifies it somewhat below

---

### Post by ckennow on 2007-12-25
Now I have two workgroups showing up in xp one called MSHOME and the other called UBUNTUHOME.

---

### Post by ckennow on 2007-12-25
> **spiderbatdad said:**
> those numbers should be 0777 and 0777  the author made a mistake but clarifies it somewhat below

chad@server1:~$ sudo mount -t cifs -o username=ubuntu,password=IIIIIIII,workgroup=MSHOME,gid=smb,uid=$USER,file_mode=777,dir_mode=777,rw "//ltpc/Shared Documents" /media/winshares
WARNING: 'file_mode' not expressed in octal.
WARNING: 'dir_mode' not expressed in octal.

---

### Post by spiderbatdad on 2007-12-25
0777 0777

---

### Post by ckennow on 2007-12-25
oops

---

### Post by ckennow on 2007-12-25
chad@server1:/media/winshares$ stat -c %a /media/winshares
755

---

### Post by ckennow on 2007-12-25
I don't think that walkthrough is what i'm looking for.  The other one worked at one point. [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Now it doesn't work at all nor does yours

---

### Post by spiderbatdad on 2007-12-25
file shares work fine. it print sharing that seems impossible for me

---

### Post by blueridgedog on 2007-12-25
I was not aware you were trying to mount the XP share to the Ubuntu box, but spiderbatdad (from southpark?) has that covered.  

How is the mounting of the share from XP to Ubuntu?  If you doubleclick Ubuntuhome do you see the server now?  Do you see the share?

BTW:  I would name the workgroups the same thing.

Merry Christmas.

---

### Post by ckennow on 2007-12-25
I was not aware i was doing that either but I am willing to try anything.  What I am trying to do is make my 500GB backup USB Drive Available on my linux box to my xp laptop.  I don't need anything on my laptop.  I don't see the workgroup at all in xp for some reason and spiders tutorial isn't working.  Let me know what to do I will co-operate completely. I am at the mercy of the linux community.

---

### Post by spiderbatdad on 2007-12-25
sorry for the confusion on that tutorial, but it is for a clean samba and smbfs. Your /smb.conf file already has numerous changes. If you go to synaptic and remove everything samba and smb, then reinstall it all...including smbfs, smb client, and go through that guide again, I can almost guarantee you will see the windows share. You may see it anyway, without going through the set up again.

---

### Post by ckennow on 2007-12-25
No I don't want to share from XP to Gutsy I just want to share from Gutsy to XP I don't need to share anything from my laptop I want to be able to see and use my backup drive that is connected to my Gutsy box

---

### Post by ckennow on 2007-12-25
I'm an idiot. I am so sorry [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) works right I missed this part:

> -> wins support = yes

**If your box doesn't have a static ip-address, or you cannot configure your router/server to provide you with a fixed dhcp-lease, change this configuration parameter to "no".**

In this case you cannot use the benefits of WINS.

---

### Post by blueridgedog on 2007-12-25
Fantastic.

---

