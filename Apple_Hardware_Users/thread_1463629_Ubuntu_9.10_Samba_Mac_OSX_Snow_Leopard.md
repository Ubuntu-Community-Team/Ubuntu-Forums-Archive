---
title: "Ubuntu 9.10 Samba Mac OSX Snow Leopard"
date: 2010-04-27
forum: Apple Hardware Users
---

### Post by servous on 2010-04-27
I've set up a Samba file server on a machine using Ubuntu Server 9.10 (64-bit). The shares works fine with all Windows machines, but there is one iMac running Snow Leopard 10.6.3 that has problems with the file permissions.

The user can mount and browse all files in the share, but not create new files/directories.

I've set up Samba with full access for all users, and then set the permissions in the file system itself. This is not the first file server I set up this way, and I haven't encountered this problem before - since there has been no Macs :)

Looking at the logs files in /var/log/samba there is a lot of errors about wide links for this perticular computer.

When it comes to Mac I'm totally lost. Any help in pointing me in the right direction is appreciated!

Here is a part of the log file:
```
[2010/04/27 12:25:52,  0] lib/util_sock.c:730(write_data)
[2010/04/27 12:25:52,  0] lib/util_sock.c:1468(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2010/04/27 12:25:52,  0] smbd/process.c:62(srv_send_smb)
  Error writing 75 bytes to client. -1. (Transport endpoint is not connected)
[2010/04/27 12:25:52,  1] smbd/service.c:1241(close_cnum)
  imac (194.47.244.35) closed connection to service XX
[2010/04/27 12:25:52,  0] lib/util_sock.c:730(write_data)
[2010/04/27 12:25:52,  0] lib/util_sock.c:1468(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2010/04/27 12:25:52,  0] smbd/process.c:62(srv_send_smb)
  Error writing 75 bytes to client. -1. (Transport endpoint is not connected)
[2010/04/27 12:25:52,  1] smbd/service.c:1241(close_cnum)
  imac (194.47.244.35) closed connection to service XYZ
[2010/04/27 12:39:03,  0] param/loadparm.c:9783(widelinks_warning)
  Share 'XYZ' has wide links and unix extensions enabled. These parameters are incompatible. Wide links will be disabled for this share.
[2010/04/27 12:39:03,  1] smbd/service.c:1062(make_connection_snum)
  imac (194.47.244.35) connect to service XYZ initially as user username (uid=1003, gid=1005) (pid 30706)
[2010/04/27 12:39:03,  0] param/loadparm.c:9783(widelinks_warning)
  Share 'XX' has wide links and unix extensions enabled. These parameters are incompatible. Wide links will be disabled for this share.
[2010/04/27 12:39:03,  1] smbd/service.c:1062(make_connection_snum)
  imac (194.47.244.35) connect to service XX initially as user username (uid=1003, gid=1005) (pid 30706)

```

---

### Post by nozyczek on 2010-04-27
Take a look here:

[HTML]http://reviews.cnet.com/8301-13727_7-20002367-263.html[/HTML]

I fixed my samba by adding 

```
unix extensions = no
```

to smb.conf

---

### Post by servous on 2010-04-28
Thank you!

Adding the following lines seemed to solve the problem:

```
follow symlinks = yes
wide links = yes
unix extensions = no
```

---

### Post by nozyczek on 2010-04-28
Great!

---

### Post by gulabpasha on 2010-05-05
Hi,

Still I'm having the same issue after adding

unix extensions = no 
follw symlinks = yes
wide links = yes 
[FONT=monospace]

Please help, looking forward to your support.

Thanks,
Gulab Pasha

[/FONT]

---

### Post by mrarsoft on 2010-05-05
Same issue here on my system with Ubuntu 10.04 and Mac OS X 10.6.3. I tried the samba settings mentioned above, but no luck.
Any other suggestions?

---

### Post by nozyczek on 2010-05-10
make sure to add these lines to [global] section in your smb.conf

and don't forget to 
/etc/init.d/samba restart

---

### Post by mrarsoft on 2010-05-12
I have restarted the samba server, but this didn't help either.

---

### Post by nozyczek on 2010-05-12
> **mrarsoft said:**
> I have restarted the samba server, but this didn't help either.

Can you post your smb.conf ?

---

### Post by mrarsoft on 2010-05-12
Here's my current smb.conf

```


# Global parameters
[global]
	workgroup = WORKGROUP
	netbios name srv01
	server string = server
#	passdb backend = ldapsam:ldap://localhost
	passdb backend = ldapsam:ldapi://%2fvar%2frun%2fldapi
	username map = /etc/samba/smbusers
	max log size = 500
# release log level
	log level = 2
# debugging auth and winbind
#	log level = 3 passdb:5 auth:10 winbind:10
#	log level = 255
#	announce version = 4.0

	# enable SMB2 (for Vista and Win7) available with samba 3.5.0 or higher
#max protocol = smb2
#smb ports = 445

	security = user
#    security = ads
#    use kerberos keytab = yes
	realm = FASTPROTECT.NET

#unix extensions = yes
	follow symlinks = yes
	wide links = yes
	unix extensions = no

	use sendfile = true
#socket options = TCP_NODELAY SO_KEEPALIVE SO_SNDBUF=8192 SO_RCVBUF=8192
	server signing = auto

#	host msdfs = yes

#	logon script = logon.bat
	# configures the roaming profile path
	logon path = \\%N\%U\profile
	# configures the home drive
	logon drive = U:
	logon home = \\%N\%U

	domain logons = Yes
	os level = 192
	preferred master = Yes
	domain master = Yes
	local master = Yes

	time server = yes
	interfaces = 127.0.0.1/8 192.168.211.1/24 192.168.212.1/24
	bind interfaces only = yes
	hosts allow = 127.0.0.0/8 192.168.211.0/24 192.168.212.0/24 192.168.213.0/24

# default of wins support is no
# don't know if it really a good idea to leave it on here.
# samba docu says it should be on only for multi subnetted installations
	wins support = yes

	unix charset = UTF8
	dos charset = CP850

#winbind use default domain = no
#winbind separator=\
#winbind cache time = 600
	template shell = /bin/bash
	template homedir = /home/%U
	idmap uid = 1000-20000
	idmap gid = 1000-20000
#	idmap backend = ldap:ldap://ldap.arsoft.homeip.net
	idmap backend = ldapi://%2fvar%2frun%2fldapi
#winbind enum groups = yes
#	winbind enum users = yes
#	winbind use default domain = Yes

	ldap admin dn = cn=Manager,o=fastprotect
	ldap delete dn = yes
	ldap suffix = o=fastprotect
	ldap machine suffix = ou=Computers,ou=Authentication
	ldap user suffix = ou=Users,ou=Authentication
	ldap group suffix = ou=Groups,ou=Authentication
	ldap idmap suffix = ou=Idmap,ou=Authentication
	ldap ssl = no
#	ldap ssl = start_tls
	ldap passwd sync = yes


    obey pam restrictions = no


# if you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   	printcap name = cups
   	load printers = yes
	printing = cups
#	default devmode = yes
# This option tells cups that the data has already been rasterized
	cups options = raw

	show add printer wizard = yes
	printer admin = +printerAdmins, +domainUsers, +Administrators
	admin users = +domainAdmins

   	template shell = /bin/false

	encrypt passwords = true
#	passwd program = /usr/sbin/smbldap-passwd %u
#	passwd chat = *Old password:* %n\n *New password:* %n\n *Retype new password:* %n\n *successfully*
#	passwd chat debug = yes
#	unix password sync = yes

	guest account = guest
	message command = /bin/mail -s 'message from %f on %m' root < %s; rm %s

	add machine script = /usr/sbin/smbldap-useradd -w '%u'
	add user script = /usr/sbin/smbldap-useradd -a -m -s /dev/false -d /dev/null '%u'
	delete user script = /usr/sbin/smbldap-userdel '%u'

	add group script = /usr/sbin/smbldap-groupadd -p '%g'
	delete group script = /usr/sbin/smbldap-groupdel '%g'

	add user to group script = /usr/sbin/smbldap-groupmod -m '%g' '%u'
	delete user from group script = /usr/sbin/smbldap-groupmod -x '%g' '%u'
	set primary group script = /usr/sbin/smbldap-groupmod -g '%g' '%u'

	abort shutdown script = /sbin/shutdown -c
	shutdown script = /usr/lib/samba/ldap/smbldap-shutdown.sh %m %t %r %f

#	print command = lp -d%p %s; rm %s
#	lpq command = /usr/bin/lpq -P%p
#	lprm command = /usr/bin/lprm -P%p %j
#	queuepause command = /usr/bin/disable %p
#	queueresume command = /usr/bin/enable %p

[netlogon]
	comment = Network Logon Service
	path = /export/netlogon
	directory mask = 0775
	create mask = 0640
	guest ok = Yes
	browseable = No
	force user = root
	force group = root
#	read only = No
	read only = yes
	write list = +administrators +domainAdmins
	hide files = /lost+found/
	csc policy = disable

[IPC$]
	hosts allow = 192.168.212.0/24 192.168.211.0/24 192.168.213.0/24 127.0.0.0/8
	hosts deny = 0.0.0.0/0
	path = /tmp
	csc policy = disable

```

Maybe someone could find the missing/wrong parameter?

---

### Post by nozyczek on 2010-05-14
Your smb.conf looks good to me. You may just wait for new build of Mac OS X 10.6.4. One of their focus is to fix smb problems and looks like it should be ready soon for a public release. 

More info here
[http://news.worldofapple.com/archives/2010/05/14/apple-seeds-third-build-of-mac-os-x-10-6-4/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+WorldOfApple+(World+of+Apple)&utm_content=Google+Reader]("http://news.worldofapple.com/archives/2010/05/14/apple-seeds-third-build-of-mac-os-x-10-6-4/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+WorldOfApple+(World+of+Apple)&utm_content=Google+Reader")

---

### Post by gulabpasha on 2010-05-18
I still have the same issue, I can't write to my samba shared folder. Please find the config of my smb.cof file.

root@ftpserver:~# testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[ftpfolder]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, ftpserver)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    unix extensions = No
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[ftpfolder]
    comment = ftpfolder
    path = /home
    read list = rose, jp, rachna, mayuri, sabita, jenny, jasmine, gulab, shreyas, shreyaa, kirthana
    write list = rose, jp, rachna, mayuri, sabita, jenny, jasmine, gulab, shreyas, shreyaa, kirthana
    read only = No

---

