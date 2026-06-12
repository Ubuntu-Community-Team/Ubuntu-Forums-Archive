---
title: "root account"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by abbasali31 on 2008-04-15
How to login as a root account after the installation?  When I was installing ubuntu it asked during the installation to create a user/password.  Now, In order to login as a built in root account what needs to be done.  

I went into a terminal mode to add an account such as:

adduser  xxxx

it didn't let and asked me to login as a root.  I thought the username/password created during the installation has a full authority, and guess I was wrong.

---

### Post by HermanAB on 2008-04-15
$ sudo adduser joesoap
Password: yourownpassword

---

### Post by spydon on 2008-04-15
> **azhar-teza said:**
> How to login as a root account after the installation?  When I was installing ubuntu it asked during the installation to create a user/password.  Now, In order to login as a built in root account what needs to be done.  

I went into a terminal mode to add an account such as:

adduser  xxxx

it didn't let and asked me to login as a root.  I thought the username/password created during the installation has a full authority, and guess I was wrong.
No you were right, but to use that authority you need to type "sudo" before your commands, like ```
sudo adduser xxxx
```

EDIT: He was faster :'(

---

### Post by neurostu on 2008-04-15
But if you want to open the root account you can type:
```

sudo su

```

however there are almost NO reasons to do this, for the most part sudo will accomplish everything you need.

---

### Post by ibutho on 2008-04-15
Ubuntu does not use the root account like other Linux distros. If you need to do any sysadmin stuff, you have to be in the admin group and prefix any commands with sudo. More info is available [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by bodhi.zazen on 2008-04-15
> **neurostu said:**
> But if you want to open the root account you can type:
```

sudo su

```

however there are almost NO reasons to do this, for the most part sudo will accomplish everything you need.

You may wish to use :

```
sudo -i
```

Use gksu (kdesu on Kubuntu) for graphical applications.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

