---
title: "Proftp problem....really very tired fighting"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by animesh on 2006-04-11
i was trying to add more user accounts with different usernames and passwords using conf files given in the HOW TO thread. Also i don't know where to give passwords.....i have been trying to configure proftpd for a long time but could get only one account working that too anonymous...now when i tried again to introduce new users i am stuck........ 

How do i add more than 1 user with diff usernames and passwords

Searched the net ......the proftp guide itself is very confusing....put in a lot of fight with no results.....](*,) ](*,) ](*,) ](*,) ](*,) :( :( 

Please help me configure proftpd

```

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 
AuthAliasOnly                   on
UserAlias Junta userftp
UserAlias UPLOAD userftp1


ServerName			"BATMAN'S DEN"
ServerType			standalone
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		40
TimeoutStalled			100
TimeoutIdle			40

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/
DefaultRoot                       ~

AllowStoreRestart		on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			10

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
#DelayEngine 			off

MaxClientsPerUser 5
AccessGrantMsg "Welcome to BATMAN'S DEN"

DefaultRoot /home/ftp

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp userftp1 
DenyALL
</Limit>



<Directory /home/ftp/Junta/*>
Umask 022 022
AllowOverwrite off
<Limit ALL>
		Order Allow,Deny
		AllowUser userftp 
		Deny ALL
	</Limit>
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/ftp/Upload/>
Umask 022 022
AllowOverwrite on
 <Limit ALL>
		Order Allow,Deny
		AllowUser userftp1 
		Deny ALL
	</Limit>
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

```

---

### Post by nalmeth on 2006-04-11
Sorry don't know much about these details..
I'd say try gftp! :D
Sorry

---

### Post by animesh on 2006-04-11
[QUOTE=nalmeth]Sorry don't know much about these details..
I'd say try gftp! :D
Sorry[/QUOTE]

are you serious.......??? and if you don't know kindly don't take the pain of replying.

---

### Post by taurus on 2006-04-11
[QUOTE=nalmeth]Sorry don't know much about these details..
I'd say try gftp! :D
Sorry[/QUOTE]
Gftp is a client while proftpd is a ftp server!!!  If you want to ftp to another machine using gftp, you NEED to install an ftp server first and one of them is proftpd while vsftpd is another.  So, can't get proftpd to work has nothing to do with gftp.

As far as I know, I have to log into your machine if you want to create an additioonal accounts using adduser command!  Try something like this from a terminal...
```

sudo adduser -m john
sudo passwd john

```
Now, see if you can ftp to your machine from another one using john!

---

### Post by animesh on 2006-04-11
thanks,but i think this is for adding new user in the system ...not in ftpserver

i tried it though  :D (just sheer desperation to get proftp working properly) and found out that it added a new user to the system...not to the ftpserver
 
any proftp guys around...........???

---

### Post by Prozzy on 2006-04-11
Proftpd use the user accounts added in linux for users.

So you will need to add a new user to the system for it to work. If you read the howto for proftpd posted in this forum it says you can just give it "a non-real homedir". 

An alternative to proftpd could be glftpd, there you can do "site adduser <name> <password>" for adding users. Search the forum there is a howto for glftpd i think.

---

### Post by taurus on 2006-04-11
Are you talking about creating an account with a home directory in /home/ftp/username instead of /home/username?  If that's what you want, /home/ftp/username, then you can use the -d option in adduser...

---

### Post by nalmeth on 2006-04-11
>  Gftp is a client while proftpd is a ftp server!!!
:oops: my bad. sorry again

This links may be helpful/relevant:
[http://www.ubuntuforums.org/archive/index.php/t-79588.html](http://www.ubuntuforums.org/archive/index.php/t-79588.html) 
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
[http://ubuntuforums.org/showthread.php?t=154511](http://ubuntuforums.org/showthread.php?t=154511)

You may indeed have seen all this already, but when I have problems I'd rather get something rather than watch my thread tumble down the page with no responses.
I will be so kind as to ignore the thread if you wish.

---

### Post by Unknowndeepness on 2006-07-14
In konsole:
```

ftp localhost
User: glftpd
Pass: glftpd
<Here it will say something like "ThanQ for logging on">
site adduser <username> <pass> <ipconfig>
```

And then your all done! :)

---

