---
title: "Networking Xubuntu to XP Help"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Gif on 2007-04-17
Hi,

I'm looking for a really basic tutorial (newbies) for connecting and forming a network with my newly installed project Xubuntu system and existing xp machine.

The Xubuntu connects via Ethernet to modem/router and the xp via wireless adapter to modem/router. Both have Internet access working via the router.

I would like to share one folder on the Xubuntu system so that the xp machine can access it.

After searching the forums and reading lots of posts, I still have no idea where to start on this - any links to tutorials or tips would be very welcome!

Thank you,
:confused:

---

### Post by joshjani on 2007-04-17
> **Gif said:**
> Hi,

I'm looking for a really basic tutorial (newbies) for connecting and forming a network with my newly installed project Xubuntu system and existing xp machine.

The Xubuntu connects via Ethernet to modem/router and the xp via wireless adapter to modem/router. Both have Internet access working via the router.

I would like to share one folder on the Xubuntu system so that the xp machine can access it.

After searching the forums and reading lots of posts, I still have no idea where to start on this - any links to tutorials or tips would be very welcome!

Thank you,
:confused:

Me too! Me too! I would love such info...Have a long post to such effect, too!
JC

---

### Post by jakev383 on 2007-04-17
To put it in a short form:
You need to install samba and share a folder.
Look in Synaptic for it - you'll see that it has a GUI interface to share the folders as well. I didn't find the GUI all that intuitive myself, but I learned to setup Samba by the CLI myself.
If you install samba, you can use this quick config to share a folder (this is a snipped one from my FC machine):
```

[global]
        log file = /var/log/samba/samba.log
        smb passwd file = /etc/samba/smbpasswd
        passwd chat = *New*password* %n\n *Retype*new*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*

        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        obey pam restrictions = yes
        useranme map = /etc/samba/smbusers
        encrypt passwords = yes
        unix password sync = yes
        public = yes
        passwd program = /usr/bin/passwd %u
        allow hosts 192.168.5. 192.168.123. 127.
        dns proxy = no
        server string = Ubuntu Server
        unix password sync = yes
        workgroup = Home Network
        os level = 20
        security = share
        max log size = 1000
        pam password change = yes
[SharedFolder]
        comment = Shared Folder
        path = /SharedFolder
        writeable = yes
        guest ok = yes
        read only = no
        public = yes
        follow symlinks = no
  vfs object = recycle
        recycle:repository = .deleted
        recycle:keeptree = no
        recycle:touch = Yes
        recycle:versions = Yes
        recycle:maxsixe = 0
        recycle:exclude = *.tmp
        recycle:exclude_dir = /tmp

```
That should give you a share called "SharedFolder" that everyone on the network can read/write to (remember to add your network address to the "allow hosts" line and don't remove the 127. entry!!!!!). It will also give you a folder called .deleted (hidden file) where when you delete files off of the share, they will be placed into this folder just like the Recycle Bin on Windows/Mac.
Enjoy!

---

### Post by dstew on 2007-04-17
To share a folder on your Xubuntu machine, you will need to install and use Samba client. If you want to see a shared folder on your XP machine from your Xubuntu machine, you need to install and use smbfs. It is easier to use smbfs than to set up the Samba client, so if you want to link the two machines, just share the folder in Windows and use smbfs to connect to it from your Xubuntu machine.

For all the gory details, this is the Samba site: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

One thing: to install Samba, do not compile from source. You can install Samba and smbfs from Xubuntu using the Synaptic package manager. Or, on the command line, you can use:

sudo apt-get install samba smbfs

This wiki has a huge page, but good instructions for doing samba client or the more simple smbfs:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by Gif on 2007-04-21
Hi,

Entered:
```
sudo apt-get install samba smbfs
```

Then went to [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper) and found [COLOR="Red"]# 21.3.6 How to share group folders with read/write permissions (Authentication=Yes)[/COLOR]
and entered:
```
sudo mkdir /home/group
sudo chmod 777 /home/group/
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
gksudo gedit /etc/samba/smb.conf
```
But received this error:
```
:~$ gksudo gedit /etc/samba/smb.conf
sudo: gedit: command not found

```

What do I do?:-k

---

### Post by quimchin on 2007-04-21
> **Gif said:**
> Hi,

Entered:
```
sudo apt-get install samba smbfs
```

Then went to [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper) and found [COLOR="Red"]# 21.3.6 How to share group folders with read/write permissions (Authentication=Yes)[/COLOR]
and entered:
```
sudo mkdir /home/group
sudo chmod 777 /home/group/
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
gksudo gedit /etc/samba/smb.conf
```
But received this error:
```
:~$ gksudo gedit /etc/samba/smb.conf
sudo: gedit: command not found

```

What do I do?:-k

gedit is a gnome specific text editor. Replace the command with something like "nano"

---

### Post by Gif on 2007-04-22
OK

Entered
```
sudo nano /etc/samba/smb.conf
```

and
```
sudo testparm
```

which output
```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Group]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/smbusers
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Group]
        comment = Group Folder
        path = /home/group
        valid users = system_username1, system_username2
        force user = nobody
        force group = nogroup
        read only = No
        create mask = 0700
        directory mask = 0700
        guest ok = Yes
```

Then Entered
```
sudo /etc/init.d/samba restart
 * Stopping Samba daemons...                                             [ ok ]
 * Starting Samba daemons... 
```

[COLOR="Blue"]What do I do next? Can see Ubuntu from XP but will not let me in - it says not accessible, you may not have permissions etc....[/COLOR]

---

### Post by Gif on 2007-04-23
I think I need to permit the XP machine in, but do not know how to go about this!   :(

---

### Post by tact on 2007-04-23
It all happened so fast for me I am not sure if I am forgetting any steps but sharing a folder was easy for me in Edgy and Fiesty...

I right clicked on a folder and then selected "share folder".   The first time I did that after installing either Edgy or Fiesty a message box popped up and said "you have to install either NFS or Samba to share folders/files" and there were checked check boxes beside NFS and Samba and an "install" button.

I clicked Install of course...  let it install both NFS and Samba.  It did all the apt-get install stuff for me.  Once it was done the file was shared.

simple?

---

### Post by Gif on 2007-04-25
The folder is sharing amongst ubuntu users + groups but not letting the windows machine see the folder!

---

### Post by lazork on 2007-04-25
I'm having the same problem.
On windows it says not accessible, you may not have permissions etc.

If it can help here's the smb.conf file:
```

[global]

   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0

   panic action = /usr/share/samba/panic-action %d

security = share

   encrypt passwords = true
 null passwords = Yes

   passdb backend = tdbsam

   obey pam restrictions = yes

   invalid users = root

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

   socket options = TCP_NODELAY

wins support = no
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

[SharedFolder]
path = /home/default/SharedFolder
available = yes
browsable = yes
public = yes
writable = no
guest ok = yes
   create mask = 0777
   directory mask = 0777
   force group = WORKGROUP
```

---

### Post by dolphin_oracle on 2007-04-25
When you browse to the share from your WinXP machine, does it ask for a login name and password?  that login name and password must have samba accounts AND ubuntu accounts.  I believe the command is 

sudo smbpasswd –a *your_login_name*  

it will then ask for a password, and then confirm it.  Make sure that that login name and password match the ubuntu user account.  

One note:   I don't believe ubuntu will let you login in with the same user name twice, in case that matters.  In other words, the XP machine must login with a different user name than whatever is currently in use on the ubuntu machine.  I could be wrong about this, but it seems to be the case in my house (xubuntu and xp machines connecting to ubuntu server).

Good luck.

---

### Post by Gif on 2007-04-25
> When you browse to the share from your WinXP machine, does it ask for a login name and password? that login name and password must have samba accounts AND ubuntu accounts

No there is no request for any login details - just says 'not accessible, you may not have permissions etc..'

---

### Post by dolphin_oracle on 2007-04-26
Here's a link to the Howto (by stormbringer) I used.  Its pretty good.

I noticed in your smb.conf file that your force_user and force_group entries are different.  In mine they are the same (the primary login) as per the howto below.

good luck.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by tact on 2007-05-03
As mentioned in an earlier post.... I just right clicked on a folder I wanted to share and after saying "ok" to a dialog box came up telling me i need to install/configure NFS and Samba it all just worked.   

I forgot one step - I think I might have had the problem whereby windows users got the "folder is inaccessible to you" message.   I fixed that by altering the permissions of the shared folder so that "others" can read/write/execute

---

