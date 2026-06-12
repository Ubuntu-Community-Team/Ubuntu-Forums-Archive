---
title: "Sharing no longer works in Ubuntu 6.10"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by joecool234 on 2007-04-01
I've been running Ubuntu 6.10 (Edgy?) for about a month now.  For several weeks, everything worked fine.  I was able to share both an HP printer (connected locally to the Edgy machine) and some file folders (on the sda2 partition) over my WinXP based network.  Now all sharing is broken.  I have a feeling the issues started after I installed Edgy updates (at some point last week, over 30 updates needed to be installed).  Can anyone tell me how to determine if the necessary servers are actually running?  I checked both cupsd.conf and smb.conf and they look kosher.

Here's the interesting part...I am logged is as the main user (I guess an administrator?) but when I try and edit the properties of a shared folder (using the System->Administration->Shared Folder GUI) it says "error accessing 'file:///media/sda2/Music': Access denied"  Why would this be.  I can browse the folder using the File Explorer just fine.  Any ideas?

---

### Post by joecool234 on 2007-04-01
Ok, now the problem gets even weirder.  I went to all of my WinXP workstations and uninstalled/reinstalled the printer.  Now all WinXP machines can print to the printer hooked up to my Edgy machine.  As for the folder issue, I can see all shares when I go to \\server.  My home directory is listed and is browseable, but all other shares give me a "\\server\music is not accessible.  You might not have permission to use this network resource...."

---

### Post by Henry Rayker on 2007-04-01
post the contents of your /etc/samba/smb.conf file

---

### Post by joecool234 on 2007-04-01
ok...here it is:
```
[global]


workgroup = 8974C
security = user
encrypt passwords = true
guest account = nobody

wins support = no
[printers]
comment = All Printers
browseable = no
path = /tmp
printable = yes
public = no
writable = no
create mode = 0700

[jlarosa]
path = /home/jlarosa
available = yes
browsable = yes
public = yes
writable = no

[music]
path = /media/sda2/Music
available = yes
browsable = yes
public = yes
writable = no

[global]
wins support = no


workgroup = 8947C

```

---

### Post by Henry Rayker on 2007-04-04
I'm sorry! I forgot about your post question. I've been too busy with my classes.

That smb.conf looks reasonably constructed. Some things I can suggest trying are, in the global section, 

map to guest = bad user (or bad password, try both)
also, you could try making the guest account your account (I assume jlarosa) just to see if it's a file permissions issue.

Again, many apologies for forgetting your thread.

EDIT: you may want to also try adding the WindowsXP usernames in a ```
valid users = [name of user]
``` (to clarify, don't include the [ and ])


ANOTHER EDIT:
also, could you add the following to the global section? A little logging never hurt anyone...
```
log file = /var/log/samba/log.%m
max log size = 50
```

---

### Post by joecool234 on 2007-04-04
I'll try this when i get home, but I think I just may need to reinstall...PERIOD.  Something is definitely wrong in the state of Denmark.  Now when I open file explorer, all the folders on my 'File System' partition have a little lock icon next to them.  I think it would be best if I start from scratch now that I know a little more about Linux.  But thanks for all of your help anyways.

---

