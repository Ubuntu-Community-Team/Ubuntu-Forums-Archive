---
title: "Sharing files"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by pippy on 2007-04-04
Hi, I have a second hard drive full of music and games that i want to share over a LAN so my flatmates can access them.

It is mounted on /media/hdb1/. I have tried to use samba to share it, but it does not like my file permissions. As the hard drive is a windows NFTS type I can't change them.

Also I have attempted to use apache (I got it to work, but when I linked it to hdb1 it 303ed), nanoweb and the default smb file sharing program on Ubuntu.

Is there a file sharing program in Ubuntu that does not have a hissy fit when I try to share a large folder (150GB)?

Also one of my flatmates has set up a small server somewhere on the network, maby a program can be installed on that so people can see my files?

---

### Post by pgilmon on 2007-04-04
Perhaps you could also try setting up a ftp server...

---

### Post by hyper_ch on 2007-04-04
I guess the problem is the ntfs drive... why not moving the files to ext3 or fat32?

---

### Post by louieb on 2007-04-04
> **pippy said:**
> Is there a file sharing program in Ubuntu that does not have a hissy fit when I try to share a large folder (150GB)?
Don't think thats a Linux problem.  Naive Linux file systems have a size limit measured in terabytes. What program did you gag trying? 
Samba will work one its configured properly.  Would tell you how to set up Samba but I haven't tried to **share NTFS data on a Linux computer over a network**.

---

### Post by pippy on 2007-04-05
Thanks for your replys, but LinuxDC++ freezes every time I try and hash the drive, gFTP does not support sharing files and some other random FTP server can't be apt-geted.

Plus theres a female in my flat, and getting her to download and use a FTP downloader will be harder then setting a server up :P (So I guess ftp is out of the question)

I was thinking about web servers, is there another web server like apache, but can share an entire drive?

---

### Post by Skrynesaver on 2007-04-05
Samba should work if set up properly, are you able to share ext3 folders ?
could you post the partition's details from fstab and the details of the share from smb.conf?
These are where an error is most likely to be if there is one.

---

### Post by pippy on 2007-04-05
/etc/samba/smb.conf:
```


[global]
   workgroup = roadkill
   netbios name = SERVER1
   server string = %h server (Samba, Ubuntu)


   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = no

   # Set CUPS for printing
   printcap name = CUPS
   printing = CUPS

   # Default logon
 logon drive = H:
   # logon script = scripts/logon.bat
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
 passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spasswor$
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

[hdb1]
path = /media/hdb1
available = yes
browsable = yes
public = yes
writable = no



```

The networks name is roadkill. is there an option for windows partitions in the [hdb1] bit?

---

### Post by pippy on 2007-04-06
Woot! I got it to work!

Heres how:

Remove the crappy apache that was there:
```

sudo apt-get remove apache

```

Install the new apache:
```

sudo apt-get install apache2

```

I also did this:
```

sudo apt-get autoremove

```

I then edited /var/www/index.html to have a link to /hdb/ which linked to /media/hdb1/.

To do this:

```

sudo ln -s /media/hdb1 /var/www/hdb1
sudo nano /var/www/index.html 

and paste '<a href=/hdb1>click here for media</a>'

ctrl + Z to exit, yes to save.

```

enter your ip into a address bar on your network to gain access. click the link togoto the folder linked

---

