---
title: "How do I Change the Setup Username and Password"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by StGeorge on 2006-08-27
I have installed Ubuntu 6.06 on my Laptop as a Stand Alone OS.
Can anyone tell me how to change the Setup Username and Password.
I would like to have no Username and Password as I can set these up in BIOS and do not really need a Ubuntu Username and Password.

---

### Post by Pragmatist on 2006-08-27
> **StGeorge said:**
> I have installed Ubuntu 6.06 on my Laptop as a Stand Alone OS.
Can anyone tell me how to change the Setup Username and Password.
I would like to have no Username and Password as I can set these up in BIOS and do not really need a Ubuntu Username and Password.

AFAIK you must have a username.  You also need a password for when you need to administrate your computer.  Using the **sudo** command, you can run administrator-level tasks but you must provide your user password.

Having no password is extremely dangerous and defeats the essence of Linux security (or any security).  At a minimum you'd be a hazard to yourself.  If you make even one mistake when working as an administrator you can wreck your whole system.  So being root all the time is treacherous.  Even windows has seperate adminstrator and user accounts.

---

### Post by mssever on 2006-08-27
What Pragmatist says is very true. There's no way to delete all user accounts without breaking your system and making it unusable. It's the way Linux is designed. However, you can remove your password if you want--although doing so isn't recommended. If you type
```
passwd
``` you can probide a blank password. If passwd refuses to allow a blank password, then do ```
sudo passwd yourUserName
```

---

### Post by almostlinux on 2006-08-27
If you want to avoid typing ubuntu username password to logon, you can enable automatic logon for your username

This way you won't see the splash screen

---

### Post by StGeorge on 2006-08-27
I have enabled automatic login.
I would like to change my username as it was given as 'oem' automatically on install, see:

[http://www.ubuntuforums.org/showthread.php?t=242764&highlight=login+problem+username](http://www.ubuntuforums.org/showthread.php?t=242764&highlight=login+problem+username)

OK so I will enter a password for the new Username and enable Automatic Logon.
But I do need to change my Username as I feel it could be interfering with my access to shared folders on Ubuntu from my desktop which is 98SE, see:

[http://www.ubuntuforums.org/showthread.php?t=244620](http://www.ubuntuforums.org/showthread.php?t=244620)

So what I need is to access and change Username and Password.
Help would be appreciated.

---

### Post by Pragmatist on 2006-08-27
> **StGeorge said:**
> I have enabled automatic login.
I would like to change my username as it was given as 'oem' automatically on install, see:

[http://www.ubuntuforums.org/showthread.php?t=242764&highlight=login+problem+username](http://www.ubuntuforums.org/showthread.php?t=242764&highlight=login+problem+username)

OK so I will enter a password for the new Username and enable Automatic Logon.
But I do need to change my Username as I feel it could be interfering with my access to shared folders on Ubuntu from my desktop which is 98SE, see:

[http://www.ubuntuforums.org/showthread.php?t=244620](http://www.ubuntuforums.org/showthread.php?t=244620)

So what I need is to access and change Username and Password.
Help would be appreciated.

Type this in a terminal:

```
man usermod
```

This will explain about the **usermod** command.  I think the invocation you need is:

```
usermod -l new_login_name 
```

Here the -l is a lowercase L.  You put your new login name after usermod -l and that should change it.  Read the above man page for more information.

To modify your password, you use the **passwd** command  Again, to find out more, type: 
```
man passwd
```

---

### Post by StGeorge on 2006-08-27
Password is no problem as I can change that in administration.

I have tried your suggestion to change temporary username on boot in recovery. No Chance there then.
It just tells me that it doesn't exist.
Basically what I don't want to do is leave the 'oem' as a username which has admin privelages and create a new username leaving the old one there.
Why an administrator is created on install is beyond me.
Surely administration should be created after installation without having to type commands in the kernel.
So basically I still can't delete the original username and create another one.

---

### Post by Pragmatist on 2006-08-27
> **StGeorge said:**
> Password is no problem as I can change that in administration.

I have tried your suggestion to change temporary username on boot in recovery. No Chance there then.
It just tells me that it doesn't exist.
Basically what I don't want to do is leave the 'oem' as a username which has admin privelages and create a new username leaving the old one there.
Why an administrator is created on install is beyond me.
Surely administration should be created after installation without having to type commands in the kernel.
So basically I still can't delete the original username and create another one.

Please post the contents of your /etc/passwd file (don't worry, the passwords aren't displayed.  They are shown only as a single 'x')

---

### Post by mssever on 2006-08-27
> **StGeorge said:**
> Password is no problem as I can change that in administration.

I have tried your suggestion to change temporary username on boot in recovery. No Chance there then.
It just tells me that it doesn't exist.
Basically what I don't want to do is leave the 'oem' as a username which has admin privelages and create a new username leaving the old one there.
Why an administrator is created on install is beyond me.
Surely administration should be created after installation without having to type commands in the kernel.
So basically I still can't delete the original username and create another one.

The reason you have an oem account is apparently because you did an OEM install--intended for computer manufacturers only--rather than one of the normal installs. If you simply want to add another user, you can do that via System > Administration > Users and Groups. If after adding the user you want to be able to administer your computer from your account, add your new user to the admin group (from the groups tab of users and groups).

Note that Linux doesn't have administrative and limited accounts as does Windows XP. Instead, in Ubuntu all accounts are more or less limited accounts. Then different accounts can be empowered to use sudo to perform specific administrative accounts. Any user in the admin group (by default the user created during the install) can by default do anything.

Once you create a new account and add it to the admin group, you can delete the oem account if you wish.

---

### Post by msak007 on 2006-08-27
To properly complete an OEM install, you have to run

```
sudo oem-config-prepare
```

This will delete the OEM user and, on next reboot, complete the OEM installer by asking you who you are, what timezone you're in, etc. I know you want to keep the OEM user as someone with admin privileges, but when it sets up the first user with the OEM configuration tool, it'll give that user admin privileges like you want. Reference [this]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview") help page for more info.

---

