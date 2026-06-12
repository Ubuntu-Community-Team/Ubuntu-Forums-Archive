---
title: "proftpd help? :("
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Stomstedt on 2006-10-15
Well, here is my situation... 

I followed the tutorial for setting up a secure FTP server with proftpd.  It works great for all of my accounts, EXCEPT for the userftp account.  I have no idea why.  I can log in with all the other users except for that one...  Please help?

---

### Post by taurus on 2006-10-15
Do you have userftp and make sure it has a shell?

```
finger userftp
```

---

### Post by Stomstedt on 2006-10-15
Login: userftp                          Name:
Directory: /home/FTP-shared             Shell: /bin/false
Last login Sun Oct 15 20:39 (EDT) on :20
No mail.
No Plan.
owner@owner-desktop:/$

---

### Post by taurus on 2006-10-15
> **Stomstedt said:**
> Login: userftp                          Name:
Directory: /home/FTP-shared             Shell: /bin/false
Last login Sun Oct 15 20:39 (EDT) on :20
No mail.
No Plan.
owner@owner-desktop:/$
Looks like userftp can't log in since it has no shell...  Maybe you want to change it to a /bin/bash and give it a password as well!

```

sudo chsh userftp
sudo passwd userftp

```

---

### Post by Stomstedt on 2006-10-15
Changing the login shell for userftp
Enter the new value, or press ENTER for the default
        Login Shell [/bin/false]: /bin/bash
owner@owner-desktop:/$ sudo passwd userftp
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

---------------------
Still having a problem :(

---

### Post by taurus on 2006-10-15
So, what does it say now when you "finger userftp"?  Also, you need to stop and start proftpd or reboot your machine again...

```

sudo /etc/init.d/proftpd stop
sudo /etc/init.d/proftpd start

```

---

### Post by Stomstedt on 2006-10-15
Login: userftp                          Name:
Directory: /home/FTP-share              Shell: /bin/bash
Never logged in.
No mail.
No Plan.

---

### Post by Stomstedt on 2006-10-15
I tried to actually log in on the username and it same something about the /home/$user directory i think something might be wrong since i have the home directory as /home/FTP-share

---

### Post by taurus on 2006-10-15
Try to reboot your machine and see if you can ftp from another machine to your machine with userftp and password that you just have created!

---

### Post by taurus on 2006-10-15
Let's have a look at your /etc/proftpd/proftpd.conf then!!!

---

### Post by Stomstedt on 2006-10-15
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron userftp

ServerName			"Lovepad"
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

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				1980

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
Umask				022	022

PersistentPasswd		off

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
DefaultRoot ~/$user

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

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/ftpd/tls.log
    TLSProtocol TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired off

    # Server's certificate
    TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off
</IfModule>

---

### Post by taurus on 2006-10-15
Okay, have a suggestion.  Why don't you change the userftp to FTP-Shared since the home directory of userftp is /home/FTP-shared.  In other words, when you ftp to your machine with userftp, it looks for /home/userftp, ~/$user, and since there is none, that's why you can't connect!  

Otherwise, link /home/userftp to /home/FTP-shared.

```
sudo ln -s /home/FTP-shared /home/userftp
```

---

### Post by Stomstedt on 2006-10-15
If i was to do that, do you know how i can make it to where the account can't go cd .. for instance?  I want them to be bound that folder and only that folder & its subfolders

---

### Post by taurus on 2006-10-15
You mean you want to jail the user in their own home directory and the subdirectories!  

I have this in my proftpd.conf...

```

# To cause every FTP user to be "jailed" (chrooted) into their home
# directory, uncomment this line.
DefaultRoot ~

```

---

### Post by Stomstedt on 2006-10-15
SO what do I do just put a # infront of that?

---

### Post by taurus on 2006-10-15
> **Stomstedt said:**
> SO what do I do just put a # infront of that?
Do you plan to put # in front of what line now?

Instead of having "DefaultRoot ~/$user" in your proftpd.conf, I only have "DefaultRoot ~" so you can remove the "/$user" and see if that would jail the user in their own home directory.

---

### Post by Stomstedt on 2006-10-15
That is what was originally there and the people was still able to go the root folder :-k

---

### Post by taurus on 2006-10-15
Have you tried using only ~?

```

DefaultRoot ~

```
Don't forget to stop and restart proftpd each time you modify proftpd.conf or reboot if you want.  Reboot is probably the safest way to go...

---

### Post by Stomstedt on 2006-10-15
That is what default is :(

---

### Post by BadDolphin on 2006-10-16
I'm having a similar issue- installed proftpd this morning, followed the doc at [http://ubuntuforums.org/showthread.php?t=51611](http://ubuntuforums.org/showthread.php?t=51611) and made sure to change the username and password in the example proftpd.conf file.  

But I cannot authenticate at all; I've tried a great many things, stopping and restarting the daemon each time.  But no matter what I do, my one and only user simply cannot authenticate.


**$ proftpd -vv**
 - ProFTPD Version: 1.2.10 (stable)
 -   Scoreboard Version: 01040002
 -   Built: do mrt 22 18:28:32 CET 2001
 -     Module: mod_core.c
 -     Module: mod_xfer.c
 -     Module: mod_auth_unix.c
 -     Module: mod_auth_file.c
 -     Module: mod_auth.c
 -     Module: mod_ls.c
 -     Module: mod_log.c
 -     Module: mod_site.c
 -     Module: mod_auth_pam.c
 -     Module: mod_quotatab.c
 -     Module: mod_ratio.c
 -     Module: mod_tls.c
 -     Module: mod_rewrite.c
 -     Module: mod_radius.c
 -     Module: mod_wrap.c
 -     Module: mod_quotatab_file.c
 -     Module: mod_delay/0.4
 -     Module: mod_readme.c
 -     Module: mod_ifsession.c
 -     Module: mod_cap/1.0


**$ proftpd -td5**
Checking syntax of configuration file
 - mod_tls/2.0.7: using OpenSSL 0.9.8a 11 Oct 2005
 - parsing '/etc/proftpd.conf' configuration
 - Compiling deny regex '\*.*/'.
 - Allocated deny regex at location 0x61f0a0.
 - warning: AuthPAMAuthoritative is deprecated
 - <Directory /home/FTP-shared>: adding section for resolved path '/home/FTP-shared'
 - <Directory /home/FTP-shared/download/*>: adding section for resolved path '/home/FTP-shared/download/*'
 - <Directory /home/FTP-shared/upload/>: adding section for resolved path '/home/FTP-shared/upload'
closet.cinci.rr.com -
closet.cinci.rr.com - Config for Hoof of the Vengeful Cow:
closet.cinci.rr.com - /home/FTP-shared
closet.cinci.rr.com -  /home/FTP-shared/download/*
closet.cinci.rr.com -   Limit
closet.cinci.rr.com -    DenyAll
closet.cinci.rr.com -   Umask
closet.cinci.rr.com -   DirUmask
closet.cinci.rr.com -   AllowOverwrite
closet.cinci.rr.com -   ShowSymlinks
closet.cinci.rr.com -   DisplayLogin
closet.cinci.rr.com -   DisplayFirstChdir
closet.cinci.rr.com -   ListOptions
closet.cinci.rr.com -   DenyFilter
closet.cinci.rr.com -   MaxClients
closet.cinci.rr.com -   MaxClientsPerHost
closet.cinci.rr.com -   MaxClientsPerUser
closet.cinci.rr.com -   MaxHostsPerUser
closet.cinci.rr.com -   AuthAliasOnly
closet.cinci.rr.com -   UserAlias
closet.cinci.rr.com -   UseFtpUsers
closet.cinci.rr.com -   AllowStoreRestart
closet.cinci.rr.com -   AccessGrantMsg
closet.cinci.rr.com -   RequireValidShell
closet.cinci.rr.com -  /home/FTP-shared/upload
closet.cinci.rr.com -   Limit
closet.cinci.rr.com -    AllowAll
closet.cinci.rr.com -   Limit
closet.cinci.rr.com -    DenyAll
closet.cinci.rr.com -   Umask
closet.cinci.rr.com -   DirUmask
closet.cinci.rr.com -   AllowOverwrite
closet.cinci.rr.com -   ShowSymlinks
closet.cinci.rr.com -   DisplayLogin
closet.cinci.rr.com -   DisplayFirstChdir
closet.cinci.rr.com -   ListOptions
closet.cinci.rr.com -   DenyFilter
closet.cinci.rr.com -   MaxClients
closet.cinci.rr.com -   MaxClientsPerHost
closet.cinci.rr.com -   MaxClientsPerUser
closet.cinci.rr.com -   MaxHostsPerUser
closet.cinci.rr.com -   AuthAliasOnly
closet.cinci.rr.com -   UserAlias
closet.cinci.rr.com -   UseFtpUsers
closet.cinci.rr.com -   AllowStoreRestart
closet.cinci.rr.com -   AccessGrantMsg
closet.cinci.rr.com -   RequireValidShell
closet.cinci.rr.com -  Limit
closet.cinci.rr.com -   DenyAll
closet.cinci.rr.com -  Umask
closet.cinci.rr.com -  DirUmask
closet.cinci.rr.com -  AllowOverwrite
closet.cinci.rr.com -  ShowSymlinks
closet.cinci.rr.com -  DisplayLogin
closet.cinci.rr.com -  DisplayFirstChdir
closet.cinci.rr.com -  ListOptions
closet.cinci.rr.com -  DenyFilter
closet.cinci.rr.com -  MaxClients
closet.cinci.rr.com -  MaxClientsPerHost
closet.cinci.rr.com -  MaxClientsPerUser
closet.cinci.rr.com -  MaxHostsPerUser
closet.cinci.rr.com -  AuthAliasOnly
closet.cinci.rr.com -  UserAlias
closet.cinci.rr.com -  UseFtpUsers
closet.cinci.rr.com -  AllowStoreRestart
closet.cinci.rr.com -  AccessGrantMsg
closet.cinci.rr.com -  RequireValidShell
closet.cinci.rr.com - Limit
closet.cinci.rr.com -  AllowUser
closet.cinci.rr.com -  DenyAll
closet.cinci.rr.com - DeferWelcome
closet.cinci.rr.com - DefaultServer
closet.cinci.rr.com - ShowSymlinks
closet.cinci.rr.com - TimeoutNoTransfer
closet.cinci.rr.com - TimeoutStalled
closet.cinci.rr.com - TimeoutIdle
closet.cinci.rr.com - DisplayLogin
closet.cinci.rr.com - DisplayFirstChdir
closet.cinci.rr.com - ListOptions
closet.cinci.rr.com - DenyFilter
closet.cinci.rr.com - UserID
closet.cinci.rr.com - UserName
closet.cinci.rr.com - GroupID
closet.cinci.rr.com - GroupName
closet.cinci.rr.com - Umask
closet.cinci.rr.com - DirUmask
closet.cinci.rr.com - AllowOverwrite
closet.cinci.rr.com - Umask
closet.cinci.rr.com - DirUmask
closet.cinci.rr.com - MaxClients
closet.cinci.rr.com - MaxClientsPerHost
closet.cinci.rr.com - MaxClientsPerUser
closet.cinci.rr.com - MaxHostsPerUser
closet.cinci.rr.com - AuthAliasOnly
closet.cinci.rr.com - UserAlias
closet.cinci.rr.com - UseFtpUsers
closet.cinci.rr.com - AllowStoreRestart
closet.cinci.rr.com - DefaultRoot
closet.cinci.rr.com - DefaultRoot
closet.cinci.rr.com - AccessGrantMsg
closet.cinci.rr.com - ServerIdent
closet.cinci.rr.com - MaxLoginAttempts
closet.cinci.rr.com - RequireValidShell
closet.cinci.rr.com - PRIVS_ROOT: unable to seteuid(): Operation not permitted
closet.cinci.rr.com - PRIVS_ROOT: unable to setegid(): Operation not permitted
closet.cinci.rr.com - PRIVS_RELINQUISH: unable to seteuid(PR_ROOT_UID): Operation not permitted
closet.cinci.rr.com - PRIVS_RELINQUISH: unable to setegid(session.gid): Operation not permitted
closet.cinci.rr.com - PRIVS_RELINQUISH: unable to seteuid(session.uid): Operation not permitted
closet.cinci.rr.com - mod_delay/0.4: error opening DelayTable '/var/run/proftpd/proftpd.delay': Operation not permitted
Syntax check complete.
closet.cinci.rr.com - PRIVS_ROOT: unable to seteuid(): Operation not permitted
closet.cinci.rr.com - PRIVS_ROOT: unable to setegid(): Operation not permitted
closet.cinci.rr.com - PRIVS_RELINQUISH: unable to seteuid(PR_ROOT_UID): Operation not permitted
closet.cinci.rr.com - PRIVS_RELINQUISH: unable to setegid(session.gid): Operation not permitted
closet.cinci.rr.com - PRIVS_RELINQUISH: unable to seteuid(session.uid): Operation not permitted
closet.cinci.rr.com - mod_delay/0.4: warning: unable to open DelayTable '/var/run/proftpd/proftpd.delay': Operation not permitted

**My config file looks like this:**
 
ServerName			"Hoof of the Vengeful Cow"
ServerType			standalone
DeferWelcome			off
MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on
TimeoutNoTransfer		1200
TimeoutStalled			1200
TimeoutIdle			2400
DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"
DenyFilter			\*.*/
PersistentPasswd		off
AuthPAMAuthoritative 		off
Port				2525
MaxInstances		12
User				nobody
Group				nogroup
Umask				022  022
AllowOverwrite			on
Umask				022	022
MaxClients 4
MaxClientsPerHost 4
MaxClientsPerUser 4
MaxHostsPerUser 4
AuthAliasOnly off
UserAlias closet userftp
UseFtpUsers off
AllowStoreRestart		on
DefaultRoot /home/FTP-shared
DefaultRoot ~

AccessGrantMsg "Welcome to the closet. Rock on."
ServerIdent                  on       "I be serveridentin"

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

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

RequireValidShell		off

After finding various mysterious things about similar problems, I think I tried disabling PAM(?), but now I'm so confused I know *less* than when I started.

---

### Post by bastiaank on 2006-11-15
Try changing the ftp users password with the 'sudo passwd' command.

After adding a user I always need to do that before proftpd lets the new user login.
:???:

---

### Post by dannyboy79 on 2006-11-17
you probably aren't able to login with ftpuser because frodon's config uses an alias, you have to use that to login!! so if you didn;t change it from his config, it is souron I believe. it's right in the begining of the config file, useralias suoron ftpuser, i think that's whay it says. also, you don't want the ftp user to have a shell, that just makes it easier for your box to be hacked. frodon's guide specifically states this! good luck

---

