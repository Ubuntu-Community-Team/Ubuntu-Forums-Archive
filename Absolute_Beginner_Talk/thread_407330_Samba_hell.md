---
title: "Samba hell"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-04-12
Im about at my wits end... i've never had this much trouble before setting up samba daemon. Im trying to share a certain directorie and all its sub directories to the windows machines on my network. i dont want them to have to have an account on my machine and log in to access it, so i have security level set to share in my samba.conf... like i said, i just want them to be able to click on teh link in My Network Places... heres my samba conf and then the most common error in almost every samba log
```

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
# "testparm" to check that you have not made any basic syntactic
# errors.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of


# server string is the equivalent of the NT Description field


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

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



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
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
passdb backend = tdbsam

obey pam restrictions = yes

;   guest account = nobody
invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

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
;   printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY
security = share
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
acl compatibility = winnt
ldap ssl = No
server signing = no

[The Goods]
case sensitive = no
strict locking = no
guest ok = yes
msdfs proxy = no
path = /data/
read only = no

```
And the error im seeing most is
```

[2007/04/12 00:11:22, 0] smbd/negprot.c:reply_nt1(316)
reply_nt1: smb signing is incompatible with share level security !

```
Like i said, i've had it set up correct before, but for the life of me cant figure out what im not doing or doing wrong this time

---

### Post by Nythain on 2007-04-12
bump for another day... any clues??? anyone???

---

### Post by Nythain on 2007-04-12
hmmm...

---

### Post by dstew on 2007-04-12
I notice that nearly all the smb.conf configuration lines are commented out. Is this intentional? In the [global] section I don't see the workgroup anywhere. I don't see any [share] section either.

EDIT: Your error may have to do with password encryption that has been enabled. I believe it uses an encryption algorithm that uses digital signing. So, what I think it is really saying is that share level security is incompatible with password encryption.

---

### Post by Nythain on 2007-04-12
almost good ideas, yet now im not on the workgroup network at all... and i cant access it with a samba client anymore

---

### Post by dstew on 2007-04-12
Do you want help with using samba client, or samba server, or both?

---

### Post by dca on 2007-04-12
...did you   'sudo smbpasswd -a <username>'   and then 'sudo smbpasswd -e <username>' after you configured smb.conf?

---

### Post by Nythain on 2007-04-12
originally samba server... but not in all my jacking around trying to fix the problem, i cant connect to workgroup with samba client anymore wich means im degressing here... did feisty do anything new or different cause i had like no problem with edgy...

ok, original problem... whenever an xp user tried to access my shared folder via my network places ----> view all workgroup computers -----> (the name of my computer) ---> they get this far, but whenver trying to access the actuall folder, it says they cant.

when i tried it on my end connecting through samba client i would get just as far as they did and it would tell me that folder "didnt exist"

now when i try to access on my machine through samba client, it tells me Workgroup doesnt exist or i dont have access to it... easily remediable back going back to my last semi working samba.conf hopefully... but im still completely clueless concerning my initial problem.

Thank you for taking your time to try and help me out... sorry if i sounded grumpy its just a day and a half with a problem i shouldnt be having all the time having mildly irritated roomates kinda made me a little grumpy

---

### Post by dstew on 2007-04-12
Since smbclient is (supposedly) simpler than samba server, let's do that one first. What happens when you try to connect. That is, when you do

smbclient //*servername*/*sharename*

what happens? Do you get an error message? Ultimately, the problem is bound to be a samba mis-configuration. One way to start to figure this out is to look at the errors when you try simple things.

If we think that the samba configuration is hopelessly messed up (fairly easy to do) we might try the minimalist approach, and rebuild a smb.conf file line-by-line from a very small beginning.

---

### Post by dca on 2007-04-12
I dunno', to get an XP box to connect to Samba Server (Linux) in Ubuntu was simply to 'sudo apt-get install samba'...  After that uncomment a few of the lines in 'smb.conf' paying attention to where the files are physically located on the Linux box, ie:  /home/Samba/user.  Then add user 'smbpasswd -a user' and 'smbpasswd -e user' to enable.  Last but not least, either stop/start or restart Samba (or simply reboot machine) and done???

---

### Post by Nythain on 2007-04-12
back from work... ok... here we go... when i try
smbclient //localhost/data
or
smbclient //localhost/Stuff
i get the same results... it asks for a passowrd, wich i DONT want it to do, and now matter what i put in i get this
```

Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]
Server not using user level security and no password supplied.
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```
when i connect to one of the xp machines the same way
smbclient //192.168.1.110/Chris\ Stuff
i get
```

Domain=[MONKEY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \>

```
and voila im connected to them
very odd
i think the problem lies in teh Domain= part... on mine its saying WORKGROUP whereas it should say Server

---

### Post by Nythain on 2007-04-12
ok, so i got a reply on my other thread recommending reducing the content of the samba.conf... wich i did... and now the xp users can access the share the way i want them to, but alas im still getting the same errors with smbclient... here's what my new conf is lookin like
```
 socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
security = share
restrict anonymous = no
domain master = no
preferred master = no

[The Goods]
case sensitive = no
guest ok = yes
path = /data/
read only = no
```

---

### Post by dstew on 2007-04-13
```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]
Server not using user level security and no password supplied.
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
```

Here, you are trying to connect to a Samba server. We need to see the smb.conf of that same server. Is that the smb.conf you have posted?

---

### Post by Nythain on 2007-04-13
yeah... the tiny revised one that now works for the xp users

---

### Post by dstew on 2007-04-13
It seems that the Samba client cares about some configuration options in your smb.conf that the XP client ignores. One clue it the Domain=[WORKGROUP] message. Here, the server tells you that it is using the workgroup name WORKGROUP, which is probably the default since you did not define a workgroup name in your smb.conf file. Add this to the top of your smb.conf file:
```
[global]
workgroup = Server
security = share
```
That is, if your workgroup/domain for your NT network is really "Server". It looks like it might be "MONKEY" from the other message.

---

### Post by Nythain on 2007-04-13
exact same result/error except the domain now = [Server] instead of [Workgroup]

---

### Post by dstew on 2007-04-13
Try [MONKEY]. Actually, this will fail if either the workgroup name or the share name are not set up in the smb.conf, or if smbclient cannot find the share name. The share name I see is [The Goods]. Maybe smbclient cannot deal with the space in the share name, but XP can. It might be better to rename your share with a single word name. Or, try enclosing the name in single quotes when you try to connect with smbclient.

---

### Post by Nythain on 2007-04-14
so i shortend the name to one word, restarted samba, went out for a cup of coffee, came back, and presto... thank you so much, all is well in samba land

---

