---
title: "Samba issue on Arch"
date: 2016-05-29
forum: Arch and derivatives
---

### Post by Bill Vincenti on 2016-05-29
Split from [Oh no! Samba issue now on Ubuntu]("http://ubuntuforums.org/showthread.php?t=2322151")

I have similar or maybe same problem with Samba in Arch, although I think it happened with recent -Syu, I was unable to roll back effectively because so many apps got broken - i removed all of them in Arch, then rolled back Samba, smbclient, and libwbclient -2 revs to what used to work and it didn't work either so had to roll it fwd to current (and re-install the removed apps). I don't see any mention of this in Arch either. Here is the error I get in journalctl:
```
May 29 20:06:24 arch-bill gvfsd[1001]: ** (process:5132): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
```. I'm not running a Gnome environment but have quite a few gnome apps, and gdm option but use lxdm, and Xfce. What is strange is that Testparm -I shows no errors and the following agrees ```
 cat /etc/samba/smb.conf
```, ```
 pdbedit -L = bill:1000:
``` looks right, this next one seems odd its empty? 
```
 sudo smbstatus Samba version 4.4.3
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing              
----------------------------------------------------------------------------------------------------------------------------------------
Service      pid     Machine       Connected at                     Encryption   Signing     
---------------------------------------------------------------------------------------------
No locked files
``` So maybe not same issue as I don't notice any strain on my CPU, but do notice that I can most times access the Windows pc's after long delays and occasional long enough to error via Thunar network, the Windows machines and Android (Google) TV can't access my Samba shares - I don't even get the option of entering password to connect (on them) two Win7pro64's laptops, one Win10pro64 desktop, and two Google TV's, they all say the network path is not available type errors. Restarting smbd, nmbd, and winbindd services don't make any difference and they all show to restart and run without errors. So I wonder if it is a gvfs problem? Nothing changed in the latest default smb.conf.default either (I have past backups to diff against). I've found some similar bugs regarding gvfs but they are addressing different issues. So I mean no disrespect to the Ubuntu community (*I have an old Ubuntu 11.04 pc that can't run any higher (c.2002 hardware), and an Ubuntu 14.04LTS vm install*) but noticed some fellow Archers and/or past Archers here so hence this post. Thanks Folks.

---

### Post by bab1 on 2016-05-30
> **Bill Vincenti said:**
> Split from [Oh no! Samba issue now on Ubuntu]("http://ubuntuforums.org/showthread.php?t=2322151")

I have similar or maybe same problem with Samba in Arch, although I think it happened with recent -Syu, I was unable to roll back effectively because so many apps got broken - i removed all of them in Arch, then rolled back Samba, smbclient, and libwbclient -2 revs to what used to work and it didn't work either so had to roll it fwd to current (and re-install the removed apps). I don't see any mention of this in Arch either. Here is the error I get in journalctl:
```
May 29 20:06:24 arch-bill gvfsd[1001]: ** (process:5132): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
```. I'm not running a Gnome environment but have quite a few gnome apps, and gdm option but use lxdm, and Xfce. What is strange is that Testparm -I shows no errors and the following agrees ```
 cat /etc/samba/smb.conf
```, ```
 pdbedit -L = bill:1000:
``` looks right, this next one seems odd its empty? 
```
 sudo smbstatus Samba version 4.4.3
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing              
----------------------------------------------------------------------------------------------------------------------------------------
Service      pid     Machine       Connected at                     Encryption   Signing     
---------------------------------------------------------------------------------------------
No locked files
``` So maybe not same issue as I don't notice any strain on my CPU, but do notice that I can most times access the Windows pc's after long delays and occasional long enough to error via Thunar network, the Windows machines and Android (Google) TV can't access my Samba shares - I don't even get the option of entering password to connect (on them) two Win7pro64's laptops, one Win10pro64 desktop, and two Google TV's, they all say the network path is not available type errors. Restarting smbd, nmbd, and winbindd services don't make any difference and they all show to restart and run without errors. So I wonder if it is a gvfs problem? Nothing changed in the latest default smb.conf.default either (I have past backups to diff against). I've found some similar bugs regarding gvfs but they are addressing different issues. So I mean no disrespect to the Ubuntu community (*I have an old Ubuntu 11.04 pc that can't run any higher (c.2002 hardware), and an Ubuntu 14.04LTS vm install*) but noticed some fellow Archers and/or past Archers here so hence this post. Thanks Folks.
The problems sound more like a misconfiguration problems than a bug of some sort.  I don't use Arch so I can't comment on Arch specific problems.  The specific error message says the SMB location (resource) is not mounted.  Don't shot the messenger (gvfs) for providing the error code.  On most Linux distros, if you use the GUI to mount and browse Samba/Windows shares, you are using gvfs libs.  As far as I know there is no problem at the present with properly configured shares.

You mention testparm but don't provide the text output.To diagnose your problems we should see that kind of information.  I'd prefer to see the entire smb.conf file myself and the output of smbtree -d5.  Post the output of these commands```
cat /etc/samba/smb.conf

smbtree -d3
```

FYI -- If you are not using this Linux host as a AD/DC domain controller you should not need/install winbindd at all.  Having this installed can cause problems.

---

### Post by Bill Vincenti on 2016-05-30
Here is testparm:
```
bill@arch-bill ~ % testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[Arch Documents]"
Processing section "[Arch Music]"
Processing section "[Arch Pictures]"
Processing section "[Arch Videos]"
Processing section "[Arch Downloads]"
Processing section "[Arch ISO]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE

# Global parameters
[global]
    bind interfaces only = Yes
    interfaces = lo enp4s0
    server string = Samba Server
    workgroup = HOMEGROUP
    local master = No
    preferred master = Yes
    log file = /var/log/samba/%m.log
    max log size = 1000
    usershare allow guests = Yes
    usershare max shares = 10
    usershare owner only = No
    printcap name = /etc/printcap
    name resolve order = host wins bcast
    dns proxy = No
    wins support = Yes
    idmap config * : backend = tdb
    create mask = 0664
    directory mask = 0775
    force create mode = 0664
    force directory mode = 0775


[printers]
    comment = All Printers
    path = /var/spool/samba
    browseable = No
    printable = Yes


[Arch Documents]
    path = /home/bill/Documents
    veto files = /.*/
    guest ok = Yes
    read only = No


[Arch Music]
    path = /home/bill/Music
    veto files = /.*/
    guest ok = Yes
    read only = No


[Arch Pictures]
    path = /home/bill/Pictures
    veto files = /.*/
    guest ok = Yes
    read only = No


[Arch Videos]
    path = /home/bill/Videos
    veto files = /.*/
    guest ok = Yes
    read only = No


[Arch Downloads]
    path = /home/bill/Downloads
    veto files = /.*/
    guest ok = Yes
    read only = No


[Arch ISO]
    path = /home/bill/ISO
    veto files = /.*/
    guest ok = Yes
    read only = No
bill@arch-bill ~ % 
```

Ok, the empty smbstatus just means none of the other network devices were on-line, one of the TV's was but was streaming mediatomb not a samba share. So what I've done having read [this]("http://ubuntuforums.org/showthread.php?t=2237855") is removed the folder "bill" from /var/lib/samba/usershares per, and removed eth0 from interfaces in /etc/samba/smb.conf as that interface doesn't exist anymore, re-ran testparm, restarted nmbd, smbd, and winbindd services and the network is working. I don't know that it's fixed as it has been up and down but for now :D:
```
bill@arch-bill ~ % sudo smbstatus

Samba version 4.4.3
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing              
----------------------------------------------------------------------------------------------------------------------------------------
13911   bill         bill         192.168.1.102 (ipv4:192.168.1.102:58911)  NT1               -                    -                    
13928   bill         bill         192.168.1.101 (ipv4:192.168.1.101:46890)  NT1               -                    -                    
13973   bill         bill         192.168.1.103 (ipv4:192.168.1.103:50093)  SMB2_10           -                    -                    


Service      pid     Machine       Connected at                     Encryption   Signing     
---------------------------------------------------------------------------------------------
Arch Videos  13928   192.168.1.101 Sun May 29 09:02:22 PM 2016 PDT  -            -           
Arch Videos  13911   192.168.1.102 Sun May 29 08:57:21 PM 2016 PDT  -            -           
Arch Documents 13973   192.168.1.103 Sun May 29 09:06:37 PM 2016 PDT  -            -           
Arch Pictures 13928   192.168.1.101 Sun May 29 08:59:35 PM 2016 PDT  -            -           
IPC$         13928   192.168.1.101 Sun May 29 09:02:17 PM 2016 PDT  -            -           


Locked files:
Pid          Uid        DenyMode   Access      R/W        Oplock           SharePath   Name   Time
--------------------------------------------------------------------------------------------------
13973        1000       DENY_NONE  0x100081    RDONLY     NONE             /home/bill/Documents   Sheri   Sun May 29 21:06:37 2016
13911        1000       DENY_NONE  0x89        RDONLY     NONE             /home/bill/Videos   The Hunger Games Catching Fire/The Hunger Games Catching Fire [2013].mp4   Sun May 29 21:37:58 2016
13928        1000       DENY_NONE  0x89        RDONLY     NONE             /home/bill/Videos   Winter's Bone (2010)/Winter's Bone.mkv   Sun May 29 21:37:06 2016
13973        1000       DENY_NONE  0x100081    RDONLY     NONE             /home/bill/Documents   Sheri/Windows7laptop   Sun May 29 21:06:40 2016
```

---

### Post by Bill Vincenti on 2016-05-30
```
bill@arch-bill ~ % cat /etc/samba/smb.conf
[global]

  usershare path = /var/lib/samba/usershares
  usershare max shares = 10
  usershare allow guests = yes
  usershare owner only = False
  workgroup = HOMEGROUP
  server string = Samba Server
    create mask = 0664 
    directory mask = 0775 
    force create mode = 0664 
    force directory mode = 0775 
   printcap name = /etc/printcap
   load printers = yes
   log file = /var/log/samba/%m.log
   max log size = 1000
   local master = no
   preferred master = yes
 name resolve order = host wins bcast
   wins support = yes
   dns proxy = no 
 bind interfaces only = yes
 interfaces = lo enp4s0

[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = no
   guest ok = no
   writable = no
   printable = yes

[Arch Documents] 
    path = /home/bill/Documents 
    read only = No 
    guest ok = yes 
    veto files = /.*/

[Arch Music] 
    path = /home/bill/Music 
    read only = No 
    guest ok = yes 
    veto files = /.*/

[Arch Pictures] 
    path = /home/bill/Pictures 
    read only = No 
    guest ok = yes 
    veto files = /.*/

[Arch Videos] 
    path = /home/bill/Videos 
    read only = No 
    guest ok = yes 
    veto files = /.*/

[Arch Downloads] 
    path = /home/bill/Downloads 
    read only = No 
    guest ok = yes 
    veto files = /.*/

[Arch ISO]
    path = /home/bill/ISO
    read only = No
    guest ok = yes
    veto files = /.*/
```

```
bill@arch-bill ~ %  smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
added interface lo ip=::1 bcast= netmask=ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
added interface enp4s0 ip=2002:c0a8:101:0:ca60:ff:fe60:b7ed bcast= netmask=ffff:ffff:ffff:ffff::
added interface enp4s0 ip=192.168.1.110 bcast=192.168.1.255 netmask=255.255.255.0
Enter bill's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name HOMEGROUP<0x1d>
Got a positive name query response from 192.168.1.104 ( 192.168.1.104 )
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
HOMEGROUP
name_resolve_bcast: Attempting broadcast lookup for name HOMEGROUP<0x1d>
Got a positive name query response from 192.168.1.104 ( 192.168.1.104 )
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
    \\VBARCHW7PRO64          
resolve_hosts: Attempting host lookup for name VBARCHW7PRO64<0x20>
resolve_hosts: getaddrinfo failed for name VBARCHW7PRO64 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name VBARCHW7PRO64<0x20>
    \\DELL-PC                
resolve_hosts: Attempting host lookup for name DELL-PC<0x20>
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
bill@arch-bill ~ % 
```
I don't get permission denied ```
[COLOR=#000000][FONT=Ubuntu Mono]tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono] if i run the smbtree command as root and enter root password. Also the VBARCHW7PRO64 machine is a virtual machine that I don't use Samba for, it shares via virtualbox and has no problem accessing other Windows pc's on the home network.[/FONT][/COLOR]

---

### Post by Bill Vincenti on 2016-05-30
At one point I had SPNEGO=YES (or NO?) in smb.conf, the opposite of it's default although I don't see it in the smb.conf.default file, I tried it based on another Samba troubleshoot forum and when the shares still weren't working i removed it. I see it attempts to access SPNEGO in smbtree, its not in smb.conf so the failure is expected, correct? I don't know what SPNEGO is supposed to do. 
I'll see about uninstalling winbind or at least disabling it as I think it comes with libwbclient app that has some other essential components.
Thanks BAB1, I'll check back tomorrow - late here.

---

### Post by bab1 on 2016-05-30
> **Bill Vincenti said:**
> ```
bill@arch-bill ~ % cat /etc/samba/smb.conf
[global]

  usershare path = /var/lib/samba/usershares
  usershare max shares = 10
  usershare allow guests = yes
  usershare owner only = False
  workgroup = HOMEGROUP
  server string = Samba Server
    create mask = 0664 
    directory mask = 0775 
    force create mode = 0664 
    force directory mode = 0775 
   printcap name = /etc/printcap
   load printers = yes
   log file = /var/log/samba/%m.log
   max log size = 1000
   local master = no
   preferred master = yes
 name resolve order = host wins bcast
   wins support = yes
   dns proxy = no 
 bind interfaces only = yes
 interfaces = lo enp4s0

[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = no
   guest ok = no
   writable = no
   printable = yes

[Arch Documents] 
    path = /home/bill/Documents 
    read only = No 
    guest ok = yes 
    veto files = /.*/

[Arch Music] 
    path = /home/bill/Music 
    read only = No 
    guest ok = yes 
    veto files = /.*/

[Arch Pictures] 
    path = /home/bill/Pictures 
    read only = No 
    guest ok = yes 
    veto files = /.*/

[Arch Videos] 
    path = /home/bill/Videos 
    read only = No 
    guest ok = yes 
    veto files = /.*/

[Arch Downloads] 
    path = /home/bill/Downloads 
    read only = No 
    guest ok = yes 
    veto files = /.*/

[Arch ISO]
    path = /home/bill/ISO
    read only = No
    guest ok = yes
    veto files = /.*/
```

```
bill@arch-bill ~ %  smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
added interface lo ip=::1 bcast= netmask=ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
added interface enp4s0 ip=2002:c0a8:101:0:ca60:ff:fe60:b7ed bcast= netmask=ffff:ffff:ffff:ffff::
added interface enp4s0 ip=192.168.1.110 bcast=192.168.1.255 netmask=255.255.255.0
Enter bill's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name HOMEGROUP<0x1d>
Got a positive name query response from 192.168.1.104 ( 192.168.1.104 )
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
HOMEGROUP
name_resolve_bcast: Attempting broadcast lookup for name HOMEGROUP<0x1d>
Got a positive name query response from 192.168.1.104 ( 192.168.1.104 )
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
    \\VBARCHW7PRO64          
resolve_hosts: Attempting host lookup for name VBARCHW7PRO64<0x20>
resolve_hosts: getaddrinfo failed for name VBARCHW7PRO64 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name VBARCHW7PRO64<0x20>
    \\DELL-PC                
resolve_hosts: Attempting host lookup for name DELL-PC<0x20>
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
bill@arch-bill ~ % 
```
I don't get permission denied ```
[COLOR=#000000][FONT=Ubuntu Mono]tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono] if i run the smbtree command as root and enter root password. Also the VBARCHW7PRO64 machine is a virtual machine that I don't use Samba for, it shares via virtualbox and has no problem accessing other Windows pc's on the home network.[/FONT][/COLOR]
The output is fine just the way it is.  You are not supposed to have access to everything.  You should not run diagnostic routines as root.

SPNEGO is irrelevant in your case.

FYI -- the handle is bab1 not babs.

---

### Post by Bill Vincenti on 2016-05-30
Apologies for BAB1, thanks for your help. I'll reboot with winbindd disabled and see what happens today.

Stopped winbindd and disabled it. Before reboot the Windows pc's and Google TV's could connect to the Samba shares on the Arch pc, but the Arch pc could not connect to "Windows Network" both before and after stopping + disabling winbindd. Rebooting the Arch pc resulted in no connections either way (Windows pc's can't access Samba shares, Arch pc can't access Windows Network", journalctl reports:
```
May 30 13:43:55 arch-bill gvfsd[984]: ** (gvfsd:984): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refusedMay 30 13:43:55 arch-bill gvfsd[984]: ** (process:1352): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
May 30 13:43:59 arch-bill gvfsd[984]: ** (gvfsd:984): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: No such file or directory
```

and as expected then, smbstatus is once again empty and smbtree -d3:
```
bill@arch-bill ~ % sudo smbstatus
Samba version 4.4.3
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing              
----------------------------------------------------------------------------------------------------------------------------------------
Service      pid     Machine       Connected at                     Encryption   Signing     
---------------------------------------------------------------------------------------------
No locked files

bill@arch-bill ~ % smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
added interface lo ip=::1 bcast= netmask=ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
added interface enp4s0 ip=2002:c0a8:101:0:ca60:ff:fe60:b7ed bcast= netmask=ffff:ffff:ffff:ffff::
added interface enp4s0 ip=192.168.1.110 bcast=192.168.1.255 netmask=255.255.255.0
Enter bill's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name HOMEGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name HOMEGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
1 bill@arch-bill ~ %
```

Now look what happens when I power up the Windows 10 pc without logging on:
```
bill@arch-bill ~ % smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
added interface lo ip=::1 bcast= netmask=ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
added interface enp4s0 ip=2002:c0a8:101:0:ca60:ff:fe60:b7ed bcast= netmask=ffff:ffff:ffff:ffff::
added interface enp4s0 ip=192.168.1.110 bcast=192.168.1.255 netmask=255.255.255.0
Enter bill's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name HOMEGROUP<0x1d>
Got a positive name query response from 192.168.1.104 ( 192.168.1.104 )
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
HOMEGROUP
name_resolve_bcast: Attempting broadcast lookup for name HOMEGROUP<0x1d>
Got a positive name query response from 192.168.1.104 ( 192.168.1.104 )
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
    \\SHERI-LT               
resolve_hosts: Attempting host lookup for name SHERI-LT<0x20>
resolve_hosts: getaddrinfo failed for name SHERI-LT [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name SHERI-LT<0x20>
Got a positive name query response from 192.168.1.103 ( 192.168.1.103 )
Connecting to 192.168.1.103 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
    \\DELL-PC                
resolve_hosts: Attempting host lookup for name DELL-PC<0x20>
resolve_hosts: getaddrinfo failed for name DELL-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name DELL-PC<0x20>
Got a positive name query response from 192.168.1.104 ( 192.168.1.104 )
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
    \\ARCH-BILL              Samba Server
resolve_hosts: Attempting host lookup for name ARCH-BILL<0x20>
Connecting to ::1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
        \\ARCH-BILL\IPC$               IPC Service (Samba Server)
        \\ARCH-BILL\Arch ISO           
        \\ARCH-BILL\Arch Downloads     
        \\ARCH-BILL\Arch Videos        
        \\ARCH-BILL\Arch Pictures      
        \\ARCH-BILL\Arch Music         
        \\ARCH-BILL\Arch Documents     
bill@arch-bill ~ %
```

However, the Samba shares are still inaccessible to the "SHERI-LT" Windows 7 laptop. Next will log on to the W10 machine and see if it can access the Samba shares.

Win10 nor Win7 can connect to Samba shares, attached are Win10 screenshots, but now Windows Network is accessible Arch to Windows pc's - at present I'm not sure how my home network got so freaking complicated, i really don't need passwords between home pc's but not sure how to disable all that one to another, it's like Windows wants its own networks and if I set up the Linux pc as client only then I hadn't found a way to lock out files (like root system stuff) from the Windows pc's when I tried that several years ago, hence went with SMB.CONF but ever since this last update it's a battle to get shares to connect on Win machines, and to get Linux to connect to Windows pc's. When they do connect its always one way or the other and not both ways, and from the Linux pc it is very slow to connect and requires passwords at least 2x to enter a Win pc. The Google TV's are android (linux) and even they too have problem connecting when the Win pc's won't connect. I suspect something to do with W10 as smbtree responded quite differently after powering up the W10 machine. Most of the times the Win machines are not on-line, but want to make it so when they are, they'll connect to the Samba shares without issue. As mentioned, winbindd is not running and is disabled. Ok no attachments yet, the attach icon isn't working?

Windows 10 screenshots (unable to connect to Samba shares)

---

### Post by bab1 on 2016-05-30
A couple of thoughts.  Well, more than a couple on my part, but I will only address two.  ;-)

First, you shouldn't be spamming your own posts.  If you have additional thoughts to add, just edit the original post.    If you don't do this, the mods will.  You most likely won't know what is edited out.  Adding additional posts makes it infinity more difficult to follow what you are talking about.

Second,  What you are posting is a mess to diagnose.  The best thing to do is start over.  At this point it will be better if you copy the current smb.conf file to something like```
smb.conf.backup
```Then copy the original (default) smb.conf file back to the directory.  Then just add the shares to the bottom of that smb.conf file.  Do not alter anything else in the file.  Then you can add the following just under the [global] label ```
# Set name resolve order
        name resolve order = bcast

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = <workgroup name>

```
If you want to set the NETBIOS NAME so that Samba doesn't have to search for it you can add this line just below the ones above```
# Declare NetBIOS name
        netbios name = <NAME of your choice>
```...where names in this <...> are your choice.

You will need to add the correct ***create mask*** and ***directory mask*** settings to each share definition.  These settings are not global settings so add them only to each share.  These are the settings I would use```
        create mask = 0664
        directory mask = 0775

```
No WINS is needed in a simple LAN and nothing other than bcast in needed to resolve the NETBIOS NAMES.  Nothing else needs to be done.  All the other default settings should work.

To restart the Samba file sharing daemon (smbd) you use this command```
sudo service smbd restart
```

You only need to post the output of the following 2 commands```
smbtree -d3

smbclient -L 192.168.1.110
```

---

### Post by Bill Vincenti on 2016-05-30
@ BAB1, I'll test your recommendations later tonight, I didn't see the above post when I posted this. I'll edit from here out to minimize spamming.

OK I followed all the directions above excluding the NETBIOS option - is there a Net BIOS name somewhere on the network or on the Linux pc that would be used, or just make up any name?
Here are the results of the new config per > [COLOR=#000000]You only need to post the output of the following 2 commands[/COLOR]
```
bill@arch-bill ~ % smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
added interface enp4s0 ip=2002:c0a8:101:0:ca60:ff:fe60:b7ed bcast= netmask=ffff:ffff:ffff:ffff::
added interface enp4s0 ip=192.168.1.110 bcast=192.168.1.255 netmask=255.255.255.0
Enter bill's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name HOMEGROUP<0x1d>
Got a positive name query response from 192.168.1.104 ( 192.168.1.104 )
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
HOMEGROUP
name_resolve_bcast: Attempting broadcast lookup for name HOMEGROUP<0x1d>
Got a positive name query response from 192.168.1.104 ( 192.168.1.104 )
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
    \\VBARCHW7PRO64          
name_resolve_bcast: Attempting broadcast lookup for name VBARCHW7PRO64<0x20>
    \\SHERI-LT               
name_resolve_bcast: Attempting broadcast lookup for name SHERI-LT<0x20>
Got a positive name query response from 192.168.1.103 ( 192.168.1.103 )
Connecting to 192.168.1.103 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
    \\DELL-PC                
name_resolve_bcast: Attempting broadcast lookup for name DELL-PC<0x20>
Got a positive name query response from 192.168.1.104 ( 192.168.1.104 )
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
    \\ARCH-BILL              Samba Server
name_resolve_bcast: Attempting broadcast lookup for name ARCH-BILL<0x20>
Got a positive name query response from 192.168.1.110 ( 192.168.1.110 )
Connecting to 192.168.1.110 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
        \\ARCH-BILL\bill               Home Directories
        \\ARCH-BILL\IPC$               IPC Service (Samba Server)
        \\ARCH-BILL\Arch ISO           
        \\ARCH-BILL\Arch Downloads     
        \\ARCH-BILL\Arch Videos        
        \\ARCH-BILL\Arch Pictures      
        \\ARCH-BILL\Arch Music         
        \\ARCH-BILL\Arch Documents     

bill@arch-bill ~ % smbclient -L 192.168.1.110
Enter bill's password: 

Domain=[HOMEGROUP] OS=[Windows 6.1] Server=[Samba 4.4.3]

    Sharename       Type      Comment
    ---------       ----      -------
    Arch Documents  Disk      
    Arch Music      Disk      
    Arch Pictures   Disk      
    Arch Videos     Disk      
    Arch Downloads  Disk      
    Arch ISO        Disk      
    IPC$            IPC       IPC Service (Samba Server)
    bill            Disk      Home Directories
Domain=[HOMEGROUP] OS=[Windows 6.1] Server=[Samba 4.4.3]

    Server               Comment
    ---------            -------
    ARCH-BILL            Samba Server

    Workgroup            Master
    ---------            -------
    HOMEGROUP            
bill@arch-bill ~ % 
```
[COLOR=#000000]
OK, it is working both ways, I commented out this section in smb.conf as it otherwise puts all the dot config files accessible to the network and more-less defeats the purpose of adding exclusive shares.
[/COLOR]```
#============================ Share Definitions ==============================
[homes]
   comment = Home Directories
   browseable = no
   writable = yes
```

I find in [Samba Chapter 5]("https://www.samba.org/samba/docs/man/manpages/smb.conf.5.html") the reference to this setting, so the other machines do not need to be listed by their NETBIOS names in smb.conf, just one name, correct?
> [COLOR=#000000]If you want to set the NETBIOS NAME so that Samba doesn't have to search for it you can add this line just below the ones above[/COLOR][COLOR=#000000]Code:
# Declare NetBIOS name
        netbios name = <NAME of your choice>[/COLOR]

```
nmblookup -A <IP address>
```

SOLVED: by renaming the smb.conf to smb_conf.old after updating Samba, libwbclient, and smbclient. Copied smb.conf.default --> smb.conf.master, updated smb.conf.master per BAB1 instructions, then ran:```
# testparm -s smb.conf.master > smb.conf
``` to generate new config file, restarted nmbd and smbd services, checked Samba (with other pc's on network up and running) with ```
% smbtree -d3
``` and ```
smbclient -L <ip address of Samba server>
``` and verified all connections.

---

