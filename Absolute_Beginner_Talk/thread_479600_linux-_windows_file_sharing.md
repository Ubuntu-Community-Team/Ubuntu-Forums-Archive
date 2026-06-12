---
title: "linux- windows file sharing"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by dhani99 on 2007-06-20
Hey reader, I 'm completely new to ubuntu. 
I'm having fun with it...
so i'm having problem,
I have another computer with windows xp . 
so   I have shared some folders from it! 
SO how do i access those! 
Thanksss.......

---

### Post by phr0ze on 2007-06-20
You can usually go up to 'Places' and select network. Keep clicking into the icons until you find your windows PC in the list. That should be it.

---

### Post by atria on 2007-06-20
Use samba. Verify that the smbfs package is installed, then do this:

```
smbmount -o username=<yourusername> //address_to_your_server/sharename /home/youruser/any_mountpoint
```

If it says you need root privileges just add a sudo infront.

---

### Post by dhani99 on 2007-06-20
> **phr0ze said:**
> You can usually go up to 'Places' and select network. Keep clicking into the icons until you find your windows PC in the list. That should be it.


but it says like this

---

### Post by dhani99 on 2007-06-20
> **atria said:**
> Use samba. Verify that the smbfs package is installed, then do this:

```
smbmount -o username=<yourusername> //address_to_your_server/sharename /home/youruser/any_mountpoint
```

If it says you need root privileges just add a sudo infront.

I don't know how to use samba, even don't know where it is.. 
i checked that through synapic package manager that it is in hdd and smbfs too.

---

### Post by phr0ze on 2007-06-20
After you use the provided command, your windows stuff will appear in your home folder. Try out the command provided and let us know what happens.

---

### Post by dhani99 on 2007-06-20
I use that command in terminal?????

---

### Post by atria on 2007-06-20
Heres a more detailed version of the procedure i mentioned above:

(The below code are all supposed to be entered into your terminal)
```

mkdir /home/<youruser>/<mount directory>

```

Replace <youruser> with your system's username and <mount directory> with any directory name you like, for example, fileshare.

```

sudo aptitude install smbfs

```

The above command installs smbfs, which is required to access the fileshare. If it is already installed then all is well, lets proceed:

```

smbmount -o username=<yourusername> //address_to_your_server/sharename /home/<youruser>/<mount directory>

```
The above command will prompt you for a password (if any) to access the fileshare.

Finally just browse to /home/<youruser>/<mount directory> using your file manager (nautilus).

When you're done with the fileshare you can unmount it using
```
umount /home/<youruser>/<mount directory>
```

If the mount commands do not work add sudo infront of them.

---

### Post by dhani99 on 2007-06-20
```

sudo aptitude install smbfs

```

Thanks man, I just did that and able to see network files.. 
Thanks Very mucccchhh..

---

### Post by dhani99 on 2007-06-20
another thing that i want to ask is that, I went to windows network places and saw this ubuntu's network over there, but when ever i click It asks me user and password, so wat do i do???

---

### Post by dhani99 on 2007-06-21
NEEED Help, guys...

---

### Post by Austin_KW on 2007-06-21
> **dhani99 said:**
> another thing that i want to ask is that, I went to windows network places and saw this ubuntu's network over there, but when ever i click It asks me user and password, so wat do i do???

You have two choices,
You can change the "security = user" to "security = share" in /etc/samba/smb.conf, This will remove the user passwords, like windows home networking (insecure)

OR usually recommended,  you can add an smb password for one of your usernames
sudo smbpasswd -a ***yourUserName***
Password: YourSudoPassword
New SMB password: YourNewSambaPassword

Then use yourUserName & YourNewSambaPassword to access  from windows etc.

---

### Post by nickpaton on 2007-06-21
Ever since I used Dapper I've always used [this]("http://ubuntuforums.org/showthread.php?t=202605") excellent HOWTO from Stormbringer, which will sort out all your problems and show you how to set up your Windows shares as well.

Remember to temporarily disable your firewall.  [This]("http://ubuntuforums.org/showthread.php?t=202605&page=30#298") HOWTO by myself explains how to set it up using Firestarter.

---

### Post by techno-mole on 2007-06-21
ive found that networking with fiesty is alot easier to set up.
all i did was to go to --> system --> administration --> and then click on shared folders, for me i get a warning saying that things need to be installed before i can set it up (samba related) once they have installed i then add the folders i want to share.
then i open terminal and typ sudo smbpasswd -a user name and hit enter
then i put new pass words in, i basically use my user name as my password.
and then i type sudo smbpasswd -e username and bobs your autnie.
i have found that you need to make sure that users are allowed to modify files on the xp machine.
we have 3 pc's 2 use xp as the main os and my pc uses ubuntu as the main and xp for some games.
cheers

---

