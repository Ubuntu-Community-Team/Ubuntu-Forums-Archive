---
title: "Samba!"
date: 2007-06-23
forum: Catalan Team
---

### Post by patrickfromspain on 2007-06-23
Hola gent!

Dintre d'uns dies entrara un 3er PC a casa meva, per al meu germa. El cas es que sera poca cosa (un athlon XP 2100, amb 30/40 gigues de disc dur). Com que jo tinc molts mp3, voldria que el meu equip es convertis en un servidor, per a que el meu germa pugui escoltar els mp3 sende haber de tenir-los al seu pc. Llavor, m'agradaria fer-ho en samba.

El cas es que estic fent probes, i de moment aconsegueixo poca cosa. He aconseguit veure el contigut compartit del portatil (amb windows XP), i desde el portatil he vist quines carpetes tinc compartides al meu PC (amb ubuntu), pero no hi puc accedir. Algo s'anima a ferme un minitutorial? Vull que els equips windows puguin accedir a les meves carpetes compartides i vull poder accedir a les seves..

Ja se que es molt demanar.. pro be, confio en vosaltres :)

Salut!

---

### Post by papapep on 2007-06-25
Si ens passes el teu smb.conf li farem un cop d'ull.

---

### Post by patrickfromspain on 2007-07-07
be, hem sembla que el samba en feisty esta bastant petat. Aixo de la comparticio de fitxers entre windows i ubuntu m'esta parant boig. 

Si vaig a llocs -> xarxa, veig el meu grup de treballa (DOMHOME), pero no hi veig cap equip. Hem surt:

"No s'ha pogut mostrar els continguts de la carpeta.

No s'ha pogut visualitzar tot el contingut de <<Xarxa de Windows: domhome>>."

En canvi, posant xmb://192.168.1.200 veig les carpetes compartides, pero duplicades: tinc compartides la C: i la D: i hi veig C, D, C$ i D$. A les que acaben en $ no hi puc accedir, demana contrasenya i usuari.


Desde el portatil, veig l'equip amb ubuntu, pero no hi puc entrar, hem diu:

No tiene acceso a \\Patrick-desktop. Puede que no tenga permiso para utilizar este recurso de red. Pongase en contacto con el administrador de este servidor para comprobar si tiene permisos de acceso.

No se ha encontrado la ruta de acceso a la red.

En canvi, si al navegador hi poso \\192.168.1.111 si que veig l'esquip i les carpetes que comparteixo i hi puc accedir..

el meu smb.conf:

patrick@patrick-desktop:~$ cat /etc/samba/smb.conf
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
workgroup = DOMHOME

# server string is the equivalent of the NT Description field
server string = proba1

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
dns proxy = yes

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
security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
passdb backend = tdbsam

obey pam restrictions = yes

guest account = nobody
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

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = no
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
acl compatibility = winnt
ldap ssl = No
server signing = Auto

[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[patrickhome]
path = /home/patrick
guest ok = yes
hosts allow = 192.168.1.200
available = yes
browsable = yes
public = yes
writable = no
patrick@patrick-desktop:~$

---

### Post by vila-seca on 2007-07-09
A veure anem a pams:

Jo la veritat és que de samba ho porto bastant malament, per a mi és més senzill treballar amb openssh, però pel que dius aqui hi han coses que no te'n massa ben definiides,

El primer de tot sembla que la resolució de noms , jo el que faria és mirar si el netbios esta funcionant, ho podries fer amb un netstat -a i mirar si et surt netbios.

[quote=En canvi, posant xmb://192.168.1.200 veig les carpetes compartides, pero duplicades: tinc compartides la C: i la D: i hi veig C, D, C$ i D$. A les que acaben en $ no hi puc accedir, demana contrasenya i usuari.[/quote]

I si poses l'usuari i la contrasenya accedeixes?

[quote= En canvi, si al navegador hi poso \\192.168.1.111 si que veig l'esquip i les carpetes que comparteixo i hi puc accedir..[/quote]

Podries solucionar el fet d'accedir a un màquina a traves del seu nom (ara no se si l'encerto, però per prova-ho no passarà res) afegint al teu arxiu de hosts (etc/hosts) l'adreça , per exemple:

192.1681.200      Patrick.

Segur q en PapaPep em corregeix :-P

Quim

---

### Post by patrickfromspain on 2007-07-09
patrick@patrick-desktop:~$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:40000                 *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      0 localhost:63775         *:* 

Sobre el fet d'have d'accedir a una maquina per la ip.. hem passa aqui i hem passa a windows. A ubuntu sembla facil d'arreglar.. pro a windows?

---

### Post by patrickfromspain on 2007-07-09
be, es igual... a debian funciona.. ho entendre com una altre d'aquest bugs d'ubuntu.. salut

---

### Post by vila-seca on 2007-07-09
A mi em funciona amb els dos ;)

> **patrickfromspain said:**
> be, es igual... a debian funciona.. ho entendre com una altre d'aquest bugs d'ubuntu.. salut

---

### Post by prostata on 2007-07-10
> **patrickfromspain said:**
> Hola gent!

Dintre d'uns dies entrara un 3er PC a casa meva, per al meu germa. El cas es que sera poca cosa (un athlon XP 2100, amb 30/40 gigues de disc dur). Com que jo tinc molts mp3, voldria que el meu equip es convertis en un servidor, per a que el meu germa pugui escoltar els mp3 sende haber de tenir-los al seu pc. Llavor, m'agradaria fer-ho en samba.

El cas es que estic fent probes, i de moment aconsegueixo poca cosa. He aconseguit veure el contigut compartit del portatil (amb windows XP), i desde el portatil he vist quines carpetes tinc compartides al meu PC (amb ubuntu), pero no hi puc accedir. Algo s'anima a ferme un minitutorial? Vull que els equips windows puguin accedir a les meves carpetes compartides i vull poder accedir a les seves..

Ja se que es molt demanar.. pro be, confio en vosaltres :)

Salut!

Mira't aquesta direcció:

[http://www.guia-ubuntu.org/index.php?title=Samba](http://www.guia-ubuntu.org/index.php?title=Samba)

ès un wiki que potser interessant, ja diràs quelcom

---

