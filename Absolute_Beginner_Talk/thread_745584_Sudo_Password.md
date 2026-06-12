---
title: "Sudo Password"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by yodomino6 on 2008-04-04
Ok, I just installed Ubuntu 7.10 Server. Having some experience with OSX, I have an idea on how the sudo command works. I know typically you would type "sudo *command*" and it would prompt for your password. The problem is it is saying I'm not in the sudoers file.
I've searched other forums and they said to create a password for the root account but typing "sudo passwd root" then it will prompt me to enter a password for root. But it still tells me I'm not in the sudoers file. How do I fix this?

Thanks.

---

### Post by Oldsoldier2003 on 2008-04-04
> **yodomino6 said:**
> Ok, I just installed Ubuntu 7.10 Server. Having some experience with OSX, I have an idea on how the sudo command works. I know typically you would type "sudo *command*" and it would prompt for your password. The problem is it is saying I'm not in the sudoers file.
I've searched other forums and they said to create a password for the root account but typing "sudo passwd root" then it will prompt me to enter a password for root. But it still tells me I'm not in the sudoers file. How do I fix this?

Thanks.

only the first account added to a ubuntu install is made a meber of the admin group by default. AFter that if you want an account to have those rpivileges you have to explicitly specify that account as  a member of the admin group or give it the privilege "administer the system" in System >Administration >Users and Groups

---

### Post by yodomino6 on 2008-04-04
Well that was the first and only account to be created on the server. Any ideas?

---

### Post by Oldsoldier2003 on 2008-04-04
> **yodomino6 said:**
> Well that was the first and only account to be created on the server. Any ideas?

can you paste the output of:

```
id <yourusername>
```

---

### Post by hurtstotalktoyou on 2008-04-04
I'm pretty much a Linux newbie myself, but from what I understand sudo is not for running commands, per se, but applications--and only in Terminal.  You can run Terminal by going to Applications > Accessories > Terminal.  Then you type in:

> sudo packagename

(where "packagename" is the name of your software package (AKA the application).

It will prompt you for a password, which you must type in.  Then it will attempt to run the application.

I assume the error you're getting looks like this.  In Terminal:

> sudo: packagename: command not found

If this is the error message you're receiving, it probably means one of two things:  Either you did not install the software you're attempting to run, or the package name for that software is not what you think it is.

To find the package name, you can check Synaptic Package Manager, Google, or ubuntuforums.org.

---

### Post by Oldsoldier2003 on 2008-04-04
> **hurtstotalktoyou said:**
> I'm pretty much a Linux newbie myself, but from what I understand sudo is not for running commands, per se, but applications--and only in Terminal.  You can run Terminal by going to Applications > Accessories > Terminal.  Then you type in:



(where "packagename" is the name of your software package (AKA the application).

It will prompt you for a password, which you must type in.  Then it will attempt to run the application.

I assume the error you're getting looks like this.  In Terminal:



If this is the error message you're receiving, it probably means one of two things:  Either you did not install the software you're attempting to run, or the package name for that software is not what you think it is.

To find the package name, you can check Synaptic Package Manager, Google, or ubuntuforums.org.

not exactly. sudo (SUperuser DO)  allows you to run commands as super user.  This comes in handy when you need to move a file that belongs to someone else or edit a configuration file, etc...

Sudo allows you to act as root in a very limited way, protecting you from a lot of potential damage that could be done if you were to log into root and just start firing off commands.

---

### Post by yodomino6 on 2008-04-04
> **Oldsoldier2003 said:**
> can you paste the output of:

```
id <yourusername>
```

```
uid=1000(username) gid=1000(username) groups=1000(username),4(adm),20(dialout),24(cdrom),
25(floppy),29(audio),30(dip),44(video),46(plugdev),
104(scanner),116(lpadmin)
```

---

### Post by JoshuaRL on 2008-04-04
> **hurtstotalktoyou said:**
> I'm pretty much a Linux newbie myself, but from what I understand sudo is not for running commands, per se, but applications--and only in Terminal.

Actually, no.  The sudo command means "super user do" and is for commands.  It allows you temporary root access for commands in the Command Line Interface (CLI).  For instance:
```

sudo apt-get update

```
is a correct use of sudo since that allows the computer to run the APT command there.

For applications that do tasks needing root privilidges sudo can be used (in fact, most commands can be considered a type of program) but it's important to remember that sudo is for the CLI ONLY, not for any graphical applications.  For graphical applications you want to launch from the CLI, try gksu.  That means "graphical sudo" and make sure you don't mess up privilidges.  For instance:
```

gksu synaptic
gksu nautilus

```
are both appropriate, but 
```

gksu apt-get upgrade

```
is not.

Hope that helps.

---

### Post by Oldsoldier2003 on 2008-04-04
> **yodomino6 said:**
> ```
uid=1000(username) gid=1000(username) groups=1000(username),4(adm),20(dialout),24(cdrom),
25(floppy),29(audio),30(dip),44(video),46(plugdev),
104(scanner),116(lpadmin)
```

you need to reboot into recovery mode (you'll be root) and from there:
```

usermod -aG admin <yourusername>
```

this will sort you out

---

### Post by yodomino6 on 2008-04-04
> **Oldsoldier2003 said:**
> you need to reboot into recovery mode (you'll be root) and from there:
```

usermod -aG admin <yourusername>
```

this will sort you out

How do I get into recovery mode?

Thanks!!

---

### Post by Tatty on 2008-04-04
> **yodomino6 said:**
> How do I get into recovery mode?

Thanks!!

Reboot, then at grub there should be an option saying "recovery mode". 

It will deliver you to a CLI and you will be logged in as root.

---

### Post by Oldsoldier2003 on 2008-04-04
> **yodomino6 said:**
> How do I get into recovery mode?

Thanks!!
restart your computer and select the version of ubuntu that has (recovery mode) beside it in the grub menu

---

### Post by yodomino6 on 2008-04-04
> **yodomino6 said:**
> How do I get into recovery mode?

Thanks!!

It says:
```
usermod: unknown group admin
```

---

### Post by anjilslaire on 2008-04-04
reinstall your server would prolly be quicker, if you've just installed it and theres no admin group...

---

### Post by Oldsoldier2003 on 2008-04-04
> **anjilslaire said:**
> reinstall your server would prolly be quicker, if you've just installed it and theres no admin group...

I agree. its probably a lot easier to reinstall to fix this

---

### Post by yodomino6 on 2008-04-04
Ok. Thanks for all your help!

---

### Post by bodhi.zazen on 2008-04-04
> **yodomino6 said:**
> Ok, I just installed Ubuntu 7.10 Server. Having some experience with OSX, I have an idea on how the sudo command works. I know typically you would type "sudo *command*" and it would prompt for your password. The problem is it is saying I'm not in the sudoers file.
I've searched other forums and they said to create a password for the root account but typing "sudo passwd root" then it will prompt me to enter a password for root. But it still tells me I'm not in the sudoers file. How do I fix this?

Thanks.

Reinstall, bah that is for whimps.

Boot to recovery mode. Add you user to the admin group. I see (from your post) there is no admin group so make one, then add your user to it.

Then run visudo and add the admin group (if I recall correctly it is removing a single comment (#) from the beginning of the line).

If not see here : 

	[http://www.debian-administration.org/articles/33](http://www.debian-administration.org/articles/33)

	[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by anjilslaire on 2008-04-05
lol, 
Good for you bodhi! Keep us in line :)

---

### Post by stephanvaningen on 2008-04-05
I think by default the members of the admin-group can acquire root privileges. This is configured by a line in the file
 ```
/etc/sudoers
```

If you have a problem that you removed all your users from the admin group, you could do a small workaround to boot using the live cd, go to a gnome-terminal, then go to the mount point of your hard disk, possibly **/mnt/some-disk** where some-disk should be something you recognize (label definedwhen you formatted the disk,...)

Then, edit the file /mnt/some-disk/etc/sudoers with **visudo** and add this line:
 ```
[color=blue]user[/color]	ALL=(ALL) ALL
```
where [color=blue]user[/color] is your user id in your existing Ubuntu installation.

Save the file, exit the editor and reboot (Ubuntu LiveCD will ask to remove the CDROM and press Enter to continue: just follow these instructions and the Ubuntu on your hard disk will restart.

Now after signing on with this user [color=blue]user[/color] you can sudo again, and go to Users and Groups to add yourself again to the admin group.

Don't forget to remove [color=blue]user[/color] from the /etc/sudoers file again, just to stay with clean configuration...

Does this solve your problem?

--

**Aja**: If your admin-group is gone, no problemo: this same problem makes sure that you can re-create the admin-group with sudo-ing also...

---

### Post by bodhi.zazen on 2008-04-06
Just as an update, I checked an Ubuntu Server install and sudo access is via the admin group. So all you would need to do is boot to recovery mode and add your user to the admin group.

> user@host:~$ groups
user admin

---

