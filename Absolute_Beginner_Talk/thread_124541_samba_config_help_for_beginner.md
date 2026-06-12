---
title: "samba config help for beginner"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by lance bermudez on 2006-02-01
i have used the config at [http://ubuntuforums.org/showthread.php?t=119486](http://ubuntuforums.org/showthread.php?t=119486) and added the user with smbpasswd. i have got the samba config set up and can see my printer and home folder but can not access my printer from my window 2000 computer or my home folder. the printer gives me the following error "the server on which the printer resides does not have the correct printer driver installed. if you want to install the driver on your local computer, click here" window 2000 does not have the driver i need for my printer but breezy does. and for my homes folder i receive the following error " the network name cannot be found" i also do not under stand the step that says "1. To get printing to work we set the spool path to be "path = /var/spool/cups" since the directory was already there. Then I had to chmod the directory to give everyone read/write/execute permissions on it." how do i add the read/write/execute part and where do i put them.  also from the windows 2000 box i do not have to give a user name or password any more i did it once when i first connected but not any more and i receive the same error no matter if i go to the network neighborhood icon or go to start and enter my Linux ip address. either way i don't have to enter a user name or password and still get the same errors. im new to Linux and samba so could you please send my any help to [email]bermudezlance@hotmail.com[/email]. below is a copy of my smb.config
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
   workgroup = LBERMUDEZ

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes 

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

 map to guest = Bad User
 show add printer wizard = No

[homes]
   comment = Home Directories
   path = /home/lance
   browseable = yes
   writable = yes
   create mask = 0700
   directory mask = 0700

[printers]
   comment = All Printers
   path = /var/spool/cups
   printable = Yes
   guest ok = Yes
   use client driver = Yes
   browseable = No

---

### Post by sas on 2006-02-02
You must install the windows 2000 driver for the printer to work in Windows

Don't worry about that directory already being there, to chmod it go to a terminal (applications > accessories > terminal) and type sudo chmod 777 /var/spool/cups

To require a username you need to use a security line, which it doesn't look like you've got, you should have "security = share" for no authentication or security = "user" to require the usernames on linux and windows to match up.

There's a graphical application to manage the folder sharing, you can access it via using "system > administration > shared folders". You may find it easier to use this, for the folders at least.

There's a guide installed in Ubuntu that may be useful, you can find it under "systems > help" Then click on "ubuntu starter guide", then "networking" on the left hand side, then "samba".

Just FYI, if you're posting help requests it's considered good etiquette to only post your problem in *one* thread. 

In future could you also include the exact text of any error messages you recieve?

Also if you subscribe to this thread then you'll recieve all replies straight to your email address and the solution will be stored on the forum for others users to find and learn from.

---

### Post by lance bermudez on 2006-02-03
my printer is attached to my linux box and no mater if i change the ""use client driver" line to = yes or no i get the error "server does not have the corret printer driver click yes to install from the local computer. i was able to find my hp PSC-750 disk and install the windows 2000 printer driver but it will not print a test page but will install the network printer from the linux box. Also i recive the error that from my linux box when i connect to the windows shared folder that the contains of the folder can not be displayed. below is my new smb.conf
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = LBERMUDEZ

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes 

#authentication
security = share

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

 map to guest = Bad User
 show add printer wizard = No

[homes]
   comment = Home Directories
   path = /home/lance
   browseable = yes
   writable = yes
   create mask = 0700
   directory mask = 0700

[printers]
   comment = All Printers
   path = /var/spool/cups
   printable = Yes
   guest ok = Yes
   use client driver = Yes
   browseable = No

---

### Post by sas on 2006-02-03
I'd guess you need to say which local user the guest should be, so you'd need to setup a local user on the linux box who has permissions to the folder(s) and printer(s) you're trying to access. You could use your own normal user for this if you wanted, but this could be a security issue.
To say which local user the guest should be you'll need something like
guest user = a_linux_account 
in the [global] section of your smb.conf.

You probably also want to set the samba printer as "browseable = yes".

Hope this helps.

---

### Post by lance bermudez on 2006-02-05
First let that I’m printing from windows 2000 to Ubuntu breezy badger where my HP PSC 750 printer is attached. And the files can be shared from the Ubuntu breezy badger to the windows but not from the windows to the breezy badger. Make sure samba, samba-common, smbclient, smbfs, libsmbclient, and libsmbclient-dev are installed.  Also make sure the printer is installed by using system administraton printing then click add printer. Now to get started the commands that need to be typed in are surrounded by “” and have to be typed in terminal using “sudo su –“ to use super user the password will be you login password. Terminal is open by clicking applications then accessories then terminal. To get this to work you have to have all to the three user mathch user names and password they are windows user, Linux user, and samba user. With the “smbpasswd –a username” hit enter and put in the password also you will have to add the root user to samba “smbpasswd –a root” this is for administration use. Then edit the smb.conf file of samba with “vi /etc/samba/smb.conf” to match what is below. To add the changes press the insert key on the key board and make it look like what is below

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
   workgroup = LBERMUDEZ

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

#authentication
security = user


# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   load printers = yes
   printing = cups
   printcap name = cups

  show add printer wizard = No

[homes]
   comment = Home Directories
   path = /home/lance
   browseable = yes
   writable = yes
   create mask = 0700
   directory mask = 0700

[printers]
   comment = All Printers
   path = /tmp
   printable = Yes
   guest ok = Yes
  public = yes 
  use client driver = No
   browseable = Yes
  printer admin = root

[print$]
  comment = Printer Drivers
  path = /var/lib/samba/printer
  browseable = yes
  read only = yes
  guest ok = yes
  write list = root

when you have typed what is above save it by pressing the esc key to exit the insert mode then press shift q then type exit. Restart samba by typing “/etc/init.d/samba restart” then type “cupsaddsmb –U root –v –a “ hit enter then enter the password that you used for the samba root account. This will add the driver to samba for the printer.  If you need help understanding this part read this web page at [http://www.linuxdevcenter.com/pub/a/linux/2005/01/13/lnxckbk_samba.html](http://www.linuxdevcenter.com/pub/a/linux/2005/01/13/lnxckbk_samba.html)
after the drivers have been copied reedit the smb.conf file and change the “security = user” part to “security = share” under #authentication comment and save and restart samba. To get printing to work download the adobe program and adobe ppd toward the botton of page from the url to the windows 2000 box. on the Ubuntu box type “/etc/cups/ppd”  hit enter then type “ls” find your printer and whrite down its name they type “cp printer name /home/shared folder name” then type “cd /usr/share/cups/model/hplip” hit enter type “ls” find your printer then type “cp printer /home/shared folder name” on the windows 2000 box connect to the Ubuntu share and copy the printer files to windows 2000. unzip the adobe ppd program and where ever you copy it to past the printer files you copied from Ubuntu into it the run the adobe program and install the printer.

---

### Post by lance bermudez on 2006-02-06
does anyone know how i can get to my windows box folder i have set up to share from my linux box? i have tryed just the server address and folder name, also i have tryed  server address, folder name, and share name and i just get the same errors from both ways saying that the contents of the folder can not be displayed. and if i try to browse the server from the network neighborhood none of the password and user names work to access the windows box.

---

### Post by lance bermudez on 2006-02-07
thank you for your help with the printing but do what do you know about accessing a window 2000 share from my ubuntu breezy box. windows has nfts file system and ubuntu has ex2. do i need to set up a fat partinton on my windows 2000 box as a share? But i not shure if i need to becuse my windows box can access my ubuntu shares with on problem. i have the same user and password for ubuntu, samba and windows. i have tryied 

mount //192.168.3.2/wshare media/wshare -o username=mother,password=mom,dmask=777,famask=777

it gives me an error say that i need to say what the file system is so i look around the forms and tried this

mount -t smbts -o username=mother,password=mom,dmask=777,famask=777 //192.168.3.2/wshare media/wshare
and it errors out to but saying that the user is wrong or something like that im on my windows box because my my modem runs faster on windows then when on ubuntu because im to cheep to pay for the full driver

---

### Post by lance bermudez on 2006-02-08
i have been using sudo. but the only thing i have done differnert is install the program that lets windows browse the ext2 file system. the program is at [http://www.fs-driver.org/extendeddl.html](http://www.fs-driver.org/extendeddl.html) could this be a problem?

---

### Post by lance bermudez on 2006-02-09
i found out it is not the program

---

### Post by lance bermudez on 2006-02-16
here is eveything working fine

First let that I’m printing from windows 2000 to Ubuntu breezy badger where my HP PSC 750 printer is attached. And the files can be shared from the Ubuntu breezy badger to the windows but not from the windows to the breezy badger. Make sure samba, samba-common, smbclient, smbfs, libsmbclient, and libsmbclient-dev are installed.  Also make sure the printer is installed by using system administraton printing then click add printer. Now to get started the commands that need to be typed in are surrounded by “” and have to be typed in terminal using “sudo su –“ to use super user the password will be you login password. Terminal is open by clicking applications then accessories then terminal. To get this to work you have to have all to the three user mathch user names and password they are windows user, Linux user, and samba user. With the “smbpasswd –a username” hit enter and put in the password also you will have to add the root user to samba “smbpasswd –a root” this is for administration use. Then edit the smb.conf file of samba with “vi /etc/samba/smb.conf” to match what is below. To add the changes press the insert key on the key board and make it look like what is below

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
   workgroup = LBERMUDEZ

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

#resole host names to ip addresses
name resolve order = lmhosts host wins bcast
bind interfaces only = yes
hosts deny = all
hosts allow =192.168.3.0/24 127.
interfaces = eth0 lo

#authentication
security = user

# encrpyt password in the smb.conf
encrypt passwords = yes
smb passwd file  = /etc/samba/smbpasswd
local master = no
dns proxy = no

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   load printers = yes
   printing = cups
   printcap name = cups
   show add printer wizard = No

[homes]
   comment = Home Directories
   path = /home/lance
   browseable = yes
   writable = yes
   create mask = 0700
   directory mask = 0700

[lshare]
  path = /home/lance/lshare
  available = yes
  browseable = yes
  public = yes
  writable = yes
  guest ok = yes

[windows]
  path = /media/windows
  available = yes
  browseable = yes
  writable = yes
  guest ok = yes

[printers]
   comment = All Printers
   path = /tmp
   printable = Yes
   guest ok = Yes
  public = yes 
  use client driver = No
   browseable = Yes
  printer admin = root

[print$]
  comment = Printer Drivers
  path = /var/lib/samba/printer
  browseable = yes
  read only = yes
  guest ok = yes
  write list = root

when you have typed what is above save it by pressing the esc key to exit the insert mode then press shift q then type exit. Restart samba by typing “/etc/init.d/samba restart” then type “cupsaddsmb –U root –v –a “ hit enter then enter the password that you used for the samba root account. This will add the driver to samba for the printer.  If you need help understanding this part read this web page at [http://www.linuxdevcenter.com/pub/a/linux/2005/01/13/lnxckbk_samba.html](http://www.linuxdevcenter.com/pub/a/linux/2005/01/13/lnxckbk_samba.html)
after the drivers have been copied reedit the smb.conf file and change the “security = user” part to “security = share” under #authentication comment and save and restart samba. To get printing to work download the adobe program and adobe ppd toward the botton of page from the url to the windows 2000 box. on the Ubuntu box type “/etc/cups/ppd”  hit enter then type “ls” find your printer and whrite down its name they type “cp printer name /home/shared folder name” then type “cd /usr/share/cups/model/hplip” hit enter type “ls” find your printer then type “cp printer /home/shared folder name” on the windows 2000 box connect to the Ubuntu share and copy the printer files to windows 2000. unzip the adobe ppd program and where ever you copy it to past the printer files you copied from Ubuntu into it the run the adobe program and install the printer.   The [window] is a fat32 part of my hard drive i use to share files with the dual boot and the network and the [lshare] is for network sharing they both allow access without needing user name and password but [home] needs user name and access. the #resole host names to ip addresses line is for security so that only my network pc can use my linux samba server and the # encrpyt password in the smb.conf line is for win 2000 and above because windows encrpyt passwords with these version but is not needed for version below. now the winows will talk to the linux but the linux will not talk to the windows tell you fix the window and linux some more. this part will not work with dhcp and may not be a problem but needs to be done on static network for computer names to be pinged in linux. on the window edit the lmhosts and hosts. for the windows hosts  should be ip space computer name
127.0.0.1       localhost
192.168.3.2	mom
192.168.3.3	breezyBadger
and for the lmhosts on the winows  should be ip address netbios name
192.168.3.3 breezybadger #PRE
192.168.3.2 mom #PRE
and for the linux hosts ip computer name
127.0.0.1 localhost.localdomain localhost breezyBadger
192.168.3.3 breezyBadger
192.168.3.2 MOM
to connect to the windows computer form linux the user must have the sharing permissions set and the windows user added to both the sharing permission and security tab. does not need a password unless your user has one for security use 
smbclient //ip address/folder share name -U username%password
example 
smbclient //192.168.3.2/wshare -U lance%bermudez
to browse the windows computer for shares use
smbclient -L //192.168.3.2 -N -U lance%bermudez

rembember to be in the command line directory you want to send files to the windows or save the files because it acts like an ftp. for a gui mount it with 
 mount //192.168.3.2/wshare /media/wshare -t smbfs -o username=lance,password=bermudez,dmask=777,fmask=777

also edit /etc/gnome-vfs-2.0/modules/smb-module.conf change the line
smb: [daemon] libsmb
to read
smb: libsmb.so
but i did
smb: libsmb
and it seems to work fine

---

