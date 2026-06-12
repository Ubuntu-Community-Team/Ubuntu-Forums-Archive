---
title: "Proftpd wont allow any ftp"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by check on 2007-02-28
Hey, I'm new to linux, this is actually my first linux server install. I've been trying to get this to work for over 2 hours and Im getting really frustrated.:confused: 

I'm trying to set up a lamp server. I think everything is working fine. I have apache running and can view my website outside my domain and locally of course. I used webmin to upload the files into the correct directory and setup apache. I tried to install pro ftp and i think that went ok as well. But for some reason it isnt working. In the process of trying to get anything to work I may have installed other ftp servers as well.

so onto the questions:

1. Does anyone know of a guide (or can you just tell me) to set up the most common settings in pro ftp (preferably in conjunction with webmin)

2. If there are mulitple ftp servers installed will this cause a problem.
    a. If so can i see a list of ones installed so that i can uninstall them

Your help is much appriciated

---

### Post by scxtt on 2007-02-28
do an equivalent of "aptitude search ftp" and see what has an "i" on the left column ...
post your /etc/proftpd.conf and we'll see if there's anything missing ...
also, make sure the service is started { **sudo /etc/init.d/proftpd start** }

---

### Post by check on 2007-02-28
This is the error im getting when i try to ftp from my windows box to the server:

Connection closed by remote host.

I'm not sure what you meain by "do an equivalent of "aptitude search ftp" and see what has an "i" on the left column ..."

here is the config file:

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

ServerName			"Debian"
ServerType			inetd
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                    49152 65534

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd		off

# Be warned: use of this directive impacts CPU average load!
#
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
# UseSendFile			off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine off
</IfModule>

<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
##   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
##   # We want 'welcome.msg' displayed at login, and '.message' displayed
##   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>
<Global>
UserAlias upload thorst
UserPassword thorst t081438875
RootLogin on
</Global>

<Anonymous ~ftp>
 User            ftp
 Group            nogroup
 UserAlias          anonymous ftp
 DirFakeUser on ftp
 DirFakeGroup on ftp
 RequireValidShell      off
 MaxClients         10
 DisplayLogin        welcome.msg
 DisplayFirstChdir      .message
</Anonymous>



I did make sure the service was started like you recomended. It said it started fine but still it isnt working.

Thanks

---

### Post by check on 2007-02-28
BUMP- Anyone have any ideas? PLEASE!  

Im new and i need help

Thanks again

---

### Post by check on 2007-02-28
Oh i figured out what you meant with the aptitude. There was another ftp installed so i uninstalled it. now there is 
ftp and proftpd with an i by it. the one that was also installed was gftp. When i unistalled it though now its showing a "IDA" beside it.

Any more ideas? This is what im getting now.

C:\Documents and Settings\check>ftp 192.168.1.70
Connected to 192.168.1.70.
Connection closed by remote host.

---

### Post by scxtt on 2007-02-28
let's start out this way ... this is my /etc/proftpd.conf -- which is a bit slimmer than yours ... so if it works, try adding "features" until it stops working ... some of my config is probably different than you've setup your box - namely the 'ftp user' and 'ftp directory' - so make sure you change it to reflect a VALID ftp login account and directory ... you might also run into problems if you've installed proftpd multiple times ... i got it working a few months ago, then uninstalled it - when i reinstalled it, it REFUSED to work until i deleted EVERYTHING a "sudo slocate proftpd" returned ... so things might get tricky ...
```
[FONT="Courier New"]#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

ServerName                      "Debian"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"

DenyFilter                      \*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd               off

# Uncomment this if you would use TLS module:
#TLSEngine                      on

# Uncomment this if you would use quota module:
#Quotas                         on

# Uncomment this if you would use ratio module:
#Ratios                         on

# Port 21 is the standard FTP port.
Port                            21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default.
#DelayEngine                    off

DefaultRoot ~

#VALID LOGINS
<Limit LOGIN>
AllowUser ftp
DenyALL
</Limit>

<Directory /home/ftp>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User                                ftp
#   Group                               nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias                   anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser on ftp
#   DirFakeGroup on ftp
#
#   RequireValidShell           off
#
#   # Limit the maximum number of anonymous logins
#   MaxClients                  10
#
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin                        welcome.msg
#   DisplayFirstChdir           .message
#
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
#
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                           022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
#
# </Anonymous>[/FONT]
```

---

