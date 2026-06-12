---
title: "SMB sharing problem - can't delete files on Ubuntu box"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by digitaldave on 2007-11-14
I've managed to share some folders on my Ubuntu box so I can see them on my Mac, but although I can add files to the Ubuntu shared areas, I can't delete them because I don't have the correct privileges :(. I set the shares up using the GUI, and they are set to read/write (at least I assume they are, the read only tick box is cleared). I'm guessing I've forgotten to do something somewhere, any ideas?

Tanks,

Dave.

---

### Post by myk.dinis on 2007-11-14
Can you do me a favor? post your /etc/samba/smb.conf

I'll help you sreamline it for your needs...

Cheers!

Myk

---

### Post by powder on 2007-11-14
If you are logging into the Ubuntu box with no authentication, then you have to set permissions on the folder for "Others" to "Create and delete files".

---

### Post by digitaldave on 2007-11-14
@myk.dinis

Here's the contents of etc/samba/smb.conf:

[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY
wins support = yes

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[user1]
path = /home/user1
comment = linux-server
available = yes
browsable = yes
public = yes
writable = yes

[user1]
path = /home/user1
available = yes
browsable = yes
public = yes
writable = yes
comment = linux-server


@Powder,

Not sure what you mean by logging in with no authentication :(. Could you elaborate a little? Once I know where to look, I'll start digging to find the answer ;).

---

### Post by powder on 2007-11-14
No authentication meaning you do **not** type in a username and password when you access your Ubuntu box.  In which case, you are automatically logged in with "Others" privileges.  You would need to check the Properties of your /home/user1 directory and make sure "Others" have "Create and delete files" next to "Folder Access".

---

### Post by digitaldave on 2007-11-14
> **powder said:**
> No authentication meaning you do **not** type in a username and password when you access your Ubuntu box.  In which case, you are automatically logged in with "Others" privileges.  You would need to check the Properties of your /home/user1 directory and make sure "Others" have "Create and delete files" next to "Folder Access".

Took me a few minutes to find it, but I've sorted it out now, many thanks :).

Dave.

---

