---
title: "getting started w/ubuntu"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by prezbedard on 2006-04-19
Hello,

I have must installed ubuntu. I have fiddled with 'nix in the past and was always prompted to enter a root password. However during the install I was asked to create a user but never to create a root password. Is there a default root password?

Also at boot time it gimes me a cli login. How do I get the gui login? I unstalled with the "server" option perhaps I need to install gnome and X windows?

Thanks,

---

### Post by Mustard on 2006-04-19
Firstly ubuntu doesnt use a root password by default.  This link explains the situation..
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Secondly, you can install either gnome, kde or xfce, (or all of them if you so desire) using these commands respectively..

```
sudo apt-get install ubuntu-desktop
#installs gnome
```

```
sudo apt-get install kubuntu-desktop
#installs kde
#you will need an active internet connection

```

```
sudo apt-get install xubuntu-desktop
#installs xfce
#again this will need an active internet connection

```

When any of these above commands ask for a password, they are asking for your user password. Read first link to find the explanation of this.

Probably best to go with gnome, as this is what is on the install CD.

---

### Post by Sef on 2006-04-19
> s there a default root password?

Root is disabled by default.  Sudo is a fake root that works just fine.

> Also at boot time it gimes me a cli login. How do I get the gui login? I unstalled with the "server" option perhaps I need to install gnome and X windows?

Server just gives you a command line.  To get gnome and X windows installed, type this:

sudo apt-get update

sudo apt-get install ubuntu-desktop

---

### Post by gondilon on 2006-04-19
[QUOTE=prezbedard]Hello,

I have must installed ubuntu. I have fiddled with 'nix in the past and was always prompted to enter a root password. However during the install I was asked to create a user but never to create a root password. Is there a default root password?

Also at boot time it gimes me a cli login. How do I get the gui login? I unstalled wit the "server" option perhaps I need to install gnome and X windows?

Thanks,[/QUOTE]
first off, which ubuntu version are you running? If its breezy, then when the installer starts, it should tell you" to install the base system only type "server" and press enter, for the default installation, press enter." the server installation does not have x windows. You need to install the full version.   ubuntu does not have a root password per say.  your password to your account that your create during installation is used at the root password when needed.  to run a command as root type sudo and then the command. You will then be prompted for your account password. sertain programs also ask for your password.

---

### Post by prezbedard on 2006-04-19
Well I have one of answers. I found out why there is no root password.

This explains it for the other newbies that may come around.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by 5-HT on 2006-04-19
i) About Root:

The root account is locked by default in Ubuntu. 
Ubuntu uses 'sudo' which allows commands to be effectively run as root.
Here's a link in the wiki that discusses the matter: [Ubuntu Wiki RootSudo]("https://wiki.ubuntu.com/RootSudo")

ii) About doing the server install:
 
Yup, X is not installed by default with a server install.
You could install X and anything else you'd like, but there are some convenient metapackages to get you up to a standard desktop install:

 a) For Ubuntu (GNOME): ```
sudo apt-get install ubuntu-desktop 
```  b) For Kubuntu (KDE): ```
sudo apt-get install kubuntu-desktop 
``` c) For Xubuntu (XFCE):  ```
sudo apt-get install xubuntu-desktop
``` 
Hope that helps.


*EDIT: wow, that was fast

---

### Post by prezbedard on 2006-04-19
Thanks for the response.

It is 5.10 breezy badger.

Thats what I figured when I didn't recieve a gui login.

---

### Post by prezbedard on 2006-04-19
Thanks 5-HT.

It gets me on the right track on what to do next.

Can I install from the CD as at the moment the station I installed on is not connected to the net. Can I assume the apt-get will ask which install method or will it automatically attempt to retrieve the package from the net?

---

### Post by Mustard on 2006-04-19
[QUOTE=prezbedard]Thanks 5-HT.

It gets me on the right track on what to do next.

Can I install from the CD as at the moment the station I installed on is not connected to the net. Can I assume the apt-get will ask which install method or will it automatically attempt to retrieve the package from the net?[/QUOTE]

Currently in your /etc/apt/sources.list there will be an entry for your CD ROM installation disk at the top of the sources.list file.  Apt-get will use that as a resource for getting packages in the absence of an internet connection.  This will restrict you to installing gnome at the moment.

---

### Post by prezbedard on 2006-04-19
Thanks people for getting me off on the right foot. :)

---

### Post by richardward101 on 2006-04-19
Root has no password, as previously stated, but if you want to give it one, eg to use su instead of sudo (bad idea) or log in as root (again bad idea), just type:

sudo passwd

in a terminal. First it'll ask you for your sudo password (the password you use to log into your regular account) then it'll ask you for a new root password and then to confirm it.

You can then log in as root and use su (logging in as root requires you to enable it in the login screen options).

---

