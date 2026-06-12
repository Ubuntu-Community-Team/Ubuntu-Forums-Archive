---
title: "Im Sorry To ask but i have to"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by RedGretsch18 on 2007-04-27
so my ubuntu 6.10 is up and running and i have to ask a massive newb question? how do you login as root the regular login screen says system admins aren't allowed to login from there thanks for any help

---

### Post by lamalex on 2007-04-27
we don't use root account. we use sudo for root administration. there are ways around it but there's no real point.

---

### Post by DrQuincy on 2007-04-27
For security you aren't meant to login as root - you use sudo every time you want to be root.

---

### Post by taurus on 2007-04-27
You don't log in as root.  Instead, you use sudo if you need to write something outside your $HOME directory.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by NICU on 2007-04-27
As far as I know - you don't log in as root.  If you want to perform administrator/root actions from the command line you have to type "sudo" before the command.  If you use an administrator application you will be prompted to enter your password.

---

### Post by SniperClops on 2007-04-27
So any user can SUDO, isn't that dangerous?

---

### Post by RedGretsch18 on 2007-04-27
oh ok i understand that makes sense this is my first time using linux well i switched from opensuse because i didnt get very far

---

### Post by thelocust on 2007-04-27
It is possible but not advised to make it so that you can login as root if you really want to go [here.]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_allow_root_user_to_login_into_GNOME") But you can just use sudo in terminal to take care of any thing you want to do as root.

---

### Post by RedGretsch18 on 2007-04-27
no you can restrict which users can sudo

---

### Post by Calash on 2007-04-27
Any user that you give the admin privileges to.   And you can restrict it even more if you want to really lock stuff down.

---

### Post by sailor2001 on 2007-04-27
> **SniperClops said:**
> So any user can SUDO, isn't that dangerous?

sudo  user has to have the password........it isn't open to "any user"

---

### Post by Tomosaur on 2007-04-27
> **SniperClops said:**
> So any user can SUDO, isn't that dangerous?

No, not every user can sudo, just those listed in the sudoers file.

---

### Post by taurus on 2007-04-27
Nobody can use sudo unless that user belongs to groups adm & admin.

```
id
```

---

### Post by jgatrell on 2007-04-27
if you have a lot to do and get sick of typing sudo you can give your shell root access by typing the following sudo bash.

Type exit to return to normal user mode.

---

### Post by ajgreeny on 2007-04-27
> **SniperClops said:**
> So any user can SUDO, isn't that dangerous?


No.  By default only the first user has sudoers rights, I think, though others can be given them if necessary.  This means the first person, ie. the one who normally will have installed the system is the only one who will know the sudo password to do any system wide activities.

---

