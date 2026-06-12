---
title: "Help with PROFTPD LOGIN ERROR!!"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-03-11
I read a lot of post and I still can't solve the following problem:
imagine that under system->administration I have the following
username: disappearedng
password: 1234

and my proftpd.conf file is this:

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
**UserAlias user0 disappearedng**



ServerName			"Victor's FTP"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 30

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "Welcome to Victor's FTP server; if you abuse, I will abuse you"
# This message is displayed for each access good or not
ServerIdent                  on       "Welcome to Victor's FTP server; if you abuse, I will abuse you"

# Set /home/FTP-shared directory as home directory
DefaultRoot /media/sdb1/Ebooks

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser user0
AllowUser user1
AllowUser user2
DenyALL
</Limit>

<Directory /media/>
Umask 022 022
AllowOverwrite off
	<Limit XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory># To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias user0 disappearedng
UserAlias user1 alex
UserAlias user2 manel


ServerName			"Victor's FTP"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 30

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "Welcome to Victor's FTP server; if you abuse, I will abuse you"
# This message is displayed for each access good or not
ServerIdent                  on       "Welcome to Victor's FTP server; if you abuse, I will abuse you"

# Set /home/FTP-shared directory as home directory
DefaultRoot /media/sdb1/Ebooks

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser user0
AllowUser user1
AllowUser user2
DenyALL
</Limit>

<Directory /media/>
Umask 022 022
AllowOverwrite off
	<Limit XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /media/sdb1/Ebooks>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /media/sdb1/Ebooks/uploads>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD >
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

UseIPv6 off

<Directory /media/sdb1/Ebooks>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /media/sdb1/Ebooks/uploads>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD >
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

UseIPv6 off

"


So the bold part, UserAlias user0 disappearedng, means that I should login to my ftp server with username: user0 and password 1234 right?
I have tried with username: user0 and username: disappearedng with password 1234 but still I get this login error.

HOW DO I CHANGE THE PASSWORD SO THAT I COULD LOGIN???

---

### Post by disappearedng on 2008-03-11
Can anyone help?

---

### Post by PaulFr on 2008-03-11
While I am not clear about all the ProFTPD directives, my plan of action would be:

1. First, would be to scan the FTPD logs in > ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xferlog
SystemLog            /var/log/syslog.logto see if they give any indication of errors.

2. I would try to comment out the **DefaultRoot** directives > # Set /home/FTP-shared directory as home directory
**# DefaultRoot /media/sdb1/Ebooks**

# Lock all the users in home directory, ***** really important *****
**# DefaultRoot ~**I also do not think that you can have **multiple** DefaultRoot lines unless you make them disjoint (i.e. only one such line is active for any logged in user), but I am not sure.

---

### Post by disappearedng on 2008-03-11
I tried that, but it doesn't work:

Here is my extended log:

fff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:46:48 -0400] "USER alex" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:46:51 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:46:51 -0400] "SYST" 215 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:46:52 -0400] "PORT 192,168,1,100,135,151" - -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:47:46 -0400] "USER disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:47:50 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:47:50 -0400] "SYST" 215 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:48:44 -0400] "USER disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:48:44 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:27 -0400] "USER disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:27 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:28 -0400] "USER disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:28 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:28 -0400] "USER disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:28 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:29 -0400] "USER disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:29 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:32 -0400] "USER Disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:32 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:39 -0400] "USER alex" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:39 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:42 -0400] "USER Alex" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:52:42 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:53:22 -0400] "USER disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:53:22 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:53:23 -0400] "USER disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:53:23 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:53:23 -0400] "USER disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:53:23 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:53:23 -0400] "USER disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:53:23 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:53:23 -0400] "USER disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:53:23 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:45 -0400] "USER disappearedng" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:45 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:49 -0400] "USER user0" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:49 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:49 -0400] "USER user0" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:49 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:49 -0400] "USER user0" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:49 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:49 -0400] "USER user0" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:49 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:50 -0400] "USER user0" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:50 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:50 -0400] "USER user0" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:50 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:50 -0400] "USER user0" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:50 -0400] "PASS (hidden)" 530 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:50 -0400] "USER user0" 331 -
::ffff:192.168.1.100 UNKNOWN nobody [11/Mar/2008:04:55:50 -0400] "PASS (hidden)" 530 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:05:00:25 -0400] "USER user0" 331 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:05:00:28 -0400] "PASS (hidden)" 530 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:05:00:28 -0400] "SYST" 215 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:05:00:32 -0400] "QUIT" 221 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:05:00:35 -0400] "USER user0" 331 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:05:00:35 -0400] "PASS (hidden)" 530 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:05:00:40 -0400] "USER disappearedng" 331 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:05:00:40 -0400] "PASS (hidden)" 530 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:14:00:57 -0400] "USER disappearedng" 331 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:14:00:57 -0400] "PASS (hidden)" 530 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:14:01:03 -0400] "USER user0" 331 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:14:01:03 -0400] "PASS (hidden)" 530 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:14:01:04 -0400] "USER user0" 331 -
disappearedng-server-ubuntu.local UNKNOWN nobody [11/Mar/2008:14:01:04 -0400] "PASS (hidden)" 530 -

How do I manage all my acconts effectively? The GUI under systen->user provides users only for the UBUNTU machine not the proftpd accounts right?

---

### Post by disappearedng on 2008-03-11
Funny thing,
I just created a test case called dude with password 1234.
Surprisingly, he is able to log in and the default home directory is /home/dude.

So now i am guessing that the problem is that my default directories doesn't give the permission. (I used chmod 755). Any suggestions?

---

### Post by PaulFr on 2008-03-12
I am not clear about what you are attempting to do, so I will ramble on a bit about what I think you want to do:

1. Do you want to give one user FTP access to your machine, or multiple users ?
2. If multiple users, do you want all these users to share a specific directory ?
3. I assume you do not want anonymous FTP.

Please clarify the above and attach your latest proftpd.conf file.

If you only want to give a single user access, using alias users is too much hassle; just create a real Ubuntu user using System->Administration (yes, System -> Administration shows you real Ubuntu users, not FTP users) and give this user a home directory, where you / the user can place the files. Then you need the > DefaultDirectory ~ to force the user to that home directory, so they cannot see files outside that directory.

If you want to give multiple users access, but they do not need to share a directory, my suggestion would be the same - just create the number of real users as required.

If you want to give multiple users access, but you want them to share a single directory, and you do not want to administer them as real users, then you should consider aliases. 

An example of using aliases from ProFTPD guide: ```

# Give Full Read-Write Anonymous Access to certain users
*<Anonymous /home/ftp>*

[B]AnonRequirePassword   on
AuthAliasOnly         on
AuthUsingAlias        on

[/B]# The list of authorized users.
# user/pass lookup is for each user, not password entry
# of server uid ('nobody' in this example).
[B]UserAlias             fred       nobody
UserAlias             joe        nobody

[/B][COLOR=DarkRed]<Limit ALL>
AllowAll
</Limit>

[/COLOR] *</Anonymous>*
```Here, fred and joe need to have valid passwords, and once they login with those valid passwords they have read write privileges to **/home/ftp**. If you wish to limit all users to /home/ftp, then you would add **DefaultRoot /home/ftp**.

---

### Post by disappearedng on 2008-03-12
So now my conf is like this

"
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on


# The list of authorized users.
# user/pass lookup is for each user, not password entry
# of server uid ('nobody' in this example).
UserAlias       alex    nobody
UserAlias       manel     nobody
UserAlias 	user0 	disappearedng
#UserAlias user1 alex
#UserAlias user2 manel

ServerName			"Victor's FTP"
ServerType 		 	inetd	
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 30

# Set the user and group that the server normally runs at.
User                  disappearedng
Group                 searchengine

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "So you are finally in I guess"
# This message is displayed for each access good or not
ServerIdent                  on       "Welcome to Victor's FTP server; if you abuse, I will abuse you"

# Set /home/FTP-shared directory as home directory
DefaultRoot /media/sdb1/Ebooks

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
#<Limit LOGIN>
#AllowUser disappearedng
#AllowUser alex
#AllowUser manel
#DenyALL
#</Limit>

############################################################################################
# Give Full Read-Write Anonymous Access to certain users
<Anonymous media/sdb1/Ebooks>

AnonRequirePassword   on
AuthAliasOnly         on
AuthUsingAlias        on



<Limit ALL>
AllowAll
</Limit>

 </Anonymous>
###########################################################################################
<Directory /media/sdb1/Ebooks>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /media/sdb1/Ebooks/uploads>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD >
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

UseIPv6 off
"

[I]1. Do you want to give one user FTP access to your machine, or multiple users ?
[/I]
What i want to do is to have 1 root user, me who could upload, download delete and have all the root privileges and my home directory is /media

*2. If multiple users, do you want all these users to share a specific directory ?*
RIght now yes. I want them to be able to access /media/sdb1/Ebooks so that they can download and upload

[I]3. I assume you do not want anonymous FTP.
[/I]
Yes you are right. 

*Here, fred and joe need to have valid passwords, and once they login with those valid passwords they have read write privileges to /home/ftp. If you wish to limit all users to /home/ftp, then you would add DefaultRoot /home/ftp.*
I do want to limit them so I am gonna add DefaultRoot /media/sdb1/Ebooks

This looks really complicated 
I have tried to add users "nobody with password 1234" on my system-> users
but then it says no body exist and that I still can't login with their names. 
I still can't even login with my name!
Where are the database of usernames stored and how do I modify their password? I guess system->users and groups is not working the way I wanted it to work out.

Please help me i m in desperate need of help

---

### Post by superprash2003 on 2008-03-12
why not install gproftpd.. it has a decent GUI .. may make it easier for u

---

### Post by PaulFr on 2008-03-12
I think the above post is right on the money - you should use gproftpd. It will be easier than going through the steps to get your .conf file into shape.

---

### Post by disappearedng on 2008-03-12
As a matter of fact,
I came from gproftpd.
I had the same issues with gproftpd when I tried creating a new account for my friend and they couldn't log in for the same reason. 

Since Gproftpd is based on proftpd, I realize that the problem with users access will STILL be there.

How do I do a fresh restart? Go to synaptic and the complete removal but how do I completely wipe out the users database?

Is there a location such as /etc/gproftpd/users.conf which records the users names?

---

### Post by PaulFr on 2008-03-13
Okay here goes; I tried creating a similar proftpd.conf setup on my machine, and here is what I did:

1. In a terminal, I ran the command ```
sudo adduser --home /media/sdb1/Ebooks extftp
```This will warn you that the directory already exists, and ask you for a password twice, then ask for a full name and some other details. Please supply the password, and a full name.

2. Now backup your /etc/proftpd/proftpd.conf file
3. Copy the following into it (**I have attached this as a compressed file as well**): ```

ServerName            "Victor's FTP"
 ServerType           standalone
DeferWelcome          on

MultilineRFC2228      on
DefaultServer         on
ShowSymlinks          on

TimeoutNoTransfer     600
TimeoutStalled        100
TimeoutIdle           2200

DisplayLogin          welcome.msg
DisplayChdir          .message true
ListOptions           "-l"

DenyFilter            \*.*/

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constraint.
# RequireValidShell   off

# Port 21 is the standard FTP port.
Port                  21

# To prevent DoS attacks, set maximum number of child processes to 30.
MaxInstances          30

# ---- User section

# Use this to jail all users in their homes
#
# N.B. Make sure that your user account has home set as /media
#
DefaultRoot           ~

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                 022  022
# Normally, we want files to be overwriteable.
AllowOverwrite        on

# ---- Dummy User section

# N.B. This assumes that you have created a special user, say extftp
#      using system -> users. Make sure to set the home of this user
#      to /media/sdb1/Ebooks
#
# This assumes user0, user1 and user2 will all share the same password
# (the password will be the one you set for extftp)
#
UserAlias   user0     extftp
UserAlias   user1     extftp
UserAlias   user2     extftp

# ---- Logging section

# Some logging formats
LogFormat             default "%h %l %u %t \"%r\" %s %b"
LogFormat             auth    "%v [%P] %h %t \"%r\" %s"
LogFormat             write   "%h %l %u %t \"%r\" %s %b"

TransferLog           /var/log/proftpd/xferlog
SystemLog             /var/log/proftpd/proftpd.log

# Logging file/dir access
ExtendedLog       /var/log/proftpd/access.log WRITE,READ write
# Record all logins
ExtendedLog       /var/log/proftpd/auth.log AUTH auth
```4. Now restart ProFTPD by **sudo /etc/init.d/proftpd restart**

5. First ftp with username as yourself and verify that you are put in your home directory (which I presume is /media).

6. Then ftp with username **user0** and password as the password of **extftp**. Verify that you are now in /media/sdb1/Ebooks as desired.

Hope this helps.

---

### Post by disappearedng on 2008-03-14
I did what you told me to, and I manage to get myself in.
Now when I try user0 with passwd 1234567, i can't seem to get in and it is giving me this error: Login error.
I have reinforced the password under system->users and groups but to no avail. 
I appreciate your help but I think we need to tackle the password issue here.

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

what does this mean?
for user0, do I have to give it a specific group in order to access my ftp server? 
I am really confused by how ubuntu handles usernames and passwords, why can't they just let the program verify?

What can I do about the login incorrect thing? How can I look into the passwords etc?
THanks for your help though, you have been really supportive. 
You are definitely an asset to the ubuntu community.

---

### Post by disappearedng on 2008-03-14
bump any ideas?

---

### Post by PaulFr on 2008-03-15
Interesting. I assume you have now the exact same proftpd.conf file that I sent you in my last post, not a single line less or more. If not, please post your proftpd.conf file.

Okay, then the next steps:

1. Remember that I asked you to create a real user account called **extftp**. Test that you can ftp using the **extftp** user account with the extftp password which by your post is **1234567**. You should be placed in  /media/sdb1/Ebooks as that is the home directory you specified when you created the **extftp** account.

2. If you have no errors in ftp using the **extftp** user account, that means the problems are with the UserAlias commands.
3. If you have problems  in ftp using the **extftp** user account, that means the problems are with the extftp account, or the authentication for it.

4. To get debug information for either of the cases above, I would suggest the following commands to be typed in a terminal: ```
sudo /etc/init.d/proftpd stop
sudo proftpd -nd9 2>&1 >& /tmp/proftpfd.log
```5. **Wait a few seconds**, and then in another terminal, type ```
ftp localhost
```and now try to login as user0.

6. Once you fail, type **quit** to exit your session.
7. Now in the first terminal, type **CTRL-C** to terminate the proftpd daemon.

You can now examine the log (using something like **more /tmp/proftpd.log**) to see which modules were consulted. On my machine, an excerpt of the log where I deliberately logged in with the wrong password: > *<my_hostname> -* dispatching LOG_CMD command 'USER user0' to mod_log
*<my_hostname> -* dispatching PRE_CMD command 'PASS (hidden)' to mod_core
*<my_hostname> -* dispatching PRE_CMD command 'PASS (hidden)' to mod_core
*<my_hostname> -* dispatching PRE_CMD command 'PASS (hidden)' to mod_delay
*<my_hostname> -* dispatching PRE_CMD command 'PASS (hidden)' to mod_auth
*<my_hostname> -* dispatching CMD command 'PASS (hidden)' to mod_auth
*<my_hostname> -* ROOT PRIVS at mod_auth_pam.c:289
*<my_hostname> -* RELINQUISH PRIVS at mod_auth_pam.c:464
*<my_hostname> -* ROOT PRIVS at mod_auth_unix.c:428
*<my_hostname> -* USER user0 (Login failed): Incorrect password.
*<my_hostname> -* dispatching POST_CMD_ERR command 'PASS (hidden)' to mod_delay
*<my_hostname> -* dispatching LOG_CMD_ERR command 'PASS (hidden)' to mod_log
*<my_hostname> -* dispatching LOG_CMD_ERR command 'PASS (hidden)' to mod_authSo you can see that mod_auth_unix is consulted and it rejects the login.

You can post the log file here if you cannot see any reason for the failure.

---

