---
title: "How do I get persmisson to access a file on my ubuntu machine through windows?"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Disorder on 2006-01-15
I recently just set up samba using a a guide I found here.

Upon doing that I connected to the samba server using my Ubuntu login name and samaba password

It added a homes folder aswell as a folder named (myusername)

I didnt really want to share those, but at least I had set up sharing.

So I added another hard drive to my system.

I added the one folder and it's subfolders on that drive to the samba share through the GUI

It then appeared alongside the homes and username folder but would not allow me to connect

I then browsed around the samba utility and went to shares>editshares>security and added the host name of the windows machine to the allow hosts field

When I tried to connect it then prompted me to logon, I ented my linux username and password , it however just hangs there and dont deny or allow me to view the folders.

How can a I get access to this folder?

Also how can I not share the homes and username folder?

Thanks

---

### Post by Mr_Grieves on 2006-01-15
I'm not very good at samba. But have you considered using SCP or SFTP?

---

### Post by Disorder on 2006-01-17
please ;)

---

### Post by Disorder on 2006-01-19
One key fact that I had forgot is the drive I wish to share is NTFS

---

### Post by Iowan on 2006-01-19
A couple of things to check:
1. Is the [HOMES} folder marked browseable?
2. Who are the valid users?

According to my Samba book, **browseable = no** still displays the share for the validated user.  A **valid users =$S** makes the only valid user the one after whom the share is named.  It also mentions that two parameters you WON'T want in the [homes] folder are **guest ok = yes** or ** public = yes**.

OOPS, I forgot to mention... this information will be in /etc/samba/smb.conf.  You can view it with a text editor  - or open up a terminal and enter **more /etc/samba/smb.conf** (space bar forwards a page at a time).

---

### Post by Disorder on 2006-01-29
I still cannot figure this out. The homes and user name folders no longer appear through windows or in the smb.conf file

Here is a copy 

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not many any basic syntactic
# errors.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = WORKGROUP
netbios name = obi_smb_server

# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
passdb backend = tdbsam guest

obey pam restrictions = yes

;   guest account = nobody
invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY 
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
ldap ssl = No
server signing = Auto

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
comment = All Printers
browseable = no
path = /tmp
printable = yes
create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

[music]
case sensitive = no
msdfs proxy = no
path = /home/obi/test/Music/My Music/music
valid users = 
hosts allow = athalon
write list =

---

### Post by Disorder on 2006-02-02
help

---

### Post by lol on 2006-02-02
You need to create a network user... (sudo smbpasswd -a system_username).

Have a look at this link : [http://ubuntuguide.org/](http://ubuntuguide.org/)
There is a samba section in which you should find answers to all your questions.

---

### Post by Disorder on 2006-02-05
I've read that, and I've also added a network user. Still not able to connect to that folder.

---

### Post by lol on 2006-02-06
> When I tried to connect it then prompted me to logon, I ented my linux username and password , it however just hangs there and dont deny or allow me to view the folders.

Now that you have created a network user, when prompted for a username and password, you should enter the username and password of the network user (which by the way, can (and should) be the same as your linux account to simplify things).
If you restarted Samba after the creating of the network user, you shouldn't have problems to log on.

---

