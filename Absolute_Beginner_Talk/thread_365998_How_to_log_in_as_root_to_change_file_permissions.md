---
title: "How to log in as root to change file permissions"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by rbradshaw on 2007-02-20
I realized why I can't save files into certain folders while in the GUI; I don't have permissions on the folders (which are owned by root). Since I have been doing most of my Ubuntu work from the GUI, I am starting to migrate slowly to the command line. My most important issue now is that I don't know how to login as root. I log into the GUI with my user name and password, and it takes me to my home directory. I don't recall ever being asked for a root password when I installed Linux. Hopefully, I don't have to re-install Linux to determine my root password. Please, any help is appreciated.

---

### Post by Maestro23 on 2007-02-20
RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ashmew2 on 2007-02-20
LOgging in as root is not recommended but u can still enable it , to do so , First of all goto 
System > Administration >Users and Groups > Double CLick root and set the password etc.

Then goto

System > Administration > Login Window > Security > Allow system admin login

Then Ctrl + alt +backspace to restart the GUI.
and login as root

---

### Post by ashmew2 on 2007-02-20
Be Extra Extra Careful When As Root!!!!!
:p

---

### Post by taurus on 2007-02-20
You can't log in as root since the account is locked.  However, you can use gksudo if you need to edit something as root.  

Open a terminal, Applications -> Accessories -> Terminal, and type
```
gksudo gedit **filename**
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by JamieC on 2007-02-20
Where can't you save files, in your home directory? 

Your root password is the password for your account. This is because you have sudo access (as you are the first or primary user). You can therefore use your account password to authenticate as root.

I'm assuming you want to change the permissions on the directory to which you do not have access?

---

### Post by teaker1s on 2007-02-20
sudo -for commandline
gksudo -for graphics

eg.
[COLOR="Red"]sudo apt-get install nameofpackage
gksudo synaptic
[/COLOR]

or root in terminal

[COLOR="Red"]sudo su[/COLOR] 
be very,very careful with this


**best way**
[COLOR="Red"]gksudo /usr/bin/nautilus[/COLOR] navigate to file and change permissions or move files as root

---

### Post by ashmew2 on 2007-02-20
OMG!! 7 replies in less than 5 minutes!! 
Ubuntu Forums really has Helpful people!!
Cheers for all you guys!!

---

### Post by rbradshaw on 2007-02-20
Yes, I want to change permissions on /var/www so I can save html files for Apache2 http server.

I don't remember during the installation of Ubuntu - is my primary user name (rbradshaw) also serving as my root login? Maybe I am logging into root using my user name as rbradshaw. I do know the permission on /var/www shows root.

Do I need to login to root to change the permissions on /var/www? How?

Sorry for the newbie factor. thanks

---

### Post by taurus on 2007-02-20
You can do something like

Applications -> Accessories -> Terminal
```
sudo chown -R rbradshaw:rbradshaw /var/www
```
Then, you are the proud owner of /var/www and you can write or delete whatever you want in there.

---

### Post by aktiwers on 2007-02-20
You can also do a :
```
gksudo nautilus
```

And then navigate to the folder you want or CTRL+L and type in the direction.

---

### Post by Bachstelze on 2007-02-20
Though there is a root user in Ubutu - like in any other Unix-like system - it is disabled for login by default. Instead, you use the sudo command to run commands as though you were root. For example, to change permissions of your /var/www folder, traditionnally, you would login as root and do :

```

chown -R username /var/www
chmod -R 755 /var/www
```

So in Ubuntu, youlogin normally and do :

```

sudo chown -R username /var/www
*** sudo will ask for a password here, it's _your_ password you need to type ***
sudo chmod -R 755 /var/www
```

Alternatively, you can use *sudo -i* to simulate an initial login as root - your shell will then behave the same way it does when you login as root in another system.

More info in the link taurus posted.

---

### Post by rbradshaw on 2007-02-21
Taurus - I want to say thank you for the clear instructions on sudo and changing permissions. I was able to change permissions using sudo chown and can copy files into /var/www folder.

Should permissions of /var/www be changed back to root? If I am the primary user (rbradshaw), why do I share the root password? When I did sudo chown, it did ask me for a password. Was it asking for root password? I see on the GUI that I can change root password. How do I verify if root password is the same as rbradshaw password?

Again - thanks for your advice, and others on this thread. I learned a lot about root, sudo, and working with permissions.

---

### Post by erani on 2007-05-03
And how can I enable root login with GUI in Kubuntu?

---

### Post by aysiu on 2007-05-03
> **erani said:**
> And how can I enable root login with GUI in Kubuntu?
Why would you do that? It's completely unnecessary and insecure.

If you want to browse as root, press Alt-F2 and type ```
kdesu konqueror
```

---

### Post by erani on 2007-05-04
For me is not necessary but my boss want this

---

