---
title: "Samba Trouble"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by lmlypfan on 2007-07-28
All I want to do is set up a work group to share files on at my home.
I am running a feisty on my laptop and desktop.

Here is what I get when I run testparm:

Load smb config files from /etc/samba/smb.conf
ERROR: Badly formed boolean in configuration file: "null".
lp_bool(null): value is not boolean!
Processing section "[homes]" 
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
NOTE: Service MyFiles is flagged unavailable.
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = STEVESNEWHOUSE
        passdb backend = tdbsam
        username map = /etc/samba/smbusers
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = CUPS
        wins support = Yes
        printing = cups
        print command = 
        lpq command = %p
        lprm command = 

[homes]
        valid users = %S
        read only = No
        browseable = No

[print$]
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        guest ok = Yes

[printers]
        path = /tmp
        guest ok = Yes
        printable = Yes
        browseable = No

[MyFiles]
        path = /media/samba/
        force user = YOUR_USERNAME
        force group = YOUR_USERGROUP
        read only = No
        create mask = 0644
        available = No
bo@bo-desktop:~$

---

### Post by lmlypfan on 2007-07-28
Anyone??

---

### Post by SonicSteve on 2007-07-28
Have you run smbpasswd? This creates the samba users. Without running this you will never connect.

---

### Post by lmlypfan on 2007-07-28
I created a user and set a password  with "sudo smbpasswd -a system_username
gksudo gedit /etc/samba/smbusers"

Now I can see my shared folder, but when it asks for user and pass, it doesn't accept it.  

Any help would be greatly appreciated.  Should I post my config file?

---

### Post by iver2435 on 2007-07-28
In your config file for your "MyFiles" share, where you have force user = YOUR_USERNAME and force group = YOUR_USERGROUP, I'm assuming you have meaningful values stored there.

Also, according to testparm, MyFiles is set as unavailable..... set available = yes and see where that gets you.

If those don't work post your config.

---

### Post by lmlypfan on 2007-07-29
Here is my config file.

[global]
    ; General server settings
    netbios name = bo-desktop
    
    workgroup = wookiecookie
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
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = bo
    force group = wookiecookie
available = yes
browsable = yes
public = no
writable = no

[WD USB 2]
path = /media/WD USB 2
available = yes
browsable = yes
public = yes
writable = no

---

### Post by lmlypfan on 2007-07-29
I should also note that "wookiecookie" is a workgroup created on a XP pro machince that is no longer.  

Would this mean that my ubuntu machine is a "primary domain controller"?  
I would then need to set values to the primary domain controller serction of the smb.conf file?

All I want to do is share files between 2 ubuntu machines.  Maybe a windows machine later, but most likely not.

Thanks

---

### Post by lmlypfan on 2007-07-29
I can now see the folders, but when I try to access them, "the folder contents could not be displayed"

I had to make the folders public, cause my user name and passwords were not working.  

Sadly I have been working on this simple project for too long now.

---

### Post by SonicSteve on 2007-07-29
Give me a bit of time to remember on this. It was a simple thing that I had over looked when I had the same problem when I setup feisty 7.04. It was a very simple thing, it's just not coming to me right now.

---

### Post by lintoon on 2007-07-29
I had problems with username and password not being accepted by the samba server.  It turned out to be I had a different password to log in to my local machine (XP) than the password used to connect to the samba server.

Make the uername and passwords identical on both the local system and the samba server if you already haven't.  Just something to check.

---

### Post by SonicSteve on 2007-07-30
The exact reason is still slipping my mind. Sorry,
I think it may have been something like needing to run smbpasswd on both systems. Sorry I do wish I could remember.

I also wish samba was a bit more straight forward and easier to setup.

---

### Post by iver2435 on 2007-07-31
> **lmlypfan said:**
> 
All I want to do is share files between 2 ubuntu machines.  Maybe a windows machine later, but most likely not.

If I were you, and this is your goal, I would edit your config file to look like this:

```


[global]
netbios name = bo-desktop
workgroup = wookiecookie
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
security = share
name resolve order = hosts wins bcast
wins support = yes
printing = CUPS
printcap name = CUPS
syslog = 1
syslog only = yes

[printers]
path = /tmp
printable = yes
guest ok = yes
browseable = no


[MyFiles]
path = /media/samba/
read only = no
guest ok = yes
create mask = 0644
directory mask = 0755
available = yes
browsable = yes

[WD USB 2]
path = /media/WD USB 2
available = yes
browsable = yes
public = yes
writable = no

```


This basically makes it okay for anyone to browse and read/write to your shares.  If you are going to share between two Ubuntu machines, I would use NFS personally, but then, that's me.....

Also, as an aside, I noticed that you have "read only" set to "no" (indicating you can write to the dir), then later you have writable = no .  Maybe the problem is with conflicting settings...

---

### Post by lmlypfan on 2007-07-31
iver,

I'll try that config file when I get home.  I have been looking at using NFS instead, but I'm still trying to wrap my hands around how to configure it.  

At this point I am leaning toward NFS, but will give samba one last try.

In my networks, it lists old windows networks.  Is there a way to get rid of them?  

There is only one windows machine on the LAN, it was part of both windows networks that I would like to remove.

---

### Post by lmlypfan on 2007-07-31
Thanks for all the help.

I ended up going with the NFS setup.  Finally got it on my second try.
Glad I can now share files on my LAN.

I mounted 1 directory to my laptop, but am having trouble getting a second to mount.

Its an external usb hard drive.  Here is my export file:

Any thoughts???????

# /etc/exports: the access control list for 
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#			



/home/bo/Desktop/mp3 192.168.1.21(rw) 

/media/WD USB 2 192.168.1.21(rw)

---

