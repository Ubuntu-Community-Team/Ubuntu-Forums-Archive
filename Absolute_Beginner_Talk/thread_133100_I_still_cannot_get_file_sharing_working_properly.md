---
title: "I still cannot get file sharing working properly"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by Disorder on 2006-02-19
I have set SAMBA set up along with a network name.

In windows, I browse to workgroup>sambaserver and use my network name to connect. I then see two folders Media(the folder I want to access) and printers and faxes.

I can connect to printers and faxes, but am denied when I try to connect Media

The drive media is on  /dev/hdb and it is on an NTFS partition. It's access path is /home/obi/Media

I've played around in system settings>shared folders and toggled some properties to no avail.

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
username map = /etc/samba/smbusers

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

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

[MEDIA]
path = /home/obi/Media/
guest ok = yes
read only = no
case sensitive = no
msdfs proxy = no
guest account = root

---

### Post by Disorder on 2006-02-19
^

---

### Post by pppetter on 2006-02-20
Try to delete the line 
> guest account = root

Do that for two reasons. First off, when I look at it, I see that it's a line that I never would use, anywhere, for security reasons. Second, earlier in your smb.conf this is stated: "invalid user = root". Third, I have never seen anyone use that line in a smb.conf file - it is not needed.

THat's what _I_ think. Tell me if it doesn't work!

---

### Post by Zimmer on 2006-02-20
If you are expecting the security to be controlled by samba users  then you have not un commented the 
security=users    option...

but that might not be your only problem... you may not have set up any samba users ( I think you have as you say you can see the folders..)

Help may be found here:

[http://ubuntuguide.squarecows.com/doku.php#samba_server](http://ubuntuguide.squarecows.com/doku.php#samba_server)

and
[http://ubuntuguide.org/#sharefolderstheeasyway](http://ubuntuguide.org/#sharefolderstheeasyway)

and [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Have a good read and see which solution will fit your particular security needs...
Regards

---

