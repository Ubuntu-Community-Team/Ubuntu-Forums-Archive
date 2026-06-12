---
title: "Filesharing hell"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2007-01-25
Ok, I really don't know much about networking, I have followed guides and guides nut all I 've managed to do is really mess up my win xp (laptop) and ubuntu (desktop) systems. 

**What I want:** Share files between the two machines through a GUI (as in Places-->network servers).

**Current configuration of both machines**: Totally messed up (both of them). Right now Windows shows only their share files on network places and both of the pc's on "computers of this groupwork", however if u cick on ubuntu machine it produces it cant connect. Ubuntu on the other hand show nothing under Places-->network servers.
I had managed to get the one to see the other, then they stopped working, I started setting each machine as as WINS and ...well I said its really messed up right now.

Notes: None of the machines in always on (in other words I dont run a server of any kind).
Both machines are connected through a switch. Ping works for both machines.

Please can someone tell me how to share files between the two systems (without formatting and installing any of the OSes would be nice ;) ).

---

### Post by Aberrix on 2007-01-25
try [this]("http://ubuntuforums.org/showthread.php?t=249889")

---

### Post by geokok1981 on 2007-01-25
> **Aberrix said:**
> try [this]("http://ubuntuforums.org/showthread.php?t=249889")

Thanks, but it seems like it more server orientated and sounds like an overkill for my case.
Besides I would really like to stick with samba.

---

### Post by hyper_ch on 2007-01-25
Here's my pretty basic samba howto (I prefer using command line, so all commands are by the command line...):

(1) Get samba installed
```

sudo apt-get isntall samba

```

(2) Make a backup of the original samba config
```

sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.old

```

(3) Enter a new samba config:
- Open nano (or any other text editor that you want)
```

sudo nano /etc/samba/smb.conf

```

- Enter the new config
```

[global]
workgroup = ARBEITSGRUPPE
hosts deny = 10.0.0.1

[Exchange]
comment = Exchange
path = /home/hyper/exchange
force user = hyper
force group = hyper
read only = No

[Appz]
comment = Appz
path = /home/hyper/appz

```

Some explanations:
workgroup = --> ADD YOUR WORKGROUP NAME
hosts_deny = --> I only want samba work in the local network... so I add there the IP of my router... hence no outside connection can use samba... leave that blank, erase that line or fill in your "undesired" IPs... you can add multiple things separated with a comma each (e.g. 10.0.0.1, 10.0.0.2, 10.0.0.9, ....)
[exchange] --> Grant read/write permissions to that folder....
comment = Exchange
path = --> Tell what you want to have as exchange folder
force user = --> the user that shall be used on default of new files created in that folder
force group = --> the group that shall be used on default of new directories created in that folder
---> You may just want to put your linux user in there....
read only = No --> Make it RW

[appz] --> Name of the read only folder
comment = Appz
path = --> Path to it...

Once you've done your edits, press "ctrl-x" to exit the file in nano... you will then be asked whether it shall be saved: type "y" and then you will be asked what name it shall have: just hit "enter"

(4) Reload samba
```

sudo /etc/init.d/samba restart

```

(5) Go to windows, go to the "add network ressource", add as path "\\your-ip\Exchange" and then "\\your-ip\Appz"

---

### Post by hyper_ch on 2007-01-25
Oh, forgot a few things...

(6) Add users to the ubuntu system:
```

sudo useradd NEW_USER

```
Of course replace NEW_USER with something else... e.g. samba... sharing... or whatever...

(7) Create a password for that user:
```

sudo passwd NEW_USER

```

(8) Add that new user to the samba user-db
```

sudo smbpasswd -a NEW_USER

```

Alternatively you can just use your normal user (the one you are currently logged in) and just do step 8 (and by-passing step 6 and 7)

---

### Post by geokok1981 on 2007-01-25
@sjau

You are the man! Thanks! you can not possibly imagine how relieved I am that it worked. The  Windows machine shows "lan-->the win machine" and "internet-->my ubuntu shares". Ubuntu  shows both shares as well.

Just two more questions:
1. After rebooting both machines if I go to Places-->Network servers and try to navigate through the folders O get an error that the workgroup can not be found. However, if I go to the win machine, click on the share, insert the username and password then both of the machines can see each other. Can we fix that so I have access from Ubunti to win without using the  win machine at all?
2. I did the smbpasswd -a thing, but the last time I had done smbpasswd -e as well. Why did we skip it now? Is there any point in doing it?Also, is it possible to have the windows machine ask for a username and password each time I try to open the shared folder?

---

### Post by hyper_ch on 2007-01-26
I haven't evere tried accessing windows shares from ubuntu so I can't help there...

And regarding the smbpasswd -e option --> no clue... I have told what I did and what works for me :)

---

### Post by geokok1981 on 2007-01-26
> **sjau said:**
> I haven't evere tried accessing windows shares from ubuntu so I can't help there...

And regarding the smbpasswd -e option --> no clue... I have told what I did and what works for me :)
It turns out that smbpasswd is only needed if you disable a user first (smbpasswd -d), otherwise -a flag is all you need. 
I hope someone can give a hint on how to access win share from ubuntu directly though, without going to windows first.

---

### Post by dann0 on 2007-01-26
You might need to install smbfs first.
**sudo apt-get install smbfs**

Then (from the terminal) create a folder to mount in, **like /home/win**
the command: **sudo mount -t smbfs //ip-to-win/share_name /home/win -o username=YOU,password=BLA,uid=YOU,gid=YOU**

username an password is what you have on the win-box, uid + gid your userID and GroupID in Linux, most likely your username.

Or you can go to Places -> Connect to server, and choose “Window share”, and fill in the rest.

---

### Post by nzmoose on 2007-01-28
thanks sjau.
this is the definitive easy way to get samba going.

---

### Post by serlex on 2007-01-31
hate to bring this thread back, trying out samba. I can load shared folder of my Windows box through 'smb://192.168.1.3', but can not see all the computers under 'Windows Network'. Same with windows, it cant see my Ubuntu box

---

