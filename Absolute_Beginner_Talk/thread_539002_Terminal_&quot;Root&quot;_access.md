---
title: "Terminal &quot;Root&quot; access"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Aucklander on 2007-08-30
I cannot use the "Terminal" command line as root, even when I type "SU" followed by the "Root" password. :confused::confused::confused: simply it doesn't work that way at all. Check the attachment plz. Any suggestion is appreciated. Thanks

---

### Post by cookies on 2007-08-30
Use 

sudo

The password is the password you use to log in.

---

### Post by jingo811 on 2007-08-30
What command are you trying to execute besides making yourself SUDO?
Like when you want to backup XORG.conf file terminal might say that you don't have permissions then you just add sudo in front of your command and type your password when asked.

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Check out some sudo examples in action in the Feisty Wiki.

---

### Post by bodhi.zazen on 2007-08-30
Ubuntu uses sudo and locks the root account :

	[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by thegreenblob on 2007-08-30
If you really wanna log in as root instead of using sudo you can go to System>Administration>Users and Groups.

And then hit properties on the root account and change the password.

---

### Post by Seti on 2007-08-30
or just do:```
sudo passwd
```

and enter a password you want to use to su to the root acct. That simple.

---

### Post by wirelessmonkey on 2007-08-30
If your REALLY need to do something as true root, that sudo won't work for (virtually nothing, btw) you can type:  sudo su

---

### Post by 5-HT on 2007-08-30
> **wirelessmonkey said:**
> If your REALLY need to do something as true root, that sudo won't work for (virtually nothing, btw) you can type:  sudo su
sudo -i will give you a full root-login shell.
cheers,

---

