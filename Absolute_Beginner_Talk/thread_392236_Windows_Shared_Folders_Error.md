---
title: "Windows Shared Folders Error"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by killernos on 2007-03-24
When I try to open my windows shared folders over my home network I get this error:

```
The filename "RONALD-FWH24EUP" indicates that this 
file is of type "desktop configuration file". The contents of the 
file indicate that the file is of type "x-directory/smb-share". If 
you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or 
received the file from a trusted source. To open the file, 
rename the file to the correct extension for 
"x-directory/smb-share", then open the file normally. 
Alternatively, use the Open With menu to choose a specific 
application for the file. 
```

Does anyone know how to fix this error??

---

### Post by lamalex on 2007-03-24
that doesn't look like an error so much as a warning. You can probably ignore it and be ok.

---

### Post by Clumber on 2007-03-24
I am having the same issue... if I ignore the warning, it  still doesn't open the Windows computer. 

:confused:

---

### Post by noMScraig on 2007-05-24
Looks like this is a bug

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/24660]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/24660")

bump...any workaround or guidance for a newbie yet??

thanks

---

### Post by noMScraig on 2007-05-30
Another low-tech answer to my problem...meaning no editing configs etc.

I tried konquerer to view my network shares and still could not get the shares to work.

I finally loaded smb4k and now I can access my windows shares

I had to configure smb4k to mount the windows shares as a super user (sudo) but now I can view through conqueror.

Anyway, that's how I got it to work.

-c

[global]
workgroup = @home
security = share
wins support = yes

# CUPS printing. See also the cupsaddsmb( manpage in the
# cupsys-client package.
; printing = cups
; printcap name = cups

[Share]
path = /home/craig/Desktop/Share
available = yes
browsable = yes
public = yes
writable = yes

[Movies and Pictures]
path = /media/NETHDD_/Movies and Pictures
available = yes
browsable = yes
public = yes
writable = yes

---

