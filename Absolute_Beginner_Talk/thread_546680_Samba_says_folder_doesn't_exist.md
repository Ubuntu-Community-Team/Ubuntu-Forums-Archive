---
title: "Samba says folder doesn't exist"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by JonaLinux on 2007-09-09
I'm used to running Debian and Samba worked fine in it. Now I'm using Kubuntu and although I can setup up the shared folder I can't access the folder in Samba.

Let's say the folder is /home/FTP and in via samba it's smb://linux/FTP

When I open a konqueror and type in smb:/ in the address bar first the MSHOME icon is shown for the domain. Click on that and I see the machine I'm after which is LINUX. After clicking on that I see the folder that I'm after which is FTP

When I click on share the error message returns with "The file or folder smb://linuxman/FTP does not exist." It obviously does exist otherwise I wouldn't have been able to click on it. Yes I've refreshed the page so it's not something that's been cached.

File permissions on that directory is 777.

The smb.conf file is below.

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[FTP]
        path = /home/ftp
        read only = No
        guest ok = Yes
        case sensitive = No
        strict locking = No
        msdfs proxy = no

[JonsHome]
        path = /home/jonathan
        read only = No
        guest ok = Yes
        case sensitive = No
        strict locking = No
        msdfs proxy = no

Any help would be great. 
Thanks
Jonathan

---

### Post by GMachine_24 on 2007-09-09
Hi:

At the least, you must change this line in your smb.conf file

server string = %h server (Samba, Ubuntu)

so instead of %h server (Samba, Ubuntu)

you have the actual name of your machine

e.g. I have a machine I named "Samba2"

so in my smb.conf file on Samba2 that line says

<code>

server string = Samba2

</code>

You remove the stuff in the parentheses.

In your case one machine would be:

<code>

server string = FTP

</code>

and the other would be

<code>

server string = JonsHome

</code>

I'm sure you know this resource exists, but howtos and fix its and a lot of other information is located here:

[www.samba.org](www.samba.org)

The fix I gave you might solve your problems. But you need to change it, whether or not you have other troubles.

--gm

---

