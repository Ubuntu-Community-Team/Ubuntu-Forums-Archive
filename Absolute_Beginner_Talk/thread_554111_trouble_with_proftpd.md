---
title: "trouble with proftpd"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by pmcjury on 2007-09-18
I recently installed proftpd, on ubuntu 7.04.  Everything has been going great other then trying to configure my FTP server.  I installed proftpd using apt-get, and i thought I changed the .conf file correctly, but everytime i try to log on to the server it kicks out a 530 error and logs out. I have tried to change a bunch of stuff in the config and am still not having any luck.  any help/tips would be greatly appreciated

---

### Post by jnorth on 2007-09-18
> **pmcjury said:**
> I recently installed proftpd, on ubuntu 7.04.  Everything has been going great other then trying to configure my FTP server.  I installed proftpd using apt-get, and i thought I changed the .conf file correctly, but everytime i try to log on to the server it kicks out a 530 error and logs out. I have tried to change a bunch of stuff in the config and am still not having any luck.  any help/tips would be greatly appreciated

Have you looked at the logs? (I don't know if this is actually the default directory, might want to check the conf file and see what the log facility is).```
sudo cat /var/log/proftpd/proftpd.log
```

Maybe also post your /etc/proftpd/proftpd.conf file```
sudo cat /etc/proftpd/proftpd.conf
```

We kind of need some more details to know what is going on.  Error 530 is usually an issue with the user setup IME.

---

### Post by pmcjury on 2007-09-18
here is the output from my log file
Sep 10 05:00:01 m4carbine proftpd[5860] m4carbine.rochester.rr.com: error setting IPV6_V6ONLY: Protocol not available
Sep 10 05:00:01 m4carbine proftpd[5860] m4carbine.rochester.rr.com: ProFTPD 1.3.0 (stable) (built Thu Mar 8 03:01:15 UTC 2007) standalone mode STARTUP
Sep 10 05:14:03 m4carbine proftpd[5860] m4carbine.rochester.rr.com: ProFTPD killed (signal 15)
Sep 10 05:14:03 m4carbine proftpd[5860] m4carbine.rochester.rr.com: ProFTPD 1.3.0 standalone mode SHUTDOWN
Sep 18 21:15:44 m4carbine proftpd[5514] m4carbine.rochester.rr.com: error setting IPV6_V6ONLY: Protocol not available
Sep 18 21:15:44 m4carbine proftpd[5514] m4carbine.rochester.rr.com: ProFTPD 1.3.0 (stable) (built Thu Mar 8 03:01:15 UTC 2007) standalone mode STARTUP
Sep 18 21:24:58 m4carbine proftpd[5514] m4carbine.rochester.rr.com: ProFTPD killed (signal 15)
Sep 18 21:24:58 m4carbine proftpd[5514] m4carbine.rochester.rr.com: ProFTPD 1.3.0 standalone mode SHUTDOWN


and her is my conf file
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias colt userftp

ServerName                      "ChezFrodon"
ServerType                      standalone
DeferWelcome                    on

MultilineRFC2228 on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer 600
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

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port                            1980

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
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

---

