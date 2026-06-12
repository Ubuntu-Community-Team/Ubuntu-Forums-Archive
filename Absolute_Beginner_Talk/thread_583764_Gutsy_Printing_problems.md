---
title: "Gutsy Printing problems"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by jdlongmire on 2007-10-20
I cannot get the System>Administration>Printing to pick up my printer.

The SMB Browser shows my Windows workstation, but will not show the printer share. HELP!

Even if I put the path in for a Windows SMB share manually (smb://workgroup/home/HPPSC160) it won't verify.

Dump of smbtree:

WORKGROUP
        \\LAPTOP-ALPHA                  Samba 3.0.26a
                \\LAPTOP-ALPHA\IPC$             IPC Service (Samba 3.0.26a)
        \\HOME           
                \\HOME\HPPSC160         HP PSC 1600 series
                \\HOME\c2             
                \\HOME\C$               Default share
                \\HOME\ADMIN$           Remote Admin
                \\HOME\F              
                \\HOME\Storage        
                \\HOME\I$               Default share
                \\HOME\print$           Printer Drivers
                \\HOME\D$               Default share
                \\HOME\IPC$             Remote IPC
                \\HOME\500GB-Storage

---

### Post by FredB on 2007-10-20
> **jdlongmire said:**
> I cannot get the System>Administration>Printing to pick up my printer.

The SMB Browser shows my Windows workstation, but will not show the printer share. HELP!

SO you have a PSC1600. Did you install hptoolbox ?

---

### Post by jdlongmire on 2007-10-20
no...

---

### Post by FredB on 2007-10-20
In Synaptic, search for hplip toolbox. Maybe it could help you.

---

### Post by jdlongmire on 2007-10-20
synaptic shows hplip is installed...now what?

---

### Post by jdlongmire on 2007-10-20
I found an hplip-gui - installing it now.

---

### Post by jdlongmire on 2007-10-20
hmmm - installed it - don't see any icons...

---

### Post by FredB on 2007-10-20
Look in system / preferences menu.

---

### Post by jdlongmire on 2007-10-20
found it!  

Still not finding the printer share...

---

### Post by jdlongmire on 2007-10-20
ok - used the CUPSS interface to config - now getting:

"Unable to connect to CIFS host"

arrrgh! can anyone help, please!!!!

Just got this:  /usr/lib/cups/backend/smb failed

---

### Post by llamakc on 2007-10-20
[http://ubuntuforums.org/showthread.php?p=161112#post161112](http://ubuntuforums.org/showthread.php?p=161112#post161112) may be of some further help. Looks like your problem has been an issue before over at launchpad.

---

### Post by jdlongmire on 2007-10-20
yeah - looks like they are stumped, too - here is an error log dump:

E [20/Oct/2007:17:04:32 -0500] CUPS-Reject-Jobs: Unauthorized
E [20/Oct/2007:17:04:35 -0500] CUPS-Reject-Jobs: Unauthorized
E [20/Oct/2007:17:04:42 -0500] CUPS-Accept-Jobs: Unauthorized
E [20/Oct/2007:17:04:56 -0500] [Job 14] No ticket cache found for userid=1000
E [20/Oct/2007:17:04:56 -0500] [Job 14] Can not get the ticket cache for jdlongmire
E [20/Oct/2007:17:04:56 -0500] [Job 14] Session setup failed: NT_STATUS_LOGON_FAILURE
E [20/Oct/2007:17:04:56 -0500] [Job 14] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [20/Oct/2007:17:04:56 -0500] [Job 14] Unable to connect to CIFS host, will retry in 60 seconds...
E [20/Oct/2007:17:05:56 -0500] [Job 14] No ticket cache found for userid=1000
E [20/Oct/2007:17:05:56 -0500] [Job 14] Can not get the ticket cache for jdlongmire
E [20/Oct/2007:17:05:56 -0500] [Job 14] Session setup failed: NT_STATUS_LOGON_FAILURE
E [20/Oct/2007:17:05:56 -0500] [Job 14] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [20/Oct/2007:17:05:56 -0500] [Job 14] Unable to connect to CIFS host, will retry in 60 seconds...
E [20/Oct/2007:17:06:56 -0500] [Job 14] No ticket cache found for userid=1000
E [20/Oct/2007:17:06:56 -0500] [Job 14] Can not get the ticket cache for jdlongmire
E [20/Oct/2007:17:06:56 -0500] [Job 14] Session setup failed: NT_STATUS_LOGON_FAILURE
E [20/Oct/2007:17:06:56 -0500] [Job 14] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [20/Oct/2007:17:06:56 -0500] [Job 14] Unable to connect to CIFS host, will retry in 60 seconds...
E [20/Oct/2007:17:07:56 -0500] [Job 14] Unable to connect to CIFS host after (tried 3 times)
E [20/Oct/2007:17:07:56 -0500] PID 7235 (/usr/lib/cups/backend/smb) stopped with status 1!
E [20/Oct/2007:17:07:58 -0500] PID 7234 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!

---

