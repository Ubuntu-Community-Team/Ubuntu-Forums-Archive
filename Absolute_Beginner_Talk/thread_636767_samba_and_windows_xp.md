---
title: "samba and windows xp"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by thamood on 2007-12-10
hi guys i have setup samba on my Ubuntu machine 7.10 and shared a folder....

the computer apears on windows xp but when ever i double click it tell me 

"\\thamood is not accessible bl bla bla you might not have permission to use network recourse contact bla bla bla"....

anyone?! HEEELLLLLPPPP

---

### Post by subs on 2007-12-10
> **thamood said:**
> hi guys i have setup samba on my Ubuntu machine 7.10 and shared a folder....

the computer apears on windows xp but when ever i double click it tell me 

"\\thamood is not accessible bl bla bla you might not have permission to use network recourse contact bla bla bla"....

anyone?! HEEELLLLLPPPP



i think this is what u need.....

> [http://www.reallylinux.com/docs/sambaserver.shtml](http://www.reallylinux.com/docs/sambaserver.shtml)

---

### Post by Irony on 2007-12-10
11

---

### Post by Irony on 2007-12-10
Here's an example of /etc/samba/smb.conf file - note that the folder /media/hda5/share must have its permissions set to allow access (its permissions supersede those of those set in the smb.conf file). Also the shared folder is on a ext3 filesystem, you can use fat32 but it becomes more complicated because it doesn't accept permissions;

```
[global]
        workgroup = HOME
        netbios name = NET
        server string = %h server (Linux)
        security = SHARE
        acl compatibility = winnt
        server signing = auto
        preferred master = No
        domain master = No
        dns proxy = No
        ldap ssl = no
	wins support = no

[homes]
        comment = Home Directories
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[share]
        comment = ext3system
        path = /media/hda5/share
        guest ok = Yes
	available = yes
	browsable = yes
	public = yes
	writable = yes
```

---

### Post by thamood on 2007-12-12
thanx guys i thnk the problem was with the firewall....and iptables....it's working fine now....

---

