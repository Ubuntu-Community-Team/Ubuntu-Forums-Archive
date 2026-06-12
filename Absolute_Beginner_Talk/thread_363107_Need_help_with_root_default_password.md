---
title: "Need help with root default password"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by henoh on 2007-02-16
I finished installing Linux with no problems. I just can't boot with the root username. I tried everything as the password; blank, password, root, admin. Any help would be very much appreciated.

Thanks,

---

### Post by taurus on 2007-02-16
The root account is locked.  If you need to run something as root, use sudo or gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by LotsOfPhil on 2007-02-16
You can't login as root.
If you want to run something as root, login with the account you set up during the install. Preface a command with "sudo" and you will run it as root.

When prompted for your password (with sudo) use the same password for the account. 

Read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by vigleik on 2007-02-16
You're not supposed to be able to log in as root. Whenever you need to execute a command as root, type "sudo your_command" in a terminal window.

If you really really want to log in as root, it is possible to enable the root account. But unless you have special needs that's a bad idea.

---

### Post by Rasidrew on 2007-02-19
I'm trying to access Networking so I can config my wireless setup.  I've tried both my root password and my user password.  Neither one works.  Help!!!!

---

### Post by Rasidrew on 2007-02-19
In addition, when I use my user password, I get "The Underlying authorization mechanism (sudo) does not allow you to run this program.  Contact the system administrator.  I've tried running sudo network-admin from the terminal but nothing happens.

---

### Post by taurus on 2007-02-19
What's the output of this command from a terminal?

```
id
```

p.s.  Which release are you using right now?

---

### Post by Rasidrew on 2007-02-19
Release 6.10 (OEM). 
uid=1000(areece) gid=100(users) groups=0(root),4(adm),100(users)
I'm the only one using this computer and Ubuntu is the only operating system on it.  I created my user id areece after not being able to log on using OEM and my installation password.

---

### Post by taurus on 2007-02-19
You also need to belong to group admin besides adm before you can use sudo/gksudo.  Therefore, boot into recovery mode from GRUB menu and at the prompt, type

```
adduser areece admin
id areece
```
What's the output of the last command?

---

### Post by Rasidrew on 2007-02-19
adduser areece admin returns "adduser: The group 'admin' does not exist"
id areece returns "uid=1000(areece) gid=100(users) groups=100(users),0(root),4(adm)"

---

### Post by Rasidrew on 2007-02-19
I used nano in recovery mode to edit etc/group.  I changed it from lsgroup to group, then I did a adduser areece admin.  But when I log in as areece and do a sudo network-admin and use my areece password, it says "areece is not in the sudoers file.  This incident will be reported."  Addendum:  I went back to recovery and used nano to edit etc/sudoers to add "# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL"

It worked!!!!

---

