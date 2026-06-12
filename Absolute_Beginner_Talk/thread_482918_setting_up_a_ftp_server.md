---
title: "setting up a ftp server"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2007-06-24
hey,

i installed proftpd server and edited the /etc/proftpd/proftpd.conf file so that it now looks like this:


#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on

ServerName			"Bogdan FTP Server"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell              	off
TimeoutLogin 			20
RootLogin 			off

#DenyFilter			\*.*/
UseFtpUsers 			off
AllowStoreRestart		on

# Use this to jail all users in their homes 
DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShells		off

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			8

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on
AuthAliasOnly 			on

UserAlias              diana   ftpuser

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

#Welcome message after succesful login
AccessGrantMsg "welcome !!!"

#Set /home/FTP-directory directory as home directory
DefaultRoot /home/FTP-directory

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser diana
DenyALL
</Limit>

<Directory /home/FTP-directory>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-directory/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-directory/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend			mysql
#</IfModule>

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

#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"

#UserAlias		diana	diana

	
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
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


problem is , when i want to connect to the server with the user

diana and the password it gives me a login failed even though i'm sure the pass is correct.
help would be appreciated :D

---

### Post by atria on 2007-06-24
You might want to post some logs. Particularly proftpd's and the relevant portion of /var/log/auth.log

---

