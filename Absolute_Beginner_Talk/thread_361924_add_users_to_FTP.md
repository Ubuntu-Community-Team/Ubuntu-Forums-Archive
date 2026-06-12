---
title: "add users to FTP?"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by ilyash on 2007-02-15
I installed proftpd... it works with the first user I created... but not the others

how do I make them all access ftp? and access only their own /home/user dirs?

Thanks

---

### Post by halitech on 2007-02-15
check here

[http://www.ubuntuforums.org/showthread.php?t=79588&highlight=proftpd]("http://www.ubuntuforums.org/showthread.php?t=79588&highlight=proftpd")

---

### Post by ilyash on 2007-02-15
hmm its saying "530 incorrect" for the other users.. here's my proftp.conf:
```

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

# Includes DSO modules
Include /etc/proftpd/modules.conf

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

# Port 21 is the standard FTP port.
Port                            21

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
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            proftpd

Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd              off

# Be warned: use of this directive impacts CPU average load!
#
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
# UseSendFile                   off

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
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
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
<Limit LOGIN>
AllowUser ilya
AllowUser anthony
AllowUser nishi
AllowUser theo
AllowUser alex
DenyALL
</Limit>

<Directory /home/ilya*>
Umask 022 022
AllowOverwrite off

        <Limit ALL>
                Order Allow,Deny
                AllowUser ilya
                Deny ALL
        </Limit>

        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>


<Directory /home/anthony*>
Umask 022 022
AllowOverwrite off

        <Limit ALL>
                Order Allow,Deny
              AllowUser anthony
                Deny ALL
        </Limit>

        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>


<Directory /home/nishi*>
Umask 022 022
AllowOverwrite off

        <Limit ALL>
                Order Allow,Deny
                AllowUser nishi
                Deny ALL
        </Limit>

        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
     DenyAll
        </Limit>
</Directory>


<Directory /home/theo*>
Umask 022 022
AllowOverwrite off

        <Limit ALL>
                Order Allow,Deny
                AllowUser theo
                Deny ALL
        </Limit>

        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>
<Directory /home/alex*>
Umask 022 022
AllowOverwrite off

        <Limit ALL>
                Order Allow,Deny
                AllowUser alex
                Deny ALL
        </Limit>

        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/shared*>
Umask 022 022
AllowOverwrite off

        <Limit ALL>
                Order Allow,Deny
       AllowUser shared
                Deny ALL
        </Limit>

        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>


```

---

### Post by ilyash on 2007-02-15
anyone?

---

### Post by ilyash on 2007-02-15
bumppp

---

### Post by halitech on 2007-02-15
do the users you have given access to actually exist as users on your system?

---

### Post by ilyash on 2007-02-16
yeah.. they can login in bash perfectly fine.

---

### Post by ilyash on 2007-02-16
it started to work... weird.. i readded the users using -m...

Another Q though... How do I give every user access to my jakarta-tomcat?
It's on /usr/local/tomcat/webapps/ROOT/

---

