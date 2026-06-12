---
title: "Printer Installation - Epson Stylus cx4600"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by Fairydustings on 2006-12-07
I am new to Ubuntu and for the life of me can not get my printer to work.](*,)   I have used the process located under System with no avail.  I have downloaded gutenprint-5.0.0(2).tar.bz2 and can't seem to install that either.  I get an error when I type in configure.

Someone please help me - and please provide easy to use step by step instructions.  I have spent 2 weeks messing around on this printer issue and it is trying me insane.:evil:

---

### Post by xpod on 2006-12-07
IF it`s Dapper you`ve got your printer seems to be in the list if you run through the printer set up...im looking at it now.

I have older epson stylus colors and they both work ok

---

### Post by lonewolf72 on 2006-12-07
> **xpod said:**
> IF it`s Dapper you`ve got your printer seems to be in the list if you run through the printer set up...im looking at it now.

I have older epson stylus colors and they both work ok

i think she is running Edgy... and the printer is a USB printer...

---

### Post by xpod on 2006-12-07
Usb whatever its in edgy too so surely it`s easy enough to setup??

---

### Post by Fairydustings on 2006-12-08
The printer is a usb printer.

The type of Ubuntu is Edgy.

My printer is in the list of printers provided by System - Administration - Printing.  I have set my printer up as the default printer through that and it still is not working.  It states it is printing and I could come back days (literally) later and it has not printed a thing.  ](*,) 

Someone please tell me what else I should do.  :-k

---

### Post by Fairydustings on 2006-12-08
I don't know why I am having such a hard time getting this printer to work.  It says that it is set up as the default printer in the System-Administator-Printing area.  I can send things to print and it says it is printing - but nothing happens wit the printer its actual self.  ](*,) 

A friend told me to do type "sudo apt-get install samba smbfs" in my terminal window.  The following are the results...  :???: 

julie@StNicolas:~$ sudo apt-get install samba smbfs
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  smbldap-tools
The following NEW packages will be installed:
  samba smbfs
0 upgraded, 2 newly installed, 0 to remove and 34 not upgraded.
Need to get 3289kB of archives.
After unpacking 8294kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main samba 3.0.22-1ubuntu4 [2904kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main smbfs 3.0.22-1ubuntu4 [385kB]     
Fetched 3289kB in 1m14s (44.0kB/s)                                             
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 98981 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.22-1ubuntu4_i386.deb) ...
Selecting previously deselected package smbfs.
Unpacking smbfs (from .../smbfs_3.0.22-1ubuntu4_i386.deb) ...
Setting up samba (3.0.22-1ubuntu4) ...
Generating /etc/default/samba...
TDBSAM version too old (0), trying to convert it.
TDBSAM converted successfully.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0
 * Starting Samba daemons...                                             [ ok ] 

Setting up smbfs (3.0.22-1ubuntu4) ...
julie@StNicolas:~$ 

SOMEONE HELP ME...  :D

---

### Post by Sef on 2006-12-08
> I have downloaded gutenprint-5.0.0(2).tar.bz2 and can't seem to install that either. I get an error when I type in configure.

Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

Read [Psychocats Installing Software]("http://www.psychocats.net/ubuntu/installingsoftware").

Samba is for networking computers.  If your printer is connected to your computer, then you don't need it.

---

### Post by lonewolf72 on 2006-12-08
thanks for all the help... we got it working (coughs) (mumblesprintersworkbetterwhenpluggedin)

---

### Post by deadgobby on 2006-12-08
That was going to be my question is the printer pugged in or on? I am :-D 
to death. Good work there, perfect sample of K.I.S.S. Keep It Simple Stupid. Not that I am calling you dumb. It is the first thing to know of keeping some things to simple instead of letting it getting the best of.
Gobby

---

