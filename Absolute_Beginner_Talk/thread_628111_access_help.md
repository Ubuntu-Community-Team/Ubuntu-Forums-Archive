---
title: "access help"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by davidexe on 2007-11-30
I have gotten the server functional but the small detail problems are driving me buggy (and that is getting to be a very short trip).  We have two sets of users. There are 2 servers running on the network. The intent (for now) is to give all users access to both servers. The other server is running Linux Fedora and the workgroup is "Cad-Drafting".  This one is "WORKGROUP" and will be running Linux Ubuntu.  There are about 8 users on Cad-Drafting and 3 on WORKGROUP.  The Cad-Drafting has been running with no problem.

I do not know exactly how to set up the users.  They typically have a "computer name" such as "Btmi" or "CAD-1". That is what is in the system. Then they have a Windows User name and password "msoto" "xxxx".  

I have the GUI installed and try to use it as I am not familar enough with Linux to just use the command line.

I have a nightmare trying to keep the drives mounted. I have two 500gb drives that are set up as "server" and "serverbu".  They will be mounted and shared and then all of a sudden they will be gone and instead there are the same folders in that directory but they are blank and do nore reflect the 500gb drives. I then have to remount and reshare.

Now, when someone copies folders to the server or creates folders on the server they show up as "LOCKED" and no one can access them. I have to go in and try to get ownership with che "chown" command.

Here is my stripped down (no comments) smb.conf file:

[global]
    ; General server settings
    netbios name = ieiserver
    
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no


[server]
    path = /home/daexe/server
    available = yes
    browseable = yes
    read only = no
    public = yes
    writable = yes
    create mask = 0644
    directory mask = 0755

[serverbu]
    path = /home/daexe/serverbu
    available = yes
    browseable = yes
    read only = no
    public = yes
    writable = yes
    create mask = 0644
    directory mask = 0755

The intent in the future will be to have multiple user groups with varying access but for right now I just want to get it running with all having access to all the folders RELIABLY.

Also, If I go into the GUI and add a user it automatically puts in a group for that same name and I cannot seem to eliminate that group.  If I do it from the command line it adds the user but not the group?  Another aggravation.

I have gone to the user computers and added the server IP to the WINS, etc. 

Any help would be GREATLY appreciated.

THANKS in advance.

---

### Post by davidexe on 2007-12-03
WOW,  must be a toughie...
Well, I think I either found the solution or at least a temporary work around until something else comes up.

I changed the directory mask to 0777 instead of 0775. Now I can create files on the Windows machines and they do not come up locked.

Thanks for all the enormous help on the other stuff. Wouldn't have gotten this far without it.

By the way, does anyone know of anyplace I can download a document that has all of the Ubuntu Server Command Line Commands?  I know that I can type "man command" and get it but that only works if I already know the command.

Thanks again.

---

### Post by lamalex on 2007-12-03
if you want every cmd just do <tab><tab> and hit 'y' for yes. It will show them all to you. Every freaking one.

---

### Post by davidexe on 2007-12-03
Yes, it will show them but is there a file of them that I can print out as an instruction manual? 

as an example, I want to change all the files and folders permissions to read, write and execute.  I have tried every variant of chmod that I can think of and nothing changes the folder I am watching to write permission for group and others.  I can do it manually but for 100 gB of data that is not what I wanted to do until Christmas. 

I am thinking that there should be a command regarding "permissions" that would do it globally throughout the entire hdd (folder).




Thanks

---

