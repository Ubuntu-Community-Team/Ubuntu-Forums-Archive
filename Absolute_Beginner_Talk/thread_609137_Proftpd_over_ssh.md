---
title: "Proftpd over ssh"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by thefunnyman on 2007-11-10
Ok, I am attempting to tunnel ftp via ssh ( putty ) on a windows machine to my ubuntu 7.10 desktop.  I can connect to my domain remotely without using ssh just fine, but when I introduce ssh tunneling, my ftp client connects but no file listing is displayed.  I am using Pspad's built in ftp client on my windows machine.  I have 2 configurations in Pspad, one using my domain as the server, the other using localhost as my server.  the one using my domain as the server works beautifully, but the one referencing localhost just does not create a file listing.  

I have also experienced the same problem using [ftp://localhost](ftp://localhost) as opposed to [ftp://my.domain.net](ftp://my.domain.net) and the one referencing domain works, but not localhost.  This makes me feel that there might be some type of proftpd configuration issue

proftpd.conf file:

```

# To really apply changes reload proftpd after modifications.
AllowForeignAddress on
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias userAlias userftp
MasqueradeAddress               thefunnyman.kicks-***.net
ServerName                      "matt-desktop"
ServerType                      standalone
DeferWelcome                    on

MultilineRFC2228 on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                     "-l"

RequireValidShell               off

TimeoutLogin 20

RootLogin                       off

# It's better for debug to create log files ;-)
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

#DenyFilter                     \*.*/

#DenyFilter                     \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you wa$
# Port                          1980
Port                            21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
# ServerIdent                  on       "you're at home"
ServerIdent off

# Set /home/FTP-shared directory as home directory
#DefaultRoot /home/FTP-shared
#DefaultRoot /var/www

# Lock all the users in home directory, ***** really important *****
DefaultRoot /var/www
DefaultRoot ~

MaxLoginAttempts    5


PassivePorts 60000 65535        # These ports should be safe...

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /var/www>
Umask 022 022
AllowOverwrite off
       <Limit All>
        AllowUser userftp
        Deny ALL
        </Limit>
</Directory>


#<IfModule mod_tls.c>
#   TLSEngine on
#   TLSLog /var/ftpd/tls.log
#   TLSProtocol TLSvl

#   TLSRequired off

#   TLSRSACertificateFile /etc/ftpcert/server.crt
#   TLSRSACertificateKeyFile /etc/ftpcert/server.key

#   TLSCACertificateFile /etc/ftpcert/ca.crt

#   TLSVerifyClient off
#</IfModule>


```

I followed the step by step in the following link to set up the ftp server:
[http://ubuntuforums.org/showthread.php?p=429783#post429783]()

I'm still pretty new to Ubuntu ( just a week running Windows-free ) and I'd like to be able to sit on my fat *** on the couch on my laptop and edit webpage files using Pspad.  There are also instances where I cannot use ftp access ( protocol is blocked ) and that is my reasoning for using ssh tunneling.  Can anyone give me any insight as to why ssh tunneling doesn't work?

Thanks in advance for any help.  I would be more than happy to provide any additional config information for ssh/router/etc.

---

### Post by thefunnyman on 2007-11-10
bump...

---

### Post by thefunnyman on 2007-11-11
bump again.....

---

