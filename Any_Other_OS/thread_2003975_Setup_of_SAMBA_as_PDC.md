---
title: "Setup of SAMBA as PDC"
date: 2012-06-15
forum: Any Other OS
---

### Post by umair4a1 on 2012-06-15
Hello Every one.
I need a help to setup samba server as primary domain controller, I configured samba as
file server with no issues. but unable to find the way to set as PDC. Need a sample of someones smb.conf file so I can paste it.  I tried my best to search but no luck yet. 
Any Help in this regard will highly appreciated.
PC specification is:
Intel Dual Core, 1 GB RAM, 120 HDD
Linux Mint 13 (I know tht its based on Ubuntu 12.04 LTS so the steps will be similar)

Regards
UMAIR

---

### Post by houstonbofh on 2012-06-15
Did you try this? [https://help.ubuntu.com/community/SettingUpSambaPDC](https://help.ubuntu.com/community/SettingUpSambaPDC)

---

### Post by umair4a1 on 2012-06-15
> **houstonbofh said:**
> Did you try this? [https://help.ubuntu.com/community/SettingUpSambaPDC](https://help.ubuntu.com/community/SettingUpSambaPDC)

Hi Thnx for reply. 
But as i mentioned that I need a sample already configured smb.conf file as I m not an expert user.  here is my smb.con file.
(note: when typed in terminal $ dnsdomainname, its shows the name linuxmint-domain where I set the domain name as MYGROUP
 [global] 
 Put your [[COLOR=darkgreen]domain[/COLOR][COLOR=darkgreen] [/COLOR][COLOR=darkgreen]name[/COLOR]]("http://www.enterprisenetworkingplanet.com/netos/article.php/1151091/Build-A-Primary-Domain-Controller-With-Samba-Part-2.htm#") and server hostname here: 
 # workgroup = NT-Domain-Name or Workgroup-Name
 **workgroup = MYGROUP**
 **netbios name = HOSTNAME**  
 # server string is the equivalent of the NT Description field
 **server string = Samba PDC %v %h **
 %v displays the Samba version number,  %h displays the hostname. This shows up in Network Neighborhood. See **man smb.conf** for a full explanation of all variable substitutions. Or say anything you want:
 **server string = Carla's Samba server, and a darn fine one it is**  
 Define subnets:
 # This option is important for security... 
 **hosts allow = 192.168.1., 127.**
 or 
 ** hosts allow = 192.168.1.0, 127.0.0.1/255.255.255.0**  
The localhost 127.0.0.1 will always be allowed access, unless denied by a "hosts deny" option. Use space, comma, or tab delimiting. Individual IPs can be excluded here with the EXCEPT keyword:  
**hosts allow = 192.168., EXCEPT 192.168.1.100**  
 # Put a capping on the size of the log files (in Kb).
   **max log size = 50**  
Side note: I like to isolate /var in its own partition, to prevent  crashes if something causes a log file to grow hugely, such as a DOS  attack or other mayhem.  
 # Security mode...
    **security = user**  
 # You may wish to use password encryption....
    **encrypt passwords = yes**  
   **smb passwd file = /etc/samba/smbpasswd** 
 # The following are needed to allow password changing from Windows to # update the Linux system password also.  
  **unix password sync = yes**  
  **passwd program = /usr/bin/passwd %u**  
  **passwd chat = *New*password* %n\n *Please*retype*new*password* %n\n *password*successfully*updated***  
 # Browser Control Options:  
   **local master = yes**  

 #OS Level ...  
    **os level = 64** 
 # Domain Master specifies Samba to be the Domain Master Browser....  
   ** domain master = yes **  
 # Preferred Master ...  
    **preferred master = yes** 
 # Enable this if you want Samba to be a domain logon server for 
# Windows95 workstations.  
  **domain logons = yes**  
 # Where to store roving profiles (only for Win95 and WinNT)
#        %L substitutes for this servers netbios name, %U is username
#        You must uncomment the [Profiles] share below
 ** logon path = \\%L\Profiles\%U**  
 Add these lines:
**logon home = \\%L\%U**
**logon drive = H: **(or whatever you like)
**logon script = netlogon.bat** 
 #=== shares ===
[B][homes]
   comment = Home Directories
   browseable = no
   writable = yes
   valid users = %S
   create mode = 0664
   directory mode = 0775[/B] 
 [B][netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   writable = no
   share modes = no[/B] 
 [B][Profiles]
    path = /home/samba/profiles 
    browseable = no[/B]


Can any body Help me that what I should do Next?
Regards
UMAIR

---

### Post by zeljkojagust on 2012-06-15
Here's mine; works like a charm.

[global]
        netbios name      = servername
        server string        = SERVERNAME
        workgroup            = domainname

        interfaces              = 192.168.0.1 127.0.0.1
        bind interfaces only    = yes
        hosts allow             = 192.168. 127.

        os level                = 200
        domain logons           = yes
        preferred master        = yes
        wins support            = yes
        name resolve order      = wins bcast
        time server        = yes
        reset on zero vc    = yes
        deadtime        = 15
        block size        = 4096
        host msdfs        = no
        dos charset        = CP852
        share modes        = no
        wide links        = no

        passdb backend          = tdbsam:/var/lib/samba/passdb.tdb
        username map            = /etc/samba/smbusers

        logon path              = \\servername\Profiles\%U
        logon script        = %U.bat

        vfs objects        = extd_audit, recycle

        recycle:repository      = .recycle
        recycle:keeptree        = Yes
        recycle:touch           = Yes
        recycle:versions        = Yes
        recycle:directory_mode  = 770
        recycle:subdir_mode     = 770
        recycle:exclude         = *.tmp, *.temp

        log file                = /var/log/samba/samba.%U.%m
        max log size            = 10240
        log level               = 1 vfs:1
        syslog                  = 0

#     printing        = cups
        load printers           = no
        show add printer wizard = no
#     disable spools        = yes
#     printcap name        = cups
#     printcap cache time     = 0

        socket options          = TCP_NODELAY 
        use sendfile            = yes
        add machine script    = /usr/sbin/adduser --quiet --force-badname --firstuid 95000 --lastuid 99989 --ingroup domcomp --shell /bin/false --home /var/lib/samba --no-create-home --disabled-password --disabled-login --gecos "" %u
        
#[printers]
#    path            = /var/spool/samba
#    guest ok        = yes
#    writable        = yes
#    printable        = yes
#    printer admin        = root, @domadmin
    
#[print$]
#    path            = /var/lib/samba/printers
#    browseable        = yes
#    guest ok        = yes
#    read only        = no

[netlogon]
        path                    = /var/lib/samba/netlogon
        guest ok                = yes
        browseable              = no
        share modes        = no
        available        = yes

[Profiles]
        path                    = /media/storage/Profiles
        read only               = no
        create mask             = 0600
        directory mask          = 0700
        profile acls            = yes
        public                  = no
        browseable        = no
        veto files              = /.recycle/
        available        = yes

[First_Share]
        path                    = /media/storage/FirstShare
        force group             = +sharegroup
        write list        = +sharegroup
        read list        = +sharegroupro
        valid users        = +sharegroup, +sharegroupro
        available        = yes
        include                 = /etc/samba/smb_common_share_settings.conf

My smb_common_share_setting.conf contains the following:

    veto files              = /.Temporary/.recycle/
    read only               = no
    create mask             = 0664
    directory mask          = 0775
    security mask           = 0664
    directory security mask = 0775
    force unknown acl user  = yes
    acl map full control    = yes
    dos filemode            = yes
    inherit acls            = yes
    inherit permissions     = yes
    map acl inherit         = yes
    store dos attributes    = yes
    ea support              = yes
    map hidden              = no
    map system              = no
    map archive             = no
    map readonly            = no
    public                  = no


Be shure to check what options you need, and based on that adjust the configuration. Also don't forget to create a Windows-to-Unix group mappings, for instance to map Windows "Domain Admins" to Unix "domadmin" group you would execute the following command:

net groupmap add type=domain rid=512 ntgroup="Domain Admins" unixgroup=domadmin

All that and many more is described in official samba configuration, but feel free to ask if something is not clear.

---

### Post by umair4a1 on 2012-06-15
[zeljkojagust]("http://ubuntuforums.org/member.php?u=1502220")
Thnx alot for the reply:
I copied ur smb.conf file and restart the samba server.
But still I m not able to connect xp machine to samba PDC, Can you tell me that how 
to check that samba PDC working without any error? I m posting a screen shot.

---

### Post by umair4a1 on 2012-06-15
> **umair4a1 said:**
> [zeljkojagust]("http://ubuntuforums.org/member.php?u=1502220")
Thnx alot for the reply:
I copied ur smb.conf file and restart the samba server.
But still I m not able to connect xp machine to samba PDC, Can you tell me that how 
to check that samba PDC working without any error? I m posting a screen shot.

zeljkojagust: I think its very hard to figure it out. Just supposed that I have a new ubuntu installed machine, which packages and steps I need to setups samba PDC?
If u or any other guy can explain in step by step thn hope that It will solve my problem:
Thnx in Advance
UMAIR

---

### Post by zeljkojagust on 2012-06-15
You're quite right, it's not so easy to figure it out. As it may seem at first as a simple procedure, on the other hand Samba is a pretty advanced piece of software with many features to consider. I urge you to start reading official documentation on [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/) and use my configuration as a reference. I can tell you what to do but without you really understand what to do it does not make much sense. Hope you understand.

---

### Post by umair4a1 on 2012-06-18
> **zeljkojagust said:**
> You're quite right, it's not so easy to figure it out. As it may seem at first as a simple procedure, on the other hand Samba is a pretty advanced piece of software with many features to consider. I urge you to start reading official documentation on [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/) and use my configuration as a reference. I can tell you what to do but without you really understand what to do it does not make much sense. Hope you understand.

Zeljkojagust:
I carefully read the the contents, which u share. I have just installed a fresh ubuntu. 
the scenario ( which i want to setup is )
ubuntu work as primary domain controller with windows xp clients
network interfaces 
host ip: 10.0.11.18 
hosts allow 10.0.11.19 to 10.0.11.100
netmast 255.0.0.0
samba users (e.g user1, user2)
(I can add a samba user n change directory permissions as per requiremnet of SAMBA)
kindly guide me step by step to achieve above mentioned setup.  
Looking for quick n positive response.
Thnx in Advance. 
Regards
UMAIR

---

### Post by bab1 on 2012-06-18
Are you trying to set up NT4 style domain domain administration of users? if so, it is fully explained [**_[COLOR="RoyalBlue"]here[/COLOR]_**]("http://www.samba.org/samba/docs/man/Samba-Guide/small.html").

This is part of the *Samba-3 by Example *series that starts [**_[COLOR="RoyalBlue"]here[/COLOR]_**]("http://www.samba.org/samba/docs/man/Samba-Guide/index.html").

Edit:  I just looked at the Thumbnail attached to post #5.  The domain listed there is NOT the same type of domain as a NT4 style domain.  The domain in that picture is an Active Directory (AD) style domain that is used by default  for all Windows clients after Windows 2000.  Windows NT4 (PDC) is not the same as Windows AD (LDAP/DNS).  You need to select WORKGROUP instead of DOMAIN to use the services of an NT4 style PDC.

---

### Post by umair4a1 on 2012-06-18
> **bab1 said:**
> Are you trying to set up NT4 style domain domain administration of users? if so, it is fully explained [**_[COLOR=RoyalBlue]here[/COLOR]_**]("http://www.samba.org/samba/docs/man/Samba-Guide/small.html").

This is part of the *Samba-3 by Example *series that starts [**_[COLOR=RoyalBlue]here[/COLOR]_**]("http://www.samba.org/samba/docs/man/Samba-Guide/index.html").

Edit:  I just looked at the Thumbnail attached to post #5.  The domain listed there is NOT the same type of domain as a NT4 style domain.  The domain in that picture is an Active Directory (AD) style domain that is used by default  for all Windows clients after Windows 2000.  Windows NT4 (PDC) is not the same as Windows AD (LDAP/DNS).  You need to select WORKGROUP instead of DOMAIN to use the services of an NT4 style PDC.
bob1:
thnx for reply n information:
I will set the smb.conf file as u mentioned also check the links which u mentioned thn 
will post the results soon
thanks
UMAIR

---

### Post by umair4a1 on 2012-06-19
Hello Guys,
I manage to configure samba as Primary Domain Controller, but the problem which 
I m facing now is user profiles. When I open My Computer in xp client , it shows me a Z drive which I mentioned for user profile, but it shows my linux machines Home directory, Also it shows the following error message when ever I Logged In or Logout.
Hope that somebody can help me to solve this:
(Note: my smb.conf file is as under, also posting a screenshots for refence)

[global]
    workgroup = home
    netbios name = UMAIR
;    passdb backend = tdbsam
;    printcap name = cups
    add user script = /usr/sbin/useradd -m %u
    delete user script = /usr/sbin/userdel -r %u
    add group script = /usr/sbin/groupadd %g
    delete group script = /usr/sbin/groupdel %g
    add user to group script = /usr/sbin/groupmod -A %u %g
    delete user from group script = /usr/sbin/groupmod -R %u %g
    add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody %u
# Note: The following specifies the default logon script.
# Per user logon scripts can be specified in the user account using pdbedit
    logon script = scripts\logon.bat
# This sets the default profile path. Set per user paths with pdbedit
    logon path = \\%L\Profiles\%U
    logon drive = Z:
    logon home = \\%L\%U
    domain logons = Yes
    os level = 35
    preferred master = Yes
    domain master = Yes
    idmap uid = 15000-20000
    idmap gid = 15000-20000
;    printing = cups
    server string = %h linuxmint
    username map = /etc/samba/smbusers
    security = user
;    encrypt passwords = yes
;    guest ok = no
;    guest account = nobody



[homes]
    comment = Home Directories
    valid users = %S
    read only = No
    browseable = No

#[printers]
#    comment = All Printers
#    path = /var/spool/samba
#    printer admin = root, maryo
#    create mask = 0600
#    guest ok = Yes
#    printable = Yes
#    browseable = No
#[print$]
#    comment = Printer Drivers Share
#    path = /var/lib/samba/drivers
#    write list = maryo, root
#    printer admin = maryo, root
# Needed to support domain logons

[netlogon]
    comment = Network Logon Service
    path = /var/lib/samba/netlogon
    admin users = root
    guest ok = Yes
    browseable = No

# For profiles to work, create a user directory under the path
# shown. i.e., mkdir -p /var/lib/samba/profiles/maryo
[Profiles]
    comment = Roaming Profile Share
    path = /var/lib/samba/profiles
    read only = No
    profile acls = Yes

Looking for positive response. 
Thnx in advance

---

### Post by umair4a1 on 2012-06-25
Hello Every One:
Refer to my Previous Post.
I just manage to solve the issue of roaming profiles with just a minor changes in 
my smb.conf file. 
here is my smb.con file. 
NOTE: (the purpose of the posting of smb.conf file is that may be it will help some one) 
[global]
    workgroup = home
    netbios name = UMAIR
    passdb backend = tdbsam
;    printcap name = cups
    add user script = /usr/sbin/useradd -m %u
    delete user script = /usr/sbin/userdel -r %u
    add group script = /usr/sbin/groupadd %g
    delete group script = /usr/sbin/groupdel %g
    add user to group script = /usr/sbin/groupmod -A %u %g
    delete user from group script = /usr/sbin/groupmod -R %u %g
    add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody %u
# Note: The following specifies the default logon script.
# Per user logon scripts can be specified in the user account using pdbedit
#    logon script = scripts\logon.bat
# This sets the default profile path. Set per user paths with pdbedit
    
    log file = var/log/samba/log.%m

    logon path = \\%N\%U\profiles
    logon drive = Z:
    logon home = \\%N\%U
    domain logons = Yes
    os level = 35
    preferred master = yes
    domain master = yes
    local master = yes
;    idmap uid = 15000-20000
;    idmap gid = 15000-20000
;    printing = cups
    server string = %h linuxmint
    username map = /etc/samba/smbusers
    security = user
    encrypt passwords = yes
    guest ok = no
;    guest account = nobody



[homes]
    comment = Home Directories
#    path = /home/umair
#    valid users = %S
    writeable = yes
    browseable = no

#[printers]
#    comment = All Printers
#    path = /var/spool/samba
#    printer admin = root, maryo
#    create mask = 0600
#    guest ok = Yes
#    printable = Yes
#    browseable = No
#[print$]
#    comment = Printer Drivers Share
#    path = /var/lib/samba/drivers
#    write list = maryo, root
#    printer admin = maryo, root
# Needed to support domain logons

#[netlogon]
#    comment = Network Logon Service
#    path = /var/lib/samba/netlogon
#    admin users = root
#    guest ok = Yes
#    browseable = No
#
[netlogon]
    path = /home/netlogon
    read only = yes
    share modes = no
    guest ok = yes

# For profiles to work, create a user directory under the path
# shown. i.e., mkdir -p /var/lib/samba/profiles/maryo
#[Profiles]
#    comment = Roaming Profile Share
#    path = /var/lib/samba/profiles
#    read only = No
#    profile acls = Yes
#    guest ok = yes
#    browseable = no
#    create mask = 0600
#    directory mask = 0700
[profiles]
browseable = no
path = /home/profiles
create mask = 0600
directory mask = 0700
#writable = yes
profile acls = yes


UMAIR

---

