---
title: "Help mounting college network drive"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by wildseven on 2006-09-22
hello all. I am having a problem mounting my schools network drive.  
I read the psycho cats website and it doesnt seems to help. I made a mount point like normal and i did this
```
mount //136.224.0.0/student/santilmgweb /mnt/SchoolDrive
```

and then it says wrong file system.

i read something about needing SAMBA, and i have not yet downloaded it yet. I read the samba website and i am still unclear what it's uses are. It says helps use windows file and printer services, does that include windows network drives?

if someone could help me mount it, and simplify the meaning of SAMBA, it would be greatly appreciated.

thank you

-wildseven

---

### Post by jordanmthomas on 2006-09-22
```
sudo apt-get install samba
```
You should, though have what you need to mount the drive already.
Do you have to supply a username and password to log in?
There is also a command called smbmount you could give a shot.

Try this
Open up a nautilus (file manager window)
Press <Ctrl>L
type
```
smb://136.224.0.0/student/santilmgweb
```
I'd be willing to bet you need a name and password, which is why your mount may not work.
At least this way you should be able to access your files, even if it's not accessible via command line.

---

### Post by wildseven on 2006-09-22
yes there is a login/password. is there an option to apply that?

---

### Post by jordanmthomas on 2006-09-22
I'm not sure.  I will look it up (you should as well))

---

### Post by jordanmthomas on 2006-09-22
Try this:
```
sudo smbmount //136.224.0.0/student/santilmgweb /mnt/SchoolDrive -o username=*username*
```
it will ask for your password (sudo) first, and then for the samba password

---

### Post by steve.horsley on 2006-09-22
That IP address looks wrong to me.

If you don't actually need to mount the drive, you can create an icon that opens a drive in Nautilus if you want. You can then just drag files to/from a nautilus window which is open on your local filesystem. I do this - I have a directory full of icons for different servers. Create a file with contents someting like this:
> 
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=SchoolDrive
Type=Application
Exec=nautilus smb://DOMAIN;username@136.224.0.0/student/santilmgweb
Terminal=False
TryExec=
X-GNOME-DocPath=
GenericName=
Comment=


---

### Post by jordanmthomas on 2006-09-23
I just add a bookmark in nautilus.

---

### Post by wildseven on 2006-09-23
thank you very much all. i just did
```
smb://student/santilmgweb
```

that seemed to work,
how do i mount it permenantly though?

---

### Post by chrisfay on 2006-09-23
Add the share in /etc/fstab.

You'll need the samba file system:

```
sudo apt-get install smbfs
```

---

### Post by wildseven on 2006-09-23
im kinda new to playing with fstab, but would i have to put that 777 stuff on it? or can someone provide me a link where i can read up on using fstab?

---

### Post by chrisfay on 2006-09-23
```
sudo mkdir /mnt/share
```

```
sudo vi /etc/fstab
```

Then add a line similar to this:

```
//CHRIS/ubu_backups  /mnt/share smbfs 0   0
```

Replace: //CHRIS/ubu_backups with your //Server/Share

Hit the 'esc' key then:
```
:wq
```
(to save the file and exit)

Then mount it using:

```
sudo mount -a
```

If you're not sure what the //Server/share is you can check it by using the command:

```
sudo smbtree
```

---

### Post by wildseven on 2006-09-23
thank you very much ^^

i don't want to be a pain heh~ but i also want to learn more about this OS. is there a link someone can send me to learn more about mounting and permissions?

---

