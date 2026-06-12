---
title: "How to log in as root through terminal"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by oddbjorn on 2007-11-23
Hey there, im am brand new do this linux distro. I'm usuing ubuntu "ubuntu-7.10-desktop-i386" in WM-ware. But when im trying to install a program it tells me that i need to log in as an admin or a superuser. But where can I do that? Sorry for beeing such a beginner. 

Best regards Oddbjørn.

---

### Post by MaximusTG on 2007-11-23
Ubuntu has no superuser by default, only a normal user which can gain superuser privileges by preceding a command that needs to be run as root with "sudo" (without quotes).
If you need to do a lot of things as root and don't want to bother with sudo for each command, enter

sudo su 

to become root.

The password sudo asks for is your own user password

---

### Post by LaRoza on 2007-11-23
You don't log in as root, although it is possible.

Run the command as usual but use "sudo": [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Znort_Ubern00b on 2007-11-23
you need to ensure ytou are in the admin group on your macine then try to install programme


check from menu.
system - admin - users and groups

then use the sudo command in terminal

---

### Post by LaRoza on 2007-11-23
If you are the user you created when you installed, you will be able to do this.

---

### Post by daplat on 2007-11-30
> **MaximusTG said:**
> Ubuntu has no superuser by default, only a normal user which can gain superuser privileges by preceding a command that needs to be run as root with "sudo" (without quotes).
If you need to do a lot of things as root and don't want to bother with sudo for each command, enter

sudo su 

to become root.

The password sudo asks for is your own user password

That helped out a lot. Thnks

---

### Post by aysiu on 2007-11-30
There's no reason to log in as root to install programs.

Please tell us what program you're trying to install, and we'll help you get it installed. 

In the meantime, read these links:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Linc1 on 2007-12-02
Ok, I am an idiot because I have read down this list four times and still have no idea what your all talking about. I want to install a printer driver and I have failed every time. I get no where with terminal and if I try to execute the 'install' then it tells me I don't have root privilages.

I need more then your offering. I have followed the links and I am still were I was before I spent the last two hours getting frustrated.

real simple thing I want but no simple way to get there. Downloaded the Ubuntu Driver from Samsung for the CLP-600 Printer. And now I need it installed.

Linc

---

### Post by akiratheoni on 2007-12-02
> **Linc1 said:**
> Ok, I am an idiot because I have read down this list four times and still have no idea what your all talking about. I want to install a printer driver and I have failed every time. I get no where with terminal and if I try to execute the 'install' then it tells me I don't have root privilages.

I need more then your offering. I have followed the links and I am still were I was before I spent the last two hours getting frustrated.

real simple thing I want but no simple way to get there. Downloaded the Ubuntu Driver from Samsung for the CLP-600 Printer. And now I need it installed.

Linc

Are you sure you're using 'sudo'? Sudo should give you root privileges to execute that task.

---

### Post by Paqman on 2007-12-02
This is from the Samsung site:

> 

[Ubuntu OS Installation]
1. Download and extract the driver
2. Open ''Root Terminal''
3. Execute installation program.
$ sudo cdroot/autorun
4. After intall, PPD path is set again.
$ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung
5. Execute Configurator, and Add your printer model name by Add Printer


Notice the way the commands are prefixed with "sudo"? That stands for Super User Do, and is the command that temporarily gives you super user ( or "root") privileges. You'll be prompted for your password at first, then your upgraded privileges last 15mins.

---

