---
title: "sharing ubuntu&gt;windows"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Balinsky on 2007-07-05
ok so in my admin pannel i have some folders shared on my ubuntu machiene. but when i try to access them from a windows computer it wants me to input a username and password. no combination works that i can tell. 

any ideas?

happens on both XP and Vista if that matters
thx
JeBsky

---

### Post by herbster on 2007-07-05
Balinsky,

I may be wrong but from what I know, Ubuntu uses the ext3 filesystem and Windows will be using at least FAT32 or NTFS, so it cannot read linux partitions.

However the opposite is entirely functional; one can view Windows filesystems in Ubuntu (I do it everyday).


Someone chime in...

---

### Post by Raineer on 2007-07-05
It can work fine if you have Samba installed.

That being said, the username and password that you logged into Linux with should work fine.

---

### Post by jackocleebrown on 2007-07-05
Hi,

I've not used the ui to setup samba file sharing but the configuration is in this file "/etc/samba/smb.conf"
I've put my smb.conf file below which does a simple file share with no login required which sounds like the kind of thing that you want. The bits after "#" are my comments on bits you'll need to change, remove them when you are done.
you'll need to open the file using sudo to have permission to edit it, you can do this from the terminal with
"sudo gedit /etc/samba/smb.conf"
make a backup of your current file just in case you want to go back.
Once you have finished making changes restart samba with this command "sudo /etc/init.d/samba restart" and see if it has worked.

I hope that this helps, let me know how you get on.

Jack.




# Global parameters
        workgroup = # put the name of your workgroup here
        netbios name = # put the name of your computer here
        server string = %h
        hide dot files = Yes
        security = share
        log file = /var/log/samba/log.%m
        max log size = 50
        wins support = no
        domain master = no
        
[MUSICA] # share name as you wish it to appear on the network
path = /musica # path to shared folder
comment = Music on Slimserver # comment appears when browsing network
available = yes
browseable = yes
public = yes
writable = yes
create mask = 0666
directory mask = 0777

---

