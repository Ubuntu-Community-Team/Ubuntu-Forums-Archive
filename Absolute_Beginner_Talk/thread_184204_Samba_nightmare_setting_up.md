---
title: "Samba nightmare: setting up"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Dafydd on 2006-05-29
Hello,

I feel so frustrated that I've given up (for now) after playing with Samba (tried so many wikis). Does anyone know how to set up a simple Samba (one ubuntu desktop as the main computer, one windows portable, one ubuntu portable, and the possibility of a 'guest').

david

---

### Post by stenka on 2006-05-29
There are many tutos on the web... did you try one ?
Or if you have a specific problem, give us more details.
What kind of problem are you encountering ?

---

### Post by Dafydd on 2006-05-29
thanks for the reply.

Yes, I've tried the ubuntuguide, then a mixture of different things.

I have a 'network' - a couple of days ago, I could copy files from my ubuntu-desktop using the windows-portable. 

But I cannot exchange files between the ubuntu-portable and ubuntu-desktop.

I think I've meddled with the smb.conf files. 

I've also added users, tried sharing files with nfs.

I just don't know anymore what to do.

Dafydd

---

### Post by stenka on 2006-05-30
Ok.
Can you browse your workgroup with nautilus or is it empty ?
Are you rejected when you try to open a computer ?

Try this command in the terminal to see if you get something and that nautilus is not buggy :

# smbtree

Also attach your smb.conf files here and I will take a look.

---

### Post by MrE on 2006-05-30
Hi,

I'm struggling with the same thing.

I have no Windows machines (anymore, hurrah!) to test with but I'm trying to share files between my Ubuntu Breezy desktop and my SuSE 10 laptop.

When I try to browse the network I don't even get to see the workgroup; after double clicking on Windows Network, Nautilus just shows a blank screen.

smbtree returns nothing either.

I'd be grateful for any advice you may have.

Cheers

---

### Post by stenka on 2006-05-30
Hi,

Nautilus is often buggy with browsing samba, but if smbtree gets nothing the problem is with samba.
Please attach your /etc/samba/samba.conf file, so that I can check.

---

### Post by Dafydd on 2006-06-01
stenka, thanks! came back to samba as i'm sick of transferring files manually (on a pendrive) from one computer to another.

here are the files... also, maybe the problem is having a samba on both ubuntu computers (that have the same user names etc).

cheers for any help
dafydd

smbtree

Connecting to host=192.168.1.6
Connecting to 192.168.1.6 at port 445
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
Connecting to host=192.168.1.6
Connecting to 192.168.1.6 at port 445
UBUNTU
Connecting to host=192.168.1.6
Connecting to 192.168.1.6 at port 445
        \\UBUNTU                        ubuntu server (Samba, Ubuntu)
Connecting to host=UBUNTU
Connecting to 192.168.1.7 at port 445
                \\UBUNTU\ADMIN$                 IPC Service (new_computer_descriptions)
                \\UBUNTU\IPC$                   IPC Service (new_computer_descriptions)

smb.conf

[global]
   workgroup = ubuntu
   netbios name = ubuntu
   server string = new_computer_descriptions

   
   passdb backend = tdbsam
   security = share
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes
   
   # Set CUPS for printing
   printcap name = CUPS
   printing = CUPS
   
   # Default logon
   logon drive = H:
   logon script = scripts/logon.bat
   logon path = \\server1\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/useradd -m %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usermod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000


   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   passwd chat debug = yes
   unix password sync = yes
   
   # set the loglevel
   log level = 3


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   browsable = no

---

### Post by Dafydd on 2006-06-01
just wasted another hour on this samba thing. nothing works now. i can only see a 'windows' share and then when i click on that nothing appears. i've tried sharing folders via samba, nfa...

please help somebody!

cheers
dafydd

---

### Post by Paloseco on 2006-06-01
I encourage you to try KDE since it has KDE control center and system preferences and you can set easily your smb.conf using graphical interfaces. There is an option "called map to guest" and you have to set it to "bad user" in order to allow anonymous access.

---

### Post by Dafydd on 2006-06-01
thanks but i don't see how that would help anymore. I've installed smk2 (which is kde based and gui) but still things don't work. Nothing works... this is frustrating.

---

### Post by Paloseco on 2006-06-01
i will pick up my smb.conf when I arrive home, is very easy to set up the samba. I think you made a mess of the conf file :-k

---

### Post by jalonsom on 2006-06-01
Many people are experiencing this problem, as there are many different threads on this.
It seems that the problem is resolving the server names.

For now, there is only a workaround: use IP addresses.

In Nautilus, press ctrl+l to display the address you are browsing, and enter smb://192.168.1.7 or whatever the ip address of the computer you want to browse is. Should work.

You can also permanently mount these shares, if you don't want to type the address every time.

Hope this helps.

---

### Post by jwd45244 on 2006-06-01
"security = share" is a bad thing, use "security = user" instead.  Are the users set up in /etc/passwd? and have you applied the "signorseal" registry entry to your Windows boxes ? (check at [www.samba.org](www.samba.org))  Have you set the users passwords using smbpasswd?  Also, so you browse by name add: "wins support = yes"

---

### Post by Dafydd on 2006-06-06
hi,
from my ubuntu-laptop, i just tried smb://192.168.1.6 in nautilus (it is the correct ip of my ubuntu-desktop). get an error message.
still no clues what to do.
daf

---

### Post by Dafydd on 2006-06-06
just installed sm4k but it crashes when i do a search for my mshome network.

here's my smb.conf for all it's worth. i think i'll give up for today.

dafydd

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
	workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
hosts allow = 192.168.1, 127.0.0.1/255.255.255.0
security = share
netbios name = ubuntu
guest account = dell

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
;   security = user username map = /etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

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

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

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
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

---

### Post by RudolfMDLT on 2006-06-06
Hi there! hope you did backup the Samba config file! :)

> [Stuff]
path = /home/rudolf
available = yes
browseable = yes
public = yes
writable = yes

[mp3]
path = /media/Drive1/mp3
available = yes
browseable = yes
public = yes
writable = yes

Try appending the above to the end of your samba config file and just rename the PATH and [NAME] properties to your relevant shares.

Under Server string(Right at the top) change "%h server (Samba, Ubuntu" to something without %h that is more descriptive and unique to each PC i.e. Dave or Kitchen. It will just make life easier when using "smbtree" command. Right now I don't know whether you can see the other ubuntu machine or if your just seeing yourself.

the 0700
> # File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
directory mask = 0700
needs to be changed to  0775 to allow most permissions - makes life easier.

By appending the shares at the bottom should bring you a long way closer to the answer. Also, I may have missed this in your post but did you add every user on the network to you computer's user and group list. AND then added each user individually with:

> 1) sudo smbpasswd -e yourname
2)Type and retype new Samba password
3)sudo smbpasswd -a XP username
(the usernames of your network users)
4)Type and retype their passwords


Anyway, good luck! :D

PS: There are a couple of posts floating around the forum with the much the same problem, search around and maybe you'll find the answers your looking for!

---

### Post by epohs on 2006-06-09
I am getting the same sort of problem.

I have two ubuntu machines, and I can browse both by IP address, but neither of the machine names are appearing in the network browsing of Nautilus.  My workgroup appears, but I get an "*Sorry, couldn't display all the contents of "windows Network: hopegroup*" error when I select it.

However, [COLOR="SeaGreen"]smbtree[/COLOR]  sees both machines and their shares.

```
HOMEGROUP
        \\LINUX-UPSTAIRS                linux-upstairs server (Samba, Ubuntu)
                \\LINUX-UPSTAIRS\ADMIN$                 IPC Service (linux-upstairs server (Samba, Ubuntu))
                \\LINUX-UPSTAIRS\IPC$                   IPC Service (linux-upstairs server (Samba, Ubuntu))
                \\LINUX-UPSTAIRS\SharedDocs             Shared Windows Documents
                \\LINUX-UPSTAIRS\Public                 Shared Files
                \\LINUX-UPSTAIRS\print$                 Printer Drivers
        \\LINUX-DOWNSTAIRS              linux-downstairs server (Samba, Ubuntu)
                \\LINUX-DOWNSTAIRS\ADMIN$               IPC Service (linux-downstairs server (Samba, Ubuntu))
                \\LINUX-DOWNSTAIRS\IPC$                 IPC Service (linux-downstairs server (Samba, Ubuntu))
                \\LINUX-DOWNSTAIRS\Public               Shared linux files
                \\LINUX-DOWNSTAIRS\print$               Printer Drivers

```


Can anyone help?  Thanks very much, guys.

---

