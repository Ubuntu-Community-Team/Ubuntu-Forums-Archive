---
title: "Virtual Hosting With Proftpd And MySQL"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by MisakAway on 2007-03-17
I have followed [this guide]("http://howtoforge.com/proftpd_mysql_virtual_hosting"), but i have serious problems..

Here is configuration file for proftpd.conf:

[PHP]#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

# Includes DSO modules
Include /etc/proftpd/modules.conf

ServerName            "Debian"
ServerType            standalone
DeferWelcome            off

MultilineRFC2228        on
DefaultServer            on
ShowSymlinks            on

TimeoutNoTransfer        600
TimeoutStalled            600
TimeoutIdle            1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                    "-l"

DenyFilter            *.*/

# Port 21 is the standard FTP port.
Port                1980


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
MaxInstances            30

# Set the user and group that the server normally runs at.
User                proftpd
Group                ftpgroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022  022
# Normally, we want files to be overwriteable.
AllowOverwrite            on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd        off

# Be warned: use of this directive impacts CPU average load!
#
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
# UseSendFile            off

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

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User                ftp
#   Group                nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias            anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser    on ftp
#   DirFakeGroup on ftp
#
#   RequireValidShell        off
#
#   # Limit the maximum number of anonymous logins
#   MaxClients            10
#
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin            welcome.msg
#   DisplayFirstChdir        .message
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
#   #   Umask                022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
#
# </Anonymous>



DefaultRoot ~


# The passwords in MySQL are encrypted using CRYPT
SQLAuthTypes            Plaintext Crypt
SQLAuthenticate         users* groups*


# used to connect to the database
# databasename@host database_user user_password
SQLConnectInfo  ftp@localhost proftpd password


# Here we tell ProFTPd the names of the database columns in the "usertable"
# we want it to interact with. Match the names with those in the db
SQLUserInfo     ftpuser userid passwd uid gid homedir shell

# Here we tell ProFTPd the names of the database columns in the "grouptable"
# we want it to interact with. Again the names match with those in the db
SQLGroupInfo    ftpgroup groupname gid members

# set min UID and GID - otherwise these are 999 each
SQLMinID        500

# create a user's home directory on demand if it doesn't exist
SQLHomedirOnDemand on

# Update count every time user logs in
SQLLog PASS updatecount
SQLNamedQuery updatecount UPDATE "count=count+1, accessed=now() WHERE userid='%u'" ftpuser

# Update modified everytime user uploads or deletes a file
SQLLog  STOR,DELE modified
SQLNamedQuery modified UPDATE "modified=now() WHERE userid='%u'" ftpuser

# User quotas
# ===========
QuotaEngine on
QuotaDirectoryTally on
QuotaDisplayUnits Mb
QuotaShowQuotas on

SQLNamedQuery get-quota-limit SELECT "name, quota_type, per_session, limit_type, bytes_in_avail, bytes_out_avail, bytes_xfer_avail, files_in_avail, files_out_avail, files_xfer_avail FROM ftpquotalimits WHERE name = '%{0}' AND quota_type = '%{1}'"

SQLNamedQuery get-quota-tally SELECT "name, quota_type, bytes_in_used, bytes_out_used, bytes_xfer_used, files_in_used, files_out_used, files_xfer_used FROM ftpquotatallies WHERE name = '%{0}' AND quota_type = '%{1}'"

SQLNamedQuery update-quota-tally UPDATE "bytes_in_used = bytes_in_used + %{0}, bytes_out_used = bytes_out_used + %{1}, bytes_xfer_used = bytes_xfer_used + %{2}, files_in_used = files_in_used + %{3}, files_out_used = files_out_used + %{4}, files_xfer_used = files_xfer_used + %{5} WHERE name = '%{6}' AND quota_type = '%{7}'" ftpquotatallies

SQLNamedQuery insert-quota-tally INSERT "%{0}, %{1}, %{2}, %{3}, %{4}, %{5}, %{6}, %{7}" ftpquotatallies

QuotaLimitTable sql:/get-quota-limit
QuotaTallyTable sql:/get-quota-tally/update-quota-tally/insert-quota-tally

RootLogin off
RequireValidShell off[/PHP]


When i look at proftpd.log i see this:

[PHP]Mar 17 10:28:57 misak-linux proftpd[29523] misak-linux: ProFTPD killed (signal 15)
Mar 17 10:28:57 misak-linux proftpd[29523] misak-linux: ProFTPD 1.3.0 standalone mode SHUTDOWN
Mar 17 10:28:59 misak-linux proftpd[30185] misak-linux: Failed binding to 0.0.0.0, port 1980: Address already in use
Mar 17 10:28:59 misak-linux proftpd[30185] misak-linux: Check the ServerType directive to ensure you are configured correctly.
Mar 17 10:29:14 misak-linux proftpd[30198] misak-linux (89-212-114-175.dynamic.dsl.t-2.net[89.212.114.175]): FTP session closed.
Mar 17 10:31:19 misak-linux proftpd[30304] misak-linux: Failed binding to 0.0.0.0, port 1980: Address already in use
Mar 17 10:31:19 misak-linux proftpd[30304] misak-linux: Check the ServerType directive to ensure you are configured correctly.
Mar 17 10:32:59 misak-linux proftpd[30410] misak-linux: Failed binding to 0.0.0.0, port 1980: Address already in use
Mar 17 10:32:59 misak-linux proftpd[30410] misak-linux: Check the ServerType directive to ensure you are configured correctly.
Mar 17 10:33:31 misak-linux proftpd[30462] misak-linux: Failed binding to 0.0.0.0, port 1980: Address already in use
Mar 17 10:33:31 misak-linux proftpd[30462] misak-linux: Check the ServerType directive to ensure you are configured correctly.
Mar 17 10:40:13 misak-linux proftpd[30691] misak-linux: Failed binding to 0.0.0.0, port 1980: Address already in use
Mar 17 10:40:13 misak-linux proftpd[30691] misak-linux: Check the ServerType directive to ensure you are configured correctly.
Mar 17 10:40:21 misak-linux proftpd[30701] misak-linux (89-212-114-175.dynamic.dsl.t-2.net[89.212.114.175]): FTP session closed.
Mar 17 10:42:21 misak-linux proftpd[30756] misak-linux (89-212-114-175.dynamic.dsl.t-2.net[89.212.114.175]): FTP session closed.
Mar 17 10:44:21 misak-linux proftpd[30805] misak-linux (89-212-114-175.dynamic.dsl.t-2.net[89.212.114.175]): FTP session closed.
Mar 17 10:46:21 misak-linux proftpd[30864] misak-linux (89-212-114-175.dynamic.dsl.t-2.net[89.212.114.175]): FTP session closed. [/PHP]

I know something is wrong. Please help me. I had no problems with installing proftpd with virtual users posted on this forums. When i followed the guide i didn't change password to something else and i used for proftpd user password 'password'. In mysql i have created everything and is ok there. 

What it the problem?

Hmm...

---

